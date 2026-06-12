---
title: "Different workgroups on same lan. How to rationalize?"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2013-12-29
We have 2 windows machines in our office in a workgroup "MSHOME". 

smbtree on my old Ubuntu 10.04 machine ("oldcomputer") shows itself (but not my new computer) listed under WORKGROUP, and below: the two windows computers in MSHOME. Neither WORKGROUP nor MSHOME are indented.

Newcomputer also shows WORKGROUP and lists oldcomputer, but does not list itself under WORKGROUP, and also shows the two windows computers in MSHOME.

Is WORKGROUP the functional equivalent of MSHOME, or is MSHOME simply one "group" under WORKGROUP?

If the former, how does one change the group name for the two linux computers to MSHOME so that all four computers can be on the same network? (This of course assumes that newcomputer is also in WORKGROUP, but I do not know how to determine this.

---

### Post by Iowan on 2013-12-29
*/etc/samba/smb.conf* has a universal setting for workgroup. By default;
```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
```

---

### Post by Odyssey1942 on 2013-12-29
Have "read" through the file, Found the referenced quote at the top of the file.

So would I be correct that if workgroup = WORKGROUP was changed to:

workgroup = MSHOME

that would do it?

And if so, does my memory serve me correctly that one should always make a copy of any system file before editing in case one mucks up the intended change, so that the copy can be copied back over the mucked up edited version?

And if all correct so far, is using gedit pretty much the same as any text editor? 

Sorry for all these basic questions, but the GUI ihas been my main vehicle for getting anyting done.

Thanks.

---

### Post by bab1 on 2013-12-30
> **Odyssey1942 said:**
> Have "read" through the file, Found the referenced quote at the top of the file.

So would I be correct that if workgroup = WORKGROUP was changed to:

workgroup = MSHOME

that would do it?

Yes that is the  correct way to change what workgroup the host is in.
> 

And if so, does my memory serve me correctly that one should always make a copy of any system file before editing in case one mucks up the intended change, so that the copy can be copied back over the mucked up edited version?

It's generally a good practice to make a copy of a configuration file that you are going to alter.  It's quicker to do this from the command line```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original
```...With this command you are having root make a copy of the file in the same directory as the original.> 

And if all correct so far, is using gedit pretty much the same as any text editor?

Yes as long as you run gedit as the root user.  The smb.conf file is owned by root.  The easiest way to to this would be like this```
gksudo gedit /etc/samba/smb.conf
```
> 

Sorry for all these basic questions, but the GUI ihas been my main vehicle for getting anyting done.
Most but not all things can be done by GUI, but it is really easier and you have more control if you learn the CLI.  Some GUI tools use arbitrary settings that could be improper for your use.

 

Thanks.

---

### Post by Odyssey1942 on 2013-12-30
lowan and bab1, thanks for your guidance.

As I try to sort out my other posted problem with network visibility, I realize that I can see the Windows computers just as easily by clicking on MSHOME, without changing the work group name for the linux computers.

Is there any compelling reason to have (or not to have) them all under the same work group name, or to have them different as they are now?

---

### Post by bab1 on 2013-12-30
> **Odyssey1942 said:**
> lowan and bab1, thanks for your guidance.

As I try to sort out my other posted problem with network visibility, I realize that I can see the Windows computers just as easily by clicking on MSHOME, without changing the work group name for the linux computers.

Is there any compelling reason to have (or not to have) them all under the same work group name, or to have them different as they are now?

It's all a visual thing.  Either way will work.  At home I put all servers under the same workgroup so I can see all the shares available easily.

---

### Post by Morbius1 on 2013-12-30
And on my local network I have several machines scattered over 3 workgroups ( at the moment ). 

Is there a rational reason for doing this? No.

 I do it just so I can post this fact when someone insists that all workgroups must be the same or else Samba will not work and the earth will cease to rotate around it's sun. :D

---

### Post by bab1 on 2013-12-30
> **Morbius1 said:**
> And on my local network I have several machines scattered over 3 workgroups ( at the moment ). 

Is there a rational reason for doing this? No.

 I do it just so I can post this fact when someone insists that all workgroups must be the same or else Samba will not work and the earth will cease to rotate around it's sun. :D

+1  Good man!

Hope your having a happy holiday season @Morbius1

---

### Post by Odyssey1942 on 2013-12-30
Thank you both. Believe I will abandon this and get on to more pressing issues.

---

### Post by Morbius1 on 2013-12-30
> **bab1 said:**
> +1  Good man!

Hope your having a happy holiday season @Morbius1
I have but it's still in a state of madness around here. Most of my posts are "drive by's" these days and nothing more than comic relief like I did in this thread ;)

I hope your's was more calming.

---

