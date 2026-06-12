---
title: "So I wanted to download 12.10"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by gladgrind on 2012-12-31
I went to the download mirror and clicked on the 12.10 64 bit download choice; but it tried to get me to download 12.04.1.

What should I do?

---

### Post by Pjotr123 on 2012-12-31
Try this link:
[http://www.ubuntu.com/download/desktop/thank-you?distro=desktop&bits=64&release=latest](http://www.ubuntu.com/download/desktop/thank-you?distro=desktop&bits=64&release=latest)

---

### Post by sudodus on 2012-12-31
Maybe you have better luck with

[http://www.ubuntu.com/download/desktop/alternative-downloads]("http://www.ubuntu.com/download/desktop/alternative-downloads")

But dare I ask why it is so important to get 12.10? 12.04 LTS is a very good alternative except for a few cases, for example if you want dual boot with Windows 8 on a brand new computer.

---

### Post by BBQdave on 2012-12-31
> **gladgrind said:**
> ...but it tried to get me to download 12.04.1.

12.04.1 is a great distro :D

Ubuntu's site is working, attempted download of 12.10 - 64, no issues.

Give the download another go :)

---

### Post by Cheesemill on 2012-12-31
You can always download any of the current Ubuntu versions by going to [http://releases.ubuntu.com/](http://releases.ubuntu.com/).

---

### Post by gladgrind on 2013-01-01
> **sudodus said:**
> Maybe you have better luck with

[http://www.ubuntu.com/download/desktop/alternative-downloads]("http://www.ubuntu.com/download/desktop/alternative-downloads")

But dare I ask why it is so important to get 12.10? 12.04 LTS is a very good alternative except for a few cases, for example if you want dual boot with Windows 8 on a brand new computer.Thanks for your reply, and for the others. 12.10 has whole-disk encryption. If I can set it up using only 12 gigs or so of the hard drive, so that it is practical to back up using clonezilla, I would prefer having the extra privacy.

If I have to encrypt the entire 160gigs of the drive, it will be impractical to back up, and I will wait until ubuntu or some other debian-based distro gets it right.

pc-bsd, by the way, does allow whole-disk encryption, and only as much of the drive as you want.

---

### Post by Cheesemill on 2013-01-01
You can set up disk encryption with 12.04 as well, you just have to use the alternate CD to do the installation. Using the alternate CD will let you encrypt whatever size partition you want, which I don't think is possible with the 12.10 installer.

---

### Post by gladgrind on 2013-01-01
> **Cheesemill said:**
> You can set up disk encryption with 12.04 as well, you just have to use the alternate CD to do the installation. Using the alternate CD will let you encrypt whatever size partition you want, which I don't think is possible with the 12.10 installer.Thanks very much. The alternate cd worked for me and the entire drive is now encrypted.

It was not possible, at least for me, to change the size of the partition that was going to be encrypted, while using the semi-guided steps.

I had to click on 'manual', which did not give me a warm and fuzzy feeling. It took about 6 tries, going back and forth, before the system liked the partitioning setup.

It is now 12GB holding both / and /home in one partition. I didn't bother with a swap file which I have never needed.

The new system has been backed up using clonezilla - took about 8 minutes to do the 12GB - and when I am feeling more ambitious I will do a dummy install, and take notes on exactly what steps are needed to change the size of the encrypted partition from the default of the entire disk to whatever size you want, and post them here.

The rest of the install using the alternate cd was just as easy as installing with the regular cd.

---

### Post by Paddy Landau on 2013-01-01
For future note, you can install Ubuntu unencrypted, but have your home folder encrypted. (The home folder contains your data; the rest contains system files.) It is much easier that way. You do it from the normal installation disk.

If your question has been answered, please [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

