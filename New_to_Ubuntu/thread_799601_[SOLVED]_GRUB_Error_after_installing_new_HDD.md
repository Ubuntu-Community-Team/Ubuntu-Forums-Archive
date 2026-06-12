---
title: "[SOLVED] GRUB Error after installing new HDD"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by src2206 on 2008-05-19
Hello

I have recently installed a SATA II HDD to add to my present 160GB SATA II and 80GB PATA. The Ubuntu is installed in the first partition of PATA 80GB.

The **Older SATA is Disc 1 and newer SATA is Disc 2. So the PATA 80GB is Disc 3**. As I try to boot from my GRUB floppy (I installed the GRUB on Floppy), I get a black screen with the word GRUB and a cursor blinking beside it.

Is there any way to get the Ubuntu working again? :confused:

---

### Post by hermes0710 on 2008-05-19
Do you reach the phase where you are supposed the os you want to boot?

---

### Post by src2206 on 2008-05-19
Nope, I do not reach to that stage.

And when the GRUB word is displayed, I can't even restart the PC using CTRL+ALT+DEL. I need to turn off the power.

---

### Post by hermes0710 on 2008-05-19
Since you don't get to the phase where you select the os i suggest booting the live cd and reinstall grub

---

### Post by rraj.be on 2008-05-19
Right now im too in the same problem but a step ahead of u

u can solve this by reinstalling GRUB...

To reinstall GRUB boot with live cd


-->open terminal..

--
>type sudo grub

-->find /boot/grub/stage1

-->if it returns like (hd0,1)

type root (hd0,1)

or respective HD number.

then type  setup (hd0)

then restart.


i am too running the same problem..

just see my thread below named ubuntu dosnt boot

---

### Post by src2206 on 2008-05-19
Well the above method did not work.

Reasons:

1. I have Edubuntu installed, which does not work as Live CD, not to mention I could not boot with this CD. Its version 7.10. So I booted with 7.04 Ubuntu Live CD.

2. I have my GRUB installed on the Floppy. But the Command find GRUB stage1 is showing me the GRUB at (hd2,4). It is showing alright, no problem with the location as it is the location where the Edubuntu 7.10 is installed. **But how do I reinstall the GRUB on the Floppy? **"setup (fd0)" does not work.
:(

---

### Post by didac on 2008-05-19
Maybe you got bad sectors in your floppy. If you don't have a backup copy, try downloading an image and formatting another floppy. If you can boot from a CD drive, it's better to download an ISO image of grub for a CD. They last longer.

Check:

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by src2206 on 2008-05-19
Ok, I got myself Super Grub Disc Floppy Image and used it.

Now I get the following error:

[B]Can not mount the partition: Error 17

[/B]:(

---

### Post by rraj.be on 2008-05-19
> **src2206 said:**
> 

2. I have my GRUB installed on the Floppy. But the Command find GRUB stage1 is showing me the GRUB at (hd2,4). It is showing alright, no problem with the location as it is the location where the Edubuntu 7.10 is installed. **But how do I reinstall the GRUB on the Floppy? **"setup (fd0)" does not work.
:(

just try 

root (hd2,4)

setup (hd2)

it will work fine

---

### Post by src2206 on 2008-05-29
Hello

This is how I've solved the problem:

1. Boot in the Live CD mode using Ubuntu 7.04 installation/Live CD.

2. In terminal logged in as Root using sudo -i

3. Opened up menu.lst file in GEdit from terminal.

4. Edited the file from (hd1,4) to (hd2,4), wherever (hd1,4) was mwntioned.

5. Saved the new menu.lst

Done...I can boot in Linux Edubuntu 7.10 again, but I have to use Super GRUB Disc as the floppy in which original GRUB was, got corrupted.

Why this simple action solved my problem? my best guess: By installing a new SATA HDD, I made my BIOS to recognize the Linux containing PATA to be recognized as 3 rd disc earlier which was recognized as the 2nd HDD.

So this simple action corrected the boot partition information for Linux and the problem is resolved.

Hope that others will also be benefited.

:)

---

