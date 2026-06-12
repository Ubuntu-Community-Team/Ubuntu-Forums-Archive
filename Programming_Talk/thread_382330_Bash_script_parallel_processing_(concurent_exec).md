---
title: "Bash script parallel processing (concurent exec)"
date: 2007-03-11
forum: Programming Talk
---

### Post by vinchi007 on 2007-03-11
Hi everyone, I need some help with bash scripting.

I have bash script which in the for loop goes through about 1000 hosts and retrieves MIB (snmp database) information using "getone" .

Example:

for i in hosts.file
do
getone cummunity host OID >> log
done

Now this process takes sooo long to go through sooo many hosts on the network, and what I would like to do is to run about 10 or 20 of those commands concurently in parallel, so instead of hours, it would take much quicker to get data collected.

Thank you soo much for your input and help.
PS command "getone" is the same as "snmpget".

---

### Post by thomasaaron on 2007-03-11
Maybe you could break your host.file into several parts, and run a separate instance of your program on each of them simultaneously?

---

### Post by vinchi007 on 2007-03-11
No problem splitting host file, an example would be helpful though.

My question is to how to fork "getone" command, how to run multiple instances simultaneously/concurrently/in parallel - how do I do that in bash? (and in one script)

---

### Post by lloyd mcclendon on 2007-03-12
sequential execution:
```
for i in `seq 1 100` ; do
    ping www.google.com
done
```

parallel execution:
```
for i in `seq 1 100` ; do
    (ping www.google.com &)
done
```

the & forks the process off into the background and immediately gives the control back to the calling shell.

---

### Post by Mr. C. on 2007-03-12
The background job is exactly what you want to do.  However, to control the number of background processes, you'll want to wait for some to finished before you go beyond your limit.  See :

```
man wait
```

to learn how to wait for background jobs to finish.

Read 10 or so lines at a time, and then start those processes going.  Wait for them to finish, and then send off another batch.

MrC

---

### Post by vinchi007 on 2007-03-14
Here let me give you an example of how this works.


FILE1=/tmp/indexfile

for i in `cat host` #contains about 5000 hosts!
do
index=`getmany $i community $OID1 ?awk ... >>FILE1 #saves to indexfile
for b in `cat $FILE1`  #goes through special index on sites
c=`getone $i community $OID2 |grep ...
d=`getone $i community $OID3 |grep ...
....
....
h=`getone $i community $OID8 |grep ....

j=`getmany $i community $OID9

echo $i, $b, $c, .....$j >>myfile
done
done

Now there are some calculations inside of it as well that are computing some extra $ (variables) and reported along to "myfile".

Now what I was thinking would be easiest and best is fork out this whole for loop. And how would I go about it. Also this particular box does have some old software, for example mentioned above "seq" does not work the shell.

---

### Post by Mr. C. on 2007-03-14
I would suggest making two while loops.  The following pseudo code suggests the idea:

```
maxjobs = 10

foreach line in the file {
     jobsrunning = 0
     while jobsrunning < maxjobs {
         do job &
         jobsrunning += 1
     }
     wait
}

job ( ){
   ...
}
```

MrC

---

### Post by vinchi007 on 2007-03-14
Thank you so much for this, it makes more sense this way indeed.

There is however a complication, I forgot to mention where job function is, one job is more dependent on the other:

c=`getone $i community $OID2.$b |grep ...
d=`getone $i community $OID3.$c |grep ...
....
....
h=`getone $i community $OID8.$g |grep ....

(Just an example)
What it means, that I cannot bg var c (&) because I think other vars will fail, or will they wait for previous to finish?
Example, $c,$d...,$h are all bg (&) jobs, will $d wait for $c, and will $e wait for $d?

Thanks for your help! :)

---

### Post by Mr. C. on 2007-03-14
Oh, now you say so! :-)

Once a job is backgrounded, when it starts and finishes is pretty much out of your control.  So, if you have dependencies, you'd cannot place them into the background.  If you have


D depends on A, B and C, you could background A, B and C, and then do a wait until they are completed and then launch D, and perhaps E and F, etc.

How you determine which jobs depend on other jobs wasn't disclosed, do I don't know how else to advise.  How do you know ?

The wait command w/out arguments will wait for ALL backgrounded jobs; with a job number or PID, it will wait for that specific job.  So, for the above case, you could do:

A &
B &
C &
wait PIDofA
wait PIDofB
wait PIDofC
D &

MrC

---

### Post by vinchi007 on 2007-03-17
Mr. C thanx for your thoughts and ideas, I just think it might work well. I will be trying this out on Monday :)

---

### Post by Mr. C. on 2007-03-17
You're welcome.  Let us know how it turns out!

MrC

---

### Post by vinchi007 on 2007-03-21
Ok, sorry for a delay, but I am happy (sort of) to report forking the way you described worked.
But results were not the happy ones I expected.

Well, I did not realize that it takes about 1 sec or 2 to go through the loop with snmp polling for one host device, now time that was saved with forking the for look contents was few milliseconds at best.

Let me ask you this, what would be a best/similar way to to write something like java has: linked list, where as I could dictate inside of the loop or function which object (host ip) to run? 
For example i java:

LinkedList a = new LinkedList ("...import file with hosts...")

for i in $a {
where it will run this poll for 1st host } &

for i in $a.next {
where next ip is taken from file} &

and have it put in while EOF loop, is that possibe?

Are there any data structure tutorials for scripting languages?

---

### Post by Mr. C. on 2007-03-21
Here's a rule of thumb...

Before trying to optimize anything, one needs to measure the system, and its components.

If one SNMP walk takes 1-2 seconds, and you have 1000 hosts, the fastest you can expect completion is 1000-2000 seconds.  By sending out two jobs, it will be 500-1000 seconds.  10 jobs at a time will be 100-200 seconds.  The system can easily handle far more than 10 jobs, so why not do 50-100 at a time.  That should allow completion in about 10-20 seconds.  Of course, the slowest walk with hinder execution of other jobs; so perhaps its better to keep a high / low water mark of how many jobs are running.

Changing languages, or creating alternate data structures isn't going to reduce the time of the simplest component.   If you feel the time it takes bash to startup a background job is too long, you could try measuing with dash.  If you find a significant improvement, then switch shells.  If none, you can assume the bulk of the time is in the actual SNMP walk itself.

You can read your entire hosts file into an array in bash, and send off N jobs.

Maybe I'm not understanding your issue - if not, please educate me.

MrC

---

### Post by Ole Tange on 2010-01-27
> **vinchi007 said:**
> 
I have bash script which in the for loop goes through about 1000 hosts and retrieves MIB (snmp database) information using "getone" .

Example:

for i in hosts.file
do
getone cummunity host OID >> log
done


Using GNU Parallel: [https://savannah.nongnu.org/projects/parallel/](https://savannah.nongnu.org/projects/parallel/) you can rewrite it as:

cat hosts.file | parallel getone {} community OID >> log 

If you want more than 10 simultaneous processes:

cat hosts.file | parallel -j0 getone {} community OID >> log

Watch the intro video to GNU Parallel [http://www.youtube.com/watch?v=LlXDtd_pRaY](http://www.youtube.com/watch?v=LlXDtd_pRaY)

---

