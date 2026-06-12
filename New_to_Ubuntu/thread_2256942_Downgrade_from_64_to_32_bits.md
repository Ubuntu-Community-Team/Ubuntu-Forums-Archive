---
title: "Downgrade from 64 to 32 bits"
date: 2014-12-15
forum: New to Ubuntu
---

### Post by guadaatenea on 2014-12-15
Hi everyone!

I've been using Ubuntu 14.04, 64 bits version, for a couple of months. I installed this version because it was what seemed to better support getting rid of a very annoying pre-installed Win8 (I tried with former versions of Ubuntu and always somehow got stuck somewhere on Win8 barriers), but I think I'll have to downgrade: even if I do have a 64 bit processor, I only have 2gb RAM, and I end up having time to go and make a cup of coffee every now and then while a gray screen goes back to normal.

The thing is, I have upgraded versions some other time (I'm posting this in "new to Ubuntu", but I'm actually a comeback, after a couple of years), but I never ever tried downgrading and I'm not sure what exactly should I do: just wipe the system and format the hard drive as if I were installing everything anew, or is there some less traumatic way?
Thanx!

---

### Post by Bucky Ball on 2014-12-15
> **guadaatenea said:**
> ... just wipe the system and format the hard drive as if I were installing everything anew ...

^^^
This. But I don't think downgrading to 32bit is going to make much difference to the issue you've outlined.

You'd be better served by posting a thread regarding the gray screen you mention (you give no detail why or when it happens) and trying to get to the bottom of that. Sounds like the real issue, not the 64bit OS.

My wife has a 64bit install with 2Gb RAM and no issue. Never seen the gray screen you mention. I'd think there is something causing it apart from the 64bit OS. :-k

PS: Welcome back. ;)

---

### Post by grahammechanical on 2014-12-15
My machine has only 1 GB of RAM. Ubuntu 14.10 64 bit works very well on it. This greying of the screen, does it happen to application windows or does it happen to the whole desktop?

When an application window greys out it is Ubuntu's way of telling us that the application is busy. I get it with LibreOffice when I have two large documents open and they are both doing a save action at the same time. I can still use other functions of the OS.

Regards.

---

### Post by oldfred on 2014-12-15
My laptop has 1.5GB of RAM and get the grey screen if I try to load too many or several large apps at once. My normal use on laptop of Firefox, Zim, and terminal work without issue, but if I load Thunderbird or Libreoffice  at same time then it starts using swap and gets real slow.
I also have a low power Intel interal video chip so even though running full Ubuntu I do not use Unity but fallback/gnome-panel which also then uses less resouces.

---

### Post by guadaatenea on 2014-12-22
Thanks everyone.
Well, this happens whenever I've got more than one application running and one of them needs to load (or load something: this goes even for trying to have browser and gedit or calculator running), or using more than two Chromium tabs. What goes gray? Everything. And nope, I can't use anything else, mouse pointer also freezes and keyboard commands won't work. It's just sit and wait.
I use to have one cloud service background (Copy or Dropbox, most of the time on standby). I mention it even though it doesn't improve much if I close them.
This is a small ASUS laptop, Celeron processor, I can't remember the video chip but it's probably the worst thing Intel still produced a year ago (when I bought this computer with a really low budget).

---

### Post by Bucky Ball on 2014-12-22
Only suggestion really is to try Lubuntu (or Xubuntu), perahps from the Live USB or DVD, and see if that gives you any joy.

---

### Post by mörgæs on 2014-12-23
It does indeed sound like the hardware is weak but let's take a look.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by oldrocker99 on 2014-12-23
> **Bucky Ball said:**
> Only suggestion really is to try Lubuntu (or Xubuntu), perahps from the Live USB or DVD, and see if that gives you any joy.

I might also mention Ubuntu MATE, which has a similarly lightweight interface, and a better file manager than Lubuntu or Xubuntu. It is, IMHO, the most full-featured of the lightweight window managers, and, besides, it has the interface we all loved before GNOME 3 and Unity.

---

