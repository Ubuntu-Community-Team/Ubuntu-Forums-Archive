---
title: "Has anyone tried Open Solaris?"
date: 2008-05-06
forum: Other OS Talk
---

### Post by the yawner on 2008-05-06
I've been reading the developments of project Indiana but I haven't really tried it. Now they've announced their first stable release, has anyone tried it out yet?

---

### Post by LeoSolaris on 2008-05-06
I'm going to give it a try now. I have been sorta curious for a while. It must be the late hour, but I want to try everything just because it's there. Somewhere around here I put that FreeBSD CD...

---

### Post by regomodo on 2008-05-06
tried to. Couldn't get it to work in Virtualbox after, what appeared to be, the worlds longest licence agreement
[edit] Got it top work. I'm a bit shocked. I upped the ram available to the VM from 240 to 512MB. Wow, 402MB used to tell me the time. Erm, i think i wont bother.

---

### Post by inportb on 2008-05-06
Isn't that ironic, now... OpenSolaris doesn't work on Virtualbox? =p

---

### Post by regomodo on 2008-05-06
> **inportb said:**
> Isn't that ironic, now... OpenSolaris doesn't work on Virtualbox? =p

gentoo's virtualbox is one version behind, for some reason

---

### Post by ibutho on 2008-05-06
I tried it and I think its very impressive. The main problem I had is that it seems to be lacking drivers for my network card (via rhine) and audio (basic sis ac97 card) out of the box. In the past I installed Solaris on a different machine and everything worked successfully. That machine had a realtek network card and intel ac97 sound.

---

### Post by mephisto56 on 2008-05-06
The theme they have is a lot better than ubuntus IMHO. After more "hands on reviews" come in I may try it too.

---

### Post by SunnyRabbiera on 2008-05-06
> **mephisto56 said:**
> The theme they have is a lot better than ubuntus IMHO. After more "hands on reviews" come in I may try it too.

Yeh the nimbus theme is neat, but I dont think its good if you use a lot of non GTK apps... also the latest ubuntu engine supports color theming, while nimbus is stuck into its purply theme.

---

### Post by pelle.k on 2008-05-06
It was **really** interesting to see that ian murdock and co. has gotten opensolaris to this point in such a short while. Everything but my usb mouse, and acpi did work without any modifications.
The theme, called "nimbus" is really polished, although i didn't like the window borders. The icons set was really consistent and professional looking, but was lacking a bit polish though.
Very organized menus, and application descriptions.

It is not ready for "my desktop" yet, but i'm so impressed in how far along they are already, considering that solaris isn't (up until now) really known for it's desktop readiness exactly. Trust me, in a year or so this is going to be a real alternative any linux distro, **if** you can live without mainstream binaries that are linux specific, like wine, alsa etc.

---

### Post by 3rdalbum on 2008-05-06
I haven't tried OpenSolaris recently, but I had a play on the distributions that came on the OpenSolaris starter pack DVD. Nexenta was slow so I tried one of the others... it didn't automount drives so I tried to manually mount. The /dev scared me away :-)

I think Linux's /dev has slowly been getting more like OpenSolaris', but the experience of looking in /dev and being completely and utterly bamboozled stayed with me :-)

---

### Post by mephisto56 on 2008-05-06
Well I didn't wait and downloaded the cd. No success on my laptop nor in virtualbox. Virtualbox had a critical error before exiting and on my laptop nothing but errors during boot until it halted at some admin login which lead to nowhere.

---

### Post by seamuso on 2008-05-06
I have it installed and running in virtualbox 1.6 .. gave it 1GB memory, pcnet fast III (host interface), 32mb video, ACPI, VT-x/AMD-V, PAE/NX

Here's a [screenshot]( http://info.bluefrogcs.com/images/more_vms.png) (720.9 KB)

---

### Post by rickh57 on 2008-05-06
I've played with a VMWare version of OpenSolaris. It seems to work fine, but doesn't feel as polished (to me, at least) as Ubuntu.

---

### Post by mephisto56 on 2008-05-06
> **rickh57 said:**
> I've played with a VMWare version of OpenSolaris. It seems to work fine, but doesn't feel as polished (to me, at least) as Ubuntu.

Can you tell more about what makes you feel this?

---

### Post by regomodo on 2008-05-06
apart from the memory consumption, i'd have to say it reminds me a lot of Debian. Everything feels solid but there is such a lack of software. At the moment ZFS seems to be its main appeal.

However, did anyone else think it was weird Openoffice and Virtualbox weren't included?
[edit] added a picture to show RAM use and the amount of packages installed compared to what is available

---

### Post by angryfirelord on 2008-05-06
> **regomodo said:**
> However, did anyone else think it was weird Openoffice and Virtualbox weren't included?
I think it's because the CD is already maxed out. There isn't any room for OpenOffice or VirtualBox.

