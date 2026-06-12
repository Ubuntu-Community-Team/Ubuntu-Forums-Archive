---
title: "[SOLVED] Virtualbox - installing win xp on a vm - Hardy"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by alloftheabove on 2008-06-20
Does anyone have experience with installing xp onto a Virtualbox vm?  When I get as far as partitioning the virtual hard drive, if I chose ntfs ( might have gotten the letters wrong order ) quick partitioning it jumps to 20% and aborts after a minute; if I choose regular ntfs partitioning it hangs without making any progress.  I need to vm win xp because my mom won't let me use her Vista computer to run my programs on, so....Yeah.

---

### Post by alloftheabove on 2008-06-20
bump?

---

### Post by alloftheabove on 2008-06-20
Hello, is anyone there?  Or is my problem too annoying to try to solve?

---

### Post by badfish591 on 2008-06-20
well i haven't ran virualbox in a while so i don't really remember what i did different than you but here is a good article about setting it up

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux]("http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux")

it pretty much gives you a step by step on the install. And helps you set it up seamlessly to the point that you can even have a windows start-bar to launch all your apps from your virtual machine.

hope that helps

---

### Post by alloftheabove on 2008-06-20
Yes but my problem is that windows xp vm is hanging during formatting.

---

### Post by cariboo on 2008-06-20
I haven't got VirtualBOx installed on this computer, but if I remeber correctly that you don't have to tell it how to format the virtual drive. In the initial setup just tell it what operating system you are installing and it does everything for you.

Jim

---

### Post by alloftheabove on 2008-06-20
The formatting is a part of the windows xp installation from the boot disc.

---

### Post by f37u5g0d on 2008-06-21
Virtual box doesn't format or partition your harddrive.  It creates a file to your specifications that the virtual machine (and operating system) use as a hard drive.  When you run the virtual machine with an operating system installation disk in a drive that is mounted it may say something about formatting or partitioning but don't worry.  It is referring to partitioning the file not your actual hard disk.  Also fyi, I have seen some stuff on the internet saying that a restore disk that came with a PC won't work but that is false.  I used my restore disk to install windows xp on my virtual machine and it worked just fine.  Also virtualbox won't work under the very newest kernel (2.6.24-19).  To find out which kernel you are running type "uname -a" into the terminal.

---

### Post by alloftheabove on 2008-06-21
1.  I didn't mean partitioning the Ubuntu hard drive, I meant the virtual hard drive ( the file ).

2.  Are you talking about the repository version of virtualbox or the one available directly from sun ( virtualbox.org ) ?

3.  The problem is that the vm hangs during the partitioning/formatting portion of the xp installation on the virtual hard drive.  The vm aborts itself.  Therefore I don't even have xp installed on my virtual hard drive, it's all just free space.

---

### Post by f37u5g0d on 2008-06-21
Ok wanted to make sure you knew what you were partitioning first.  Second, I am referring to the repo version.  I don't know if the version from Sun directly is any different.  When you say that vm hangs.  Do you mean virtualbox?  VMware and virtual box are different.  I have some experience with vbox but none with vmware however I have heard good things about both.  Last, does your install disk have a scratch / smudge?  Also is your file large enough?  5 gigs is a good amount if you're unsure.

---

### Post by alloftheabove on 2008-06-21
1.  When I say that the vm hangs, I mean the virtualbox virtual machine I created for xp.

2.  Yes, I do have the latest kernel version.

3.  The install cd just shipped in today.  And I just checked, it has no scratches.

and 4.  I gave windows a 60 gig partition ( then again, I have a 250 gig hard drive ).

---

### Post by f37u5g0d on 2008-06-21
60 gigs is more than enough for xp.  They used to sell xp machines 5 years ago that had 40 gig hard drives.  I think you might be treading in bug territory.  If you can re-create the error than you should post the bug on launchpad.  In any event I was quite sure from the beginning of this that your problem was a bug.  No program should ever freeze or close on it's own no matter what the user does.

