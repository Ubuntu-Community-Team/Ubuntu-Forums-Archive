---
title: "Exe"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by JimVicious on 2008-09-19
Hey everyone.
How do i run a setup.exe?

thanks

---

### Post by Perfect Storm on 2008-09-19
Well as you might know .exe is a windows file format and therefore can't be used in Linux.

However with an application called wine, you can with a bit of luck,hack, tweak and pray running it.

It's in the repositories.

Here's some info that's good to know before starting: [http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

---

### Post by Elfy on 2008-09-19
With windows ;) or depending on what it's for you could try wine or maybe a virtual machine.

What is the exe for?

---

### Post by JimVicious on 2008-09-19
i inserted a windows cd
and i dont know how to run the setup.

what do i do?

---

### Post by northern lights on 2008-09-19
Windows CD as in "a CD with Windows compatible content" or as in "Windows distribution setup CD"?

In the latter case, you'd want to boot from it, in order to install.

---

### Post by Perfect Storm on 2008-09-19
Might be a good idea to know what oftware/game you want to run.

But a start;

```
sudo apt-get update && sudo apt-get upgrade
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get install wine
winecfg
wine <path>/setup.exe
```

---

### Post by JimVicious on 2008-09-19
> **northern lights said:**
> Windows CD as in "a CD with Windows compatible content" or as in "Windows distribution setup CD"?

In the latter case, you'd want to boot from it, in order to install.



do i just restart and that will run it? or what?

---

### Post by Tatty on 2008-09-19
As Artificial Intelligence said, you need to install wine, which is a linux app which attempts to run windows executables.  It is far from perfect, some apps work brilliantly, lots work a bit buggy, most work very buggy, some dont work at all.

Wine is in the repos, or if you want the latest version you can add the semi-official wine ubuntu repo:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

What software are you trying to install?

Check out the appdb at the wine website to see how well your software is supported in wine. [http://www.winehq.org/](http://www.winehq.org/)

EDIT: woah i was slow typing, this was supposed to be post #5 when i started :)

---

### Post by JimVicious on 2008-09-19
Windows XP Professional

---

### Post by Elfy on 2008-09-19
<snip>

Are you trying to remove ubuntu and reinstall xp

---

### Post by JimVicious on 2008-09-19
[edit]

yes.

ubuntu is too hard for me to use.
I need a stupid people program 
I will be going to a course in order to learn how to use it though

---

### Post by Perfect Storm on 2008-09-19
Okay, but you have to tell us what you're trying to do. You want to dual-boot so you have Ubuntu and Windows on your computer?

---

### Post by northern lights on 2008-09-19
> **forestpixie said:**
> No you probably don't want to restart - northern lights is talking about ifd it was a xp disc for example.
Which it appears to be.:)

@the OP:
Reboot with CD inserted. If you're not asked whether to boot from CD or not, add you CD drive to the boot sequence in the BIOS (hit 'DEL' when booting).

---

### Post by Locutus_of_Borg on 2008-09-19
i really hope your joking

0/10

---

### Post by Paqman on 2008-09-19
> **JimVicious said:**
> Windows XP Professional

You need to boot from the CD. Put the CD in the drive and reboot. It should pop up and say "Press any key to boot from CD", if it doesn't do this, you need to change your boot settings in your BIOS to boot from the CD drive. To get into BIOS look for a line just after powering on that say something like "Press Del/F2/whatever to enter setup" or some such.

**Be careful though**, unless you've created a separate partition to install XP onto installing it will completely overwrite your Ubuntu install. Is that what you want?

---

### Post by JimVicious on 2008-09-19
> **northern lights said:**
> Which it appears to be.:)

@the OP:
Reboot with CD inserted. If you're not asked whether to boot from CD or not, add you CD drive to the boot sequence in the BIOS (hit 'DEL' when booting).

what would the code be to do that 

thanks in advance

---

### Post by northern lights on 2008-09-19
> **JimVicious said:**
> what would the code be to do that

Ain't no "code" involved.

Physically insert the CD. Reboot.

When it says "Press DEL to enter setup", hit DEL key.

Make CD drive first boot device.

Sav and quit.

Choose to boot from CD.

Follow Windows Setup instructions.

---

### Post by Elfy on 2008-09-19
I really would just slow down a bit here - if you're going to be doing a course to use ubuntu/linux then at some point you will be needing it again.

It would be best to dual boot as artificial intelligence has pointed out, your choice obviously :)

There  is no code to run the windows install as such - do as you've been told to get it to boot.

---

### Post by Tatty on 2008-09-19
Make sure you back up anything you dont want to lose!  Because unless you have partitioned before running the installer, windows will wipe everything.

---

