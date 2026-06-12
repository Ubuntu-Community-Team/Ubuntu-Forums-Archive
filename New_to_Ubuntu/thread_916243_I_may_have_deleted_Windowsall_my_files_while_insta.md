---
title: "I may have deleted Windows/all my files while installing Ubuntu...help!!"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by stebmania on 2008-09-10
It all started when I decided to dual-boot Ubtuntu on my cheap (Acer) laptop to make it run faster/better then my current Windows XP can run it. I know close to nothing about computers, so this friend entered Remote Assistance and installed Virtual Box or something--basically, it let us install Ubuntu on a virtual computer so I can practice partitioning and installing it without deleting my files/Windows. Clearly, this wasn't enough as I still messed up somehow.
     So, it was all going fine until I got to the partitioning step. On the virtual PC, there was no previous partitions...on my laptop there was. So I went through the same things I did on the virtual PC, changed nothing in the steps. But the first thing I noticed was once I made the first partition was that three extensions that were there before now turned into empty slots. I thought tat maybe it was making room and they just weren't being displayed, so I continued, and all went as planned from there.
     Now what I'm left with is confusion and desperation. Someone have any ideas on how to boot back into Windows XP? I'm new to this so if you could be thorough that would be great :P

---

### Post by SunnyRabbiera on 2008-09-10
Very unusual issue, do you have a windows recovery disk of some kind?
If not you may be up the creek.
What virtual machine client did you use?
If you can remember the exact name of the app perhaps we can help you.

---

### Post by niccholaspage on 2008-09-10
You really no nothing about a Virtual Machine....You didn't destroy any single Windows File at all.You can still boot into Windows XP.Just Open Virtualbox and delete the Virtual Machine you setup and try again.A Virtual Machine can NEVER effect any files on the Host(Real Machine)

---

### Post by oilchangeguy on 2008-09-10
> **stebmania said:**
> It all started when I decided to dual-boot Ubtuntu on my cheap (Acer) laptop to make it run faster/better then my current Windows XP can run it. I know close to nothing about computers, so this friend entered Remote Assistance and installed Virtual Box or something--basically, it let us install Ubuntu on a virtual computer so I can practice partitioning and installing it without deleting my files/Windows. Clearly, this wasn't enough as I still messed up somehow.
     So, it was all going fine until I got to the partitioning step. On the virtual PC, there was no previous partitions...on my laptop there was. So I went through the same things I did on the virtual PC, changed nothing in the steps. But the first thing I noticed was once I made the first partition was that three extensions that were there before now turned into empty slots. I thought tat maybe it was making room and they just weren't being displayed, so I continued, and all went as planned from there.
     Now what I'm left with is confusion and desperation. Someone have any ideas on how to boot back into Windows XP? I'm new to this so if you could be thorough that would be great :P

I've said this before, always, always back up your data. BEFORE doing something like this. That being said, if you selected use entire disc, your windows install is no more. And once a drive has been formatted it's very expensive to get any data back.

---

### Post by SunnyRabbiera on 2008-09-10
> **niccholaspage said:**
> You really no nothing about a Virtual Machine....You didn't destroy any single Windows File at all.You can still boot into Windows XP.Just Open Virtualbox and delete the Virtual Machine you setup and try again.A Virtual Machine can NEVER effect any files on the Host(Real Machine)

yes but we really dont know if it was an actual virtual machine he installed, he could have had some confusion on what he did.

---

### Post by oilchangeguy on 2008-09-10
> **niccholaspage said:**
> You really no nothing about a Virtual Machine....You didn't destroy any single Windows File at all.You can still boot into Windows XP.Just Open Virtualbox and delete the Virtual Machine you setup and try again.A Virtual Machine can NEVER effect any files on the Host(Real Machine)

the op seems to state that they used a vm, and then tried to install it on his computer.

---

### Post by niccholaspage on 2008-09-10
But I really don't think this could happen.Maybe somehow a VirtualBox Hard Disk was some huge size as a fixed size image,And this consumed the whole hard drives's space?
If this is true than the OP needs to get a Windows Recovery Disk..

---

### Post by SunnyRabbiera on 2008-09-10
> **oilchangeguy said:**
> the op seems to state that they used a vm, and then tried to install it on his computer.

