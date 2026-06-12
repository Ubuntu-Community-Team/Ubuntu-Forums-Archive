---
title: "How to parallel several jobs in bash"
date: 2009-07-14
forum: Programming Talk
---

### Post by flylehe on 2009-07-14
Hi,

(1) I wonder how to in a bash script(or other languages if more convenient) manage independent jobs(executables with command line arguments) and make them run in parallel? 

(2) If there is a way to create several sub-process without waiting them to finish, will it paralleling the sub-processes? If not how to?

(3) If open a terminal for each task to execute it, will Linux automatically make full use of its own resources to parallel these tasks? Is this same as above "create several sub-process without waiting them to finish"?

(4) Which one is faster: multi-threading or multi-process?

Thanks and regards!

---

### Post by lavinog on 2009-07-14
> **flylehe said:**
> Hi,

(1) I wonder how to in a bash script(or other languages if more convenient) manage independent jobs(executables with command line arguments) and make them run in parallel? 

(2) If there is a way to create several sub-process without waiting them to finish, will it paralleling the sub-processes? If not how to?

(3) If open a terminal for each task to execute it, will Linux automatically make full use of its own resources to parallel these tasks? Is this same as above "create several sub-process without waiting them to finish"?

(4) Which one is faster: multi-threading or multi-process?

Thanks and regards!

1-2: the using *&* at the end of a command will put it in the background
Bash will store the pid of the backgrounded app in the variable *$!*
the command *wait * will wait for all backgrounded apps to complete. *wait $pid* where $pid is the variable that holds the pid of a backgrounded app will only wait for that app to finish.
ex:
```

fun1(){
 for x in {1..9}
 do
  echo $x
  sleep 1
 done
}

fun2(){
 for x in {21..25}
 do
  echo $x
  sleep 1
 done
}

fun1&
pid1=$!

fun2&
pid2=$!

wait $pid2
fun2&
wait
echo 'all done'

```

3: Yes

4: It really depends on the task. Some tasks can only be single threaded tasks. If the task involves analyzing data in a particular order, then multi-threading might not be an option. If you have multiple files that need to be analyzed, then you can spawn multiple processes for each file .

When spawning multiple processes, you should be aware that it is easy to spawn too many processes. If you use up all of your physical memory, your system can become unresponsive. If you have a quad core processor, you should keep the number of simultaneous operations to 4 or less.

---

### Post by lisati on 2009-07-14
Although not specific to Ubuntu or Bash, [this]("http://en.wikipedia.org/wiki/Computer_multitasking") makes for interesting reading

---

### Post by Ole Tange on 2010-06-14
GNU Parallel [http://www.gnu.org/software/parallel/](http://www.gnu.org/software/parallel/) is a general solution to running jobs in parallel in bash.

See the intro video: [http://www.youtube.com/watch?v=LlXDtd_pRaY](http://www.youtube.com/watch?v=LlXDtd_pRaY)

---

### Post by geirha on 2010-06-14
This explains how to run processes in parallell in bash, and the limitations. [http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)

---

