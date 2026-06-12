---
title: "problem in dual booting ubuntu with windows 8"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by aaashu on 2014-06-14
Hi, I am trying to dual boot ubuntu 14.04 with my windows 8. The laptop is sony vaio vpceg 25en. I have done everything that is required that is freeing up enough space approx 150 GB on my windows 8. Installation of ubuntu starts smoothly. But the problem arises at the step where the option comes whether i want to install alongside windows or erasing the whole disk and install ubuntu. Firstly, the option is not 'alongside windows' rather it asks inside windows. AS soon as i press enter it says remove the installation media and press enter. I have swept google but to no avail. Please help. I have previously dual booted this system and it was no problem. Please help. Thanks in advance

---

### Post by Bucky Ball on 2014-06-14
You are attempting to install Wubi by the sounds of it. Don't go there. Where did you download the ISO?

Ideally, you would download using a torrent file from down the page here:

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

12.04 LTS or 14.04 LTS, which ever suits. You can also get 14.04 LTS here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by oldfred on 2014-06-14
Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Sony's also usually have issues as Sony has modified UEFI to only boot Windows. Work arounds require moving and renaming a couple of files.

If an Ultrabook or dual video see sub sections in link in my signature. Also lots of good links including the two above.

---

### Post by hakuna_matata on 2014-06-15
> **aaashu said:**
> Firstly, the option is not 'alongside windows' rather it asks inside windows.
Same problem:  [http://askubuntu.com/questions/69481/why-dont-i-have-the-option-install-ubuntu-alongside-with-them/](http://askubuntu.com/questions/69481/why-dont-i-have-the-option-install-ubuntu-alongside-with-them/) 
IMHO best answer: [URL="http://askubuntu.com/a/272036"]http://askubuntu.com/a/272036
[/URL]

---

