---
title: "Lubuntu boots into tty1"
date: 2021-05-28
forum: New to Ubuntu
---

### Post by Juanchi-09 on 2021-05-28
So I booted up an old laptop I had with Lubuntu. I had it with Lubuntu 16.04 and I think it broke when I updated it to 17.04 so I just left it there (it's a dual boot with Windows 7), but I thought I'd finally fix it.
I have two problems:
When I start it, Lubuntu boots into tty1 and, I think, read-only mode. I log in and do.
```
sudo mount -o rw,remount / 
```
This takes me to the graphical interface. Once there, it works correctly, but now there is a problem: even though I connect to my Wi-Fi network (and I know my network works so that's not the problem), and Lubuntu shows it as connected, it still won't connect to anything, so I can't update nor upgrade packages nor enter the web nor anything. The other problem is that once I shut it down and turn it on again, it will boot to tty again. I'd like to be able to have it boot normally into graphical interface and also to fix the network problem. Any help is appreciated, thank you.

---

### Post by ajgreeny on 2021-05-28
17.04 hasn't had any support for well over three years so updating will be a bit pointless, and as Lubuntu has not even recommended updating from 18.04 to 20.04 because of the complete change of DE from LXDE to LxQt, I think you will have to do a clean install of the Lubuntu (or other version) of your choice.

Download a new iso image file of the version you want on another computer, put it onto a USB flash drive and then boot to that live system to check everything works as you want, then install using the desktop icon that should show on the live desktop.

---

### Post by GhX6GZMB on 2021-05-28
And DON'T get the .ISO image from anywhere else than lubuntu.me this is the official site.

---

### Post by guiverc on 2021-05-28
Just an FYI:

Lubuntu 16.04 LTS had two upgrade paths that were fully QA-tested (by the Lubuntu team).

(1) to the next release; or 16.10
(2) to the next LTS release; ie. 18.04 LTS (*opened **after** 18.04.1 was released*)

(17.04 not being a LTS had only one upgraded path, to the next release or 17.10)

If you skipped a release (16.04 LTS to 17.04) you went outside of QA-testing on actual hardware, so increased the chance of issues, so I'd suggest in future upgrading using intended upgrade paths.

 Either way no release you mentioned is supported any longer, so I'll repeat what was already suggested; start again using modern Lubuntu using LXQt (20.04 LTS or 21.04 downloaded from an official Ubuntu/Lubuntu site; don't use *google* unless you can pick the correct site from what *google* offers).

Naturally backup any important files first using *live* media or your used system.
Question also asked at [https://askubuntu.com/questions/1341281/lubuntu-boots-into-tty1-and-when-mounted-networks-connects-but-does-not-work](https://askubuntu.com/questions/1341281/lubuntu-boots-into-tty1-and-when-mounted-networks-connects-but-does-not-work)

---

### Post by Juanchi-09 on 2021-05-28
Thank you all, will re-install the latest version, then!

---

