---
title: "Compiling init sequence"
date: 2007-05-16
forum: Programming Talk
---

### Post by adelgado on 2007-05-16
I don't know if the right place to say his is here, but anyway; you can just move the thread if you feel I misposted it...

The thing is: I was wondering, the init scripts that boot up the computer are just a series of specially ordered bash scripts that call (usually) small applications to perform boot-time tasks.

If we could ompile these scripts into a single executable binary, couldn't we get a way faster init?

I tried to search google for this, but I didn't find anything...



Well, this is it... Thanks in advance for the answers...

---

### Post by seamless on 2007-05-16
Init would be faster if it was one large compiled executable written in a language like C. However, like you said it is currently a bunch of little files that are called in a specific order. Having it as multiple files allows for you to easily change what is called in the init process. By putting it all in one compiled application then to make any changes to the init process you would have to modify the source and re-compile init. Meaning the process is hard to change and a nightmare to maintain. Every system configuration would have to have their own version of the source specifically modified for that specific system. It is a sacrifice of speed for maintainability and configurability.

---

### Post by FuturePast on 2007-05-16
The phrase "false economy" seems apt.

---

### Post by adelgado on 2007-05-17
> **seamless said:**
> Init would be faster if it was one large compiled executable written in a language like C. However, like you said it is currently a bunch of little files that are called in a specific order. Having it as multiple files allows for you to easily change what is called in the init process. By putting it all in one compiled application then to make any changes to the init process you would have to modify the source and re-compile init. Meaning the process is hard to change and a nightmare to maintain. Every system configuration would have to have their own version of the source specifically modified for that specific system. It is a sacrifice of speed for maintainability and configurability.

I though about that...

And what if the system was automatic? I though about it this way: Instead of being a folder (/etc/init.d) it could be a tar file, such as (/etc/init.d.tar). This way, you could easily track any changes to the file.

The first time it would boot, it would compile the files, and then it would only boot the same compiled binary, until it detecs that /init/init.d.tar has changed. If /etc/init.d.tar changes, it would re-compile and boot the newly-compiled binary.

In the event of a compile error, it would then boot the last working compile...

I wasn't thinking of an C implementation of init, or something like that. I was thinking of actually compiling the bash files...


Thanks for the answers...

---

### Post by seamless on 2007-05-17
[QUOTE="adelgado"]I wasn't thinking of an C implementation of init, or something like that[/QUOTE]
I think you are a bit confused on how the init process works. /sbin/init is written in C. It is the first process that run and looks in specific places on the disk namely /etc/rcX.d depending on the run level it is in and runs those files. The speed decrease comes from the context switches to call the shell interpreter for the application init scripts and to a lesser extent to the length of the script itself.

[QUOTE="adelgado"]I was thinking of actually compiling the bash files[/QUOTE]
Compile it to what exactly? The reason shell scripting is used is because it's easy to work wtih, it can easily change the environment and a lot of people know it. You could change all the scripts to another language and then compile them down.

The only way you are going to get any real benefit is if you remove the context switches to the shell interpreter. If you change it to lets say Python (being that you can generate .pyc files) you still have that switch which is where the majority of the time is lost. The only way you are going to get any real savings is by having everything in C which once again is a nightmare to maintain. This would also require a rewrite of all the entire init process as wells as a rewrite of all the application init scripts. Not to mention that it would still be modular and require context switches to read the compiled files which is where the majority of the slow down comes from.

---

### Post by adelgado on 2007-05-17
> **seamless said:**
> I think you are a bit confused on how the init process works. /sbin/init is written in C. It is the first process that run and looks in specific places on the disk namely /etc/rcX.d depending on the run level it is in and runs those files. The speed decrease comes from the context switches to call the shell interpreter for the application init scripts and to a lesser extent to the length of the script itself.


Compile it to what exactly? The reason shell scripting is used is because it's easy to work wtih, it can easily change the environment and a lot of people know it. You could change all the scripts to another language and then compile them down.

The only way you are going to get any real benefit is if you remove the context switches to the shell interpreter. If you change it to lets say Python (being that you can generate .pyc files) you still have that switch which is where the majority of the time is lost. The only way you are going to get any real savings is by having everything in C which once again is a nightmare to maintain. This would also require a rewrite of all the entire init process as wells as a rewrite of all the application init scripts. Not to mention that it would still be modular and require context switches to read the compiled files which is where the majority of the slow down comes from.

