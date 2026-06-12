---
title: "Partion a drive for Linux already in NFTS?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-08-21
My XP OS has gone through significant adjustments and I'm too lazy to tank my drive and partition it to put on Ubuntu and have an XP or Ubuntu setting at boot. Is there a way to partition the HDD even though XP is on it or do I have to wipe the thing and start over? I realize there are some emulators, but that defeats my reason for having a second OS. If XP breaks and wont load, I obviously cant use an emulator.

---

### Post by niccholaspage on 2008-08-21
You can use WUBI.It installs a program to your computer which is actually Ubuntu and you can dual boot between Ubuntu And Windows Without the need to partition your system.You also don't need to burn Ubuntu to A CD.You can get WUBI Here:[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by meanburrito920 on 2008-08-21
I would suggest against WUBI unless you are only taking ubuntu for a test run. I say this because having ubuntu on a seperate partition has benefits, namely the fact that you can access your windows drives through it ( I dont believe you can do this in WUBI due to the nature of the beast). When you boot up the live cd and go to install, Ubuntu will allow you to turn free space on your drive into another partition, touching none of your old stuff. It is always a good Idea to back up your documents, but Ubuntu rarely, if ever, has problems with partitioning. If you feel ambitious, you can also define your own partition table, but you should make sure you know what you are doing before you do something like that.

---

### Post by niccholaspage on 2008-08-21
Good Point meanburrito920.There are some weird problems with Wubi.If you want to try it just download the Ubuntu ISO and you can burn it to a CD.

---

### Post by ugm6hr on 2008-08-21
> **Lateforgym said:**
> Is there a way to partition the HDD even though XP is on it or do I have to wipe the thing and start over?

Yes.

The Ubuntu Live (or Alternate) CD installer allows you to "dual-boot" by resizing Windows, and creating 2 new Ubuntu (/ and swap) partitions.

But defrag XP first, and make sure everything's backed up, since resizing partitions will always put your data at potential risk.

You can do things manually with GParted (on the LiveCD) and then choose Manual install if your prefer (as I do).

---

