---
title: "Run Windows under Linux"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2011-11-15
Hey,

what is the best way to run a fully functional Windows 7 x64 under Ubuntu? Using VmWare or something equivalent seems to be the best solution. Are there any system performance issues (i wont need every single FPS while playing computer games or other applications) with it?

I need to run Applications like Inventor 2011, AutoCAD, ......

Thanks

---

### Post by ofnuts on 2011-11-15
> **Krabby.Linux said:**
> Hey,

what is the best way to run a fully functional Windows 7 x64 under Ubuntu? Using VmWare or something equivalent seems to be the best solution. Are there any system performance issues (i wont need every single FPS while playing computer games or other applications) with it?

I need to run Applications like Inventor 2011, AutoCAD, ......

ThanksYour best bet is "VirtualBox". There are several "editions" out there, IIRC the "Open source edition" is on your Ubuntu repository.

---

### Post by lukeiamyourfather on 2011-11-15
You will likely run into issues with those applications as they use hardware acceleration for the graphics. Virtual machines don't handle this very well. VirtualBox does have a hardware accelerated graphics feature but is experimental and has many limitations.

[http://www.virtualbox.org/manual/ch04.html#guestadd-3d](http://www.virtualbox.org/manual/ch04.html#guestadd-3d)

They may work just fine but if they don't the best option would probably be to dual boot with Windows.

---

### Post by drmrgd on 2011-11-15
I would fully agree, and also add that you'll need a ton of RAM in your box in order to handle running the two OSes at once. I think dual booting would be the best option for you if you want to run graphics and memory intense applications.

---

### Post by Krabby.Linux on 2011-11-15
Dual Boot sucks because i dont want to boot up to 20 times a day just to use other programs.

What about running Ubuntu inside Windows? Better choice?

---

### Post by mylesg on 2011-11-15
> **Krabby.Linux said:**
> Dual Boot sucks because i dont want to boot up to 20 times a day just to use other programs.

What about running Ubuntu inside Windows? Better choice?

For what it's worth, that's the way I'm doing it (for much the same reasons) and it works quite nicely for me.

---

### Post by carranty on 2011-11-15
> **Krabby.Linux said:**
> Dual Boot sucks because i dont want to boot up to 20 times a day just to use other programs.

What about running Ubuntu inside Windows? Better choice?

To be honest, if you're really that dependent on Windows I'd stick with windows and not use Ubuntu.  What windows programs are you using, it may be that there are alternatives available that run in Ubuntu.

---

### Post by Jacobonbuntu on 2011-11-15
No matter which OS is the first one, the OS running *under *another one is limited by definition. The hardware is approached indirectly, and a lot of functionality is derived from the 1st OS. The weakest shackle defines the strength.

---

### Post by Krabby.Linux on 2011-11-15
> **carranty said:**
> To be honest, if you're really that dependent on Windows I'd stick with windows and not use Ubuntu.  What windows programs are you using, it may be that there are alternatives available that run in Ubuntu.

There are lots of similar Programs but not usable for me. I need tons of Electronic and Mechanical Software like Eagle, Inventor AutoCaD etc etc. ALL the alternatives suck very very very hard. There is a reason why these programs usually have costs between 1000$ to 50000$ :-)

---

### Post by 11jmb on 2011-11-15
I agree that dual booting is a pain. perhaps you might want to try the inverse: an Ubuntu VM on a native Windows install

---

### Post by ofnuts on 2011-11-15
> **drmrgd said:**
> I would fully agree, and also add that you'll need a ton of RAM in your box in order to handle running the two OSes at once. I think dual booting would be the best option for you if you want to run graphics and memory intense applications.Depends a bit what you run. I spend most of my work day with a 3GB Windows VB. That leaves 500MB to the Linux apps, but that's more than enough for the run-of-the-mill sutff (mail, web, openoffice...).

---

### Post by greendragons on 2011-11-15
By using virtual machine u'll degrade the performance of both the OS... dual boot is best option...
Even i have to work on visual studio... it's resource intensive application i can't use it with windows installed on vmware or virtual box running on top of ubuntu and expect to run smoothly.....

---

### Post by drmrgd on 2011-11-15
> **ofnuts said:**
> Depends a bit what you run. I spend most of my work day with a 3GB Windows VB. That leaves 500MB to the Linux apps, but that's more than enough for the run-of-the-mill sutff (mail, web, openoffice...).

