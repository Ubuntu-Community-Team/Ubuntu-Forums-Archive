---
title: "Individual GRUB install without distro?"
date: 2008-09-18
forum: Other OS Talk
---

### Post by Fzang on 2008-09-18
tl;dr - Looking for a GRUB-only install CD

Is it possible to find a GRUB install that can install independently of whatever might be installed on the harddisk?

For some reason the mandriva live CD won't install GRUB in either way, it just freezes...

---

### Post by volkswagner on 2008-09-18
I believe you can install grub via most any live cd.  I have never done it myself.

You may be interested in super grub boot disk.
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by caljohnsmith on 2008-09-18
> **Fzang said:**
> tl;dr - Looking for a GRUB-only install CD

Is it possible to find a GRUB install that can install independently of whatever might be installed on the harddisk?

For some reason the mandriva live CD won't install GRUB in either way, it just freezes...
Sure, it's definitely possible to install Grub independent of any distro, and you only need a Live CD to do it. From your Live CD, please post the following:
```
sudo fdisk -lu

```

---

### Post by Fzang on 2008-09-19
> **caljohnsmith said:**
> Sure, it's definitely possible to install Grub independent of any distro, and you only need a Live CD to do it. From your Live CD, please post the following:
```
sudo fdisk -lu

```

Uh... sudo is for ubuntu only, right?

So, every version of linux (except slackware) uses the same GRUB which works cross-distro all over? Can I then create a USB distro and install GRUB from there?

---

### Post by caljohnsmith on 2008-09-19
> **Fzang said:**
> Uh... sudo is for ubuntu only, right?

So, every version of linux (except slackware) uses the same GRUB which works cross-distro all over? Can I then create a USB distro and install GRUB from there?
"sudo" is just to run the single fdisk command as root in Ubuntu (and most other Debian distros I think), but for a Red Hat based distro like Mandriva, I think you usually first switch to root user and then run the command:
```
su -
fdisk -l

```
And yes, Grub is basically the same for all distros. If you want to create your own USB distro, and add Grub to it afterwards, I'm almost certain you can do that. I can give you the steps if you need help with the Grub install part.

---

### Post by 67GTA on 2008-09-19
Mandriva used to use Lilo. Have they switched to Grub?

---

### Post by caljohnsmith on 2008-09-19
> **67GTA said:**
> Mandriva used to use Lilo. Have they switched to Grub?
Mandriva 2008 Spring uses Grub if I remember correctly.

---

### Post by Fzang on 2008-09-19
Does it matter which GRUB I'm installing? I'm having some ACPI problem that won't let me boot distros after ~2007 versions. Ubuntu gutsy and mandriva 2007 works...

---

### Post by caljohnsmith on 2008-09-19
> **Fzang said:**
> Does it matter which GRUB I'm installing? I'm having some ACPI problem that won't let me boot distros after ~2007 versions. Ubuntu gutsy and mandriva 2007 works...
The acpi problems should be related only to your hardware and its interaction with those distros, so you might as well use the latest Grub if you can. But if you can only use an older distro that comes with a slightly older Grub, that should be fine too.

---

### Post by jaqie on 2008-09-19
> **Fzang said:**
> Uh... sudo is for ubuntu only, right?
***NO*!**
You can even use it in FreeBSD, and it's a good idea, as well, though I usually just "su -" and then ran a root console for a while. I am such a careful type that I never made any mistakes in that console, but mistakes in other places once in a while.

---

### Post by 67GTA on 2008-09-19
> **caljohnsmith said:**
> Mandriva 2008 Spring uses Grub if I remember correctly.

Cool. The last time I used it, it was still Mandrake:)

---

### Post by Fzang on 2008-09-24
Mandriva fails to install GRUB

Tried the newest fedora now... but I can't even find a place to install GRUB only :O??

Downloading PCLinuxOS now -_-'

---

### Post by rsambuca on 2008-09-24
Fzang, you do not have to go through a installation procedure to re-install grub.  You can install grub just from the terminal of any live CD.  Get virtually any liveCD and boot it up.  Then open a terminal and enter the command ```
grub
```  Depending on the distro, you may need to use 'sudo'.  This will get you to the grub shell, where you can run the 'root' and 'setup' commands.

---

