---
title: "HOWTO: iBook G4, boot from external firewire drive"
date: 2005-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by interrupt on 2005-04-26
Don't know if this is useful but I have got Ubuntu to successfully boot from an external firewire drive connected to my G4 iBook.

I don't have much time now so am going to post only the bare essentials but it should be enough if combined with lots of research online.

The problem I faced is not being able to install Ubuntu (to be honest I'm not sure if it's Warty or Hoary - whatever!) on my external firewire disk. The install worked but fell-down when it came to the install yaboot stage.

I first did another install on some spare space on the iBook's internal drive and got a functioning standard Ubuntu system. Next I made swap space and a root partition on the external drive and used dd to mirror the root partition from the internal drive to the new root partition on the external drive.

I first tried to boot off the kernel on the internal drive and pass it root=/dev/sda5 (my root partition on the firewire drive is on sda5). Naturally, this failed because the firewire drive is not recognised until after the root partition is already up and running (Catch-22).

The answer is to boot via an initrd whose linuxrc script gets the firewired drive "up" on the scsi bus, then switches root to be on the root partition on the now-recognised firewird drive.

So, the linuxrc script first scans the scsi bus using:
[COLOR=Indigo]echo "add-single-device 0 0 0 0" > /proc/scsi/scsi[/COLOR]
(0 0 0 0 worked on my system - use output from cat /proc/scsi/scsi to determine)

then I have the script wait for a bit (sleep 1)

then switch root to the firewire root partition with:
[COLOR=Indigo]echo 0x805 > /proc/sys/kernel/real-root-dev[/COLOR]
(0x805 is for /dev/sda5 which is the root partition on my firewire drive - get this number by doing ls -al /dev/sdxx for your external root partion and getting the major and minor device numbers)

then unmount /proc, then exit and ubuntu will continue to boot off the external firewire drive. I think you should have changed /etc/fstab on the external root drive to reflect the fact that your going to be using the external partiton as root.

You can then use yaboot to boot from the external drive. The only trouble I had here was finding the openfirmware alias for my firewire drive. devalias didn't work but I found the information by examining the /proc structure:
[COLOR=Indigo]find /proc/device-tree -name disk@\* | grep firewire[/COLOR]
(the bit starting pci@... is the openfirmware alias)

Like I said this is a bit sketchy but should help.

cheers.

---

### Post by kant on 2005-05-25
Thank you interrupt for the info,
Does this mean that you could just install ubuntu on an internal disk (PowerBook G4 FW800) and take the disk out, put it in a firewire enclosure and boot from that?
I think I will try it...

Thank you again!

---

### Post by interrupt on 2005-05-25
Not sure if you're joking, kant  ;-) 

The main problem with booting from an external firewire disk is that even with a correctly configured kernel (i.e. one that can communicate with the firewire drive), firewire drives only become accessible *after* the root filesytem has been set up (I think this is a kernel flaw). This is a classic Catch-22™ situation. I got around it by booting via a temporary RAM disk which gets your firewire disk visible to the system then transfers the root filesystem over to it, then quits and lets the boot process continue from the firewire drive.

---

### Post by kant on 2005-05-26
D'oh,
I did not realize that...
My bad.

---

### Post by squirll on 2005-06-02
that ened up being exactly what i tried to do today, except i didn't know it would be a problem.

do you think that could be put in plain english for a noob?

---

### Post by xale on 2005-06-18
interrupt, could you please post your entire linuxrc file? ... or at least the relevant parts of it?

i'm struggling with explainations on several sites, and it's some sort of an headake if you've never done something like this before!

however, thank you for your post!

a.l.e

---

### Post by dendave on 2005-07-01
Thanks for the info. This is the most interesting post on this topic I have seen. Of course booting first from the internal drive is not an option for all of us. What would be great is if this procedure could be scripted in such a way that the drive is usable on macs without prior install or openfirmware fiddling. This seems to be the achilles heel. Of course we know that folks at IBM and YDL have somehow figured it out but there is little or no info on this.  Your post is the first that offers a clue. Firing off a ram disk does sound like the way to go.

---

### Post by omigosh on 2005-07-05
Hi there, I am looking into getting an external hard drive as a backup solution for my powerbook G4 (just in base it dies on me). I believe that I can boot powerbook G4 from an external hard drive. If this is correct, what type of hard drive should I look for and what specifications should I keep a lookout for?

If this is a silly question, please excuse me, as I am quite a non-Mac savvy person as I just got into Mac.

Cheers!
Liz.

---

### Post by interrupt on 2005-07-08
sorry i've been away from these parts for a while.

someone else started a thread about external drive booting issues so if any of you want to post questions

[here](http://ubuntuforums.org/showthread.php?p=245867#post245867) 

i'll try to help.

cheers

---

### Post by glenboarder99 on 2008-03-12
Can you tell me how to install it on an ex HD without putting it on the internal

---

