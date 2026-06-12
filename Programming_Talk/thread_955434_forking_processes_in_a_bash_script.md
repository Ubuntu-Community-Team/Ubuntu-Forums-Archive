---
title: "forking processes in a bash script?"
date: 2008-10-22
forum: Programming Talk
---

### Post by silver_lynx on 2008-10-22
Hi everyone, 

in a bash script, can I fork several processes and wait until they are done? Like:

process1 &
process2 &

wait until the processes are done

process3 

any help would be great!

---

### Post by wd5gnr on 2008-10-22
Sure. wait makes the shell wait for all subprocesses.

So:

#!/bin/bash
foo &
bar &
wait
foo_bar

Does what you want. You ought to be able to do something with a subshell too like:

( foo & bar ) && foo_bar

I think that's right but its early still too.

---

### Post by silver_lynx on 2008-10-22
thanks wd5gnr!

it worked, both ways :)

---

### Post by wd5gnr on 2008-10-22
Guess I wasn't as sleepy as I felt.

---