The GUI for the package manager looks like Synaptic (a good thing) and it seems in this release, Sun is finally implementing a decent package manager. It also automatically configured my wireless atheros card and loaded the nvidia driver for me. I'm going to have to install it and play around with it under the hood. I've only heard good things about ZFS.

---

### Post by aamukahvi on 2008-05-06
> **angryfirelord said:**
> I think it's because the CD is already maxed out. There isn't any room for OpenOffice or VirtualBox.

The GUI for the package manager looks like Synaptic (a good thing) and it seems in this release, Sun is finally implementing a decent package manager. It also automatically configured my wireless atheros card and loaded the nvidia driver for me. I'm going to have to install it and play around with it under the hood. I've only heard good things about ZFS.

I wonder why OpenOffice, when installed through the IPS system, weighs in at over 400MB?!? And it seems to download individual files, not just one package.

---

### Post by gsmanners on 2008-05-06
I think OpenOffice.org now includes openclipart (which is about 200 MB all by itself).

---

### Post by Antman on 2008-05-06
Burning CD now... will install as soon as it's done.:popcorn:

---

### Post by Foster Grant on 2008-05-07
I once would have killed for something like this. Now? Five years too late. Linux has won.

And there's a legal issue to be considered. Didn't Sun get SCO's permission to open up the Solaris (System V Release 4) code? Because the court held in *SCO v. Novell* that Novell holds the rights to the SysV branch of Unix.

This could be the opening of yet another can of legal worms.

---

### Post by Em-Buntu on 2008-05-07
I am running the Live CD right now.

I think it's a great system and has come a long way since I first played with it a year or two ago.

I'm running it on an ASUS K8N-DL Server/Workstation board. The Device Manager found everything on my workstation except 3 devices;

1. MIDI port
2. Silicon Image SATA Controller
3. Game port

Of the 3 I would only miss the Silicon Image controller when I get around to building a BIG RAID.
It's not a show stopper since it does see my NVIDIA RAID as well as my add-in LSI Logic SAS controller.

I suspect it runs so well on my workstation because it's an Quad Opteron (dual 800 series dual cores) system, and Sun is a BIG Opteron user. I noticed though, when I downloaded the LIVE CD, it didn't have an x86 32 or 64 option, Just languages.

For some reason System Monitor says this is a release candidate 3, not a formal release. This system manager is the same as the version used in Feisty and Gutsy. Not as slick as the new one in Hardy.

After playing with this, I think I'll put it on another system by itself to use as a NAS/file server with backup for my other systems. The ZFS system should add great reliability for backing everything up to it.
It seems to read or recognize ext3 format. I'm not too sure that Ubuntu will recognize ZFS though, and I'm not going to take the chance installing it on the same system or disk.
I may install it on another disk tomorrow just to play with it a little more. 

Overall, I'm impressed with the speed, appearance, and capability of OpenSolaris. I expect, it will just continue to get better and better with each update.

At this point, I'd give the developers an A. I may up/down this grade later on as I get more hands on with ZFS.  :guitar:

---

### Post by seamuso on 2008-05-07
> **gsmanners said:**
> I think OpenOffice.org now includes openclipart (which is about 200 MB all by itself).

I installed OO from the package manager .. it was a 400MB dl.

I also couldn't resist .. Installed opensolaris as a vm in virtualbox .. installed virtualbox in solaris vm ... [hahaha](http://info.bluefrogcs.com/images/os_vm_haha.png) .. viertualbox 1.6

---

### Post by FreakTech on 2008-05-07
I tried it and was very impressed.  There were a few problems though.  I installed it on my test machine, a HP 6710b latpop with Intel 3945 a/b/g wireless and a broadcom gigabit extreme wired NIC, 1gig ram.  The memory usage with nothing running is an issue, over 400 megs.  It also did not have a driver for my wired NIC out of the box.  The wireless NIC works great unless you have WPA on your AP.  This is a problem with the the solaris encryption kit only supporting 128 bit RC4.

---

### Post by the yawner on 2008-05-07
> **Foster Grant said:**
> I once would have killed for something like this. Now? Five years too late. Linux has won.

And there's a legal issue to be considered. Didn't Sun get SCO's permission to open up the Solaris (System V Release 4) code? Because the court held in *SCO v. Novell* that Novell holds the rights to the SysV branch of Unix.

This could be the opening of yet another can of legal worms.

And Novell has stated that opening up of the Unix codes in Solaris was not in their best interest as that would be in direct competition with their Linux business. I wonder what would happen next...

---

### Post by phidia on 2008-05-08
> **FreakTech said:**
> I tried it and was very impressed.  There were a few problems though.  I installed it on my test machine, a HP 6710b latpop with Intel 3945 a/b/g wireless and a broadcom gigabit extreme wired NIC, 1gig ram.  The memory usage with nothing running is an issue, over 400 megs.  It also did not have a driver for my wired NIC out of the box.  The wireless NIC works great unless you have WPA on your AP.  This is a problem with the the solaris encryption kit only supporting 128 bit RC4.

