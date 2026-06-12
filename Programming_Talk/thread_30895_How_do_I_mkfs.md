---
title: "How do I mkfs?"
date: 2005-04-30
forum: Programming Talk
---

### Post by Takis on 2005-04-30
Hi duders,
As part of one of my uni classes we're making a (really, *really*) simple filing system just to learn more about working inside the kernel. We're supposed to make extensions to the system, and I'd like to port it onto a floppy. At the moment the system is just loaded into RAM as nodev. I've been told I need to write my own mkfs program and I have nooooo idea where to start. Does anybody have any pointers?

TIA

---

### Post by jerome bettis on 2005-04-30
get the source for an existing mkfs maybe?  :idea: 

what filesystem or do you get to design your own?  give us a lot more details about the specification and maybe we can help you out.

---

### Post by Takis on 2005-05-01
[QUOTE=jerome bettis]get the source for an existing mkfs maybe?.[/QUOTE]

I've been trying to find one for minix but I have no idea where to look for it. Google hasn't been much help.

The filesystem is a custom-built one that doesn't have many features at all. I don't want to put up too much about it cause I should do the work myself, but what I was wondering is what a mkfs implementation needs to be able to do.

---

### Post by banadushi on 2005-05-01
It needs to be able to:

1. Open a device
2. Write your filesysystem's structure to the device
3. Do anything else to prepare your filesystem to be mounted or otherwise used.

You might want to take a look at the source to mkdosfs from dosfstools at [ftp://ftp.uni-erlangen.de/pub/Linux/LOCAL/dosfstools](ftp://ftp.uni-erlangen.de/pub/Linux/LOCAL/dosfstools) to give you a good idea of how to start.

---

### Post by Takis on 2005-05-01
[QUOTE=banadushi]3. Do anything else to prepare your filesystem to be mounted or otherwise used.[/QUOTE]

The filesystem is mountable as nodev at the moment, so there shouldn't be anything else to do for that at the moment (is my guess).

Thanks for the pointers duders. I'll come back in about a week for a progress report.

---

### Post by Takis on 2005-05-14
Okeydokey now I can format the media (a floppy) the way I want it, but what do I need to do when it mounts? i.e. what kernel calls are made to my file system when mounting a pre-existing filesystem?

---

