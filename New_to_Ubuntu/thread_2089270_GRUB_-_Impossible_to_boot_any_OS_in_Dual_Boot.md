---
title: "GRUB - Impossible to boot any OS in Dual Boot"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by AlexDeA on 2012-11-28
Hi Everyone.

I'm experiencing an issue with the boot of the system.

I did not use ubuntu for several months and when I had begun to use it again, I had decided to update it at the version 12.04 LTS. 

After this upgrade I was no more able to choose any OS installed in my PC (Ubuntu and WinXP). I mean that the new graphical "purple" version of GRUB 1.99-21ubuntu3.4 seems freezed and it does not respond to any input from the keyboard to go ahead. 

I have just tried to advance the version to 12.10 through the live CD, but I have not solved the issue.

Could you please help me?

Thanks in advance!

---

### Post by oldfred on 2012-11-28
Welcome to the forums.

What version were you at before?

If going from 10.04, did you test with liveCD/DVD/flash to see if system worked ok with you hardware. Many have video issues and there is a major change in the default gui - Unity.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
From liveCD post link to Boo

---

### Post by BertN45 on 2012-11-28
Try:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It seems also to work in simular freeze cases.

---

### Post by AlexDeA on 2012-12-01
Hi Everyone.

Thanks for your kind replies and suggestions.

I've tried different solution without success. 

The unique way was to reistall again the version 10.04, but I was not able to move the option selection as in 12.04 LTS. 

In this case Ubuntu (first choice) ran up and the boot was successful.

Through the GRUB menu I had modified the default, setting Win XP as OS to boot up. Now I can work with Win, but no way to access to Ubuntu.

Thanks again.

---

