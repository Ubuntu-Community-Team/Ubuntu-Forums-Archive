---
title: "Acer Aspire 5600U"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by olielonline on 2013-12-26
Hello, 

I'm trying to install Ubuntu 13.10 but what seems as a fun project at first has turned into a nightmare. 
I'm getting the message "reboot and select proper boot device" after installation. 

I read online and tried using boot-repair, but nothing helps. 

The only thing that I can think of based on forums and similar topics, is that this computer BIOS is not supported.. (makes sense?)

I'd appreciate any help. Got a small laptop and love the Ubuntu, will be very disappointed to re-install Windows at this point.

---

### Post by JonPaul on 2013-12-26
You will probably need to change to legacy bios and turn secure boot off in your bios settings.

---

### Post by fantab on 2013-12-26
Post more information about your 'small laptop's hardware, like CPU, RAM and Graphics etc.
It is possible that ubuntu.iso didn't burn properly to the DVD/USB. Burn again and try.

BIOS doesn't seem to the issue here. 

However, one thing to check will be HDD boot order in BIOS. On some machines USB/DVD drive becomes first HDD or /dev/sda, and your HDD is second, /dev/sdb. Grub by default install to /dev/sda and this can cause issues...

If you are not sure how to check then post the output of the following commands; after booting Ubuntu USB/DVD and "Try Ubuntu without installing":

```
sudo parted -l
sudo fdisk -l
```

---

### Post by TheDigitalNinja on 2014-01-27
I too am having this exact issue with this exact system. I have tried installing it with and without uefi secure boot. I can boot just fine off of a live usb and even tried installing it that way (as opposed to directly from the usb installer). 

/dev/sda is the correct drive in the machine and it is in the correct boot order. I can even hit f12 to select what to boot and select the HDD and get the same "Reboot and Select proper Boot Device or Insert Boot Media in selected device and press a key" :(

---

### Post by fantab on 2014-01-27
Start a new thread and post the output of the above two commands. It looks more like a HDD issue.

---

### Post by TheDigitalNinja on 2014-01-27
It ran windows just fine until 5 hours ago when I first started trying to get Ubuntu 13.10 installed on it. Should I still start a new thread? Pretty sure it is the exact same issue.

---

### Post by TheDigitalNinja on 2014-01-27
FIXED IT
After installing it once boot off the live cd/usb again
then download and run the [boot repair tool]("https://help.ubuntu.com/community/Boot-Repair")
choose advanced and disable the "Secure boot" option.
follow the instructions it gives, reboot, rejoice.

---

### Post by Bucky Ball on 2014-01-28
> **fantab said:**
> Start a new thread and post the output of the above two commands. It looks more like a HDD issue.

Next time, take this advice and start a new thread rather than hijacking someone else's. It is unfair to the OP, different issue and probably not even the same machine (or possibly release). You will also greatly increase your chances of getting help if you start a new thread rather than tagging on to bottom of one that hasn't seen action in a month and has a thread title that has nothing to do with your issue.

You also can't mark this thread as solved so anyone looking for help would have to get very lucky to stumble across your fix and get any benefit from it here. Thanks.

---

