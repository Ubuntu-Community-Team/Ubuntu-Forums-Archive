---
title: "I ran the dmesg command. Oh boy"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by vanhenryjr on 2011-09-25
I am working with ubuntu a few weeks and have a book (Unbuntu Unleashed). They mention that after you install to run dmesg and discover unseen problems. I run and save as a text file and I have "pages" of results. 794 lines to be exact! 

Now what? I need to work through this one line at a time? How do I know what is important and what is not important? If I need to correct all these I think a reinstall sounds much more reasonable.  

I know of a few problems (can't get kubuntu to start, goes into suspend/hibernate and won't come out without unplugging the computer, occasional crashes) but things seem otherwise ok. 

btw, I tried to attach the txt file, but it is over 50 kb, well about the 19 kb limit for text files.

---

### Post by Toz on 2011-09-25
Don't let dmesg scare you. It's nothing more than a log file and the information contained in that log file isn't necessarily errors (the file also contains  informational-type messages). The only time you would review this file is if you're having a specific problem - there may be a hint to help with troubleshooting. 

So....Are you having a specific problem that you need to troubleshoot?

---

### Post by tgalati4 on 2011-09-26
dmesg | grep error
[ 3792.409917] nautilus[3430]: segfault at b571bd50 ip b571bd50 sp bfa98a9c error 4 in 7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2[b6079000+2000]
[ 7573.582890] ipw2200: Firmware error detected.  Restarting.
[44353.994946] ipw2200: Firmware error detected.  Restarting.


Right after you boot up, searching for "error" will turn up things that the kernel is having problems with.  For me, when suspending my laptop, it has to reload the firmware for the wireless card--which is not always successful.  Could be a timing issue during rewaking.  So you look for the wakeup script and add some sleep statements.  Post what errors that you find and others can weigh in on what needs fixing and what can be ignored.

You can also search for:

dmesg | grep Error
dmesg | grep info
dmesg | grep Info
dmesg | grep Warn
dmesg | grep warn

Dmesg is the first tool to use when something fishy is happening.  It's like lifting the hood of a car when you hear a strange rattle.

To page through the file:

dmesg | more 

or

dmesg | less   (so you can go backwards and forwards through the file)

Plug in a USB device then:

dmesg | tail -20

That will give you the last 20 lines to see how your USB device is handled.

Run in a terminal to monitor real time:

dmesg | tail -f

Now plug in your USB device and see the messages scroll as they happen.  Good for troubleshooting keyboards or other intermittent hardware problems, like a failing hard disk.

---

