---
title: "Ubuntu - Kubuntu shared problem"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by arieleoar on 2014-07-14
Hello there!

I've a problem, i installed ubuntu 13.10 a year ago but i haven't used it for long because i was affected by an older bug with unity plugin and my nvidia VCard.
Looking here i've found a partial solution to that a few months (before the ubuntu 14.04 upgrade came) that was to change to Kde with ```
sudo apt-get install kubuntu-desktop
```
I've to recognize that i don't know what i was doing but that solved the problem because kubuntu haven't problems with my Vcard.

The thing is that when I upgrade Ubuntu and Kubuntu to 14.04 the bug in unity was solved (then i started to use ubuntu too) but some things in kde stopped of running normally, i list:

[LIST]
[*]_*The login screen of kde (that is now the predefined when i installed kubuntu) doesn't show any background, only the buttons (the image, the listbox with the distributions, etc, luckily)*_
[/LIST]
_*&#8203;*_**Fixed: Downloading and installing KDM then active it over lightdm login screen solves this for me, and makes the login more customizable too. It's a good tool if you are a "customizaholic" (hehe **:p**).**

[LIST]
[*]*I've to run some aplications in sudo privilegies to write caches or temporaries (like blender for example, I lost much work in electrical cuts)*
[/LIST]
*&#8203;***I mark this fixed, but partially, putting kdesudo after the command in the properties of an icon opens a dialog asking the password, was better because i was running the programs from konsole directly with sudo.**


[LIST]
[*]_*In Ubuntu, the applications shows the color scheme of kde inside the windows, but with the windows borders and the "taskbar" shows with the ubuntu's scheme*_
[/LIST]
**Fixed: In an actualization of the KDE runtimes packages of the last week fixed that for me, however seems ubuntu distro has the sudo privilegies in the pc, and a application running in kdesudo is shown with the ubuntu theme.**


[LIST]
[*]_*The splash screen (before grub) now shows in a creepy system font "kunbutu 14.04 ...." and system messages of the hardware initializing instead the inglowing "kubuntu" in blue (the same with the shutdown*_)
[/LIST]
**Fixed: it was a problem related to the nvidia propietary driver, it was solved modificating the grub configuration.**


By the way, in the crazy case i want to install the ubuntu-studio distro, how should i do that without having this problems?

Sorry if I writed too much, and for the english too :p.

**I Mark the thread solved, thanks for reading, thanks for answering!**

---

### Post by grahammechanical on 2014-07-14
I once installed all five alternative desktop environments just to see what would happen. It became a mess. I took the easy way out. I re-installed. Hard disks are large enough these days for us to set aside a few 15 - 20 GB partitions to install the complete distributions and dual boot into Xubuntu, Kubuntu, Lubuntu and Ubuntu Studio and Mythbuntu as well as Edubuntu. This is what I do. This is what I recommend.

I do not think that there is a Ubuntu studio desktop in the same way that there is a Kubuntu desktop. Besides, Ubuntu Studio uses a special Linux kernel called a low-latency kernel that the other distributions do not use. This low-latency kernel is preferable when working with audio and visual files. Of course, we can install the various packages that we get with Ubuntu Studio but in my opinion it is better to dual boot into the specialist distributions.

I have an installation of Ubuntu that I never mess with. It is there for when my experiments in other installs of Ubuntu break the OS. In this way I still have a working OS. This is my way of working. 

Regards.

---

### Post by arieleoar on 2014-07-14
Thanks for reply!
> **grahammechanical said:**
> I once installed all five alternative desktop environments just to see what would happen. It became a mess.
I'm trying to imagine the problems with installing the same app (like web browser) in every desktop distro, jeje! :p

I won't mess with the system anymore, so i won't uninstall any distro, because i won't have problems with the other users of the pc (specially my father, isn't to much friendly with the tecnology). The problems are minor "bugs" but there is a way to repair them?
[QUOTE=grahammechanical][COLOR=#000000]my opinion it is better to dual boot into the specialist distributions.[/COLOR][/QUOTE]
Off topic, how can i install a new os in a new partition without messing with grub? lately i installed windows with an ubuntu 10 version and then i cant run ubuntu, it's going to happen the same if i install an ubuntu-studio?

Again thank you! regards!

---