FreakTech, we have similar laptops. I tried the recent release of open solaris today and I liked it. Interesting that it loads the Nvidia driver in the livecd-of course there are linux distros that do that too. Solaris couldn't load a driver for sound or the wifi chipset (Atheros ar5007eg) which took some time & effort to get working in 64bit Gutsy. I see references to a 64 bit version (or two variations actually) at the [open solaris download site]("http://www.opensolaris.org/os/downloads/") has anyone tried either of those, and if so what was the result?

---

### Post by mybunche on 2008-05-11
I posted what is below in another thread:

I have tried the liveCD and everything worked fine except my wifi, it didn't detect my wireless USB dongle (Netgear WG111 v2)so I couldn't get online. Apart from that, the artwork was good and behaved like any other live CD. With good hardware detection and if there is a much improved package installer it will give Linux and BSD a good run. Technically it will be a good OS in the future. It is for reasons other than the technical that I support Ubuntu.

Have a question though:
Is the kernal in opensolaris the same as the kernal in solaris proper?

---

### Post by kazoo boy on 2008-05-12
I've thought about trying Solaris straight from Sun because I'm pretty sure it's free. The only thing I wonder is, who uses it, are there any good apps for it and what makes it special versus Linux? Well, I still have to try out another distro today, but maybe when that's over I can see what Solaris is all about...

---

### Post by chachawpi on 2008-05-12
Unless you are a developer that uses SunStudio or you have high scalability needs, you should leave Solaris alone.  FreeBSD is a decent alternative to Linux for a desktop.  At least there is software available for it!

---

### Post by pelle.k on 2008-05-12
> FreeBSD is a decent alternative to Linux for a desktop. At least there is software available for it!
When the freebsd community hires ian murdock to do what he is doing to opensolaris now (and what he did to debian), then yes, freebsd will probably be the better alternative.
But as things are now, freebsd isn't going anywhere. I mean that in a good sense, mind you. Freebsd are great workstations and servers, but they require a lot more from the administrator, and isn't what you would call an "out of the box" desktop *nix.
There's a lot of software available for opensolaris. Where did you get the idea that there isn't? It's got pretty much any open source linux application that doesn't depend on linux kernel *specific* features. Just like freebsd.

---

### Post by cardinals_fan on 2008-05-12
> **pelle.k said:**
> 
There's a lot of software available for opensolaris. Where did you get the idea that there isn't? It's got pretty much any open source linux application that doesn't depend on linux kernel *specific* features. Just like freebsd.
Most of it is not available throught the IPS package system.

---

### Post by chachawpi on 2008-05-12
> **pelle.k said:**
> When the freebsd community hires ian murdock to do what he is doing to opensolaris now (and what he did to debian), then yes, freebsd will probably be the better alternative.
But as things are now, freebsd isn't going anywhere. I mean that in a good sense, mind you. Freebsd are great workstations and servers, but they require a lot more from the administrator, and isn't what you would call an "out of the box" desktop *nix.
There's a lot of software available for opensolaris. Where did you get the idea that there isn't? It's got pretty much any open source linux application that doesn't depend on linux kernel *specific* features. Just like freebsd.
The average "Hey Ubuntu looks cool, is OpenSolaris cool too?" user is not going to have any clue how to run a BrandZ or even install anything that isn't in the built in IPS.  There also isn't exactly a large amount of Solaris help out there like there is for Linux.  

I do have to give OpenSolaris kudos for packaging the NVidia drivers.  They work on my 4 GB of RAM system while the FreeBSD ones do not.  They also package Flash, or at least the SXDE I tried did.

---

### Post by pelle.k on 2008-05-13
> The average "Hey Ubuntu looks cool, is OpenSolaris cool too?" user is not going to have any clue how to run a BrandZ or even install anything that isn't in the built in IPS. There also isn't exactly a large amount of Solaris help out there like there is for Linux.
Hey, I thought we were comparing opensolaris to freebsd? I'm the first to admit that ubuntu is a clear winner in that situation.

---

### Post by babylon2233 on 2008-05-19
I heard the opensolaris repo only contain around 1,000 package. If it is true, so, no way I gonna replace my Ubuntu with this OS even I have try it on VirtualBox.

---

### Post by Blakefreak on 2008-05-19
Tried it because I am the guy who said "Wow Ubuntu looks cool... wonder what OS is like".
And predictably I couldn't do anything with it..
Took a while to just get my wired or wifi to work.. even though on the live cd it picked up my wifi immediately.. Odd.
Also after an hour or two my used RAM was up to 2.5GB and the system started to get choppy.
I did however thnk that the desktop effects were a bit more solid feeling than Ubuntu... smoother.

---

