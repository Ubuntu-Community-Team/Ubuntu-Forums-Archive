---
title: "Ubuntu and Lubuntu 11.10 beta 2 in VirtualBox Issues"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by loukingjr on 2011-09-24
I just installed Lubuntu 11.10 b2 yesterday and the built in VirtualBox additions and drivers won't activate.

I installed Ubuntu 11.10b2 this morning and the VirtualBox drivers do activate, however Unity 3D doesn't seem to work. The screen and panels draw fine but when I try to open anything, Firefox, Nautilus, System Settings etc, you can't see them on the screen. Unity 2D seems to work though.

---

### Post by makitso on 2011-09-24
I run the beta in VB and do not see the problem.  Let me ask the obvious, 

Your using the 4.2.1 release of VB?
You have the full 128MB and 3d selected oo display?
You have the Guest Additions installed?

And last, once in VB and after running 11.10, under System Setting, Additional Drivers, you have the Addition actually running?

---

### Post by loukingjr on 2011-09-24
> **makitso said:**
> I run the beta in VB and do not see the problem.  Let me ask the obvious, 

Your using the 4.2.1 release of VB?
You have the full 128MB and 3d selected oo display?
You have the Guest Additions installed?

And last, once in VB and after running 11.10, under System Setting, Additional Drivers, you have the Addition actually running?

Yes, running the 4.1.2 release of VB.
Yes, 128MBs and 3D enabled.
Yes, it comes with them installed.

and last, yes once in VB I enabled the Additional VB drivers. However, I updated everything first before enabling them.

---

### Post by makitso on 2011-09-24
"It comes with them installed"  The Guest Additions have to be build for the kernel release -- thus one has to select them from Drivers.  You know their working if you can change the size of your desktop once into the Guest.  I know under Fedora I needed to manually install them step by step

Try unchecking the 3D driver box, booting the guest, then exit, recheck the 3d box

---

### Post by loukingjr on 2011-09-24
nope, didn't work. I am running the 64bit version of Ubuntu 11.10b2 btw.

edit: the additions were working. I could resize the screen, run full screen, shared folders are working, mouse integration etc.

---

### Post by loukingjr on 2011-09-24
I tried disabling the GA's, rebooting then re-enabling them, rebooting once more. Didn't help. I can actually see whatever windows I had opened for a brief second when logging out of 3D.

beats me.

---

### Post by dino99 on 2011-09-24
everyone knows about 64 bits headaches in many cases, why are you still using it ?

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by loukingjr on 2011-09-24
> **dino99 said:**
> everyone knows about 64 bits headaches in many cases, why are you still using it ?

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)
that was helpful.

---

### Post by makitso on 2011-09-24
Yea, 64 bit works.  I upgraded from 10.04 32bit to 11.04 64 bit about a week ago and I have found nothing that is a problem.  Now I have 8GB available for memory and VB no longer locks up on the Ubuntu 11.10 Guest.

---

### Post by loukingjr on 2011-09-24
I have no idea what the problem is. Unity 3D works fine in Ubuntu 11.04 64bit. I don't have  clue why it doesn't with Ubuntu 11.10 64bit.

---

### Post by thatguruguy on 2011-09-24
> **dino99 said:**
> everyone knows about 64 bits headaches in many cases, why are you still using it ?

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

I run the 64-bit version of the OS because I do stuff like video processing, which is a LOT faster when run on a 64-bit platform.  Using PAE allows addressing memory beyond the 4 gigabyte limitation of 32-bit OSes, but it does noting to allow additional threads being run.

If you think that there is no difference, performance-wise, between running a multi-threaded application on a 64-bit OS vs. running the same application on a 32-bit OS with PAE enabled, you are significantly mis-informed.

---

### Post by makitso on 2011-09-24
I have the same setup as you do.  As an FYI, I also have Fedora 15 running in VB.  I had some troubles getting full G3  as well.  After doing all of the above I unchecked the Display 3D box and rebooted the entire thing and then quit all and reset the 3D bit and then it worked.  As a side note, the Fedora install requires some additional kernel drivers to be loaded and a manual run of the driver sh.

---

### Post by loukingjr on 2011-09-24
> **makitso said:**
> I have the same setup as you do.  As an FYI, I also have Fedora 15 running in VB.  I had some troubles getting full G3  as well.  After doing all of the above I unchecked the Display 3D box and rebooted the entire thing and then quit all and reset the 3D bit and then it worked.  As a side note, the Fedora install requires some additional kernel drivers to be loaded and a manual run of the driver sh.

well, just to try it I installed the 32bit version and it does exactly the same thing, except for the fact that in the 64bit version, I can log into gnome, gnome classic (with or without effects), Ubuntu and Unity 2D. The odd thing is in the 32bit version I only have Ubuntu and Unity 2D listed

. as far as 64bit vs 32 I agree, 64bit versions of various Linux guests I run are significantly faster.

I have Fedora 15 running G3 just fine.
[IMG]http://www.linuxscreenshotsforum.com/download/file.php?id=2445&t=1[/IMG]

[IMG]http://www.linuxscreenshotsforum.com/download/file.php?id=2443&t=1[/IMG]
edit: I'm not sure we have the same exact set up btw, I'm running an iMac with an i7.

---

### Post by BrownieBoy on 2011-09-27
I had the same problem with 11.10 32-bit guest running in a 11.04 64-bit host.