### Post by basenvironment on 2008-09-25
> **Fzang said:**
> tl;dr - Looking for a GRUB-only install CD

Is it possible to find a GRUB install that can install independently of whatever might be installed on the harddisk?

For some reason the mandriva live CD won't install GRUB in either way, it just freezes...

any livecd with grub installed

grub
root(hd0,0)
setup(hd0)
quit

*adjust root and setup to your needs

---

### Post by Fzang on 2008-09-25
So, even if the GUI GRUB freezes, the command-line still works?

Also, if windows is on my C partition and mandriva having the rest of the disk, how would the GRUB install have to look like if I'm installing it from terminal?

---

### Post by Fzang on 2008-09-26
Tried doing a guided grub install on a ubuntu live and it keeps throwing "not found" and "permission denied" at me

CMON...! How hard can it be to install a bootloader?

Also, does it matter where grub is installed on the computer, or do I have to choose my linux root partition or something?

Gahhh!!! Why am I having so much trouble on this laptop! :(

---

### Post by rsambuca on 2008-09-26
If you are using the ubuntu live cd, you have to enter ```
sudo grub
```

---

### Post by Fzang on 2008-09-27
Alright,

```
sudo-grub 
```

gives me a hell lot of commands to try

I'm not familiar with any type of terminal though...

I entered

```
grub-install /dev/sda5

```
... Or was it just "install..". Well that's the root partition of my mandriva install... grub gives me "permission denied"

What else do I try? It's pretty annoying to reboot all the time to try the live CD

---

### Post by basenvironment on 2008-09-27
root would be the partition you want to have control of the grub menu. The one where you would edit menu.lst to change boot options and so forth.

setup would be the main drive in your system.

grub manual may help - [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by Fzang on 2008-09-27
But does it matter where I install GRUB? Can I just pick my windows partition, first partition, harddisk, anywhere? If it turns out that computer won't boot I can always use the fix MBR command on windows XP disc?

If my windows partition gets deleted I'd have to kill myself, I've spend countless hours customizing it

---

### Post by basenvironment on 2008-09-27
the mbr of the main drive is where you install grub

---

### Post by Fzang on 2008-09-27
So, hd0 is the basic place to install it if I have a windows bootloader on C?

---

### Post by basenvironment on 2008-09-27
**should** be

Do you have more than one drive?

---

### Post by Fzang on 2008-09-27
I have 1 harddisk, with partitions:

dev/sda1 - windows XP
dev/sda5 - mandriva root
dev/sda6 - swap
dev/sda7 - mandriva home

Usually when GRUB is installed on a CD, it installs to sda1, right?

Also - most importantly - how do I add windows to the boot list in terminal, so I can dual boot, instead of having a linux-only GRUB?

---

### Post by basenvironment on 2008-09-27
root (hd0,4)
setup (hd0)

To add a windows boot option you should edit /boot/grub/menu.lst and add it if it doesn't already have it.

If you get a grub prompt when you boot your computer, then you can load windows using grub commands, something like...
root (hd0,0)
chainloader +1
boot

---

### Post by Fzang on 2008-09-27
Are you sure it's not hd(0,5) and not 4 to hit the mandriva root? Just wondering because I can't seem to connect a '4' with any of what I listed

---

### Post by rsambuca on 2008-09-27
Basenvironment is correct.  The drive designations start counting at zero, so sda5 is actually (hd0,4)

hd0 is the first drive, the 4 is the fifth partition of that drive.

---

### Post by Fzang on 2008-09-27
I see... odd

Alright, I'll give it a go

---

### Post by Fzang on 2008-09-28
Wait! What if it won't boot windows? Will a repair disc with the command "fix MBR" work?

---

### Post by rsambuca on 2008-09-28
You will be able to boot into Windows by either the fixmbr command, or by adding the Windows entry to your grub menu.lst, although it will probably be automatically added.

---

### Post by Fzang on 2008-09-28
Alright... here goes!

---

### Post by Fzang on 2008-09-29
Phail!

Doesn't want to work

On the IRC channel #grub I was told that I need some grub files... however the /boot/grub folder is empty and I keep getting messages like "file not found" no matter what commands I try

Maybe I should just pick a different distro with similar hardware support :o

It's gonna be impossible for my acer though..

---

