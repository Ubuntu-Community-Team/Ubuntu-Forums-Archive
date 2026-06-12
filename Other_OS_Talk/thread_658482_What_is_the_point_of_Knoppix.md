---
title: "What is the point of Knoppix?"
date: 2008-01-04
forum: Other OS Talk
---

### Post by Pogeymanz on 2008-01-04
I am very excited about Linux, so I downloaded a bunch of liveCDs to "spread the word" so-to-speak.

Since Knoppix is only intended to be a liveCD and not an installation, what is the point? I can show somebody openSUSE, Vector, PCLOS, and Ubuntu and then install them if he/she wants. Is there anything special about Knoppix that makes it worth being in my arsenal?

---

### Post by N8K99 on 2008-01-04
Knoppix is really great as a System Repair toolkit- it is also really quite handy for fixing broken MS boxes as well.

Additionally, Damn Small Linux is also based upon Knoppix- and it can be run completely from within RAM or installed on the disk, which is great for resurrecting old hardware. I have a Toshiba Tecra laptop that's at least 12 yrs old that runs DSL.

---

### Post by Steveway on 2008-01-04
Knoppix was one of the first (if not the first) Linux- Live-CDs.
Also it's very well put together and includes a lot of apps.

---

### Post by Incense on 2008-01-04
Long before the *buntu's, SuSE, Fedora and the like had live CD's, Knoppix was the only kid on the block. I have saved a lot of data thanks for having a Knoppix disc in my tool kit. These days I use an OpenSUSE live disc for rescue (Love YaST), and I'm really not sure what Knoppix is up to these days. I'm sure it's still a fantastic and very usable live system though.

---

### Post by r4ik on 2008-01-04
> **EmosSuck777 said:**
> I am very excited about Linux, so I downloaded a bunch of liveCDs to "spread the word" so-to-speak.

Since Knoppix is only intended to be a liveCD and not an installation, what is the point? I can show somebody openSUSE, Vector, PCLOS, and Ubuntu and then install them if he/she wants. Is there anything special about Knoppix that makes it worth being in my arsenal?


Installation Procedure
To get Knoppix installed onto your hard drive:
Boot the Knoppix CD.


