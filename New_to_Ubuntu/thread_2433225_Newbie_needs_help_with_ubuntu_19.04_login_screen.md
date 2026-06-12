---
title: "Newbie needs help with ubuntu 19.04 login screen"
date: 2019-12-15
forum: New to Ubuntu
---

### Post by drelliott06 on 2019-12-15
Background Story:

I had an old computer setting around and I decided to turn it into an ubuntu plex media server.

I installed ubuntu 18 and updated to 19.04.

It took forever to get everything working as I am less than an amateur with linux, however I did get it setup.

I tried to login the other day to update ubuntu and plex but everytime I type my username and password it says "incorrect login"


Now the Problem:

I do not have a GUI installed.  I am stuck on the ubuntu 19.04 TTY1 login screen in terminal.  

I have read so many solutions online and watched a ton of videos most of which say that I need to get to GRUB so I can get into recovery and reset my password.

I can't do anything beyond this login screen.  So I am asking for assistance on my next step.

Thank you in advance.

---

### Post by Impavidus on 2019-12-16
Exactly as all those guides tell you: you have to access the grub menu to boot in recovery mode. Hit shift (or escape, if UEFI, I think) as soon as the computer boots to get to the menu.

For the next time: it is possible to configure grub to always show the menu for a few seconds before booting the default entry. That makes it easier to access the menu. If you really can't get to the grub menu, it's also possible to fix this (change the password or make the grub menu visible) using a live disk.

BTW, a media server is exactly the kind of thing where it makes most sense to use LTS releases. It would have been better to stay with 18.04.

---

### Post by drelliott06 on 2019-12-16
Thank you for the reply.

I just discovered last night about the LTS releases.  Definitely going to pay closer attention to that.  Good advice. 

I have tried the shift key and every other possible way to get to the grub menu.  Does not work for me.  Goes straight to login screen. 

I made some progress.  A little.

I got the boot USB working and under the help menu I got shell access.  

At this point I think I need to get out of the recovery system and gain root access into my system.

I am having trouble with this part.

---

### Post by Impavidus on 2019-12-16
Have a look here:
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)
Although it mentions a live cd, it's the same with a live usb or dvd. It's a bit older, but still correct.

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
This allows you to use the tools from your live disk on the installed system.

And for the lazy solution, I think boot-repair's recommended repair unhides the grub menu:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by drelliott06 on 2019-12-16
> **Impavidus said:**
> Have a look here:
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)
Although it mentions a live cd, it's the same with a live usb or dvd. It's a bit older, but still correct.

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
This allows you to use the tools from your live disk on the installed system.

And for the lazy solution, I think boot-repair's recommended repair unhides the grub menu:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


This is great information.  Thank you.

I tried the lazy solution already and could not get it to work.  Not sure why.

I will try the change root method as this is were I got to last night.  I can't seem to get chroot to work in the live usb shell.  More reading!

---

### Post by mörgæs on 2019-12-16
> **drelliott06 said:**
> 
I installed ubuntu 18 and updated to 19.04.


This is probably where all problems originated. Better to pick the release you want and do a clean install.

As you have to proceed from 19.04 in january anyway you could consider installing 19.10 now.

---

### Post by drelliott06 on 2019-12-16
Despite multiple attempts with every method I could find, I simply can not get this to work.

I have decided to redo the server install using ubuntu server 18.04 LTS as suggested.  

Thanks everyone for the help.

---

### Post by drelliott06 on 2019-12-16
> **mörgæs said:**
> This is probably where all problems originated. Better to pick the release you want and do a clean install.

As you have to proceed from 19.04 in january anyway you could consider installing 19.10 now.


I think you are correct.  I am doing a clean install.

---

### Post by drelliott06 on 2019-12-17
I have the new ubuntu server up and running better than ever!

I have a question.

I created an LVM volume and mounted that to /mnt/media (LVM volume is 10TB)

I installed samba and in the config file I listed the path as /mnt/media

When I access the media file via windows it is only listed as 5TB.

Is this just how windows views LVM or did I do something wrong.  

Thanks,

---

### Post by deadflowr on 2019-12-17
> **drelliott06 said:**
> I have the new ubuntu server up and running better than ever!

I have a question.

I created an LVM volume and mounted that to /mnt/media (LVM volume is 10TB)

I installed samba and in the config file I listed the path as /mnt/media

When I access the media file via windows it is only listed as 5TB.

Is this just how windows views LVM or did I do something wrong.  

Thanks,

I would suggest starting a new thread on this issue so those who understand lvm and/or samba can help.
Otherwise they might not even see the issue in this thread.

---

### Post by drelliott06 on 2019-12-17
> **deadflowr said:**
> I would suggest starting a new thread on this issue so those who understand lvm and/or samba can help.
Otherwise they might not even see the issue in this thread.


Sounds good.

---

### Post by hk42 on 2019-12-17
> **mörgæs said:**
> This is probably where all problems originated. Better to pick the release you want and do a clean install.

As you have to proceed from 19.04 in january anyway you could consider installing 19.10 now.

+1
Having installed  19.04 with no problems at all on 2 computers
I tried 19.10 it crashed on both.
So I stay with 19.04 and I'm happy :-)

---

