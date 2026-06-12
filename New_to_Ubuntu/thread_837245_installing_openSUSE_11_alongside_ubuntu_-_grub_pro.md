---
title: "installing openSUSE 11 alongside ubuntu - grub problems?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by benji.ijneb on 2008-06-22
hi,

i've seen the new opensuse 11 KDE4, and i'm thinking of installing it alonside my ubuntu install (dual-booting). my question is, will it overwrite GRUB so that i can't boot into ubuntu any more? what do i have to do to stop/fix this?

i'm a bit of a newbie, so simple instructions, please!

thanks for all your help...

---

### Post by phidia on 2008-06-22
I have run the livecd of opensuse (Gnome) but not the installer. 
You should be able to opt out of installing grub at all but you will need to know which partition you installed opensuse to. 
When I multibooted I found it easiest to have grub install to the root partition then you just use the chainload command in menu.lst  See examples of that[ here]("http://forums.debian.net/viewtopic.php?t=3506") and [here]("http://www.mepis.org/docs/en/index.php/Chainload_GRUB").

---

### Post by benji.ijneb on 2008-06-22
> **phidia said:**
> I have run the livecd of opensuse (Gnome) but not the installer. 
You should be able to opt out of installing grub at all but you will need to know which partition you installed opensuse to. 
When I multibooted I found it easiest to have grub install to the root partition then you just use the chainload command in menu.lst See of that examples [here]("http://forums.debian.net/viewtopic.php?t=3506").

i'm a bit confused...
what's the whole chainloader thing? is that all i have to do? which menue.lst should i do that on? (ubuntu or openSUSE?)

---

### Post by phidia on 2008-06-22
> **benji.ijneb said:**
> i'm a bit confused...
what's the whole chainloader thing? is that all i have to do? which menue.lst should i do that on? (ubuntu or openSUSE?)

Sorry I just gave a brief summary and the grub you are using now is  the one installed by the Ubuntu installer so that would be the one to edit. When installing opensuse you need to choose advanced, I think, when the grub install option comes up, and from there you would select the partition (Not the MBR) that you installed "/" of opensuse on. Is that clearer? I hope so. 
You can also search the forums at opensuse since they probably have answered this question before too and know more of the specifics with the 11 installer.

---

### Post by benji.ijneb on 2008-06-22
would it be possible to install openSUSE w/out GRUB, and then add it to ubuntu's menu.lst?

how would i go about doing this - it seems like the easiest option...

thanks for all your help...

---

### Post by phidia on 2008-06-22
It is possible-like i said it's probably a good idea to check the opensuse forums. There's a [thread there]("http://forums.opensuse.org/install-boot-login/386053-using-other-distros-grub-bootloader.html") on this topic in fact. 
Not installing grub though has some effects in that opensuse will start up in commandline rather than the green graphical boot up and there won't be any auto updating of kernels thru grub because grub wasn't installed. Take a look at that and related thread there and you'll understand more-I think.
Possibly you can enable the graphical boot up and the thread I linked will tell you how to install bypassing grub.

---

### Post by meindian523 on 2008-06-22
> **phidia said:**
> It is possible-like i said it's probably a good idea to check the opensuse forums. There's a [thread there]("http://forums.opensuse.org/install-boot-login/386053-using-other-distros-grub-bootloader.html") on this topic in fact. 
Not installing grub though has some effects in that opensuse will start up in commandline rather than the green graphical boot up and there won't be any auto updating of kernels thru grub because grub wasn't installed. Take a look at that and related thread there and you'll understand more-I think.
I don't think that openSUSE will drop to commandline because it's GRUB is not installed.But,there will be surely no auto updating of kernel updates in openSUSE until you edit Ubuntu's GRUB's menu.lst to that teffect.

---

### Post by benji.ijneb on 2008-06-22
> **phidia said:**
> It is possible-like i said it's probably a good idea to check the opensuse forums. There's a [thread there]("http://forums.opensuse.org/install-boot-login/386053-using-other-distros-grub-bootloader.html") on this topic in fact. 
Not installing grub though has some effects in that opensuse will start up in commandline rather than the green graphical boot up and there won't be any auto updating of kernels thru grub because grub wasn't installed. Take a look at that and related thread there and you'll understand more-I think.