indeed, if the original poster installed Ubuntu in full without knowing it then that can mess up ones day for sure.

---

### Post by niccholaspage on 2008-09-10
Oh.I am dumb.I guess the OP will need to use a Windows Recovery Disk.

---

### Post by Charcoal1981 on 2008-09-10
stebmania - can you confirm that your laptop (the real one not the virtual one) no longer boots? Secondly, do you have access to an ubuntu live cd?

---

### Post by stebmania on 2008-09-10
What SunnyRabbiera said is true. I practiced with this friend on the virtual machine, then installed it on my actually computer (convinced there was NOTHING that could go wrong). And about this disk recovery...when I reboot something about Grub prompts me to press Esc and gives me a three second countdown. I did this once and I chose the option with (recovery) beside it. So all is going well and white text is scrolling down the black screen faster than I can comprehend. Then it wants me to enter something... I typed in boot and my password and was stumped. Any ideas?

---

### Post by oilchangeguy on 2008-09-10
> **stebmania said:**
> What SunnyRabbiera said is true. I practiced with this friend on the virtual machine, then installed it on my actually computer (convinced there was NOTHING that could go wrong). And about this disk recovery...when I reboot something about Grub prompts me to press Esc and gives me a three second countdown. I did this once and I chose the option with (recovery) beside it. So all is going well and white text is scrolling down the black screen faster than I can comprehend. Then it wants me to enter something... I typed in boot and my password and was stumped. Any ideas?

run the computer from the live cd, and see if your windows partition is still there.

---

### Post by SunnyRabbiera on 2008-09-10
> **stebmania said:**
> What SunnyRabbiera said is true. I practiced with this friend on the virtual machine, then installed it on my actually computer (convinced there was NOTHING that could go wrong). And about this disk recovery...when I reboot something about Grub prompts me to press Esc and gives me a three second countdown. I did this once and I chose the option with (recovery) beside it. So all is going well and white text is scrolling down the black screen faster than I can comprehend. Then it wants me to enter something... I typed in boot and my password and was stumped. Any ideas?

Then you did probably wipe out windows off your drive, and for that I am most sorry.
But you may have some hope, when grub loads when you press the escape key do you have other options other then recovery mode?
That recovery mode you speak of is for your linux system and WONT restore windows... sorry
but if you can boot into linux then at least you have a OS to work with right now.

---

### Post by stebmania on 2008-09-10
It appears I am up said creek, then. I can reboot real quick and write down on pen and paper what happens when I press escape if that will help? Also, let's jsut pretend all went smooth and what not, how would I have gotten back into XP before?

---

### Post by SunnyRabbiera on 2008-09-10
> **stebmania said:**
> It appears I am up said creek, then. I can reboot real quick and write down on pen and paper what happens when I press escape if that will help? Also, let's jsut pretend all went smooth and what not, how would I have gotten back into XP before?

Grub would have displayed XP if you didnt dedicate the whole drive to Ubuntu.
And yes write down what comes up in grub.
Now currently how are you making posts, from another computer?

---

### Post by oilchangeguy on 2008-09-10
> **stebmania said:**
> It appears I am up said creek, then. I can reboot real quick and write down on pen and paper what happens when I press escape if that will help? Also, let's jsut pretend all went smooth and what not, how would I have gotten back into XP before?

please see post #12.

---

### Post by stebmania on 2008-09-10
I can try and be a bit clearer, sorry. All this happened on this computer. I'm simply using Ubuntu. Not that Ubuntu isn't good or anything but, I'd really like to hvae my files/XP back. And, this friend came on MSN (I was using this application called "Pidgin" to contact him) and he basically told em to come here and ask for help as he has work 'till 11 tonight. And he mentioned something about SuperGrub disk? Can anyone explain what SuberGrub does/how it can help, please? 

EDIT: Also when the thread dies down for a sec i'll go reboot, I'd like to have all the information first :D.

---

### Post by Charcoal1981 on 2008-09-10
super grub disk repairs grub if it breaks. This is not your issue. You have deleted your windows partitions and over-writen with ubuntu, so you cannot salvage either windows (as was) or your files short of professional disk recovery services (even then only maybe).

If you want XP back you will need to reinstall it.

---

