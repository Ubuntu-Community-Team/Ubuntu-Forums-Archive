---
title: "how much cpu and ram is using a linux command"
date: 2010-01-15
forum: Programming Talk
---

### Post by Sycron on 2010-01-15
I want to see the sistem resources used by a console application. For example I wish to know how much cpu and ram was used for compressing some images like:```
zip -0 -o a.zip *.jpg
```.
I tried with time and ps but I ended doing nothing.

I used the example from man page```
time -f "%E real,%U user,%S sys" ls -Fs
``` but i got ```
-f: command not found

real	0m0.441s
user	0m0.344s
sys	0m0.080s
```.

Any help is good.

---

### Post by blur xc on 2010-01-15
Try top or htop (need to intall that one)...

BM

---

### Post by denarced on 2010-01-15
You should have read man more carefully
```

To  run  the command ‘ls -Fs’ and show just the user, system, and total
       time:
            time -f "%E real,%U user,%S sys" ls -Fs

       To edit the file BORK and have ‘time’ append the elapsed time and  num&#8208;
       ber  of  signals  to the file ‘log’, reading the format string from the
       environment variable ‘TIME’:
            export TIME="%E,%k" # If using bash or ksh
            setenv TIME "%E,%k" # If using csh or tcsh
            time -a -o log emacs bork

       Users of the bash shell need to use an explicit path in  order  to  run
       the  external time command and not the shell builtin variant. On system
       where time is installed in /usr/bin, the first example would become
            /usr/bin/time wc /etc/hosts

```

notice where it says "users of the bash shell" blaa blaa..
if I run:
```

denarced@deskUbu:~$ whereis time
time: /usr/bin/time /usr/include/time.h /usr/share/man/man7/time.7.gz /usr/share/man/man1/time.1.gz

```
so your command should be:
```

/usr/bin/time -f "%E real,%U user,%S sys" ls -Fs

```

Hope you understand my explaining
good luck

---

### Post by Axos on 2010-01-15
You have to explicitly use /usr/bin/time otherwise you get the shell built-in command instead.

It looks like Linux does not track the memory usage because here's the output using the -v option (everything) and all the memory stats are zero:

        Command being timed: "md5sum -c Music.md5sum"
	User time (seconds): 58.46
	System time (seconds): 11.68
	Percent of CPU this job got: 48%
	Elapsed (wall clock) time (h:mm:ss or m:ss): 2:26.05
	Average shared text size (kbytes): 0
	Average unshared data size (kbytes): 0
	Average stack size (kbytes): 0
	Average total size (kbytes): 0
	Maximum resident set size (kbytes): 0
	Average resident set size (kbytes): 0
	Major (requiring I/O) page faults: 0
	Minor (reclaiming a frame) page faults: 234
	Voluntary context switches: 55982
	Involuntary context switches: 448
	Swaps: 0
	File system inputs: 15728776
	File system outputs: 0
	Socket messages sent: 0
	Socket messages received: 0
	Signals delivered: 0
	Page size (bytes): 4096
	Exit status: 0

---

### Post by dwhitney67 on 2010-01-15
> **Sycron said:**
> I want to see the sistem resources used by a console application. For example I wish to know how much cpu and ram was used for compressing some images.
It appears that you have received some responses.  Great!

Now, I would like to ask why do you want to know this information?  Are you doing this for school work?  I ask this because it is not a typical question.  Please continue reading...

Are you going to write a dissertation based on the information you have been offered?  Are you going to alter your weekend activities bases on the responses so far?

Seriously, what do you expect to yield from the responses given? As the "devil's advocate", what are you hoping to yield from your query?

Unless you plan to implement your own algorithms/utilities, instead of those provided by the "system", what is it that you are striving to accomplish?  Are you hoping to acquire knowledge that on my puny little system, it take 5 milliseconds to accomplish something, whereas on Richie Rich's system it take 5 nanoseconds?  Seriously, what does this information buy you?

Ok, on the other end, perhaps you meant to ask another question, and your first did not come across correctly.

---

### Post by Sycron on 2010-01-16
I love my photos, I don't want them to be stealed. I thought about making something to protect them.

I don't want to tell how it works, as it helps discovering how to bypass this, but however it doesn't matter now. 

In a folder, I have the photos, and users login on the site and download them. Before downloading, in one exif tag of each photo is added the hash of the user requesting the download. After that the photos with exif modified are zipped, and this process takes time. Editing exif takes time too.

For 63 photos, 1.2mb each, first download request the results are:```
Md5ing in 2.398s.
Zipping in 1.819s.
Total: 4.217s.
```
For the second request the times are considerably smaller, and I don't understand why.
```
Md5ing in 0.757s.
Zipping in 0.587s.
Total: 1.344s.
```

Getting over this, the system resources are limited, for example the ram is on the edge. Other problem is that I don't want users to wait for the zipping process, and I thought that is a good idea to start zipping and download onthefly, while zipping, but for the moment is just an idea.

Thanks blur xc, denarced, axos, dwhitney67 for responses.

---

### Post by dwhitney67 on 2010-01-16
> **Sycron said:**
> 
For 63 photos, 1.2mb each, first download request the results are:```
Md5ing in 2.398s.
Zipping in 1.819s.
Total: 4.217s.
```
For the second request the times are considerably smaller, and I don't understand why.
```
Md5ing in 0.757s.
Zipping in 0.587s.
Total: 1.344s.
```

The apps that you are using to accomplish the MD5 and Zipping are probably loaded into RAM on the first pass; this takes some time to load.  For the second pass, since they are already in RAM, the process possibly (and evidently) goes faster.

Utilizing all of the available RAM on a computer is a good thing, because it makes apps run faster.  The main issue to worry about is when a new application (that is not currently sitting in RAM) is launched.  This forces the OS to arbitrarily copy the memory used by an existing application to the "swap" space on your HDD.  This is awfully slow.  Subsequently, if the app whose contents have now been written to swap needs to continue running, the OS does the opposite; it restores the swapped application, but moves another app to swap.

If you notice that the swap space is used a lot on your system, it is probably time for you to upgrade the system with more RAM, or consider running less applications.

---

### Post by Zugzwang on 2010-01-16
It's still an interesting question, though: Why isn't the "time" utility able to determine the peak memory consumption of an application?

I see such values in computer science papers comparing different solution techniques (and implementation) for certain problems a lot, but I've never seen a way to obtain these in Linux.

---

### Post by Axos on 2010-01-16
If you are concerned about how certain programs (like file archivers) affect other users on a multi-user system, run those programs with the "nice" command. Nice runs a program with lower scheduling priority. So if other people are running programs which use a lot of CPU, your program won't get any time slices until no other higher-priority process needs them. This indirectly reduces the memory impact of your program as well since it won't be scheduled as often. It will still have some impact in a memory-constrained situation but it will be reduced. Your only other option is not to run the programs you are concerned about at all.

---