at the end of that it says that openSUSE will probably recognize other distros. this would be the simplest option - would it be possible to confirm that this will happen? that way there ought not to be any difficulties.

if it doesn't work, would it not be as simple as reinstalling GRUB from the ubuntu livecd to fix this (using [this]("http://ubuntuforums.org/showthread.php?t=224351"))

and then from that i could try to use [this]("http://ubuntuforums.org/showthread.php?t=658644") to add openSUSE.

what do you think?

---

### Post by phidia on 2008-06-22
> **meindian523 said:**
> I don't think that openSUSE will drop to commandline because it's GRUB is not installed.But,there will be surely no auto updating of kernel updates in openSUSE until you edit Ubuntu's GRUB's menu.lst to that teffect.

I edited that since I worded it unclearly (typing too fast).
What I meant is that if you boot through ubuntu's grub and don't include specific options-I don't know what those are-you lose the pretty graphical boot. I know because I've done it that way. 
You still have a login and a desktop but you lose the green opensuse boot screen and get a blackscreen with the startup logs.

---

### Post by phidia on 2008-06-22
> **benji.ijneb said:**
> at the end of that it says that openSUSE will probably recognize other distros. this would be the simplest option - would it be possible to confirm that this will happen? that way there ought not to be any difficulties.

if it doesn't work, would it not be as simple as reinstalling GRUB from the ubuntu livecd to fix this (using [this]("http://ubuntuforums.org/showthread.php?t=224351"))

and then from that i could try to use [this]("http://ubuntuforums.org/showthread.php?t=658644") to add openSUSE.

what do you think?

Yes, if you use the suse grub you will then boot through that-suse replaces the ubuntu installed grub on your mbr, and if anything goes wrong you can use the livecd to reinstall grub.

As I said previously when I multibooted I liked have each distro boot through it's own grub-that way kept things the way I liked it and it made sense to me, but try whatever you like you can always change it if you find another way works better.

---

### Post by meindian523 on 2008-06-22
Well,it probably should happen,about 98% of the time.And those are good backup threads in case you fall in the unfortunate 2%.

---

### Post by benji.ijneb on 2008-06-22
> **phidia said:**
> Yes, if you use the suse grub you will then boot through that-suse replaces the ubuntu installed grub on your mbr, and if anything goes wrong you can use the livecd to reinstall grub.

As I said previously when I multibooted I liked have each distro boot through it's own grub-that way kept things the way I liked it and it made sense to me, but try whatever you like you can always change it if you find another way works better.

it sounds easiest to do that. the worry is that it might bugger up my system so i can't boot into ubuntu (this happened once before  - but in different circumstances) - is it likely that something like this will happen?

also, on a completely unrelated thing, do i need to partition my HD before i install, or is there an option to do that in the openSUSE installer?

---

### Post by Pjotr123 on 2008-06-22
Typing this in openSUSE 11, on my tenfold bootable laptop (Ubuntu is my default OS).

What's important here, is that Grub consists out of two parts. One part is in the MBR and one part (the menu.lst for example) is on the active Linux partition. If you install openSUSE, Grub will use the menu.lst of openSUSE. But you can tell Grub to use the menu.lst of Ubuntu again, by doing this:
[http://ubuntutip.googlepages.com/grub](http://ubuntutip.googlepages.com/grub)
(number 1 )

Then all you have to do, is copy the boot lines of openSUSE from it's /boot/grub/menu.lst, into the /boot/grub/menu.lst of Ubuntu. At least, if you want the Ubuntu menu to be your "master menu.lst".

Note: after kernel updates, you will have to copy the boot lines of the updated Linux (when it's not the active one) into the "master list" again.

Example of an older version of my own multiple "master list":
[http://computertip.googlepages.com/voorbeeldgrubmenu](http://computertip.googlepages.com/voorbeeldgrubmenu)
(the blue text).

Greeting, Pjotr.

---

### Post by meindian523 on 2008-06-22
Well,you have to take care that you don't overwrite any Ubuntu partitions while installing Ubuntu,a list of sizes of your Ubuntu partitions might be handy.I believe openSUSE installer will have a partitioner,otherwise,boot into your Ubuntu and use GParted(if you have installed it) or use the partition editor in the Ubuntu Live CD.

---