I confirmed 3D was working in the guest: glxgears gave me nearly 400fps in the guest.  Yet I could only get Unity 2D to appear there.

When I looked in Additional Drivers, it showed that "Oracle VM VirtualBox Guest Additions for Linux Module" was enabled, but I don't think that it really was.  I clicked on something in that dialog unil I got another dialog saying that the driver was being downloaded and installed.  I let this second dialog do its thing then rebooted, and voila: Unity 3D in the guest!

---

### Post by loukingjr on 2011-09-27
that's not my problem. as I said, I can login to Unity 3D just fine. however, other than the dash I can see no windows when they open.

edit: I thought visual aids might help...

Unity 3D open and running...
[IMG]https://lh5.googleusercontent.com/-AAI6ws87thI/ToGd33UIAKI/AAAAAAAAJgM/rDJMK-7YlF4/s640/Screeny%252520Shot%252520Sep%25252027%25252C%2525202011%2525205.38.37%252520AM.png[/IMG]
Unity 3D with dash...(sorry bout the Mac task bar, I wasn't fast enough)
[IMG]https://lh5.googleusercontent.com/-zndWOHgeG7w/ToGd30gkk9I/AAAAAAAAJgQ/1Dw2HkPIQY8/s640/Screeny%252520Shot%252520Sep%25252027%25252C%2525202011%2525205.38.02%252520AM.png[/IMG]
Unity 3D with FF and Nautilus open. As you can see, (well not see), the windows don't display. I can click where the window is suppose to be and bring up the menu as hopefully you can see.
[IMG]https://lh5.googleusercontent.com/-AAI6ws87thI/ToGd33UIAKI/AAAAAAAAJgM/rDJMK-7YlF4/s640/Screeny%252520Shot%252520Sep%25252027%25252C%2525202011%2525205.38.37%252520AM.png[/IMG]

btw, sometimes I can log into Gnome3, sometimes not...
[IMG]https://lh4.googleusercontent.com/-XRQHzBMfaAo/ToGd4FUmRcI/AAAAAAAAJgU/ZwhkIpgss0w/s640/Screeny%252520Shot%252520Sep%25252027%25252C%2525202011%2525205.50.27%252520AM.png[/IMG]
I also cannot log in Gnome classic with Compiz running.

---

### Post by amjjawad on 2011-09-27
**Real** Test could be done only when you install it on your Hard Drive as a normal installation.

I've been testing Lubuntu 11.10 Beta 2 for two days now and reported some bugs. That's the best way to do that.

---

### Post by loukingjr on 2011-09-27
> **amjjawad said:**
> **Real** Test could be done only when you install it on your Hard Drive as a normal installation.

I've been testing Lubuntu 11.10 Beta 2 for two days now and reported some bugs. That's the best way to do that.

no way jose. :p
besides, there are others running it in VB without issue apparently. I think I found the problem though. will know shortly.

---

### Post by Jason86 on 2011-09-27
i had the same problem, where i didn't see anything on the desktop, but i saw the open programs in "Workspaces".  Re-installing fixed the problem. After installing ubuntu, install the updates before installing the guest additions.

---

### Post by amjjawad on 2011-09-27
> **loukingjr said:**
> no way jose. :p
besides, there are others running it in VB without issue apparently. I think I found the problem though. will know shortly.

How many will do normal installation and use Lubuntu on daily basis VS how many will install it on VB for testing or whatever reason? 

That's my point :)

---

### Post by loukingjr on 2011-09-27
> **amjjawad said:**
> How many will do normal installation and use Lubuntu on daily basis VS how many will install it on VB for testing or whatever reason? 

That's my point :)
well it's a valid point. I however only run Linux in VB :D

Lubuntu is running fine now that I took out the included VB modules and installed the Oracle additions. Xubuntu 11.10b2 is also working. I'm just having an issue with the Ubuntu version and I suspect it's the new Compiz.

---

### Post by amjjawad on 2011-09-27
> **loukingjr said:**
> well it's a valid point. I however only run Linux in VB :D

Ok, that explains a lot :)
So you are a Windows User if I may say that?

> Lubuntu is running fine now that I took out the included VB modules and installed the Oracle additions.

Good to know :)

---

### Post by loukingjr on 2011-09-27
> **amjjawad said:**
> Ok, that explains a lot :)
So you are a Windows User if I may say that?



Good to know :)

nope, although I run Windows XP and 7 in VB. I am a Mac user since late '85

currently running OSX 10.7 Lion on an iMac Quad Core i7 with 12GB of ram.

Lubuntu 11.10b2 running in VB...
[IMG]http://www.linuxscreenshotsforum.com/download/file.php?id=2708&t=1[/IMG]

---

### Post by amjjawad on 2011-09-27
> **loukingjr said:**
> nope, although I run Windows XP and 7 in VB. I am a Mac user since late '85

currently running OSX 10.7 Lion on an iMac Quad Core i7 with 12GB of ram.

Lubuntu 11.10b2 running in VB...


One of my dreams is to own a Mac but as long as I'm jobless, it's like Mission Impossible Part 5 :D

---

### Post by seattle vic on 2011-09-28
I've had a similar problem, in that I'm running 11.10 as both a guest and host.  I upgraded VB to 4.1.2 and when I try and run the guest additions from a shell, nothing happens.  It immediately goes back to a prompt.

I did see a reference to 4.2.1, but cannot find that version of the virtualbox website.

Anybody else having problems like this?

---