I understand (most of) how the init process works.

When I say compile, I mean using some sort of program that would transform the bash script in some kind of language than can be compiled (like C o even Python), without any human interaction...

---

### Post by FuturePast on 2007-05-17
[CCshTM, "The Bourne Shell Compiler"]("http://www.comeaucomputing.com/faqs/ccshlit.html") - it's not free.

Anyway, sysv scripts will not last very long given that Ubuntu developed [Upstart]("http://upstart.ubuntu.com/") specifically to get rid of them.

---

### Post by seamless on 2007-05-17
> **adelgado said:**
> I understand (most of) how the init process works.

When I say compile, I mean using some sort of program that would transform the bash script in some kind of language than can be compiled (like C o even Python), without any human interaction...
The issue is not so much the speed of running the init script but the context switch that calls the init script or in this case the compiled script. Even compiling it will not remove this. Running in a serial and calling a separate program is where most of the slow down comes from. Converting from a script to a binary file will only give you a marginal benefit.

---

### Post by FuturePast on 2007-05-18
> **seamless said:**
> The issue is not so much the speed of running the init script but the context switch that calls the init script or in this case the compiled script. Even compiling it will not remove this. Running in a serial and calling a separate program is where most of the slow down comes from. Converting from a script to a binary file will only give you a marginal benefit.
Not that I'm too bothered about making boot time faster, but is there some concrete reason that you know this to be true (i.e. you've measured it?)
Forking processes is *extremely* efficient in Linux, and I can almost guarantee that it's IO combined with running the scripts consecutively that causes boot times to be as long as they are.

When upstart is fully implemented so that services are brought up as and when needed and the dependencies between them taken into account, I'm sure we will see far greater improvements in boot time.

---

### Post by seamless on 2007-05-18
> **"FuturePast"]with running the scripts consecutively that causes boot times to be as long as they are.[/QUOTE]
I did say above that running the scipts in serial is a major reason why init is so slow.

[QUOTE="FuturePast"]is there some concrete reason that you know this to be true (i.e. you've measured it?)[/QUOTE]
I have to an extend. Here is a simple example demonstrating. Lets take two files. One if a bash script and one is a C program. Both are empty all they is start then stop without running any instructions. This will show not execution time but time it takes to start and stop the application based on the context switch to them. *Note all times are averages over five trials.

First the bash script
```
#!/bin/sh
```

Then the C program
```
int main()
{
        return 0 said:**
> When upstart is fully implemented so that services are brought up as and when needed and the dependencies between them taken into account, I'm sure we will see far greater improvements in boot time.
Upstart when it's no longer being used in SysV compatibility mode will provide a large benefit. No arguing that but this is mainly from the event driven model it uses vs the serial execution model of SysV.

> **&#8221 said:**
> Forking processes is extremely efficient in Linux,
The original question was about compiling the init scripts themselves for a speed benefit not about using an alternative init or forking an existing one. Which will not give you much of a benefit because execution speeds are very close between C and sh in the case of init scripts but the time is wasted in a context switch between init and the script that is calling the application not the execution speed of the shell interpreter. Meaning compiling down will give you little to no benefit because even the time from the context switch between sh and a C program is tiny.

---

### Post by FuturePast on 2007-05-18
Thanks for your comprehensive explanation.

It's clear, then, as we've both pointed out, that the effect of C vs. script, fork vs context switch etc.
plays very little role in the speed of booting.

---

### Post by adelgado on 2007-05-19
Thanks for the attention, and for the comprehensive explanation.

I see now that it would be a little-to-no benefit thing, compiling the crpits in the init sequence.

About Upstart, does it still runs in SysV compatibillity mode in 7.04? If it does, will it start to run by default in no-compatible mode in 7.10?

---

### Post by seamless on 2007-05-19
Scripts in /etc/init.d are SysV scripts and are run in compatibility mode. The ones in /etc/event.d are not. It is a matter of getting the scripts converted to the new format more than anything else. Slowly SysV scripts will be converted. It is a slow and tedious process that few people actually want to take the time to do. Eventually compatibility mode will not be used (it will be there just in case but nothing in the repos will need it). Upstart is designed that it doesn't have to be in "upstart mode" or SysV mode. It is designed to be able to run scripts in both modes. That way one SysV script won't throw off the entire init process and they don't have to be convered all at once.

---

