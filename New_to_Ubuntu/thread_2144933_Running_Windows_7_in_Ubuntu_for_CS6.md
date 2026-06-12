---
title: "Running Windows 7 in Ubuntu for CS6"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by brad12d3 on 2013-05-13
I have been wanting to try Ubuntu for a long time and the only thing holding me back is that Adobe CS6 is not compatible with this OS. However, I have been considering getting Ubuntu and running Windows 7 on a virtual machine. I just wonder if it's worth the trouble though and am I going to take a performance hit running windows inside Ubuntu? How easy is it to launch Windows inside Ubuntu? 

How I wish Adobe would make an Ubuntu version..

---

### Post by fantab on 2013-05-13
Before I made my move to Ubuntu I had similar apprehensions. What I did eventually was, **"Dual-Boot" Windows and Ubuntu**. Then I gradually got acclimatized to GIMP, Inkscape Openshot etc in Linux. I still have Windows on a HDD of its own, but it has been quite a while since I used Windows.

So... Instead of WUBI or VM its far better to do a 'true' Dual-Boot, (until some day you realize you've stopped using windows completely).

Browse through this: [http://linuxappfinder.com/graphics?page=1&sort=alpha](http://linuxappfinder.com/graphics?page=1&sort=alpha), you will find some interesting linux alternatives. 

Welcome to Ubuntu!
Regards...

---

### Post by brad12d3 on 2013-05-14
Thanks for the response. I am pretty invested in Adobe's software and use Premier, After Effects, and Photoshop extensively on professional projects. So unfortunately until Adobe decides to support Ubuntu I am going to have a need for Windows to run these programs. However, I might try a dual boot. What kind of resources will I be draining if I did a VM? Am I going to see a big difference between using it in straight windows vs Windows running in a VM?

I have a i7 2600k Sandy Bridge 3.4 GHz, 32 GB ram, two EVGA Geforce 670ti 4GB cards SLI, on an Asus p8z77 motherboard, running windows 7 pro.

It would be nice to switch over to my Adobe software without having to reboot.

---

### Post by squakie on 2013-05-14
The beauty is that you can dual-boot and try the virtual machine in the Linux "half", install your software there and try it out.  If it ends up being acceptable to you, you can always delete windows and expand Linux later.  I've run vm's (via virtualbox) for many types of OS's - including Windows XP and Windows 7 as many, many, many have done.  As long as your hardware is up to snuff it shouldn't be a problem.  The only drawback for you might be the video support.  It sure can't hurt to try it!

---

### Post by mastablasta on 2013-05-14
Hmm if Ubutnu (or rather nvidia) supports SLI it's instalation is probably not trivial.

you could run it in VM however for best performance in graphic intensive programmes it is better to use them in native environment. so Dual boot.

or install Ubuntu inside VM: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

that way you can use it for browsing, experiementing learning new OS and such with no slowdown or any issues with the original OS.

so you can do photoshopping and thne when you feel like it run ubuntu. you maschine should handle it nicely.

or mayb eeven install virtual desktops on windows 7 and then switch between OS. or have one os on one screen and the other os on another etc.

---

### Post by DuckHook on 2013-05-14
> **squakie said:**
> It sure can't hurt to try it!+1  I run both VMs and multi-boot machines and both fantab and squakie are correct: they can work marvelously for some, and not that well for others, but the beauty of Linux is that it costs you nothing other than some time and trouble to try. Because of your professional needs, I doubt that you will ever be able to completely sever your need for Windows. However, you may also find yourself using it less and less. As for VMs, they come in many different sorts and flavours. A VM like VirtualBox is easier to use but suffers performance penalties especially in the video department. However, a VM like Xen can run video almost like it runs on bare metal. This would give you almost native Windows performance inside a VM: the best of both worlds, so to speak. The cost is complexity: Xen is difficult to set up and very finicky about the HW it runs on.I would not recommend going the Xen route until you are more familiar with Linux. Besides, you may find user-friendly VMs like VirtualBox sufficient for your needs, especially as HW gets so fast that it renders the performance hit a non-issue.

---

### Post by brad12d3 on 2013-05-14
Thanks guys you have been very helpful. One other question. Let's say I want to give my HW an upgrade so that I can run a VM more efficiently.. What is taking the biggest hit when I am running a VM? How much strain am I putting on the cpu ? Would faster ram suffice initially?

---

### Post by DuckHook on 2013-05-14
Your HW is already high horsepower. Not surprising, given what you do professionally, but there's very little further upward potential at this point. I mean, dual bleeding-edge GeForce cards? What's to improve?

If you are finding 3D rendering to be only so-so with your current get up, then clearly, the diminished capacity of a traditional VM layer is not going to sit well. I hasten to note that this would be true only of traditional VMs like VirtualBox, which virtualize a (usually low-end) legacy video card. The advantage of Xen is that it passes your video through to the bare hardware, so that your Windows VM would be using native drivers and addressing the video card almost directly. It's a neat trick and very powerful, but it is complicated and very HW specific. Last I heard, Xen works well with AMD but not NVidia. Your GeForces could be problematic.

OTOH, if you are finding that your current HW has tons of room to spare, then a VM may actually yield acceptable performance. I run XP in a VirtualBox VM to play some old 2D games. On my modern box, the games run fine; sometimes even too fast. On my older boxes, they are sluggish. On my ancient boxes, it is painful and will often crash the VM. That reflects the performance curve that HW has taken this past decade.

With respect to your larger question, a VM has multiple bottlenecks. Which bottleneck bites you is highly dependent on your usage. With Web servers, it's usually the NIC. Fileservers, it's the disk array. With me, because I like simulations, it's the CPU. In your case, it will likely be the video subsystem. Faster RAM is not likely going to make much of a difference. And as mentioned, the rest of your system is already so maxed out that any additional improvement will not make a material difference either.

Rather than focusing on further HW tweaks, I second fantab/squakie/mastablasta. Start fooling around with actual dual boot and VM installation itself. Then you will be the one telling us what works/doesn't work rather than relying our our educated guesses.

Best of luck and Happy Ubuntuing!

---

