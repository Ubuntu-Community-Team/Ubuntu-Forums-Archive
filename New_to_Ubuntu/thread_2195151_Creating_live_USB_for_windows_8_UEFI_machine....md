---
title: "Creating live USB for windows 8 UEFI machine..."
date: 2013-12-22
forum: New to Ubuntu
---

### Post by nzdreamer55 on 2013-12-22
Hello everyone,

I have windows 8 Pro x64 installed on my computer and I would like to create a live ubuntu USB drive to scan my system for viruses.  I tried this once in the past (6-8 months ago) and had problems rebooting to my windows OS.  I must of done something wrong and thus I want to ask for advice before trying it again.  

Thanks

Steve

---

### Post by devine.steve on 2013-12-22
As long as you don't install the OS it won't change anything. Also it would be best to mount the internal disk in RO mode. 
(/dev/sda1 may have to be changed to fit the situation.)
mount -o ro /dev/sda1 /mnt

---

### Post by varunendra on 2013-12-22
I see that Steve has received good advice from Steve (the devine one :P). I'd just like to add something..
> **nzdreamer55 said:**
> ..and I would like to create a live ubuntu USB drive **to scan my system for viruses**.  I tried this once in the past (6-8 months ago) **and had problems rebooting to my windows OS**.  I must of done something wrong and thus I want to ask for advice before trying it again.

Not only Linux ones (like ClamAV), but any external antivirus program will tend to repair/remove any files that it detects as 'infected'. By 'external' I mean an antivirus program that is running off a different OS or a Live cd/usb etc., and not installed on the same OS which you are scanning.

Now many viruses tend to corrupt windows system files first, and if your antivirus 'repairs' or removes those files, windows will almost certainly fail to boot, or at least fail to work properly. Although most of the antivirus programs ask the user what action to take before modifying/moving/deleting any files, it is upto you to verify it is not going to affect any **system files**, and if it is, make the hard decision of either taking the risk or leaving it infected (thus defeating the purpose of scanning).

If you just want to make sure that your Windows partition is not infected, devine.steve's suggestion to mount it as **read-only** is a good one. But if infections are found, you'll have to remount it with read/write permission to be able to repair/remove the infections. Obviously, it would be upto you to verify that the detections are not 'False Alarms', and the action is not going to affect windows system files.

One last thing - Not all antiviruses are good at detecting latest viruses. So make sure the one you are going to use is known for good detection rate, and its virus definition database is up to date.

---

### Post by nzdreamer55 on 2013-12-25
Thanks for the wonderful help.  Can you suggest which version of ubuntu I should try and how to create a usb disk with it as a live version of this task?  I have a AMD cpu, 16gb ram, and ASUS Mobo ~ 1-2 years old.  Also do I want to create a live version that allows me to save changes?

-S

---

### Post by varunendra on 2013-12-26
All supported versions will get the same most up to date virus definitions when updated, so any of them would do. I personally would suggest to go with the latest LTS which is 12.04.3, although the next LTS is going to be released in April next year.

If you intend to use this live usb on different computers and are not sure which architecture they may be of (32 bit or 64 bit), go with the 32 bit version, otherwise if all the computers it will be used on are 64 bit, go with 64 bit.

For method, I personally prefer the inbuilt Startup Disk Creator program which can be run from the live CD/DVD, and the same CD/DVD will then be used by it as the source of live setup for the usb drive. If you want to directly use the ISO and don't want to burn a CD/DVD, you can either use the same method on a virtual machine, or some external program like Unetbootin, whose success rate is quite good.

---

### Post by nzdreamer55 on 2013-12-26
> **varunendra said:**
> 
For method, I personally prefer the inbuilt Startup Disk Creator program which can be run from the live CD/DVD, and the same CD/DVD will then be used by it as the source of live setup for the usb drive. If you want to directly use the ISO and don't want to burn a CD/DVD, you can either use the same method on a virtual machine, or some external program like Unetbootin, whose success rate is quite good.


Wonderful.  This help.  So I am going to go with the current release and not wait until april 2014.  I don't actually have a optical drive that will write to media.  I will need to create a usb drive with ubuntu live.  I will check out unetbootin.

The one issue that I had last time is that I set up my USB live to save changes that I made while running the linux os from the usb.  I'm not sure what this is called (Permence?).  Do I need to do this to accomplish what I am trying to do?

-S

---

### Post by varunendra on 2013-12-26
> **nzdreamer55 said:**
> The one issue that I had last time is that I set up my USB live to save changes that I made while running the linux os from the usb.  I'm not sure what this is called (Permence?).  Do I need to do this to accomplish what I am trying to do?

Oh yeah, you do need 'Persistence' (this is what it is called by the way :)). Unetbootin supports that (the "Space used to preserve files across reboots.." option).

Although it is not necessary, but it makes much more sense to install programs and update them (including virus-definition database) once and be able to carry these programs/updates to different computers, than to install and update everytime you need to use it.

---

