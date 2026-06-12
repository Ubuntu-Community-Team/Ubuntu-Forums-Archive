---
title: "Trying to install on an old computer?"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2011-11-26
Im trying to install Ubuntu(Xubuntu 10.04) in my old computer its a Pentium 4. At first I had a problem were it said "No Default or UI configuration". So I formatted the USB to FAT instead of FAT32. And it worked (I am using unetbootin). But now when the screen were I should choose Default, Help, Try Xbuntu without.... etc comes and I select an option the screen blinks and justs sits like that(hangs). What should I do?

---

### Post by BC59 on 2011-11-26
Xubuntu has a requirement of at least 256MB RAM but strongly recommends 500MB.....or more.

---

### Post by BC59 on 2011-11-26
Here you can find some ideas on how you could do it.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by arochester on 2011-11-26
1) How much RAM have you got?
2) Did you verify the ISO to make sure that it is good? (See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) ---OK it's about CDs, but it includes verification.)
3) There are two install disks. The Desktop is a LiveCD and uses a lot of RAM to install. The Alternate is a straight install and uses only 64Mb to install. If possible use the Alternate.
4) What are the basic specs of your computer? I run a P3 but it has funny video...

---

### Post by mastablasta on 2011-11-26
> **cyb3r_sn4k3 said:**
> Im trying to install Ubuntu(Xubuntu 10.04) in my old computer its a Pentium 4. At first I had a problem were it said "No Default or UI configuration". So I formatted the USB to FAT instead of FAT32. And it worked (I am using unetbootin). But now when the screen were I should choose Default, Help, Try Xbuntu without.... etc comes and I select an option the screen blinks and justs sits like that(hangs). What should I do?


it could be that it's loading to RAM but very slow. try hitting esc to see if there are any messages on screen. 

it could also be the video. might be that you will need to use alternate CD. lso as mentioned you need at least 256 MB RAM for the Xubuntu to be of any use to you.

---

### Post by cyb3r_sn4k3 on 2011-11-26
> **BC59 said:**
> Xubuntu has a requirement of at least 256MB RAM but strongly recommends 500MB.....or more.

It has 1GB of RAM.

---

### Post by cyb3r_sn4k3 on 2011-11-26
The specs are
Pentium 4
1 GB  RAM
128MB internal grfx
250GB HDD

---

### Post by alecdebian on 2011-11-26
some video hardware got problem in installation. just tweak it out in the bios and change the internal graphics to default memory size. may i know what brand of board do you have.?

---

### Post by cyb3r_sn4k3 on 2011-11-26
> **alecdebian said:**
> some video hardware got problem in installation. just tweak it out in the bios and change the internal graphics to default memory size. may i know what brand of board do you have.?

Its a asrock p4i45gv.

---

### Post by cyb3r_sn4k3 on 2011-11-27
Bump!

---

### Post by BC59 on 2011-11-27
Well the only coming to my mind is that sometimes the installation through USB gives errors. So try to recreate the USB or burn the .iso in a CD.

I don't know if someone has a better idea.

---

### Post by 2F4U on 2011-11-27
What kind of graphics card is that (brand and model)? Without knowing any details about the card, you could try to add nomodeset as kernel parameter in the grub boot menu.

---

