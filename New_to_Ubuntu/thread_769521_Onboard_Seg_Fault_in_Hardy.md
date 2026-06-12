---
title: "Onboard Seg Fault in Hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by WildcatWhiz on 2008-04-26
Hey forums,

I've noticed, on my Hardy machine and two others, that Onboard (the on-screen keyboard packaged with Assistive Technologies) doesn't load. In terminal "sudo onboard" gives a Segmentation Fault. 

I've tried messing around with settings in System->Preferences->Assistive Technologies but to no avail.

Any ideas?

---

### Post by Tatty on 2008-04-26
Not really a full answer for you, but these two links explain what a segfault is...

[http://www.linuxquestions.org/questions/linux-newbie-8/what-does-segmentation-fault-mean-149530/](http://www.linuxquestions.org/questions/linux-newbie-8/what-does-segmentation-fault-mean-149530/)
[http://aplawrence.com/Unixart/segmentation_fault.html](http://aplawrence.com/Unixart/segmentation_fault.html)

Usually segfaults are caused by hardware, but as you are reporting it on the same piece of software on several machines, it seems less likely to be hardware.

Hope that helps you starting off in solving this one :)

---

### Post by WildcatWhiz on 2008-04-27
/bump plz

---

### Post by sir_skiner on 2008-04-28
same thing happened to me on fresh 8.04 install.

what is strange is that onboard works fine from live cd. i'm doing another install, maybe it'll help. if not i don't know what to do. i think i'll heve to go back to 7.10 :(

---

### Post by frafu on 2008-04-28
Hello, 

onboard is working here on my system when used locally. (it does not work when I connect from a remote computer to the gnome session) 

You might try the following: 

- reinstall the software: 
-- open the Synaptic Package Manager (in menu System->Administration) and do a complete removal of onboard and python-virtkey
-- then go into your home directory and rename the .sok directory something else, so that onboard does not find it anymore. (the .sok directory is a hidden directory; nautilus (the file manager) has an option in its menus to make them visible)
-- install python-virtkey and onboard with the Synaptic Package Manager 

Hoping that this solved the problem. Otherwise you might try the following: 
- instead of letting onboard use a keyboard layout that it generates when starting up, make it use a layout stored in your home directory. The layouts are stored in a subdirectory of the .sok directory. It should be possible to create the layout files by calling onboard-settings in the terminal and by choosing to customize the layout, or something similar. I don't remember the exact procedure, but I can look it up... 

Cheers 

Francesco

---

### Post by morinpatmorin on 2008-05-08
I'm having the same problem using onboard on my laptop (a Thinkpad X61).

```

morin@shaggy:~$ onboard
Segmentation fault

```

This problem started after some update.  It seems onboard is just plain broken.

Pat

---

### Post by trinitrotoluene on 2008-05-09
Using an M1400 and I am having the same issue after updating to 8.04.  Just tried uninstalling and reinstalling onboard and python-virtkey with no luck.

---

### Post by tlawson on 2008-05-10
There's a [bug report here]("https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/220475") about a bug in python-virtkey, together with a listed fix.  I'd post more detailed instructions about how to install the patch, but I'm currently in a hurry; does anybody need it?

---

### Post by trinitrotoluene on 2008-05-14
Updates now include the fix to virtkey.  So while you are fixing OpenSSL/SSH get that update too.

---

