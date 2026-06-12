---
title: "Forgot ALL KINDS of passwords. Cant get in recovery mode"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by Granola on 2013-04-29
As the title says, I forgot my user password and root password... I can enter in ubuntu though because I have the autologin set.

I tried pressing and holding ESC and SHIFT while grub is loading, while the computer is turning on and, after selecting Ubuntu in the grub menu but I can't get to recovery mode so I can reset my passwords. 

I can't install anything without the root password and I really need to.

I have Ubuntu 12.10

Please me! Thanks for reading.

---

### Post by fantab on 2013-04-29
Why can't you get into "Recovery" mode? Does it show on Grub Menu? 
If you can get into recovery mode then this should Help: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If you can't get into 'recovery' mode for some reason then you can [**chroot**]("https://help.ubuntu.com/community/BasicChroot") into your installed Ubuntu from Ubuntu LiveDVD/USB.

---

### Post by davidbaumann on 2013-04-29
Shouldnt chpasswd work when you are logged in, anyways?

David.

---

### Post by fantab on 2013-04-29
> **davidbaumann said:**
> Shouldnt chpasswd work when you are logged in, anyways?

David.

But then OP has to enter his/her "current password", doesn't he/she?

---

### Post by audiomick on 2013-04-29
> **davidbaumann said:**
> Shouldnt chpasswd work when you are logged in, anyways?

David.

> **fantab said:**
> But then OP has to enter his/her "current password", doesn't he/she?


Yes, the current password would be needed for that. I assume that would need to be run with sudo, and you need your password for that.

---

### Post by grahammechanical on 2013-04-29
> [COLOR=#000000] I forgot my user password and root password.[/COLOR]

I only have a user password. I never had to set a root password. In Ubuntu we only need a user password even when we need Administrator privileges. So, I am a bit concerned when you say that you have forgotten your root password. How long have you had this machine? How long have you been using Ubuntu. If you think that I am a bit suspicious, then understand that I do not know you. You do not have reputation on this forum.

Regards.

---

### Post by Granola on 2013-04-29
> [COLOR=#000000]I only have a user password. I never had to set a root password. In Ubuntu we only need a user password even when we need Administrator privileges. So, I am a bit concerned when you say that you have forgotten your root password. How long have you had this machine? How long have you been using Ubuntu. If you think that I am a bit suspicious, then understand that I do not know you. You do not have reputation on this forum.[/COLOR] < I am new to ubuntu. I think I never set the root password.  Nevertheless, I can't remember my user password either. I get that you dont trust me because of my reputation but I didnt come here without looking for solutions before. I've been trying to solve these for 2 days now but I can't!

> [COLOR=#000000]Shouldnt chpasswd work when you are logged in, anyways?[/COLOR]   < Does not work.

> [COLOR=#000000]Why can't you get into "Recovery" mode? Does it show on Grub Menu?[/COLOR] < No it doesnt. It only shows my windows 7, ubuntu, and memtest

---

### Post by MrSteve on 2013-04-29
please try

Booting into recovery mode

    Switch on your computer
    Wait until the BIOS finishes loading (you will probably see a logo of your computer manufacturer)

    The following messages may show up:

    Grub loading stage1.5

    Grub loading, please wait...

    Quickly press the Shift key or Escape, which will bring up a boot menu. (If you see the Ubuntu logo, you've missed the point where you can enter the GRUB menu)

    Select the line ending with '(recovery mode)', probably the second line, something like:

    Ubuntu, kernel 2.6.17-10-generic (recovery mode)

    Press enter and your machine will begin the boot process.
    After a few moments, your workstation should display a menu with a number of options.

---

### Post by Elfy on 2013-04-29
do you not see something like 

Advanced Options for Ubuntu 

if you do - use that and you should see a new menu with 

Ubuntu <kernel>
Ubuntu <kernel> recovery mode

---

### Post by Granola on 2013-04-29
> **MrSteve said:**
> please try

Booting into recovery mode

    Switch on your computer
    Wait until the BIOS finishes loading (you will probably see a logo of your computer manufacturer)

    The following messages may show up:

    Grub loading stage1.5

    Grub loading, please wait...

    Quickly press the Shift key or Escape, which will bring up a boot menu. (If you see the Ubuntu logo, you've missed the point where you can enter the GRUB menu)

    Select the line ending with '(recovery mode)', probably the second line, something like:

    Ubuntu, kernel 2.6.17-10-generic (recovery mode)

    Press enter and your machine will begin the boot process.
    After a few moments, your workstation should display a menu with a number of options.


I tried doing that. I really did. After doing that it shows the grub with only 4 options (Windows 7, Ubuntu, and MEMTEST 2 TIMES)

---

### Post by Granola on 2013-04-29
> **Elfy said:**
> do you not see something like 

Advanced Options for Ubuntu 

if you do - use that and you should see a new menu with 

Ubuntu <kernel>
Ubuntu <kernel> recovery mode

I just dont see it.! -- I've tried with LEFT SHIFT, ESC, RIGHT SHIFT AND ENTER

---

### Post by Granola on 2013-04-29
I think the advanced options in the grub is not showing because I hid it whit a program called "Grub Customizer" which ironically I can not use because I need the user password to open it.

Ideas anyone?

---

### Post by oldfred on 2013-04-29
Is this a wubi install?

Post this.

sudo fdisk -lu

---

### Post by Granola on 2013-04-29
> **oldfred said:**
> Is this a wubi install?

Post this.

sudo fdisk -lu

No, it is not a wubi install. 

I can't use that command since I don't have the password.

---

### Post by deadflowr on 2013-04-29
Look here

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by fantab on 2013-04-30
Granola, it will be very difficult for you 'reset' password without remembering your present password and not having Ubuntu 'recovery mode has made it nearly impossible. 

My suggestion is **BACK UP your important DATA** and **RE-INSTALL Ubuntu**.

---

### Post by TRPrecht on 2013-04-30
> **fantab said:**
> Why can't you get into "Recovery" mode? Does it show on Grub Menu? 
If you can get into recovery mode then this should Help: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If you can't get into 'recovery' mode for some reason then you can [**chroot**]("https://help.ubuntu.com/community/BasicChroot") into your installed Ubuntu from Ubuntu LiveDVD/USB.


Thanks for the link, one of my coworkers just asked about how to do this and I couldnt remember the entire process.

---

### Post by Bunkerman1 on 2013-05-10
Thanks for the link fantab, password reset to one I can remember :)

---

