---
title: "UM20 does not boot due to ACPI error"
date: 2020-10-31
forum: New to Ubuntu
---

### Post by tiam-tj on 2020-10-31
Hi,

I am new to Linux and Ubuntu and have been using Ubuntu Mate 20.04 (64bit) for a couple of weeks now on my toshiba satellite l755d-13v notebook.

All in all everything has been working well but right now the system won´t boot. Instead I get the error messages:
1.55 No irq handler for vector
ACPI BIOS error (bug): Could not resolve symbol [\_PR.C002.PPC] , AE_NOT_FOUND
 
As you can see in the attached picture there was some more output which I unfortunately could not make much sense off.

After googling the Problem i tried setting acpi=strict in the GRUB advanced options. This didnt solve the problem. 

Any help would be much appreciated. Thank You!

Best Regards,
Tiam

---

### Post by yapidumoac on 2020-10-31
Boot from a bootable DVD and run fsck on vgubuntu-mate-root

---

### Post by tiam-tj on 2020-11-01
Hi first of all thank you for your answer. 

Can you please be a bit more specific as to what I have to do once I booted from DVD - I mean how do I "run run fsck on vgubuntu-mate-root"? Trough the terminal? If yes what exactly do I have to type in?

---

### Post by tiam-tj on 2020-11-02
when I type fsck into the terminal it says fsck from util-linux 2.34

---

### Post by yapidumoac on 2020-11-02
>> Can you please be a bit more specific as to what I have to do once I booted from DVD - I mean how do I "run run fsck on vgubuntu-mate-root"? Trough the terminal? If yes what exactly do I have to type in? 

"Using the text console in Linux Mint is very easy. Access it by pressing Ctrl-Alt-F1"

[https://securitronlinux.com/bejiitaswrath/using-the-text-console-in-linux-mint-13-how-to-use-linux-the-proper-command-line-way/](https://securitronlinux.com/bejiitaswrath/using-the-text-console-in-linux-mint-13-how-to-use-linux-the-proper-command-line-way/)

> when I type fsck into the terminal it says fsck from util-linux 2.34 

[https://phoenixnap.com/kb/fsck-command-linux](https://phoenixnap.com/kb/fsck-command-linux)

---

### Post by ajgreeny on 2020-11-02
You can not run fsck on a partition of your running system which is why **yapidumoac** told you to run it from a live system.

You should boot to a live Ubuntu USB (or any of the *buntu family) and then run command ```
sudo e2fsck /dev/sdx#
``` where sdx# is the root partition of the installed system.

---

### Post by tiam-tj on 2020-11-03
So yesterday I tried booting from DVD and then running fsck from the terminal. This didnt work as I couldnt access vgubuntu-mate-root         . I figured the reason might be because the disc is encrypted.

Then I tried to boot normally and ran fsck from start. (I realize now that this was probably a mistake)

However the system was able to run fsck from there and it showed some errors that could be fixed.  (See [https://ibb.co/SQYXKDT](https://ibb.co/SQYXKDT) )

Now the system still wont boot. The difference is that now there is no error message it just gets stuck on the loading screen.

---

### Post by CelticWarrior on 2020-11-03
That's the problem with encryption: You MUST have good backups. Having them a reinstallation is fast and easy. I'n afraid that's what you have to do now.

---

### Post by tiam-tj on 2020-11-03
> **CelticWarrior said:**
> That's the problem with encryption: You MUST have good backups. Having them a reinstallation is fast and easy. I'n afraid that's what you have to do now.

Well thats bad. Youre sure there is no working alternative?

---

### Post by QIII on 2020-11-03
Between the encryption issue and running fsck on a mounted partition -- which is a destructive process and resulted in the ruination of your system -- your options are limited to just the one indicated.  You might have a very slim chance of recovering a small portion of your data from a live system using something like photorec -- but you would have to know what you were doing and have storage media connected to accept the files.  Even then, some of the meta-data, such as file names and dates, would likely be lost.  It would also have been encrypted with little chance of decryption at this point.

You can have fsck run on startup if you set things up properly or issue a particular command to have that happen once at next boot, but it will be done just after loading certain parts of the kernel before the other partitions are mounted.  If you run it from the command line, that is to say after the file system is mounted, you will most certainly utterly destroy things.

By the way, if anyone tries to tell you that they have never done something just like this when they were learning, make sure you have your rubber overshoes on.  There will be a lot of unsavory stuff to step in.  We have ALL been where you are.  You are in good company.

Bear this in mind:  If you have root or sudo rights when you do something, Linux will assume you know what you are doing.  It's best to actually know what you are doing -- which you can learn by asking first.

---

### Post by tiam-tj on 2020-11-04
> **QIII said:**
> Between the encryption issue and running fsck on a mounted partition -- which is a destructive process and resulted in the ruination of your system -- your options are limited to just the one indicated.  You might have a very slim chance of recovering a small portion of your data from a live system using something like photorec -- but you would have to know what you were doing and have storage media connected to accept the files.  Even then, some of the meta-data, such as file names and dates, would likely be lost.  It would also have been encrypted with little chance of decryption at this point. 

Well first of all thanks for your help and the clarification. I will therefore re-install. Luckily I was able to access my home folder and backup the data trough a live version. I just had to type in my password. I am curious why you thought this wouldnt be possible?

---

