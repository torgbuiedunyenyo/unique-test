# unique-test

Writeup of the results of this experiment can be found here: https://handshakefyi.substack.com/p/which-llm-produces-more-unique-ideasaccording

In this analysis, a writer model produced an output, which was accepted or rejected by a judge model.

Each experimental run began with the writer model producing a baseline output. This was sent to the judge model. If the output was not accepted, the first model would iterate once on the output, and return the new output to the judge model for another evaluation. The writer model would have 5 chances to improve the output after creating the baseline output (so 6 iterations total). If the output was accepted, then the experimental run stopped and a new one began.

Multiple rows with the same experimental ID are considered the same trial (the same experimental run).

The experiment column refers to the number of the overall experimental run.
The iteration column refers to the iteration within the experimental run. The column is base 0, so every baseline output will have an iteration number of 0. These numbers increment until the output is accepted by the judge model, or the iteration number reaches 5, whichever comes first.

improvements_to_acceptance will have a -1 value if the output of the writer model was never accepted, even after 6 iterations.

was_accepted refers to whether any iteration within an experiment was accepted, not whether the specific iteration was accepted. is_iteration_accepted refers to whether the specific iteration was accepted.

So, to reiterate:
Every experiment started with generating a baseline output at iteration 0. This was sent to a judge model. So if the baseline output was accepted, the experiment would end and new one would begin. If it was not accepted, the experiment would continue to iterate until acceptance.

So the highest iteration number for an experiment ID will either be the iteration that was accepted OR it will be 5. If it is 5, it either means that the output was accepted after 5 improvements, or it means that no output from the writer was accepted by the judge within that experiment.

Experiments that have a different experiment_type have different configurations. So if an experiment ID=1 but the experiment_type column is different, it means that they were different experiments with different judge prompts.