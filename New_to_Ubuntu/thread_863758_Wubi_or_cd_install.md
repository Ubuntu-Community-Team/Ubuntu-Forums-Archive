---
title: "Wubi or cd install"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Sithely on 2008-07-18
Hi,
I am new to Linux and have tried a little of Ubuntu and I like it.
My question is should I install it with wubi or do the partition hard drive and install Ubuntu that way?

Which will give me the best performance?  If it matters my comp is:
AMD Athlon64 X2 3800+, 2Gig Ram, Nvidia 8800GT 512mb, 250Gig HDD.

Thanks.

---

### Post by jamewill on 2008-07-18
wubi to try out with no partition changes to your hd

then, when you like it take the step to make a partition or two for linux

(of course you can go the VM WARE route too)

jw

---

### Post by Sithely on 2008-07-18
Yeah I used Wubi with a real small install size (like 10 Gigs) but that's not enough for me to try and see if I can get World of Warcraft running right as well as find a replacement for quicken so I can ditch windows.

If i partition the hard drive does that mean that Ubuntu is permanent?  Or can I remove it later without harming the windows partition?

BTW thanks for quick reply :)

---

### Post by SunnyRabbiera on 2008-07-18
You can dual boot with the help of the live CD, the live CD will enable you to try out the OS before you install it.

---

### Post by Sunfist on 2008-07-18
I tried Wubi first but couldnt get it to run right on my system, some kind of video issue. So I repartitioned my HD and did a full install and it worked perfectly. Dont know why Wubi didnt work and the full cd install did, but thats how it went.

---

### Post by Sithely on 2008-07-18
> **SunnyRabbiera said:**
> You can dual boot with the help of the live CD, the live CD will enable you to try out the OS before you install it.

Ok, If i do the dual boot w/ the live cd and I want to later install do I have to start over?

Thanks.

---

### Post by Sef on 2008-07-18
> Ok, If i do the dual boot w/ the live cd and I want to later install do I have to start over?

If you dual boot, you would have installed Ubuntu.  The Live CD can run off of the CD or can be installed.

---

### Post by SunnyRabbiera on 2008-07-18
> **Sunfist said:**
> I tried Wubi first but couldnt get it to run right on my system, some kind of video issue. So I repartitioned my HD and did a full install and it worked perfectly. Dont know why Wubi didnt work and the full cd install did, but thats how it went.

Wubi is still a bit experimental around the edges so any issues are expected.
Anyhow if you partitioned right you should have a dual boot of windows and linux after you take out the live CD.
Though there might be one or two issues you may need to correct.

---

### Post by Mesenfants1 on 2008-07-18
I think I have installed 8.04 Desktop into Windows XP with Wubi, but I am having a problem. The Ubuntu loading screen, with the moving orange bar, comes up, but then the screen goes dark and a small message comes up in the midle of the screen. It says something like Cannot work in this display mode. What can I do to get the oS to run and show? Thank you for help.
Chuck

---

### Post by steveneddy on 2008-07-18
I would partition and install it to a hard drive.

Partitioning is really a basic operation for a power user, but if it scares you a little to divide your HD up into smaller pieces (partitioning) then I suggest that you read up on it a little so you will feel a little more confident.

Partitioning tools are available natively on XP and Vista.

Here's a link to help you.

