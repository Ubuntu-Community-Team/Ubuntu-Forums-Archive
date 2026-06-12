---
title: "VMware Player Vs. Virtualbox"
date: 2010-04-28
forum: Recurring Discussions
---

### Post by Dportner on 2010-04-28
hey there
k so im just curious as to which virtual machine you guys prefer? iv read acouple of comparisons and i would just like some user input from other ubuntu users as to which one they like better

il be putting windows 7 professional on the virtual machine (i got a free cd key from my college :P)

---

### Post by CharlesA on 2010-04-28
I like VBox.. I tried VMWare server but it was a pain in the backside to get running (and it wouldn't start the VM for me).

VBox "just works" for me - added it from the virtualbox.org repos.

VMWare has a bit more features then VBox.

---

### Post by carl4926 on 2010-04-28
+1 to virtual box

---

### Post by .:PiXi²:. on 2010-04-29
VirtualBox runs faster than VMware. And I agree with CharlesA, just install and you're ready to go.
If you have some more time, try [KVM]("http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine"), it runs even faster, but it needs some tweaking.

---

### Post by Dportner on 2010-04-29
oh and another question.

do u guys think i should wait till i upgrade to 10.04 to install the vm?
or does it really matter? :/

---

### Post by CharlesA on 2010-04-29
Are you going to use 10.04 as the host or guest?

EDIT: Duh me. It shouldn't really matter. virtualbox.org doesn't have a repo for Lucid yet, but I've heard that the repo for Karmic works fine.

---

### Post by .:PiXi²:. on 2010-04-29
That shouldn't matter.

---

### Post by Dportner on 2010-04-29
it will be the host.
like linux will always be my main OS now :]

i just want a vm for certain things like my blackberry and ipod and a buncha other stuff.
cuz blackberry support on linux isnt the greatest :/
and Barry doesnt make sense to me lol.
plus, it would be cool to have a virtual machine :]

---