### Post by SunnyRabbiera on 2008-09-10
> **stebmania said:**
> I can try and be a bit clearer, sorry. All this happened on this computer. I'm simply using Ubuntu. Not that Ubuntu isn't good or anything but, I'd really like to hvae my files/XP back. And, this friend came on MSN (I was using this application called "Pidgin" to contact him) and he basically told em to come here and ask for help as he has work 'till 11 tonight. And he mentioned something about SuperGrub disk? Can anyone explain what SuberGrub does/how it can help, please?

your issue is understood, hey I feel your pain as the first time I tried to dual boot linux/ windows I accidentally wiped off XP by mistake.
Dont worry about supergrubdisk right now, trust me it wont do any good for recovering a completely lost XP partition.
If you installed Ubuntu totally over XP there is no way of recovering it, sorry...
So if you told Ubuntu tot totally partition over XP there is no way to get it back... period.
Sorry there is not a lot we can do for you.
But to make 100% sure I want you to go to "system" then to "administration"
and then to "system monitor" in ubuntu.
go to the file systems tab and see if there is indeed a windows drive listed, if not you have no hope of getting your files back...
even if you get a XP recovery disk it wont get your files back.

---

### Post by stebmania on 2008-09-10
It isn't a SURE thing that I ahve deleted the files. This friend has had a much more indepth explaination (not to mention some cussing and threatening) of things. He said it's unlikely that I have deleted Windows and my files. Also, something that was said in the MSN conversation:
"(05:15:27 PM) Lawrence: Check if you still have the partitions
 (05:15:33 PM) Lawrence: Open Partition Editor
 (05:15:50 PM) Lawrence: Go to System > Administration > Partition Editoer"
I did this and couldn't find what he said. Where else would this program be? Do I have to install it? Right now my computer is factory direct (I think that's the term anyways) so I hvae nothing but what Ubuntu starts off with.

---

### Post by SunnyRabbiera on 2008-09-10
> **stebmania said:**
> It isn't a SURE thing that I ahve deleted the files. This friend has had a much more indepth explaination (not to mention some cussing and threatening) of things. He said it's unlikely that I have deleted Windows and my files. Also, something that was said in the MSN conversation:
"(05:15:27 PM) Lawrence: Check if you still have the partitions
 (05:15:33 PM) Lawrence: Open Partition Editor
 (05:15:50 PM) Lawrence: Go to System > Administration > Partition Editoer"
I did this and couldn't find what he said. Where else would this program be? Do I have to install it? Right now my computer is factory direct (I think that's the term anyways) so I hvae nothing but what Ubuntu starts off with.

Dont worry about partition editor, it will do nothing if you wiped off windows and could make matters worse.
Your friend here doesnt seem to be much of a friend...
Again if you wiped off all your files you have my sympathies, but hey at least you have a OS...
My first try I didnt even have a OS to work with when trying to dual boot, no windows, no linux, no nothing.
So thats somewhat of a bright side, you have a OS at least and dont have a totally blank system like i did when I first tried to dual boot.
But as I said use the system monitor to check if there is still a windows drive on your system...
If windows isnt listed we will know.

---

### Post by Charcoal1981 on 2008-09-10
I am afraid that if XP is not one of the options in your grub boot menu then there is a 99% chance that you have indeed wiped your files.

If you really want to check. the partion editor needs to be installed by entering "sudo apt-get install gparted" into a terminal. when this is complete, the partion editor will be available in your menu as your friend describes

---

### Post by SunnyRabbiera on 2008-09-10
> **Charcoal1981 said:**
> I am afraid that if XP is not one of the options in your grub boot menu then there is a 99% chance that you have indeed wiped your files.

If you really want to check. the partion editor needs to be installed by entering "sudo apt-get install gparted". when this is complete, the partion editor will be available in your menu as your friend describes

Indeed, but take caution when doing this as it can make matters wose if you have no idea what you are doing.

---

### Post by lisati on 2008-09-10
One of the ways of seeing if there's a Windows-capable partition is with the "fdisk" command, I'm surprised no-one has mentioned this so far.....

---

### Post by stebmania on 2008-09-10
Well, this is so far over my head I can't even express it. I typed in what was said by lisati and this is what I got:
jake@ubuntu:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

Translation?

---

