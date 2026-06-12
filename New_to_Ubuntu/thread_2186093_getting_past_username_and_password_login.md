---
title: "getting past username and password login"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by bsbuttars on 2013-11-05
I am trying to upgrade the speed of a home built arcade purchased off of a classified a few years ago. I thought all I had to do is put the hard drive in to another machine but it looks like it doesn't like the video card. I can't install any drives because I can't log in. Which is why I need help. It is running Ubuntu 6.06. I don't know if there is a way for me to get past the log in or if could some how save the arcade files and upgrade the OS then put the arcade files back on. I would like some input on this either a work around or let me know if I am screwed and have to just use the old hardware.

---

### Post by DuckHook on 2013-11-05
Where there's a will, there's a way. And especially so if you have physical access to the box/HDD. That said, the caveat here is that my memory doesn't go as far back as 6.x anymore (6.04?!), so some of the tricks/techniques might not work--or at least, they may need substantial revision.

[Here]("http://www.psychocats.net/ubuntu/resetpassword") is a link to putting your box into root mode at the GRUB bootup. From there, it is not difficult to create a new user with sudo privilege, change passwords of existing users, etc, instructions in the link provided. As said, these procedures may look very different for something as old as you've got, so you may have to do some detective work and improvisation. 'fraid I won't be of much further help here. I barely remember 10.04 never mind 6.x!

Let us know how it goes.

---

### Post by Impavidus on 2013-11-05
Indeed 6.0**6** LTS, the only Ubuntu release that was delayed by two months. It was the first I installed. That same machine now runs Xubuntu 12.04. No surprise the kernel doesn't have the drivers for that new computer, assuming it's less than seven years old.

If you want to go on-line with your machine or don't want a lot of trouble manually installing drivers you can better install a recent Ubuntu. Assuming your arcade application works with it, which you can test from a live system. I wouldn't upgrade as it's a rather long route, especialy with the intermediate releases end-of-life too. I upgraded my computer from 6.06 to 12.04, but that was over the course of five years. If you want a new release you can better do a fresh install and move the files over.

---

### Post by DuckHook on 2013-11-06
> **Impavidus said:**
> Indeed 6.06 LTS, the only Ubuntu release that was delayed by two months. It was the first I installed.I dabbled with Ubuntu back then, but frankly, was only a tourist. Was still stuck trying to decipher Mandriva in my spare time, but was mainly confined to the jailware universe because of the tyranny of the working life.> I upgraded my computer from 6.06 to 12.04, but that was over the course of five years.Really?! Wow. And that long sequence of upgrades never choked at any point? That must constitute a record of some kind. My upgrade from 7.04 to 7.10 screwed up. Likewise to 8.04 and then to 8.10. After that, I resolved to always make pristine installs, lately even inheriting the /home directory and it's been just peachy. Hmm... maybe I'll roll the dice again with 14.04.

---

### Post by Impavidus on 2013-11-06
> **DuckHook said:**
> Really?! Wow. And that long sequence of upgrades never choked at any point? That must constitute a record of some kind. My upgrade from 7.04 to 7.10 screwed up. Likewise to 8.04 and then to 8.10. After that, I resolved to always make pristine installs, lately even inheriting the /home directory and it's been just peachy. Hmm... maybe I'll roll the dice again with 14.04.
Just LTS to LTS, so that's three upgrades. I only once lost my network connection, but that was relatively easy to solve.

---

### Post by Bucky Ball on 2013-11-06
If it has a disk drive, boot from a LiveCD, 'Try Ubuntu', save the arcade stuff somewhere safe, install. You don't need to login to 6.06 to do any of this.

This could all be done from a 12.04 LTS install CD or whatever release you are after (if you are after long-term support, LTS is the place to be).

---