### Post by bpalone on 2010-04-29
If you go the VirtualBox route, be sure to get it from [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads").  The open source version does not have USB support, so get the PUEL version.

---

### Post by maddg3241 on 2010-04-29
I prefer VirtualBox more that any other

---

### Post by ttshivers on 2010-04-29
> **maddg3241 said:**
> I prefer VirtualBox more that any other

I also prefer VirtualBox over VMware Player because it has a simpler and easier to understand user interface.

---

### Post by _0R10N on 2010-04-29
I've worked with virtualized environments under both, Windows and Linux for a few years. On Windows I ran VirtualBox and VMWare. On Linux Qemu and VirtualBox. I got the best performance running VirtualBox in Linux. But, beware, you need to install de OSE vesion in order to have some features like USB support.

Kind regards!

_0R10N >>

---

### Post by Objekt on 2010-04-29
> **_0R10N said:**
> I've worked with virtualized environments under both, Windows and Linux for a few years. On Windows I ran VirtualBox and VMWare. On Linux Qemu and VirtualBox. I got the best performance running VirtualBox in Linux. But, beware, you need to install de OSE vesion in order to have some features like USB support.

Kind regards!

_0R10N >>

You mean the Personal Use and Evaluation License (PUEL) version.  The Open Source Edition (OSE) of Virtualbox does not include USB device support.

I ran into that one when I was hosting an awful Winprinter on a virtual XP machine.  Stupid Canon and their complete lack of Linux support.

---

### Post by dabl on 2010-04-29
I'm a happy VMware Player user.  I have had a Win XP VM for several years.  A couple weeks ago I made a Win 7 VM and it is running fine, too.

I haven't tried VBox for over a year.  The one time I tried it I never made it all the way to "works", and the lack of USB support at that time was deal killer anyway. I'm sure it's better now.

---

### Post by bodhi.zazen on 2010-04-29
I prefer KVM - It is open source and you have a number of choices on running guests from  command line to virsh to virt-manager.

KVM is easier to keep up to date.

The downside is you need the hardware to support KVM and KVM lacks a little in the graphics (no 3d easily available) and you can not copy / paste between guest and host the way you can with VBox and VMWare.

It does lack a few features, but none that are a show stopper for me.

VMWare player != VMWare server and player is lighter weight and more efficient on system resources then server or workstation, although it has less features then server.

Server also varies with version, 1.x is IMO more stable and more functional then 2.x.

However, VMWare player/server/workstation can be frustrating to continuously tinker with with every kernel update on unsupported OS (kernels) such as Ubuntu.

VBox is available in the repositories as OSE or PUEL , in general, PUEL has a few more features and in general is less hassle then VMWare.

---

### Post by Leppie on 2010-04-29
> **bodhi.zazen said:**
> VBox is available in the repositories as OSE or PUEL
how do you get the puel version from the repos? i've only seen the ose version in repos and downloaded the puel version from the virtualbox site.

---

### Post by carl4926 on 2010-04-29
Check this page
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

part way down and to end

---

### Post by _0R10N on 2010-04-29
> **objekt said:**
> you mean the personal use and evaluation license (puel) version.  The open source edition (ose) of virtualbox does not include usb device support.

I ran into that one when i was hosting an awful winprinter on a virtual xp machine.  Stupid canon and their complete lack of linux support.

i fail! :(

---

### Post by _0R10N on 2010-04-29
> **carl4926 said:**
> Check this page
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

part way down and to end

Don't forget the following finger-print, also available in the same page.

```

AF45 1228 01DA D613 29EF  9570 DCF9 F87B 6DFB CBAE
Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>

```

_0R10N >>

---

### Post by bodhi.zazen on 2010-04-29
> **Leppie said:**
> how do you get the puel version from the repos? i've only seen the ose version in repos and downloaded the puel version from the virtualbox site.

I think you misunderstood what I am said.

PUEL is not in the Ubuntu repos, it is what one downloads from the Sun (Virtual Box) site.

Ubuntu repos -> OSE
Sun (Virtualbox) web site / repository -> OSE or PUEL

If you look on the virtualbox download page:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You will see they maintain a repository as well, which you may add to /etc/apt/sources.list if you wish.

---

### Post by bodhi.zazen on 2010-04-29
> **Objekt said:**
> You mean the Personal Use and Evaluation License (PUEL) version.  The Open Source Edition (OSE) of Virtualbox does not include USB device support.

I ran into that one when I was hosting an awful Winprinter on a virtual XP machine.  Stupid Canon and their complete lack of Linux support.

It was possible in the past to manually configure USB support with the OSE. Now it may be that SUN has disabled these "hacks", I do not know.

---

### Post by FunkyChicken on 2010-04-30
I'm using a 64 bit lucid host with the virtual box 3.2 beta to run win7 guest and it works great. + 1 vbox.

---

### Post by ayates on 2010-04-30
I've been using Vmplayer for a few years now and I've always found it to be faster than Virtualbox.
YMMV though.

---

### Post by Calash on 2010-04-30
If you have access to it, VMWare Workstation is an incredible product.  That aside my number 1 choice, as many have already said, is Virtualbox PUEL.  Have to manage your updates via .deb files but it does a good job alerting you when a new version is available.

---

### Post by bodhi.zazen on 2010-04-30
> **Calash said:**
> If you have access to it, VMWare Workstation is an incredible product.  That aside my number 1 choice, as many have already said, is Virtualbox PUEL.  Have to manage your updates via .deb files but it does a good job alerting you when a new version is available.

No you do not, there is a repository you may add to /etc/apt/sources.list

It is listed on the [VirtualBox downloads page]("http://www.virtualbox.org/wiki/Linux_Downloads")

> 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) gutsy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) dapper non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) etch non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) sarge non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian)  xandros4.0-xn non-freeI imagine there will be a lucid repo soon enough, for now I would imagine the karmic repo would work.

---

### Post by CharlesA on 2010-04-30
I can vouch for the karmic version working on Lucid. Haven't had any problems (just needed to import the VM and it was off and running)

---

### Post by bgreenaway on 2010-04-30
Big +1 for VirtualBox and very simple to use. Running Lucid 10.04 in a VM on a Win7 host and it runs very nicely.

---

### Post by venik212 on 2010-04-30
Same here-- Vbox worked much better than VMware on my 64 bit Kubuntu.

---

### Post by Chrysantine on 2010-04-30
Depends on your needs - for us commercial business users (yes, I have red horns and spout noxious fumes) VMWare plows Virtualbox off the map due to centralized management and ability to do tricks like move virtual machines from one system to another without taking down the system (ESX/i).

However, I've found VBox to be slightly faster on single system installations so if you're just going to run it at home, I'd say VB might be better choice - YMMV.

---

### Post by CharlesA on 2010-04-30
> **Chrysantine said:**
> Depends on your needs - for us commercial business users (yes, I have red horns and spout noxious fumes) VMWare plows Virtualbox off the map due to centralized management and ability to do tricks like move virtual machines from one system to another without taking down the system (ESX/i).

However, I've found VBox to be slightly faster on single system installations so if you're just going to run it at home, I'd say VB might be better choice - YMMV.
Agreed, using VMWare on an enterprise level rocks (my company uses it).

It makes me wonder what the host OS is, since I had a hell of a time trying to get VMWare Server running on an Ubuntu box.

---

### Post by bodhi.zazen on 2010-04-30
> **CharlesA said:**
> It makes me wonder what the host OS is, since I had a hell of a time trying to get VMWare Server running on an Ubuntu box.

ESX/i