### Post by Charcoal1981 on 2008-09-10
> **SunnyRabbiera said:**
> Indeed, but take caution when doing this as it can make matters wose if you have no idea what you are doing.

Agreed...

---

### Post by SunnyRabbiera on 2008-09-10
> **lisati said:**
> One of the ways of seeing if there's a Windows-capable partition is with the "fdisk" command, I'm surprised no-one has mentioned this so far.....

That would have been next on my list of suggestions actually, but one step at a time as fdisk is a command line tool and we are dealing with a nervous windows user who might have erased windows by mistake.

---

### Post by stebmania on 2008-09-10
I skipped that whole..."Indeed, but take caution when doing this as it can make matters wose if you have no idea what you are doing." step. As you may have gussed by now...I'm clueless. Beyond that. So, anyone know what my last post meant?

---

### Post by SunnyRabbiera on 2008-09-10
> **stebmania said:**
> Well, this is so far over my head I can't even express it. I typed in what was said by lisati and this is what I got:
jake@ubuntu:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

Translation?

That just gives you the base on how to use it, I would not use this terminal command at this time.

---

### Post by mgna003 on 2008-09-10
Hi

sorry for your mishap, but if when you boot, you get no option on your grub boot menu for xp, you probably delete the files(99%).
The fdisk command should also show you partions if available.
Also if you check your you partions on the ubuntu machine you should be able to see the windows partion if its still there

---

### Post by SunnyRabbiera on 2008-09-10
> **mgna003 said:**
> Hi

sorry for your mishap, but if when you boot, you get no option on your grub boot menu for xp, you probably delete the files(99%).
The fdisk command should also show you partions if available.
Also if you check your you partions on the ubuntu machine you should be able to see the windows partion if its still there

again dont suggest fdisk right now, you will only confuse him.
its not a good time to force a command on him now, let him assess his damage first.

---

### Post by Charcoal1981 on 2008-09-10
> **stebmania said:**
> I skipped that whole..."Indeed, but take caution when doing this as it can make matters wose if you have no idea what you are doing." step. As you may have gussed by now...I'm clueless. Beyond that. So, anyone know what my last post meant?

Your last post meant you didn't enter any of the require arguments for fdisk. type "man fdisk" for some instructions if you are really determined, but I'm sorry to say if I was you I would be looking for an XP install disk if you really want windows back.

---

### Post by stebmania on 2008-09-10
Well, I was excited and anxious when it was installing. And giddy like a schoolgirl when I got my hands on it. I don't mind using a new OS, it's more losing all my sweet, sweet files...OH!! I just remembered that I had Norton 360 installed on this computer. And it was a green check mark regarding Norton 360 Back-up files!! Do they save my files on their database or something? If I installed Norton 360 on Ubuntu will it give me my files back??

---

### Post by SunnyRabbiera on 2008-09-10
> **Charcoal1981 said:**
> Your last post meant you didn't enter any of the require arguments for fdisk. type "man fdisk" for some instructions if you are really determined, but I'm sorry to say if I was you I would be looking for an XP install disk if you really want windows back.

Aye thats why I said dont use fdisk...
Sometimes I hate command line guru's, they do more harm then good in scenarios like this. I know from experience trust me.

> **stebmania said:**
> Well, I was excited and anxious when it was installing. And giddy like a schoolgirl when I got my hands on it. I don't mind using a new OS, it's more losing all my sweet, sweet files...OH!! I just remembered that I had Norton 360 installed on this computer. And it was a green check mark regarding Norton 360 Back-up files!! Do they save my files on their database or something? If I installed Norton 360 on Ubuntu will it give me my files back??

I dont think so, when you told ubuntu to overwrite your drive it would have wiped off norton 360 as norton 360 is a windows app.

---

### Post by starcannon on 2008-09-10
You may safely type in 
```
sudo fdisk -l
```
at a terminal.

If your windows partitions do not come up in the list, then don't get panicked yet, recovering your important files may still be possible even if the partition is gone; it will however mean a bit of work.

So first lets get that partition list, then it can be determined whether or not we can fix this install to work properly, or whether we need to start recovering files.

GL

---

### Post by mgna003 on 2008-09-10
I'm not sure if you would be able to get your files from norton backup since mostly they backup to a section of your hard drive.

