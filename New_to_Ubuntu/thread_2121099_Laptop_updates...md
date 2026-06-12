---
title: "Laptop updates.."
date: 2013-02-28
forum: New to Ubuntu
---

### Post by testosteroar on 2013-02-28
Hi, obviously I am new to ubuntu and I am curious as to how I get drivers and updates from samsung for my laptop? I have a Samsung Np700g7c so2us gamer laptop. Any help is very appreciated.

---

### Post by Bashing-om on 2013-02-28
testosteroar; Hi ! Welcome to the forum.

Let me try and prase this properly and not be demeaning of Windows.
"ubuntu" is not Windows and downloading a driver from OEM is the verry verry last resort to obtain a driver. The ubuntu kernel provides "nearly" every driver required.
The process goes something like this:
The native open source driver 1st; If there are problems then go to
Proprietary drivers is 2nd ; available in the ubuntu software center available via "Additional Drivers" utility
cutting edge open source drivers are a 3rd option available from a Personal Package Archive
Then one might 4thly resort to the card manufacturer and down load and install a proprietary driver.

With the above said, what problems have you encountered with your present graphics driver,
How may we be of assistance ?[INDENT=2]
hope this helps - we are here to guide
[/INDENT]

---

### Post by testosteroar on 2013-02-28
Okay that makes a lot of since now haha, I posted another thread about this (sorry im new haha) but before I choose nvidia as my driver my screen would distort when I would start up or restart my laptop, now with driver installed the distortions seem to be gone but everytime I restart the screen stays a solid purple for some time then a nvidia logo pops up and goes away and a bad resolution of a ubuntu logo comes and and finally goes away and everything is back to normal and I can login.

---

### Post by UltimateCat on 2013-02-28
;)Hi

Welcome to the Ubuntu Forum!

To get updates for your system open the terminal (as a root user) and run:
```
apt-get update

```
And then run:
```
apt-get upgrade

```

Here's the page to help you learn more about your version of Ubuntu.

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://www.ubuntu.com/business/services](http://www.ubuntu.com/business/services)

Another good place is Ultimate Edition. They too provide support for Ubuntu -
[https://www.ultimateeditionoz.com/forum/](https://www.ultimateeditionoz.com/forum/)

Enjoy your distro!

---

### Post by testosteroar on 2013-03-01
Probably a stupid question but how do I use terminal as a root user

---

### Post by QIII on 2013-03-01
Use sudo, i.e.:

```
sudo apt-get update
```

You'll be asked for your password.  Just use your login password.  You won't see any keystrokes echoed on the screen.  That is normal.

sudo elevates your privileges temporarily.  You shouldn't log in as root.

---

### Post by testosteroar on 2013-03-01
Thank y'all for your help I got it all working now!

---

### Post by GrouchyGaijin on 2013-03-01
> **testosteroar said:**
> Probably a stupid question but how do I use terminal as a root user

Not at all a stupid question!  If you don't know, you don't know.  If you are new you may not even know where to look for the answer.
Ubuntu is Linux for people, not just uber-geeks.  People will not respond with Read the F****** Manual, in this forum.

---

### Post by jrz on 2013-10-12
I recently purchased a Samsung Series 7 Gamer, NP700G7C-T02TH, which came pre-loaded with Windows 8. I disabled UEFI in the BIOS, reformatted both hard drives and installed Linux Mint 15 with no problems, and find everything functions properly as it should.

---