When the boot prompt comes up, choose your language.
Most of us speak English, so we'll type:
boot: knoppix lang=en
then press ENTER (you don't type the 'boot:' part, of course)


Wait till the system is fully launched, including the KDE desktop


Press CTRL-ALT-F1, to get a root console. You should see a shell prompt


Type: knoppix-installer


Follow the guided installation menus. This will include:


Creating a Linux partition (at least 2.5GB
Creating a Linux Swap partition (at least 256MB)
'Mounting' the Linux partition as root
Initialising the swap partition
Copying all the required files (automatically)
Setting up networking
Setting passwords
Setting up the bootloader (Note: take care with this stage - it could render your system incapable of booting into Windows. If you really need Windows, then it might be a good idea to set up GRUB Bootloader with a 'chainloader' entry, so that you can dual boot. Working this out is an exercise left to the reader - there are too many possible scenarios for me to cover in this short guide. Also see man grub and the files in /usr/share/doc/grub)
Rebooting (without the CD)


When you've rebooted Knoppix from your hard disk, click on the KDE Control Centre icon in the launcher at the bottom of the screen (icon of a colour monitor with a card in front of it)


Within the Control Center, click on Personliche Einstellungen


Click on Land und Sprache


Choose the locale and language of your choice


Click on Andwenden at bottom of that window


Close and restart the Control Center


Click on Peripherals, then Keyboard, and choose your preferred keyboard layout (which will probably be US.English. Click OK and close the window


Press CTRL-ALT-F2 to get to the root console, and log in as root (using the password you chose when you ran the installer)


(Optional) - type apt-get update (followed by ENTER). This will update your list of available packages, and takes about 5-10 minutes.


Hey, presto, you've got a fully installed GNU/Linux desktop


From here on in, you'll probably want to fine-tune a few things, set up themes, backgrounds etc. But most of the hard work is already done for you!

From RAV TUX.

[http://ubuntuforums.org/showthread.php?t=231244](http://ubuntuforums.org/showthread.php?t=231244)

---

### Post by darrelljon on 2008-01-05
I beg to differ on openSuSE - I've never encountered an openSuSE (or Fedora or Mandriva I think) disc which runs live and installs. KnoppiX does both (in fact the installer looks better than Vectors) and can save changes to USB, and is one of my favourite distros as a result.

---

### Post by Pogeymanz on 2008-01-05
I beg to differ. I have installed from a liveCD, openSUSE and one of the others (I forgot which one) you mentioned. I just did openSUSE a few days ago, so I'm not imagining it.

---

### Post by Incense on 2008-01-05
> **darrelljon said:**
> I beg to differ on openSuSE - I've never encountered an openSuSE (or Fedora or Mandriva I think) disc which runs live and installs. KnoppiX does both (in fact the installer looks better than Vectors) and can save changes to USB, and is one of my favourite distros as a result.

Then you're not looking hard enough, (or at all) mate.

OpenSUSE live disc on this page.
[http://software.opensuse.org/]("http://software.opensuse.org/")

Fedora Live on this page.

[http://fedoraproject.org/get-fedora]("http://fedoraproject.org/get-fedora")

Mandriva Live on this page

[http://www.mandriva.com/en/download/free]("http://www.mandriva.com/en/download/free")

All with friendly little icons that help you install the live image onto your hard disc.

---

### Post by SomeGuyDude on 2008-01-05
OpenSUSE's LiveCD claims to install, but I beg to differ on that. :lolflag:

---

### Post by agim on 2008-01-05
Someguydude, where did you get that quote?

---

### Post by SomeGuyDude on 2008-01-05
> **agim said:**
> Someguydude, where did you get that quote?

It's from The Prestige, said by the man in my avatar. :popcorn:

---

### Post by scorp123 on 2008-01-05
> **darrelljon said:**
> I beg to differ on openSuSE - I've never encountered an openSuSE (or Fedora or Mandriva I think) disc which runs live and installs.  These are very very very new features. OpenSUSE 10.3 can be now downloaded as "Gnome Live CD" or "KDE Live CD" which is also installable. So chances are you haven't yet heard about this or kinda missed it in the news on various Linux news sites. But don't bother with those. As far as Live CD's go and in my experience so far Knoppix is still the one you want to have, especially for repairing broken boxes. One Knoppix to rule them all ... :)

---

### Post by SunnyRabbiera on 2008-01-05
> **Steveway said:**
> Knoppix was one of the first (if not the first) Linux- Live-CDs.
Also it's very well put together and includes a lot of apps.

well knoppix is a big pioneer in the live CD market, after all without it most of todays live CD or DVD distributions would not exist.
though it was not the first live CD version of linux (Yggdrasil was the first) without it I dont think Ubuntu would be as useful as it is today

---

### Post by liquidfunk on 2008-01-05
> **N8K99 said:**
> I have a Toshiba Tecra laptop that's at least 12 yrs old that runs DSL.

 Is that the Tecra 8100? I have LinuxMint Fluxbox running on one of those. I fixed it up for a friend. He was fed up after some idiot put XP on it. Its pretty nippy.

 Magic!

---

### Post by maybeway36 on 2008-01-05
Knoppix is handy for partitioning too, if you type
```
knoppix desktop=icewm noswap
```
at the boot prompt and then run "sudo gparted".

---

### Post by SunnyRabbiera on 2008-01-05
Yeh knoppix is like a swiss army knife, its very helpful for recovery, setting up partitions and all sorts of other stuff.
The only reason why most suggest not to install it is its issues, I have heard people having bumps along the road with it as its not meant for install...
but it does work for many though

---

### Post by scorp123 on 2008-01-05
> **SunnyRabbiera said:**
>  The only reason why most suggest not to install Knoppix is its issues, I have heard people having bumps along the road with it as its not meant for install...  Knoppix is using lots of packages from the "Debian unstable" and even "Debian experimental" repos. There is no problem for as long as you use the software off the live CD (I assume they tested if everything works OK before releasing their ISO images :) ....) .... The problem is that with the HD installation you most likely will install additional packages sooner or later or maybe perform an update. And that's where most people run into problems because all this "unstable" and "experimental" stuff is likely to break things.

---

### Post by 67GTA on 2008-01-05
I've used Knoppix for years to rescue data from failing hard drives. You can install it to ram, and then use your CD/DVD drive to burn data. It has wine on the live cd already configured. You can run many Windows apps like "regedit". I rescued my cousin's PC by running regedit from the live cd, and fixing a mess he had made by running an experimental registry cleaner. There are a lot of live cd's now as compared to when Knoppix hit the scene, but most of the newer ones are focused on Desktop installs.

---

### Post by darrelljon on 2008-01-06
Last openSuSE I tried was a 10.2 Live DVD and a 10.2 Install DVD so things may have changed with 10.3.

---

