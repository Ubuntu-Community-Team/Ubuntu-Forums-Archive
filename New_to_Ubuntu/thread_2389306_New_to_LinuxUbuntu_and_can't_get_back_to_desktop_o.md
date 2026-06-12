---
title: "New to Linux\Ubuntu and can't get back to desktop or anything?"
date: 2018-04-15
forum: New to Ubuntu
---

### Post by savmick on 2018-04-15
First off I did ask a question about the boot error I have failed to connect to lvmetad in general help.  Anyway I know it is not a good thing to post twice but I am not going to ask the same question. I just want to know how to do a clean install if I am stuck in boot not getting to login. I don't have access to a computer running Windows at the moment only my Moto G5 running Android 7.1. I really need to get my laptop back running tonight cause I am going to a meet to fly fpv drones tomorrow and can't access Betaflight Configurator to setup new flight controller. I am so mad at myself for upgrading today and ruining my install I just got serial port access and Betaflight Configurator and BlHeli Configurator working perfect! Sucks I have been reading all afternoon and can't get it figured out! PLEASE HELP ME get a working version of Unbuntu installed cause I doubt I can fix the current problem. Failure to connect to lvmetad! Thanks again!

---

### Post by kerry_s on 2018-04-15
> Failure to connect to lvmetad! 

that's nothing standard message when using lvm.

have you tried rebooting & waiting again? some times it can take a little longer to boot after upgrade.

---

### Post by savmick on 2018-04-15
> **kerry_s said:**
> that's nothing standard message when using lvm.

have you tried rebooting & waiting again? some times it can take a little longer to boot after upgrade. Hey thanks for the reply! Yeah I waited at least 30 mins a couple times. I have tried the only other kernel that is a option to boot but it did the same thing. Can I recover back to 16.04 some way? I would even be happy to reinstall if I could use a iso that I have for 16.04. But it isn't a bootable image  it's standard iso. I am reading a ton about Grub and other stuff but it is a bunch of stuff and takes a while to learn what to do when things go south. Anyways I can supply more info just not sure what will help. Thanks again!

---

### Post by kerry_s on 2018-04-15
does your boot options let you select efi file?
boot option=f12, f2, esc, f9

the key you can press to select boot device from list

---

### Post by savmick on 2018-04-15
> **kerry_s said:**
> does your boot options let you select efi file?
boot option=f12, f2, esc, f9

the key you can press to select boot device from list

From the device bios or in grub? I am going to try it now. Sorry I fell asleep last night. Its going to storm here so no fpv drone meet today . Anyway I really appreciate you taking the time to help me!

---

### Post by savmick on 2018-04-15
> **savmick said:**
> From the device bios or in grub? I am going to try it now. Sorry I fell asleep last night. Its going to storm here so no fpv drone meet today . Anyway I really appreciate you taking the time to help me!

I think you meant my laptops bios menu which is a older device just has bios. I finally figured out how to get update through virtual terminal and lan cable. BUT it's still hanging at checklist after splash screen! Arrggggghhh! I see a bunch of people have this same issue! I wish I knew more about the grub 2 options and more command line. Oh well I guess I am not going to be able to use it for awhile!

---

### Post by bsodx on 2018-04-17
It seems like you need to reinstall Ubuntu- I'm not a ubuntu pro(yet) so can't help with recovering, only thing I can help is to reinstall.

You need a computer or some real much Android knowledge and a rooted phone, and you need a way to make bootable disks form an android, which I know is very hard

When you get access on a computer(any one that has internet and can burn a bootable usb) you install ubuntu iso and burn it with rufus

You then use that drive to delete the partition of ubuntu and rewrite the grub

---

### Post by QIII on 2018-04-17
Don't reinstall.  That is like blasting off and nuking the planet from orbit.

Let's try a bit more at solving ths problem before we jump to reinstallation, please.  While it may come to that, reinstallation should not come first to mind.

Thanks.

---

### Post by bsodx on 2018-04-17
I can't think of a solution right now-mainly because I'm still on the basic-ish level.

If we can have a solution that'd be better indeed, I really want to see where's the culprit.

---

### Post by savmick on 2018-04-17
Hey again I appreciate your time and help! But I already did a clean install with iso, Rufus, and USB stick. I really didn't want to reinstall but no biggie since I had only installed the original setup about 3 weeks ago. Again thank you! I am going to be a Linux user for awhile and hope to learn the in and outs of the OS.

---

