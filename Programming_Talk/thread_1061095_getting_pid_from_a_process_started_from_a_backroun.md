---
title: "getting pid from a process started from a backround process"
date: 2009-02-05
forum: Programming Talk
---

### Post by wtruong on 2009-02-05
Hi,

I want to know if it is possible to grab the pid from a process that was started from a background process.  

so for instance:

start.sh&

start.sh calls server, which is the pid I want.

Thanks

---

### Post by geirha on 2009-02-05
```

$ start.sh &
$ p=$!          # $p will now contain the pid of start.sh
$ ps --ppid $p  # This should list all processes which have $p as parent pid.

```

---

### Post by lensman3 on 2009-02-06
At the command prompt type in "jobs".  It will list the just  spawned jobs.

To kill it do;  "kill %1" where the number is the number listed by the jobs command. 

"fg" for fore ground will bring a stopped jobbed or a background job back to the bash shell where you can CNTL-C it.

CNTL-Z will stop a job and "fg" will bring it back into the fore ground.

Remember, if you kill a parent job, the spawned child is called a "zombie" in Unix lingo.  The ps command will list a zombie, which can be hard to kill and remove from the queues. 

Hope this helps.

---

### Post by kerry_s on 2009-02-06
```
pidof server
```

---

