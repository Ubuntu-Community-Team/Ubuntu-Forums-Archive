---
title: "Stuck on purple screen"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by holywhistler on 2011-10-31
Hello,

So here is my case, I recently upgraded from 11.04 to 11.10 and I am experiencing some booting problems. 

when I turn my laptop on (Compaq Presario V3000 with Nvidia Geforce 7150m, code C67) I get to a purple screen and cannot move from it, if I restart the pc I get the grub screen to choose from Linux 3, Linux 3 (recovery version) and the memory tests. I would obviosly choose the first options, which takes me to a black screen with a blinking cursor, after a couple of seconds I am taken to the Busy Box/initramfs (before with 11.04 I always had to boot from previous linux version which would as well would take me to initramfs there i would just wait a couple of minutes, type exit and get a login screen) now however when I type exit I just get the same initramfs over and over, then after a couple of seconds I would automatically display some lines saying some <process killed by signal 9> things, I would wait till that stops, then I would again type exit and finally I get a login screen and I can access my system. I been using this "process" for the past couple of days while trying some grub editing tips with no results, I tried adding a lot of different words to GRUB_CMDLINE_LINUX_DEFAULT= with no results.

I had some similar issues with 11.04, since I always had to boot from an old linux version to get a desktop otherwise I would just gets stuck on the same purple version.

Now with 11.10 because of the upgrades I lost all the other linux versions so is Linux 3 or nothing.

Please help me with this. I love ubuntu with my heart but is a little frustrating to get this booting problems.

Thanks!

---

### Post by holywhistler on 2011-10-31
sorry to bump so early, anyone?? any help??

---

### Post by holywhistler on 2011-10-31
I guess there is no resolution to this issue.
 
I'll have to deal with it till I buy a new PC, hope I can do that soon.:(
 
Thanks!

---

### Post by Norm24 on 2011-10-31
Backup /home and do a clean install.Upgrades have always been undependable.

---

### Post by holywhistler on 2011-10-31
thanks for your reply, the first time I upgraded from 11.04, second and third times I performed a clean install and the problem persisted.

---

### Post by F.G. on 2011-10-31
> **Norm24 said:**
> Backup /home and do a clean install.Upgrades have always been undependable.
yeah, i agree. i think if your getting as far as grub your hardware is probably fine (i suppose there could a hard disk fault, but it's probably something else). i'd certainly not rush to pcworld just yet.

I'd try booting from a live cd or usb, copy the data you need or want to a separate location, and then do a fresh install.

I'm sure that the issue could probably be fixed, but that sounds like a lot more hassle than just reinstalling it.

---

### Post by F.G. on 2011-10-31
> **holywhistler said:**
> thanks for your reply, the first time I upgraded from 11.04, second and third times I performed a clean install and the problem persisted.
that's interesting, so you can use 11.10 from a live disk, but then not when it is installed?

---

### Post by holywhistler on 2011-10-31
I can use it after going to through the whole process of:
 
> I get the grub screen to choose from Linux 3, Linux 3 (recovery version) and the memory tests. I would obviosly choose the first option, which takes me to a black screen with a blinking cursor, after a couple of seconds I am taken to the Busy Box/initramfs, when I type exit I just get the same initramfs over and over, then after a couple of seconds I would automatically display some lines saying some <process killed by signal 9> things, I would wait till that stops, then I would again type exit and finally I get a login screen and I can access my system.
 
And from a live CD/USB.
 
The sytems works fine, the process mentioned however is the problem
 
Thanks!

---

### Post by F.G. on 2011-10-31
sorry, i got no idea, sounds like some kind of bug. i take it you tried updating grub.

---

### Post by Miljet on 2011-10-31
I just ran across this thread last night. It seems to address the problems you are having. I have not had to use it and therefore can't vouch for how well it works.

---

### Post by holywhistler on 2011-10-31
I did several times with no results, I read about adding some lines to the "quiet splash" thing, none made any difference.

---

### Post by holywhistler on 2011-11-01
> **Miljet said:**
> I just ran across this thread last night. It seems to address the problems you are having. I have not had to use it and therefore can't vouch for how well it works.
 
I guess you wanted to give me a link right?? Please do so any info would be appreciated.

---

### Post by holywhistler on 2011-11-01
Anyone? Any further Help?:(

---

### Post by F.G. on 2011-11-01
my only suggestion would be to drop back to 10.04 or 11.04, if that works. i doubt 11.10 is really worth the frustration.

---

### Post by holywhistler on 2011-11-01
Yes I am considering that, but I want to use all my fixing options before, besides that none of the previous versions booted perfectly for me.

---

### Post by Miljet on 2011-11-02
I am so sorry. I just realized that I had another of those "senior moments" and forgot to include the link. Here it is.

[http://ubuntuforums.org/showthread.php?t=1743535&highlight=black](http://ubuntuforums.org/showthread.php?t=1743535&highlight=black)

And I apologise again.

---

### Post by holywhistler on 2011-11-04
Thanks pal. I will review the info.:popcorn:

---

### Post by anewguy on 2011-11-04
For every step you have tried, be sure to reverse out anything that changed.  You need a "clean slate" each time you make a change or you can just compound errors.

I haven't looked at the link that was posted yet, but I would try 2 things:

- reverse out everything you've done so far, then do update-grub

- reboot -> edit the boot line for "normal" boot to include nomodeset after the quiet nosplash options and then let it boot


If it comes up okay post back.  If not, post back with any error codes, symptoms, etc..

Dave ;)

---

### Post by ConfusedButEnthused on 2011-11-06
I had same symptom with eMachine T3882, 2GB RAM, NVidia 512 MB GeForce 8400 GS, trying to bring up 11.10 for the first time, and I stumbled upon another cause.  
On the blank screen, I pressed the Esc key and some messages came up indicating failure to mount my ntfs partition on boot-up (the one that always mounted on prior versions).  Next attempt, when I got the blank screen, I shrugged my shoulders and typed in 'skip' and pressed ENTER.  Low and behold it booted!  Now if only I can find out how to get that ntfs partition to mount upon boot-up, ...  :p

---