[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

---

### Post by alienexplorers on 2008-07-19
Go with the live CD.  Load it without installing it and play with it for a while.  If you then want to keep Ubuntu you can install it and make partitions for it.  You can then go and edit grub menu.lst and add your other operating system if it hasn't already been installed.   Dual boot is kind of neat.  If certain things like my camera and scanner will not work in linux, I can always run them in windows.

---

### Post by pikabuntu on 2008-07-19
> **alienexplorers said:**
> Go with the live CD.  Load it without installing it and play with it for a while.  If you then want to keep Ubuntu you can install it and make partitions for it.  You can then go and edit grub menu.lst and add your other operating system if it hasn't already been installed.   Dual boot is kind of neat.  If certain things like my camera and scanner will not work in linux, I can always run them in windows.
This is also what i did.

---

### Post by William T. East on 2008-07-22
Hi,

Install on USB using WUBI.  Install comes up with

>grub

Any ideas?  Thanks.

---

### Post by fidamehran on 2008-07-22
Why is everybody advising the newcomers to install with partitioning? I remember when I tried installing Fiesty (Ubuntu 7.04) for the first time, I was quite tense about the partitioning. What's the harm in installing Ubuntu through Wubi and trying it out? I think, when a user will be confident enough, he can ditch the whole junkload of Windows and do a fresh install of Ubuntu by CD booting.
I am still very fresh to Ubuntu and being delighted to see the Wubi option for the first time in 8.04, I used it to install it. My Ubuntu 8.04 is running like magic.
Don't discourage it. This could be a whole new dimension of doing things.

---

### Post by fidamehran on 2008-07-22
> **William T. East said:**
> Hi,

Install on USB using WUBI.  Install comes up with

>grub

Any ideas?  Thanks.

On USB? How large is your pen drive? :-O

---

### Post by William T. East on 2008-07-22
> **fidamehran said:**
> On USB? How large is your pen drive? :-O

Not pen, 100 gb disk.  Some sort of message, possibly about graphics, flashes too fast to read before

>grub

appears.

---

### Post by fidamehran on 2008-07-22
Oh, of course. But with Wubi, after you install, you are supposed to boot into a graphical interface, right?
a) Did you download Wubi, and then download an installer image on your HDD to install it?
b) If you did that, are you sure that you downloaded the normal/default Ubuntu CD image or did you by mistake download the Alternate CD Image?

I think the alternate CD image installs a text based Ubuntu primarily.

---

### Post by William T. East on 2008-07-22
> **fidamehran said:**
> Oh, of course. But with Wubi, after you install, you are supposed to boot into a graphical interface, right?
a) Did you download Wubi, and then download an installer image on your HDD to install it?
b) If you did that, are you sure that you downloaded the normal/default Ubuntu CD image or did you by mistake download the Alternate CD Image?

I think the alternate CD image installs a text based Ubuntu primarily.

Download was ubuntu-8.04.1-desktop-i386.iso.

---

### Post by Paqman on 2008-07-22
> **fidamehran said:**
> Why is everybody advising the newcomers to install with partitioning? I remember when I tried installing Fiesty (Ubuntu 7.04) for the first time, I was quite tense about the partitioning. What's the harm in installing Ubuntu through Wubi and trying it out? I think, when a user will be confident enough, he can ditch the whole junkload of Windows and do a fresh install of Ubuntu by CD booting.
I am still very fresh to Ubuntu and being delighted to see the Wubi option for the first time in 8.04, I used it to install it. My Ubuntu 8.04 is running like magic.
Don't discourage it. This could be a whole new dimension of doing things.

I couldn't agree more.

People are creatures of habit though. Since pretty much every experienced Linux user had to partition to install, that's what they tell the newbies to do. I would highly recommend anybody who plans to spend time in the absolute beginners forum familiarise themselves with Wubi so that they can provide informed advice.

I've really, really gone off advising most newbies to partition. It's a MAJOR obstacle to Linux adoption for many people.

---

### Post by a0u on 2008-07-22
> **Sithely said:**
> ...as well as find a replacement for quicken so I can ditch windows.
[Free and open-source alternatives to Quicken]("http://www.osalt.com/quicken")
 
> **Sithely said:**
> If i partition the hard drive does that mean that Ubuntu is permanent? Or can I remove it later without harming the windows partition?
Both are true. Partitioning is the the conventional installation method. Personally, I consider Wubi to be a useful but ultimately temporary experience, and a serious user should opt for partioning. However, "permanent" does not mean "undeletable" - you can always use GParted to delete the Ubuntu partition (thus getting rid of Ubuntu) and resize the Windows partition to reclaim the freed space.
 
> **fidamehran said:**
> 
I think the alternate CD image installs a text based Ubuntu primarily.
No, the alternate CD uses a *text-based* installer (e.g., no fancy GUI), but it still can install the same system as the LiveCD.  It's useful for computers that cannot run a LiveCD.

---