[http://www.vmware.com/products/esx/](http://www.vmware.com/products/esx/)

> VMware ESX and VMware ESXi are “bare-metal” hypervisors, meaning they  install directly on top of the physical server and partition it into  multiple virtual machines that can run simultaneously, sharing the  physical resources of the underlying server.

I agree, Enterprise level virtualization is a different animal then home use of VirtualBox.

---

### Post by CharlesA on 2010-04-30
Ah hah. That would be why it works so well.

Also explains why you need to use vSphere client to configure and use the VMs.

---

### Post by ChemicalForce on 2010-05-01
I prefer virtualbox because it's simple it works out of the box.

---

### Post by AlexanderDGreat on 2011-03-26
Sorry to kill the VirtualBox party. BUT I've terrible experience with VirtualBox - we still use a Fax modem, and I bought nearly 5 usb modems, ALL OF THEM FAIL in VirtualBox.

Now, I switched to VMware Player (free) - which can now install a guest, ALL 5 OF MY USB External Modems WORKS Like a Charm! **Amazing USB Support.**

Unity is amazing, you know what?

You can't DRAG AND DROP files Between HOST Ubuntu and Guest VirtualBox...

Guess what?

YOU CAN **DRAG AND DROP files** Between HOST Ubuntu and GUEST VMWare.

One more...

I have **DUAL Monitors**, when USING VirtualBox's VBox Tools, it's such a pain in the *** to setup the FULL Screen Windows in your right, Ubuntu on your left thingy Desktop.

You guessed it.

VMWare - one-click And you WILL HAVE Windows and Ubuntu -side by side- (I need MS Word vs OpenOffice that's why)... Dual Monitors is so easy with VMware (with matching Full Screen). VBox just confuses the hell out of you with X11, it's really hit and miss.

There's even a LONG Tutorial how to do this in our community, BUT in VMWare, it's just an icon and it's magic.

Sorry for sounding so biased with VMWare... but it's the truth, I'll never gain anything by tricking you guys. I don't work for VMWare.

Finally...

Can you **play games** on VirtualBox?

NO.

But on Vmware. You know the answer.

If that won't convince you, just try it, I've RUN ONLINE GAMES, cashflow, capitalism, emulators, and what have you. That's all.

Really, my last observation...

You can PUT a **Bios Password** on Your Guest Machines, I really had trouble with security with VirtualBox, as there's NO WAY TO PROTECT your Virtual Machines, when users want to TINKER with them via "BOOT FROM CD" option in the Bios.

I sent numerous email to VirtualBox and the Community about this, their answer is simply in the tone of, Well, that shouldn't be one of your concerns, you're probably PARANOID. Geesh...

With VMware again, just put a password on the BIOS menu, then you can sleep soundly at night. :)

Hands down, I would recommend VMWare Player / Workstation over VirtualBox anytime of the day.

**VMware WINS OVER VirtualBox - No doubt about it.**

How about cons?

The only thing I don't like about VMware - from what I've heard ONLY, not real experience, every time you do a kernel update / upgrade, you'll have to reinstall it. Is it true?

But ask yourself, is it worth it? Yes, definitely, anyway, it has a one-two-three click process to install via a nice GUI.

Plus, I don't even update my kernel anymore, they break your system and boot you to a grub> prompt if you're unlucky. (had 2 experiences).

I'm sure there's tons of pros and cons more, but VMware just works better for me really.

---

### Post by Cracklepop on 2011-03-26
> **AlexanderDGreat said:**
> Sorry to kill the VirtualBox party.

-- snip --

   You make me want to try vmware next time I install a vm...

EDIT: Perhaps not... Is vmware free? Is the client in the repos all I need?  Confused...now I remember why I chose vbox ;)

---

### Post by johntaylor1887 on 2011-03-27
> **Cracklepop said:**
> You make me want to try vmware next time I install a vm...

EDIT: Perhaps not... Is vmware free? Is the client in the repos all I need?  Confused...now I remember why I chose vbox ;)

It doesn't appear to be free. Screw that.

---

### Post by NightwishFan on 2011-03-27
I have always liked virtualbox. It certainly lets me play games and etc. I do not know about usb support or whatever, but it sounds like the things you want to do with it are possible just not by default. And if they arent possible its just not a goal for the software. Use what works.

---

### Post by AlexanderDGreat on 2011-03-27
Yes VMware Player is 100% FREE. VMware workstation is the one NOT Free because it has extra features like snapshots, etc...

But nothing like a deal-breaker. I don't trust snapshots anyway, it's just too risky for the un-techie user. I just backup VM's every week.

**I can confirm I can play Warcraft 3 in VMware Player.**

---

