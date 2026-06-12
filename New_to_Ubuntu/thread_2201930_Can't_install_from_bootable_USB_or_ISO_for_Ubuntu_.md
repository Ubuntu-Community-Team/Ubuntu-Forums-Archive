---
title: "Can't install from bootable USB or ISO for Ubuntu Desktop."
date: 2014-01-26
forum: New to Ubuntu
---

### Post by ajborkowski1031 on 2014-01-26
[COLOR=#333333][FONT=UbuntuRegular]I'm not exactly new to installing an OS, and I've read that Linux based systems are super easy. But I cant figure out what it isn't working for me. I'm dirt poor and only have a flash-drive available to put the installation on as a boot-drive. I attempted mounting the ISO and run off of that - failed. I also attempted the boot from USB (in all the USB slots I have) after following all the steps to make a working bootable USB for Windows - failed. I'm just sick of Windows and would like to have a better OS suited for someone who's trying to become a good programmer/developer. I currently have Windows 7 Home Premium with one hard-drive partitioned into two drives. They both contain Windows files. 

What I'm getting at is, I want to kick Windows to the curb and begin using Ubuntu. Should I just wait 'till payday and buy a CD/DVD to try booting from?

I uploaded my log file onto DropBox because it was rather lengthy from several install attempts.
[https://www.dropbox.com/s/5ab9deaux4jns61/wubi-12.04.1-rev273.log](https://www.dropbox.com/s/5ab9deaux4jns61/wubi-12.04.1-rev273.log)

[/FONT][/COLOR]

---

### Post by DuckHook on 2014-01-26
Hello ajborkowski1031 and welcome to Linux and the forums.

I'm of very limited help here because I know very little about WUBI. What I do know is that it has been deprecated and is no longer supported as an install method. It isn't even available beyond 12.04, so you won't be able to upgrade, and it has always been a quirky temperamental methodology that the majority of forum members cannot help with because we don't use it.

You may wish to consider dual booting with Windows. There are a number of good guides available including [this]("https://help.ubuntu.com/community/DualBoot/Windows") one. The best tool to do the actual burning is *unetbootin*. Download for Windows along with instructions is [here]("http://unetbootin.sourceforge.net/").

Re: sick of Windows.

I would not recommend that you eliminate Windows yet. Even those of us who use Linux almost exclusively still keep Windows around for things that will only run on Windows (tax software, games, itunes, etc). If you choose the dual-boot option, please be sure to:

1. Backup all important data first.
2. Make Windows recovery/install disks.

Re: Linux based systems are super easy.

It is important to approach Linux with the proper expectations. Unrealistic expectations is the number one cause of failed transitions because they are impossible to fulfill. If using the above method, then run Ubuntu as a LiveUSB session from the USB stick first *without installing*, and see how you like it. Also, important to read [this]("http://linux.oneandoneis2.org/LNW.htm") and [this]("http://www.psychocats.net/ubuntu/index") as primers. The first link, "Linux is not Windows", is especially important as it sets proper expectations.

Let us know how it goes!

---

### Post by C.S.Cameron on 2014-01-26
As Duckhook says, UNetbootin is probably the easiest way to make a bootable Ubuntu USB if you don't have a CD drive.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

