---
title: "Screen resolution issues on Toshiba netbook"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by Dagdah on 2012-05-31
I'm quite new to Ubuntu and Linux in general and have just installed Ubuntu 12.04 on a new Toshiba netbook (model: NB510-11E) and everything works fine except for the screen resolution which is fixed at 800x600 with no options to change it. I've applied all updates that were avaliable and checked for drivers but I can't find anything that helps. 
If someone could point me in the right direction I'd be so grateful, it's driving me mad having the screen all stretched out.

(Incidentally, I've had exactly the same issue when I tried it with Ubuntu netbook remix 10.10 and 10.04, as well as Linux Mint 13 which I tried on a whim but had the same issue... I have a feeling I've missed something really obvious.)

Some help would really be wonderful. Thanks.

---

### Post by shashanksingh on 2012-05-31
It would be helpful if you could post your /etc/X11/xorg.conf file and the output of the command 'lspci' so people can know your driver and your config file

---

### Post by Dagdah on 2012-05-31
Thank you for replying. 
Well, the lspci command gives me this:

[http://tinypic.com/r/20nu4p/6](http://tinypic.com/r/20nu4p/6)

I couldn't find the xorg.conf file though, at least not in the x11 folder. I'm assuming that could be part of the problem I'm having?

---

### Post by Mark Phelps on 2012-05-31
You won't see anything in additional drivers because you're using an Intel graphics chip and those drivers are only for AMD and Nvidia chips.

Most likely, the problem is that the generic intel video driver that was installed is not able to properly handle a new version of the intel video chipset.

According to Google, your netbook has the Intel GMA 3650.  You could do a search, both in the hardware section, and in the video section, to see if anyone else has posted on this chipset.

---

### Post by Dagdah on 2012-05-31
Oh I see, I think I understand. I'll have a look in the other forums then and see if anything helps.
Thanks for the advice.

---

### Post by gordintoronto on 2012-05-31
Even though this thread is about a different video chipset, the information might help you:
[http://ubuntuforums.org/showpost.php?p=11888245&postcount=13](http://ubuntuforums.org/showpost.php?p=11888245&postcount=13)

---

### Post by idoitprone on 2012-05-31
> **Mark Phelps said:**
> You won't see anything in additional drivers because you're using an Intel graphics chip and those drivers are only for AMD and Nvidia chips.

Most likely, the problem is that the generic intel video driver that was installed is not able to properly handle a new version of the intel video chipset.

According to Google, your netbook has the Intel GMA 3650.  You could do a search, both in the hardware section, and in the video section, to see if anyone else has posted on this chipset.

intel 3650 is not an intel graphic chip. It is misleading because it is a powerVR chip

Here is a thread
[http://communities.intel.com/message/156287?tstart=0](http://communities.intel.com/message/156287?tstart=0)

This was Intel's mistake by letting powerVR graphics in their chipset. Now, Linux users are mad because Intel cannot opensource their drivers. This will change on the next iteration of their atom chips.

OP start begging Intel and PowerVR. Go and write on their thread.

---

### Post by NikTh on 2012-06-01
> **idoitprone said:**
> intel 3650 is not an intel graphic chip. It is misleading because it is a powerVR chip

Here is a thread
[http://communities.intel.com/message/156287?tstart=0](http://communities.intel.com/message/156287?tstart=0)

This was Intel's mistake by letting powerVR graphics in their chipset. Now, Linux users are mad because Intel cannot opensource their drivers. This will change on the next iteration of their atom chips.

OP start begging Intel and PowerVR. Go and write on their thread.

wow ! 
I didn't know anything about it. 
Thanks for info .. 
Your answer went to my bookmarks. 

What if he try to install a newer version of **xserver-xorg-video-intel** ? 
I mean from x-edgers ppa .

---

### Post by idoitprone on 2012-06-01
> **NikTh said:**
> wow ! 
I didn't know anything about it. 
Thanks for info .. 
Your answer went to my bookmarks. 

What if he try to install a newer version of **xserver-xorg-video-intel** ? 
I mean from x-edgers ppa .
unless that has a powerVR sgx545 linux graphic driver
then dont bother

fastest way is to beg intel or powervr

---

### Post by Dagdah on 2012-06-01
> **gordintoronto said:**
> Even though this thread is about a different video chipset, the information might help you:
[http://ubuntuforums.org/showpost.php?p=11888245&postcount=13](http://ubuntuforums.org/showpost.php?p=11888245&postcount=13)

I've had a look and I'll definitely give this a go and see what happens, thanks for the pointer.
 
 
> **idoitprone said:**
> intel 3650 is not an intel graphic chip. It is misleading because it is a powerVR chip

Here is a thread
[http://communities.intel.com/message/156287?tstart=0](http://communities.intel.com/message/156287?tstart=0)

This was Intel's mistake by letting powerVR graphics in their chipset.  Now, Linux users are mad because Intel cannot opensource their drivers.  This will change on the next iteration of their atom chips.

OP start begging Intel and PowerVR. Go and write on their thread.

I see, I didn't know any of that. So does this mean there's not much I can do at the moment then (apart from begging intel and powerVR, which I'll get onto shortly)? 

Thanks everyone for the advice, really appreciate it.

---

