---
title: "How uninstall Ubuntu 12.04 and keep the Windows platform?"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by BSG Fan on 2013-07-17
how uninstall Ubuntu 12.04 and only allow the Windows platform to stay as originally it came?

This computer is borrowed and I need to turn Friday back to its electronics rent-to-own company. I absolutely do not want to mess with the original system.

Thank you.

---

### Post by snowpine on 2013-07-17
Hi, can you tell us please, whether you did a WUBI install, or a full install of Ubuntu on its own partition?

---

### Post by Warren Hill on 2013-07-17
Take a look at this question on Ask Ubuntu

[h=1][How to remove Ubuntu and put Windows back on?]("http://askubuntu.com/q/133533/107450")[/h]

---

### Post by BSG Fan on 2013-07-17
Hello Snowpine.

well,,, in my own words: I had a CD-ROM where I downloaded and burned the Ubuntu 12.04, so :
1- re-started the rented computer,
2- I installed Ubuntu as a partition (taking some space without messing with Windows);
and that is it.
.
Every time I start the computer, the screen give me 2 options: Ubuntu or Windows. So, Bingo! that means that I did a full install on its own partition. Applauses to me.

What I do now?
Windows is still installed.

---

### Post by snowpine on 2013-07-17
I think the article Warren posted covers the topic quite well: [http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

Understand you have already "messed with the original system" by repartitioning the drive and installing Ubuntu, so please don't be dishonest with the owner of the computer. ;)

---

### Post by Mark Phelps on 2013-07-17
Since you probablt don't have a Windows CD, this being a rented machine, if it is running Windows 7, then you need to do the following:

1) Use the Win7 Backup feature to create and burn a Win7 Repair CD
2) Boot from that CD and run Startup Repair three times -- that's right, three times
3) Once you boot back into win7 OK, then open the Disk Management utility and remove the Linux filesystem partition(s)
4) When that is done, use the same utility to expand Win7 partition to fill up the space previously used by Ubuntu.

---

### Post by I2k4 on 2013-07-17
I have an old dual boot install I'll get rid of one of these days, meanwhile happy enough running from USB drive.  Thanks Warren Hill for the link - it's where I would start.  

My impression is that the hard part is getting rid of Linux GRUB boot loader that replaces Windows MBR loader.  That screen offering a choice between Windows and Ubuntu is GRUB.  I think a lot of users "trying out" dual boot installations aren't aware that GRUB is separate from the operating system and very intrusive.

---

### Post by suicideking on 2013-07-17
I sort of went through this unintentionally:

I wanted Ubuntu on my Netbook and installed Ubuntu as a dual boot. Literally two days later, another friend emails me that he's selling his laptop for $50 which is nicer than my Netbook. So get the new (to me) laptop and put Ubuntu on in, then want to sell my Netbook. 

So I do a Factory restore on my Dell Netbook. Runs fine and wipes the Win7 partition, but doesn't touch the Linux part. So I figure out through google searches how to default the Ubuntu loader to Win7, then figure I can use Windows to get rid of the Linux partition. Do so, but now the boot loader crashes because it can't find anything. I can't remember the error, but it was in some sort of rescue command line interface.

So more google searches + still had my Ubuntu boot to USB key that worked. Booted to it, Used a Linux boot repair util and selected all defaults: It got rid of the Ubuntu loader and all was fixed.

I know, a little vague in some areas. I'm an Ubuntu noob, but a techie veteran... ):P

---

### Post by mastablasta on 2013-07-18
yeah... well you could restore - remove ubuntu and add disk space to windows and then fix the boot with windows CD. or "fix the boot" (fixmbr) first then restore, , remove ubuntu and add disk space to windows.

---

### Post by BSG Fan on 2013-07-20
I have no the Window's CD-ROM and I am thinking to turn-in the computer to the owner and tell them about the Ubuntu partition. I am sure there will not be a problem.

but my last question:
if I use the same Ubuntu CD-ROM that I used to install the Ubuntu in the computer (in company with the Windows), is there any option in the CD that allow me to erase the Ubuntu WITHOUT affecting adversely (if any) the Windows?

Thank you.

---

