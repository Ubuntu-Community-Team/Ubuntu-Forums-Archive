---
title: "Capture Child process exit"
date: 2010-07-26
forum: Programming Talk
---

### Post by ak_saravanan on 2010-07-26
hi,

Not sure if this is a good place to ask unix shell scripting question.

I have a job that spawns multiple child processes in background.. Catch is i want to wait for some jobs to finish before i spawn more background processes. (each job creates a file and deletes at the end of it . so i don't want start new jobs after x amount of disk size is used up)

now, i setup trap 
trap  child_exit_handler CHLD
to increment and decrement a counter. but this traps executes only once for any number of child exits. Can somebody shed light what mistake i am doing. or a better way to do this.

here is my actual program.
I wanted to increment / decrement TOTAL_PROC variable . since i can't change this inside child job, i am trying to increment before child starts and decrement when child exits.


```
#!/bin/ksh

set -o monitor # must set to invoke CHLD signals

typeset -i TOTAL_PROC
function do_child
{
echo "ENTER CHILD $PPID with total  $TOTAL_PROC"
sleep 5
echo "Exit CHILD $PPID total $TOTAL_PROC "
exit 0
}

function child_exit_handler
{
echo "Enter child handler total $TOTAL_PROC "
(( TOTAL_PROC  -=  1 ))
echo "Exit child handler total $TOTAL_PROC "
}

TOTAL_PROC=0

LOOP_COUNT=0
MAX_COUNT=$1

typeset -x COPID=

echo "ENTER WHILE $$ at `date`"

while [[ $LOOP_COUNT < $MAX_COUNT  ]]; do

echo "LOOP IS $LOOP_COUNT , $MAX_COUNT"

(( TOTAL_PROC  += 1 ))
do_child  & COPID="$COPID $!"  # capture PID of coprocess
trap  child_exit_handler CHLD

echo "Inside while total $TOTAL_PROC "
(( LOOP_COUNT  += 1 ))
done
echo "Outside while total before wait $TOTAL_PROC "

wait
echo "Outside while total after wait $TOTAL_PROC "
echo "EXIT WHILE $$ at `date`"

```

---

### Post by gmargo on 2010-07-26
I tested this under bash, not ksh, so YMMV.

The main problem I found was the while loop test using "<" within [[...]].  This is for a textual comparison, instead you should use "-lt" for integer comparison.  Under bash, with the "<", it only spawned two processes.  With the "-lt" it spawned all 10 I asked for.

---

### Post by ak_saravanan on 2010-07-26
thanks for your reply. but in ksh comparison symbol <  , just works fine . see how the output looks like
ENTER WHILE 11201 at Mon Jul 26 16:06:59 EDT 2010
LOOP IS 0 , 3
last child id 11201
Inside while total 1 
LOOP IS 1 , 3
ENTER CHILD 11203 with total  2
ENTER CHILD  with total  1
last child id 11201
Inside while total 2 
LOOP IS 2 , 3
ENTER CHILD 11204 with total  3
last child id 11201
Inside while total 3 
Outside while total before wait 3 
Exit CHILD  total 1 
Exit CHILD 11204 total 3 
Exit CHILD 11203 total 2 
Enter child handler total 3 
Inside handler child   parent 11201 
Exit child handler total 2 
Outside while total after wait 2 
EXIT WHILE 11201 at Mon Jul 26 16:07:04 EDT 2010


what i expecting is, "Outside while total after wait " to be zero at the end of loop.  if trap had worked for each of the child, it would have been, but here it trap runs only once. 


thx

PS: i even changed to -lt and its same resutls .

---

### Post by gmargo on 2010-07-27
The more I played with it, the more confusing it became.  I'm convinced that I'm getting more SIGCHLDs than I expect.  Probably due to backgrounding a shell function instead of a command, but still it was difficult to keep track.  And there does not seem to be a way for either the signal handler to know what child quit, or have the wait function return on every child.  

I highly recommend that you try this loop in Perl instead of the shell.  There you'll have full access to the process ids and exit statuses; keeping track via signals would be much easier.

---

### Post by ak_saravanan on 2010-07-28
thanks for your replies.

what i found was, trap is just active for the first child exit.
it seems to be inactivated after that.

when i put my background process in serial it captures eachchild exit. 

while loop
do

trap child_handler CHLD
do_job&
wait

done

this just works fine , i.e for each child exits is captured. but it doesn't serve my purpose.  i wish if trap continue to be active until whole program exits.. 

anyway, for now, i am working around creating a inner while loop for number of background process can be up at any given  time , so i am kind of solved my problem with a workaround.
something like this
while loop
do
       while `jobs |wc -l` > $MAX_PARALLEL_JOB 
        do
          sleep 2
         done
do_job&
done
wait


thx

---

