---
title: "Mobizen replacement"
date: 2021-04-15
forum: New to Ubuntu
---

### Post by nginmu on 2021-04-15
I used to use Mobizen with a USB lead to operate my smartphone from the Windows desktop. It worked well, back in 2016.

I now have a Lubuntu 20.04.2 LTS PC, and Mobizen seems to be dead.

My current phone is a Samsung Galaxy S10 (Android).

I'm wondering if anyone could recommend something I could use to connect to, screen mirror, transfer files & operate the phone from my Lubuntu PC.

I heard of KDE Connect but not sure if I could use it on Lubuntu?

---

### Post by guiverc on 2021-04-15
I have no experience using KDE Connect so I can't really comment, but I would expect it to operate on Lubuntu/LXQt.

A quick look at [https://packages.ubuntu.com/focal/kdeconnect](https://packages.ubuntu.com/focal/kdeconnect) shows it uses KDE Frameworks 5, so whilst LXQt uses the same Qt5 toolkit/library as KDE does, you'll need to have KF5 in memory just as you do with KDE so you'll be using more RAM than the LXQt desktop itself needs (*but few users worry about that anyway; it matters if you're on a resource limited box though*).

You can also see many blog sites that suggest it'll work too - [https://linuxreviews.org/KDE_Connect](https://linuxreviews.org/KDE_Connect)  (*search for LXQt and you'll see it's used specifically as example of it working on other desktop*s)
[I]
FYI:  The last daily for Lubuntu hirsute (20210414) included KDE Connect anyway I believe (as we had problems) .. but that'll hopefully be fixed in the new ISO being spun now (20210415)...[/I]

---

### Post by ActionParsnip on 2021-04-16
There's something in Chrome web browser too. I forget it's name. What are you using on your phone that needs the screen? You can transfer files to your phone using Bluetooth. Just tell the device to always accept files from your computer.

---

### Post by Irihapeti on 2021-04-16
I've had a play with [Scrcpy]("https://github.com/Genymobile/scrcpy"), which looks interesting for remote control. Apparently you can also use it for sending files, but I've not tried that.

---

### Post by nginmu on 2021-04-16
> What are you using on your phone that needs the screen?

My 50 year old eyes lol

It's mainly for convenience - I find the small screen and on screen keyboard on the phone a bit fiddly, and find it much much easier to operate when at home, by bringing it up on my desktop monitor and using my computers keyboard and mouse.

I do have a little USB-C hub type device which when plugged into the phone's USB-C port, prompts it to go into it's proprietary "Samsung DeX" ("Desktop Experience") mode but it's a little clunky and completely steals (via hand-plugged / hardwired HDMI cable) the 2nd monitor off the linux box.

With the Mobizen I used to be able to put my old Nokia in the window where it got a good signal, and then use all features remotely on the PC in the other corner of the room, where the phone itself never got a signal. And see everything clearly

---

