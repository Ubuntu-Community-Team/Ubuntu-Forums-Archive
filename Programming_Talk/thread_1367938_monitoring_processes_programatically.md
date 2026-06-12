---
title: "monitoring processes programatically"
date: 2009-12-30
forum: Programming Talk
---

### Post by idigitall on 2009-12-30
Hi, I'm not sure if this is the correct forum to post this but...

I have a script that launches two processes (process data) into the background simultaneously.
I have another script that also launches two (different) processes (generate graphs) into the background, simultaneously.
The second script can only be run when the first two processes are complete.
How can I check, in one script that controls it all, when the first two processes are done so that the next two processes can be started?

I'd prefer this done in a bash script..

---

### Post by kwyto on 2009-12-30
execute the processes that generates the data first then execute the other two later. also, look at concurrent programming. may give a little insight in the matter.

---

### Post by idigitall on 2009-12-30
yeah thanks but I don't want to rewrite stuff concurrently.

I just want a bash script way of:
./launch1.sh  &      (save process id  in pid1)
./launch2.sh &        (save process id in pid2)
while ((kill -0 pid1 != 1) && (kill -0 pid2 !=1)) 
            sleep(5 minutes)
wend
./launch3.sh &
./launch4.sh &

I just don't know which bash commands return the processid and can be used the way I need. If anyone else has an idea, a reply would be much appreciated.

---

### Post by kwyto on 2009-12-30
pid=$! //pid of the last process ran 
 pid=$$ //pid of the current process 

check this [tutorial]("http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/internalvariables.html")

---

### Post by idigitall on 2009-12-30
great tut, thanks

---

### Post by sujoy on 2009-12-30
rather you can redesign your first script for a pre-exit hook, and attach the second script to that

---

