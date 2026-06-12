---
title: "Saving Ubuntu installation"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by medusa93 on 2012-04-01
I would like to learn to save my Ubuntu installation. I have windows XP and Ubuntu installed on my laptop. My windows is acting up and I want to overwrite my windows with an image that I have saved of my windows installation nearly a year back. 

[LIST=1]
[*]Will that mean that I will loose my Ubuntu installation as well?
[*]Can I image my Ubuntu installation like how I did with windows?
[/LIST]

---

### Post by HiImTye on 2012-04-01
you will be able to install Windows with probably no issue but you will need to use an Ubuntu LiveCD to put a bootloader back to load Ubuntu

---

### Post by medusa93 on 2012-04-01
Thank you for the reply. I don't want to reinstall Ubuntu from scratch. What I can I do to retain my settings, installed software etc.

---

### Post by r-senior on 2012-04-01
How did you install Ubuntu? Did you install alongside Windows as a dual boot, or did you use Wubi? If you used Wubi, Ubuntu is probably still within your Windows disk partition and will be lost if you re-install or re-image.

What's the tool you are using for re-imaging? Do you know that it is capable of re-imaging partition by partition, or is it going to re-image the whole disk?

---

### Post by medusa93 on 2012-04-01
Thanks for you reply
I installed Ubuntu alongside Windows as a dual boot. 

I seek advice regarding imaging and reimaging Ubuntu so that I do not loose my settings

With regard to Windows which I want to reimage, I use a tool called Driveimage XML which can reimage partition by partition. I plan to reimage the C drive from an external harddrive by booting with a BartPE boot CD which has a DriveImage XML plugin

---

### Post by medusa93 on 2012-04-01
Will PartImage serve my purpose? I have been Googling a lot and this looks like the thing

---

### Post by mastablasta on 2012-04-01
> **medusa93 said:**
> 
I installed Ubuntu alongside Windows as a dual boot. 

then if you reimage windows partition you can restore just that part. but liek it was mentioned you might need to restore GRUB boot loader using ubuntu liveCD. it's fairly easy thing to do. 4 steps:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

the data on Ubuntu parittion should be left untouched. 

i do not know your programme you used to make the image. but one of the most featurefull and free is Clonezilla, hwoever i find it's graphical interface to be very poorly designed and you need to know what you are doing sicne you can't simpyl go back and change the setting.
more easy to use is redobackup (see my signature).

---