No doubt about it.  I was just concerned about the programs the OP wanted to run.  I could be wrong, but they seem like much more memory intense programs than just the run-of-the-mill stuff, which is why I suggested he might need a ton of RAM. For routine work, your suggestion would be just fine :)

---

### Post by haqking on 2011-11-15
I am running Debian x64 with 4GB Ram.

I currently have clementine running playing music, evolution open and minimised.  Qbitorrent currently downloading, signed in to Xchat.

I have 2 VM's open, one is XP with 512 Mb ram, running skype where i am using a webcam currently chatting to my buddy in US and i have photoshop minimised as i was working on a jpeg.

My other VM is running Ubuntu 11.10 with 768 MB ram assigned which i keep minimised to troubleshoot the usual "blah blah blah 11.10 dont do this and that" questions on the forum.

Everything is running with no issues and my current resources on host are 1.8 gb memory being used of the 4, 1 cpu is at 42% the other 12% and no swap is being used.

all good in the hood with vbox here ;-)

---

### Post by ofnuts on 2011-11-15
> **drmrgd said:**
> No doubt about it.  I was just concerned about the programs the OP wanted to run.  I could be wrong, but they seem like much more memory intense programs than just the run-of-the-mill stuff, which is why I suggested he might need a ton of RAM. For routine work, your suggestion would be just fine :)I run Websphere Integration Developer (a mutant cousin of Eclipse) in the Windows VB. Doesn't feel any worse than running iit native :) Might even be better...

---

### Post by drmrgd on 2011-11-15
Heh! I stand corrected.  I'm not sure why it's always so sluggish for me on my end.  Looks like it might be time for a new computer.  Now taking donations...  

Thanks guys!

---

### Post by 11jmb on 2011-11-15
I don't know what kinds of 3D graphics OP's programs require, but if you are just concerned with memory and CPU resources, you should almost definitely be fine.

---

### Post by ofnuts on 2011-11-15
> **drmrgd said:**
> Heh! I stand corrected.  I'm not sure why it's always so sluggish for me on my end.  Looks like it might be time for a new computer.  Now taking donations...  

Thanks guys!Make sure you have the virtual machine stuff enabled in the BIOS. Without it the VBOX crawls (a good test without looking at the BIOS is to try to assign more than one CPU to the VBox).

---

### Post by lukeiamyourfather on 2011-11-29
> **mylesg said:**
> For what it's worth, that's the way I'm doing it (for much the same reasons) and it works quite nicely for me.

In situations where I must use Windows I usually just install Cygwin. While not Linux it makes a lot of tasks easier on Windows (for example backing up files with rsync).

---

### Post by lolpenguin on 2011-11-30
Have you tried Wine? It provides a native emulation layer for Windows executables to run on, and makes full use of your hardware capabilities (in fact, the executables even show up in System Monitor!)

---

### Post by haqking on 2011-11-30
> **Krabby.Linux said:**
> Hey,

what is the best way to run a **fully functional** Windows 7 x64 under Ubuntu? 

I need to run Applications like **Inventor 2011, AutoCAD,** ......

Thanks

> **lolpenguin said:**
> **Have you tried Wine**? It provides a native emulation layer for Windows executables to run on, and makes full use of your hardware capabilities (in fact, the executables even show up in System Monitor!)

If you read the OP, he wants fully functional windows, that is not Wine.

They also want [Inventor 2011]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19752") ([WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19752") rates as garbage) and [Autocad ]("http://appdb.winehq.org/appview.php?appId=86")(Most recent versions on [WineHQ]("http://appdb.winehq.org/appview.php?appId=86") are also rated garbage)

Cheers

---

### Post by drmrgd on 2011-11-30
> **ofnuts said:**
> Make sure you have the virtual machine stuff enabled in the BIOS. Without it the VBOX crawls (a good test without looking at the BIOS is to try to assign more than one CPU to the VBox).

Wow!  This thread is still alive!

Anyway, thanks for the tip.  I didn't realize that option was available.  Alas, though, my system is a little too old, and there are no virtualization options in my BIOS.  My work computer is quite a bit newer, and once I adjusted my BIOS settings, the virtual machine is screaming along.

---

### Post by gordintoronto on 2011-11-30
Here's the option I like: two computers with a KVM switch. A small box to run Kubuntu doesn't cost very much.

---

