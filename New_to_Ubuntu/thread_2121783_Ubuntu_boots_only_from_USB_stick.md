---
title: "Ubuntu boots only from USB stick"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by vdhyani on 2013-03-03
Hi All,

Previously I had Windows 7 installed on my system and I was not really happy with it. so I decided to move to Ubuntu some time back.

I installed Ubuntu by creating the bootable USB stick.  Followed the steps as explained in following link for windows OS:-
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I was able to replace Windows7 successfully with Ubuntu 12.04.

The only problem, I am facing now is:-


[LIST]
[*]Now my lappy boots only from the USB stick from which I installed Ubuntu OS. 
[*]I even tried changing boot order, to boot it from internal hard drive, but that does not work. 
[*]I know that I am missing some very basic step here so that I don't need to plug in USB drive every time to boot my lappy, but I am not able to find out. 
[/LIST]

Please help me with it. I want to boot my laptop now without USB drive. Please suggest me the solution for it.

Thanks in advance..

Vikas Dhyani

---

### Post by carl4926 on 2013-03-03
Boot your installed ubuntu as you would using the usb

Now open a terminal and do

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

reboot without the USB

---

### Post by dvks on 2013-03-03
Is it possible that you never really installed Ubuntu on your local drive and just run it from the USB? The instructions link explain how to create the distribution USB but not how to create local installation. Once you have the Ubuntu USB stick ready and you boot from it you should get a selection table and you need to move the cursor to the 3rd line that says something about installing the ubuntu and follow with series of questions about the installation process, only after you are done with this process you actually have Ubuntu installed on your system otherwise you keep running it from the USB.

---

### Post by darkcrimson on 2013-03-03
Without the USB drive inserted, does the computer boot into Windows 7?

---

### Post by pierreyy on 2013-03-03
How exactly did you replace windows 7?

---

### Post by ahmad000012 on 2013-03-03
the simple way is that you delete partition and install fresh install of ubuntu

---

### Post by vdhyani on 2013-03-03
> **carl4926 said:**
> Boot your installed ubuntu as you would using the usb

Now open a terminal and do

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

reboot without the USB


Thanks a lot carl..!
This was really useful and worked like a Charm..!
Thanks again... O:)

---

### Post by carl4926 on 2013-03-03
> **vdhyani said:**
> Thanks a lot carl..!
This was really useful and worked like a Charm..!
Thanks again... O:)

You are most welcome

---

