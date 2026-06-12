---
title: "Help needed for re-installing kubuntu (KDE4--&gt;KDE3)"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by xJippu on 2008-07-12
Hey guys!

In a nutshell:
-Kubuntu KDE4 doesn't work properly - been told that KDE3 would work better
-Can't install KDE3 from Live CD

I have a problem. I installed Kubuntu Hardy Heron KDE4 to my old laptop (Compaq presario 2100) about two weeks ago. I've had problems with it ever since; my DVD-rom can't be mounted and my internet connection got cut off randomly and never recovered. I've tried numerous ways to get the internet back with no success. A more linux-aware friend told me the KDE3 might work better than the KDE4 I have installed now. So I loaded [THIS]("http://www.kubuntu.org/getkubuntu/download") (the top selection, not the KDE4 remix - hope that's the KDE3 version of kubuntu?), made an image and thought I'd simply re-install it as I did for the current version.

So I booted from CD and the familiar install kubuntu menu appeared, but as I chose any of the functions in that menu (for example "test the disc for errors" or "install kubuntu") nothing happened and the computer froze.

I then opened the KDE4 and looked the CD up in Dolphin (strangely this CD works but any of the others I've tried don't...) And could see the contents of the Live CD. I can't find a file there that would re-install kubuntu.

Do I need to format my system completely and try to boot from the just created Live-CD or what. I have nothing important in the computer so a complete formatting would be in place.

Thanks for any input.

---

### Post by Gannon8 on 2008-07-12
I believe APTonCD would work, but I have not tried it.
```
sudo apt-get install aptoncd
```Or look for it in your package manager.

Then you should install KDE3 from the cd.

BTW, don't do
```
sudo apt-get install kubuntu-desktop
```
The konqueror browser has a problem installing, and it will ruin your dependencies.

---

### Post by xJippu on 2008-07-12
Is there a place to install the program via USB-memory or something, my Kubuntu computer can't get to internet so installing it via apt-get is impossible.

EDIT: sorry, got it downloaded

---

### Post by xJippu on 2008-07-12
okay, so I installed aptoncd but it just doesn't wan't to open.

Can I do something like in windows format c:, just to get a clean start and then boot from cd using the LiveCD. I have no idea why the computer freezes everytime I try to boot from the cd.. Would this problem appear even if I formatted the whole drive?

---

### Post by xJippu on 2008-07-17
Sorry for the bump, tried getting APTonCD to work for days now and I'm running out of ideas.

How can I format my whole HD in kubuntu? 

I'll try that and then try to install the KDE3 from the cd. And if that fails, I'll install windows and try again.

---

### Post by xJippu on 2008-07-22
Got this one solved.

I had all sorts of problems with the Hardy heron, mostly because of my lack of linux skills.

Then I tried to install Gutsy from a LiveCD which I burned on a computer with a bad DVD-burner.

Now I have a functional live CD and a functional Gutsy in the old laptop. Hope to master the art of linux one day :)

---

### Post by rng on 2011-06-17
Anyone searching on this subject may check this link: 

[http://www.trinitydesktop.org/](http://www.trinitydesktop.org/)

---