### Post by SeijiSensei on 2011-03-27
> **AlexanderDGreat said:**
> Sorry to kill the VirtualBox party. BUT I've terrible experience with VirtualBox - we still use a Fax modem, and I bought nearly 5 usb modems, ALL OF THEM FAIL in VirtualBox.

Now, I switched to VMware Player (free) - which can now install a guest, ALL 5 OF MY USB External Modems WORKS Like a Charm! **Amazing USB Support.**

Were you using the version of VirtualBox at Oracle's site, or the one in the repositories?  The open-source "OSE" version is well-known not to support USB; the proprietary, but free-for-non-commercial-use [version at Oracle]("http://www.virtualbox.org/wiki/Linux_Downloads") supports USB.

> You can't DRAG AND DROP files Between HOST Ubuntu and Guest VirtualBox...

Create a "shared folder" or use a network file share.

---

### Post by 3177 on 2011-03-27
> **AlexanderDGreat said:**
> Sorry to kill the VirtualBox party. BUT I've terrible experience with VirtualBox - we still use a Fax modem, and I bought nearly 5 usb modems, ALL OF THEM FAIL in VirtualBox.

Now, I switched to VMware Player (free) - which can now install a guest, ALL 5 OF MY USB External Modems WORKS Like a Charm! **Amazing USB Support.**

Unity is amazing, you know what?

You can't DRAG AND DROP files Between HOST Ubuntu and Guest VirtualBox...

Guess what?

YOU CAN **DRAG AND DROP files** Between HOST Ubuntu and GUEST VMWare.

One more...

I have **DUAL Monitors**, when USING VirtualBox's VBox Tools, it's such a pain in the *** to setup the FULL Screen Windows in your right, Ubuntu on your left thingy Desktop.

You guessed it.

VMWare - one-click And you WILL HAVE Windows and Ubuntu -side by side- (I need MS Word vs OpenOffice that's why)... Dual Monitors is so easy with VMware (with matching Full Screen). VBox just confuses the hell out of you with X11, it's really hit and miss.

There's even a LONG Tutorial how to do this in our community, BUT in VMWare, it's just an icon and it's magic.

Sorry for sounding so biased with VMWare... but it's the truth, I'll never gain anything by tricking you guys. I don't work for VMWare.

Finally...

Can you **play games** on VirtualBox?

NO.

But on Vmware. You know the answer.

If that won't convince you, just try it, I've RUN ONLINE GAMES, cashflow, capitalism, emulators, and what have you. That's all.

Really, my last observation...

You can PUT a **Bios Password** on Your Guest Machines, I really had trouble with security with VirtualBox, as there's NO WAY TO PROTECT your Virtual Machines, when users want to TINKER with them via "BOOT FROM CD" option in the Bios.

I sent numerous email to VirtualBox and the Community about this, their answer is simply in the tone of, Well, that shouldn't be one of your concerns, you're probably PARANOID. Geesh...

With VMware again, just put a password on the BIOS menu, then you can sleep soundly at night. :)

Hands down, I would recommend VMWare Player / Workstation over VirtualBox anytime of the day.

**VMware WINS OVER VirtualBox - No doubt about it.**

How about cons?

The only thing I don't like about VMware - from what I've heard ONLY, not real experience, every time you do a kernel update / upgrade, you'll have to reinstall it. Is it true?

But ask yourself, is it worth it? Yes, definitely, anyway, it has a one-two-three click process to install via a nice GUI.

Plus, I don't even update my kernel anymore, they break your system and boot you to a grub> prompt if you're unlucky. (had 2 experiences).

I'm sure there's tons of pros and cons more, but VMware just works better for me really.

It seems you only tried running virtualbox OSE, and no it has no usb support. As for games, I run all the windows games wine cant handle. I use ubuntuone to move my stuff from system to virtual-system. I dont remember the name of the other virtualbox though, I think it starts with an f(other than OSE).

---

### Post by Sporkman on 2011-03-27
Virtualbox (downloaded from oracle, with non-free plugins) works great for me, both on the desktop and as headless virtual servers.

---

### Post by johntaylor1887 on 2011-03-27
I just tried VMware Player for the first time, and have to say it works well, but I don't notice any difference from virtualbox. Whoever said you could play games on it would be wrong, unless you are talking about *very* basic games. 3D pinball ran at about 2 frames a second. :(

But for general usage, I don't see any advantage for either virtual platform, as they both work well and do the same thing.

---

### Post by 3177 on 2011-03-27
> **johntaylor1887 said:**
> I just tried VMware Player for the first time, and have to say it works well, but I don't notice any difference from virtualbox. Whoever said you could play games on it would be wrong, unless you are talking about *very* basic games. 3D pinball ran at about 2 frames a second. :(

But for general usage, I don't see any advantage for either virtual platform, as they both work well and do the same thing.


diablo 2 runs at a solid 52 fps on OSE.

---