[https://launchpad.net/](https://launchpad.net/)

You'll have to create an account to report a bug but it's extremely helpful to the ubuntu team for users to make bug reports so please do.

---

### Post by Pecster on 2008-06-21
i'm having the same problem for months now, and i can't figured out yet, but if i do i gladly let you know

---

### Post by badfish591 on 2008-06-21
> **f37u5g0d said:**
> Also virtualbox won't work under the very newest kernel (2.6.24-19).  To find out which kernel you are running type "uname -a" into the terminal.


> **alloftheabove said:**
> 2.  Yes, I do have the latest kernel version.


maybe this is your problem, have you tried booting an older kernel and setting up your virtual machine?

---

### Post by alloftheabove on 2008-06-21
Did you notice from an earlier post of mine that I am using virtualbox from virtualbox.org, not from the repos?  And besides, how do you boot an earlier kernel?  And then, when I set up my virtual machine, would it still work if I reboot into the current kernel?

---

### Post by badfish591 on 2008-06-21
> **alloftheabove said:**
> Did you notice from an earlier post of mine that I am using virtualbox from virtualbox.org, not from the repos?  And besides, how do you boot an earlier kernel?  And then, when I set up my virtual machine, would it still work if I reboot into the current kernel?

1.yes i did notice, that may or may not matter.
2. you can choose which kernel you boot from with a program called Startup-manager. to install run, from terminal
```
Sudo apt-get install startup-manager
```
once you install, it will be located under: System->Administration->Startup-manager, and as long as you haven't manually deleted any old kernels after you have updated they should be there.
3. no, but startup-manager will allow you to continually boot from the older kernel until virtualbox is supported in the new one, then you just switch back.



now this may not work but it should take you a grand total of ten minutes to try, so it shouldn't hurt to try.

---

### Post by alloftheabove on 2008-06-21
Well, I just finished trying it...I set it to .18 instead of .19, and it _was_ working.  However windows xp installer finished 'formatting' the virtual hard disk, and I think it aborted itself.  Maaaan...

Then I tried the 'quick' partition option, and this time, it jumped to 20% and then ( I think ) it used up all the cpu and even froze linux, and I don't know what the damage may be, if any.

Before all that, I tried using the OSE version instead, however it wouldn't even pop up when I was in .18 kernel.  So that is when I reinstalled the sun .deb version again, and got the above results.  I wish I knew what the problem was...

---

### Post by badfish591 on 2008-06-21
that sucks, the only thing that i can think for you to even try is to use VMware, i have heard from many people that it is as good or better than virtualbox. it should allow you to do the same thing as virtualbox, but maybe this program likes your computer. it sounds like you don't really have any choice but to virtualize windows, maybe switching programs will make life easier for you.

---

### Post by alloftheabove on 2008-06-21
But I ordered windows xp just for virtualizing it....

Which I suppose is a bit funny, but...Isn't there some application that can virtualize windows xp using the disc I have?

---

### Post by Ev1L on 2008-06-21
first one question(no offense):
have you chose windows xp when creating the new VM?

then, i suggest to try 5GB partition to check if that's the problem.
i recently had problems with both a ruined windows xp CD and too big partition handling.

---

### Post by alloftheabove on 2008-06-21
Yes I did choose windows xp when I created the new VM, and maybe I'll try moving the partition down to 30gigs, like I used to have.  Be back with the results.

---

### Post by alloftheabove on 2008-06-21
Well...I created a new virtual disk for it to work on, I chose ntfs formatting ( this time it gave me choice of ntfs, ntfs quick, fat, and fat quick ), it got to 100% and it was doing really well, and sadly it is frozen, at least I think it is.  I'm giving it time to see if it can work itself out.  Should I choose fat formatting this next time?

EDIT: I suppose the vm took up all the cpu power.  My computer is restarting now.

---

### Post by CH1C0 on 2008-06-21
Sorry if this is off topic, but anyway, I tried to install XP Home in Sun Virtualbox. I have a legit copy i bought and the product key was rejected. I then tried a bunch of keys I got from different sources and none worked. Is there some kind of setting in Virtualbox to fix this?

---

### Post by Ev1L on 2008-06-21
mmmhhh i really suggest to give it a simple try with 5GB partition (i know it's time consuming, but since you ordered an xp license, let's try to understand where's exactly the problem).

i suggest to use vmware only as last resort because in my experience it is way slower.

by the way, could you remind me which version of ubuntu, kernel and vbox are you using please?

(good night and good luck, i'll read tomorrow morning)

---

### Post by Ev1L on 2008-06-21
> **CH1C0 said:**
> Sorry if this is off topic, but anyway, I tried to install XP Home in Sun Virtualbox. I have a legit copy i bought and the product key was rejected. I then tried a bunch of keys I got from different sources and none worked. Is there some kind of setting in Virtualbox to fix this?
if you have an original copy i suppose that the attached code MUST work.
if you mean the activation code for windows expiration, then it could be possible to be blocked, but since you're an authorized user, just call them to solve the misunderstanding :)

i don't think it can depend on vbox and even less it provides some solution

---

### Post by alloftheabove on 2008-06-21
Ubuntu 8.04 Hardy Heron, kernel version 2.6.24-18 ( using startup manager ), VirtualBox version 1.6.2.  Be back with the results.

---

### Post by alloftheabove on 2008-06-21
Well, apparently it gets to 100% easily and then the virtual machine it's setting up on aborts itself.  That's what happened this time.

---

### Post by alloftheabove on 2008-06-21
UPDATE: I lowered the ram that I gave it to 256 mb, then tried again with the 5gb virtual drive.  IT INSTALLED AND IT WORKS!  Should I try with 30 or 60 gb?

EDIT: It's amazing that my computer was able to do it...My computer may have 1.5gb of ram, but it only has 1 ghz of processor power.  Lol.  I've seen p3s with more processor power than my computer.  My old p4 has 2.4 ghz total, I wouldn't mind using it right now, but it takes ddr ram, and it __is__ 5 years old lol.

EDIT_2: My activation code will still work if I change the virtual hard drive and install, won't it?  I hope it does.  I don't know that much about activation codes.

---

### Post by f37u5g0d on 2008-06-21
You should mark your thread as "solved."  It's under "thread tools."

---

### Post by dondad on 2008-06-22
> **f37u5g0d said:**
> Virtual box doesn't format or partition your harddrive.  It creates a file to your specifications that the virtual machine (and operating system) use as a hard drive.  When you run the virtual machine with an operating system installation disk in a drive that is mounted it may say something about formatting or partitioning but don't worry.  It is referring to partitioning the file not your actual hard disk.  Also fyi, I have seen some stuff on the internet saying that a restore disk that came with a PC won't work but that is false.  I used my restore disk to install windows xp on my virtual machine and it worked just fine.  Also virtualbox won't work under the very newest kernel (2.6.24-19).  To find out which kernel you are running type "uname -a" into the terminal.

It will work with the latest version of the kernel if you install the hardy version binary from the virtual box website. I had to uninstall the older one, then install that one and it works fine. If you just do an uninstall of the old one and not a complete removal, it does not destroy the winxp installation that was there.

---

### Post by seuzy13 on 2008-06-22
Your activation code should definitely work more than once. I used the same code twice on this computer (once, when Windows was activated...before it was purchased, and twice when I installed in virtualbox). Glad to here you solved your problems!

---

### Post by Victormd on 2008-06-22
> **alloftheabove said:**
> UPDATE: I lowered the ram that I gave it to 256 mb, then tried again with the 5gb virtual drive.  IT INSTALLED AND IT WORKS!  Should I try with 30 or 60 gb?

I probably wouldn't go over 10Gb, but it depends on what you're going to be using it for.

As for your memory, if you have 1.5GB RAM and you really want to use windows in a virtual machine, you should upgrade to at least 2GB and use at least 512MB for windows... this is for it to run. If you want it to run well, allocate 1Gb for windows.

If upgrading your ram isn't an option, I would allocate at least 512MB for windows

> **alloftheabove said:**
> EDIT: It's amazing that my computer was able to do it...My computer may have 1.5gb of ram, but it only has 1 ghz of processor power.  Lol.  I've seen p3s with more processor power than my computer.  My old p4 has 2.4 ghz total, I wouldn't mind using it right now, but it takes ddr ram, and it __is__ 5 years old lol.

Yeah, I'm running Hardy on a P4 3.2GHz and have XP virtualized with 1GB RAM allocated to it. I haven't had to boot it for a while but it was Ok... no 3D acceleration so don't bother with games... :)

> **alloftheabove said:**
> EDIT_2: My activation code will still work if I change the virtual hard drive and install, won't it?  I hope it does.  I don't know that much about activation codes.

With XP you can activate it as many times as you'd like, as long as you only have one copy installed at a time. Vista on the other hand, once you activate it, if you need to reinstall, you have to call microsoft and get a new code.

---

### Post by 7raTEYdCql on 2008-06-22
I never had a problem while installing XP on my virtual box.

Had some problems starting it, editted the newly created virtual box group and linked it to my name, in /etc/passwd. Hope this helps when your VB starts.

---

### Post by CH1C0 on 2008-06-22
> **Ev1L said:**
> if you have an original copy i suppose that the attached code MUST work.
if you mean the activation code for windows expiration, then it could be possible to be blocked, but since you're an authorized user, just call them to solve the misunderstanding :)

i don't think it can depend on vbox and even less it provides some solution

I bought it way back in 2002 so I guess it could be one of those blacklisted pirate codes. It's not the activation code, it's the product key to install Windows. However I gave up and just got a new mp3 player so I don't need Sonic Stage anymore. That program was bloat-tastic anyway. :guitar:

---

### Post by Ev1L on 2008-06-22
> **CH1C0 said:**
> I bought it way back in 2002 so I guess it could be one of those blacklisted pirate codes. It's not the activation code, it's the product key to install Windows. However I gave up and just got a new mp3 player so I don't need Sonic Stage anymore. That program was bloat-tastic anyway. :guitar:
if you bought it, you have the right to have a valid one (i don't remember any expiration date of licenses)

---

### Post by Ev1L on 2008-06-22
Well, it sorted out that the problem is either the partition size or the RAM size.
Since he plans to use windows quite a lot, it makes sense to have a bit bigger partition and more ram to make it fast, but in general, i am using xp with 192mb of RAM and partition of 4GB and it provides me all what Ubuntu is lacking (Office 2007 in the first place).

I have 2GB RAM here on laptop.

At work with 2GB RAM as well, i use Ubuntu with 3 other Ubuntu VM with 256MB RAM and it is still working quite well, so I am not sure about extending his RAM (which is always a good idea if possible) to assign more to XP.


> **Victormd said:**
> I probably wouldn't go over 10Gb, but it depends on what you're going to be using it for.

As for your memory, if you have 1.5GB RAM and you really want to use windows in a virtual machine, you should upgrade to at least 2GB and use at least 512MB for windows... this is for it to run. If you want it to run well, allocate 1Gb for windows.

If upgrading your ram isn't an option, I would allocate at least 512MB for windows



Yeah, I'm running Hardy on a P4 3.2GHz and have XP virtualized with 1GB RAM allocated to it. I haven't had to boot it for a while but it was Ok... no 3D acceleration so don't bother with games... :)



With XP you can activate it as many times as you'd like, as long as you only have one copy installed at a time. Vista on the other hand, once you activate it, if you need to reinstall, you have to call microsoft and get a new code.

---

### Post by alloftheabove on 2008-06-22
Hello, I just woke up a few minutes ago.  Thanks for all the replies!  I'm gonna try setting up a 30gb virtual hard drive for it with the ram I gave it and see how it goes.  Be back with the results.

---

### Post by alloftheabove on 2008-06-22
Ok I will mark this thread as solved.  Oh, and by the way, my activation code still works like you guys said, and the 30gb install is starting to wrap up!  I am happy.  Thank you, all of you for helping me!

---

