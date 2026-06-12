---
title: "complicates reflecting output from a child process"
date: 2019-09-21
forum: Programming Talk
---

### Post by Skaperen on 2019-09-21
my program needs to launch some child processes.  for each child, it needs to copy that child's output as if it had produced the output.  but rather than concurrently read every child in parallel, the output would make more sense if it started and completed copying each child without interleaving them.  i see 2 ways to do this, both copy a single child from start to finish.  one is t start the child that becomes ready first, and the other is to copy them in a fixed specific order.  in the latter case there is still a timing improvement as the processes beyond the first one are spending time in parallel to be ready to output sooner, instead of waiting for the first output over and over if parallelism were not used.

and now for the complication.  it turns out that some of the output needs to go to stderr instead of stdout.  the child process is the one producing that output and the parent process is the one actually outputting from the run of this program.  the user may be redirecting stderr and stdout differently. so i need 2 pipes from each child.  this means a simple read-then-write loop is not good enough.  i will need to read both pipes in parallel.  that means either using select/poll, or doing this with 2 threads in the parent.

i also see another solution.  just use one pipe and identify each line of output as "stdout" or "stderr" and program the parent to pick up on that and output appropriately.  that means a lot of recoding in the child to change every print call, but the parent becomes simpler.  i can cut that down to just recoding the "stderr" and not "stdout" to prefix each "stderr" line with something "stdout" output would never have, such as a leading control character byte value 0x02.  the parent would read each line and check if the leading byte is 0x02.  if not, output the line to stdout.  if so, output what follows the 0x02 to stderr.

i will be doing this in python3.

my questions are:

1.  does this make sense?

2.  do you see any pitfalls in the latter solution?

3.  can i safely eliminate output flush calls in the child of the latter solution?

4.  which method would you use?

---