When i first installed ubuntu I did the exact same thing, and had to learn the hard way,
If you have any file recovery software you might be able to get some of your files back.

---

### Post by oilchangeguy on 2008-09-10
"giddy like a schoolgirl" this thread is getting scary. it's time for a mod to close it. i'm thinking the op is a troll. and besides 4 pages and the op still doesn't understand what to do???????????????????

---

### Post by Sef on 2008-09-10
> ou may safely type in 
 	Code:
 	fdisk -l 


Actually the code is 

```
sudo fdisk -l
``` Small L

That will show you (and us) what partitions that you have.  Paste your results here.

---

### Post by SunnyRabbiera on 2008-09-10
> **Sef said:**
> Actually the code is 

```
sudo fdisk -l
``` Small L

That will show you (and us) what partitions that you have.  Paste your results here.

again, not a good time for you command line guru's, trust me you might scare him with all these commands right now.

---

### Post by stebmania on 2008-09-10
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d439a11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974        1034      489982+  82  Linux swap / Solaris

I'm pretty sure this means no more XP :( 

PS: What's a troll?

---

### Post by starcannon on 2008-09-10
> **Sef said:**
> Actually the code is 

```
sudo fdisk -l
``` Small L

That will show you (and us) what partitions that you have.  Paste your results here.

nod sorry, edited and fixed it.

---

### Post by SunnyRabbiera on 2008-09-10
> **stebmania said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d439a11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974        1034      489982+  82  Linux swap / Solaris

I'm pretty sure this means no more XP :( 

PS: What's a troll?

yes that means no more XP... again I am sorry.
As for what troll is, usually a troll is a malicious forum user who contributes little to the forum other then spam or useless topics.

---

### Post by stebmania on 2008-09-10
This may be a little useless to you guys, but I learned a lot in this little thread, thanks a lot all! starcannon has offered to start a remote assistance session, s hopefully he can better describe my situation and give you more information than I did. Thanks again, you've all been great!

---

### Post by ieduarte73 on 2008-09-10
According to the fdisk information, you have wiped off your windows partition, as you can notice there are only two valid partitions now in your computer

---

### Post by SunnyRabbiera on 2008-09-10
> **stebmania said:**
> This may be a little useless to you guys, but I learned a lot in this little thread, thanks a lot all! starcannon has offered to start a remote assistance session, s hopefully he can better describe my situation and give you more information than I did. Thanks again, you've all been great!

Well dont feel you are a troll, you had an honest problem so we tried to provide honest answers.
trust me I know what it feels like to be a beginner so thats why I try to help when I can.

---

### Post by starcannon on 2008-09-10
Good recovery software that has brought a few people back from the brink can be found here:
[http://ubuntuforums.org/showpost.php?p=2504668&postcount=1](http://ubuntuforums.org/showpost.php?p=2504668&postcount=1)

Step By Step Directions here:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

GL

---

### Post by starcannon on 2008-09-10
Testdisk looks like the ticket, and its a nice enough looking that I think I'm gonna spend a bit of time getting familiar with it.

Definitely the windows partition got destroyed.

---

### Post by stebmania on 2008-09-10
Hmm, considering I'm new to Linux and all, how do I download the program? :S
I mean I have it saved on my desktop but I just keep seeing a bunch of text files in the folders...help? xD

---

### Post by niccholaspage on 2008-09-10
Open a Terminal(Applications>Accessories>Terminal)
And type:
```
sudo apt-get install gparted
```Now go to System>Administration>Partition Editor.Tell us what you see

---

### Post by Buddy's Pal on 2008-09-10
If you have (had) vital files in Windows that you absolutely must keep, you can most likely get most of them back.

I messed up when I first tried to set up a dual boot with Ubuntu and Vista. I installed Ubuntu but wiped Vista by mistake. (Mixture of impatience, overconfidence and boneheadedness)

I contacted a local data recovery guy and he told me to use the computer as little as possible so as not to overwrite data that was still on the drive.

I gave this fellow the drive and he was able to recover most of my stuff.

A down side is that file names are lost. For example I got back 670 .doc files but the file names were 0.doc --> 669.doc. This was back in Feb and I'm still going through those and renaming the ones I want to keep! :(

Cost me $125.

Good lesson!

---

