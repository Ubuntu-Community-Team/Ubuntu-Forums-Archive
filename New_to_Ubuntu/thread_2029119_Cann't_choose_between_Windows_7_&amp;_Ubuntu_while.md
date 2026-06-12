---
title: "Cann't choose between Windows 7 &amp; Ubuntu while booting"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by Linuxour on 2012-07-19
Hello,

I installed Ubuntu 12.04 **alongside** Widows 7 - it took space from ( C ) driver but when i use Windows 7 the Linux Drive doesn't appear -   when i boot my system it **automaticly** run Windows 7 , it doesn't make me choose between Windows 7 and Ubuntu .

* I installed Ubuntu using a USB .

What should i do ?

---

### Post by rukiaEnix on 2012-07-19
Did you install grub at installation time?

---

### Post by Linuxour on 2012-07-19
> **rukiaEnix said:**
> Did you install grub at installation time?

Sorry , but i don't know what you mean 

Can you tell me how to install it , please ?

And i'll tell you if i installed it or not .

---

### Post by rukiaEnix on 2012-07-19
When you installed Ubuntu with the USB, did it ask to install the grub boot loader?

Try to remember.

If not, first identify your hard disk.

Please post the result of this:

```

sudo fdisk -l

```

---

### Post by Kopkins on 2012-07-19
So it sounds like you can't boot to Ubuntu, correct?

The reason you can't see linux from windows is that the default Ubuntu filesystem is not compatible with windows, so windows cannot see it.

Grub would normally be installed automatically during the install. There is an option for bootloader install. The default is /dev/sda, which is what you would want. If you change it to another partition chances are you're not going to get to grub.

The users who asked you to post the results of a command are asking you to do so from Ubuntu, in a terminal. 

If you can't boot to Ubuntu, boot from the liveCD. Then go to the dash, and type terminal.
When the terminal opens you can copy and paste the commands they requested.

Best of luck,
Kopkins

---

### Post by Linuxour on 2012-07-20
[CENTER][SIZE=2]Thanks a lot every one , the problem was solved
[/SIZE][/CENTER]

---

### Post by Kopkins on 2012-07-20
Don't forget to mark your thread as solved by editing your first post. 
 
Kopkins

---

### Post by NikTh on 2012-07-20
> **Kopkins said:**
> Don't forget to mark your thread as solved **by editing your first post. **

I think this is not necessary. 
Just click on **Thread Tools** and then **mark this Thread as solved**. 
:)

---

### Post by Kopkins on 2012-07-21
> **NikTh said:**
> I think this is not necessary. 
Just click on **Thread Tools** and then **mark this Thread as solved**. 
:)

Ah, yes. On the Arch Linux forums you have to edit the first post. Thanks.

---

