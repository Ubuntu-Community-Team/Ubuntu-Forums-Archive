---
title: "[SOLVED] What is a splash?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by LeetSpeak on 2008-08-15
Hey, I was on gnome-look.org and I saw something about splashes, someone care to tell me what those are?

---

### Post by Crafty Kisses on 2008-08-15
> **LeetSpeak said:**
> Hey, I was on gnome-look.org and I saw something about splashes, someone care to tell me what those are?

It's the splash screen for Ubuntu, when you first boot up, or it could be like a Compiz splash, when you are first in the GUI it will show the Compiz logo.

---

### Post by LeetSpeak on 2008-08-15
> **Codename said:**
> It's the splash screen for Ubuntu, when you first boot up, or it could be like a Compiz splash, when you are first in the GUI it will show the Compiz logo.

Oh, are you talking about were you login? or were Ubuntu is loading? Sorry new to this whole thing :confused:

---

### Post by iaculallad on 2008-08-15
A configured image that shows up on Ubuntu's startup stage (booting..). This usually hides the "text mode" initialization of your application and systems devices.

---

### Post by Rolcol on 2008-08-15
It's like when you open up openoffice.org.  That small window in the center with the loader bar is a splash screen.

---

### Post by Crafty Kisses on 2008-08-15
> **LeetSpeak said:**
> Oh, are you talking about were you login? or were Ubuntu is loading? Sorry new to this whole thing :confused:

When Ubuntu is loading, you can change the splash by going to System>Preferences>Appearance, or you can change it manually by doing the following:
```
cd /usr/share/pixmaps/splash
sudo mv path_to_your_splash.png ./mysplash.png
sudo rm ubuntu-splash.png       => (we're just deleting a link, not the png)
sudo ln -s mysplash.png ubuntu-splash.png
```
Just put whatever image you want in there and it should appear.

---

### Post by Ryadt on 2008-08-15
> **LeetSpeak said:**
> Oh, are you talking about were you login? or were Ubuntu is loading? Sorry new to this whole thing :confused:

Yes...where you input your username and passsword:)

---

### Post by Crafty Kisses on 2008-08-15
> **Ryadt said:**
> Yes...where you input your username and passsword:)

I thought that was GDM.

---

### Post by LeetSpeak on 2008-08-15
> **Codename said:**
> When Ubuntu is loading, you can change the splash by going to System>Preferences>Appearance, or you can change it manually by doing the following:
```
cd /usr/share/pixmaps/splash
sudo mv path_to_your_splash.png ./mysplash.png
sudo rm ubuntu-splash.png       => (we're just deleting a link, not the png)
sudo ln -s mysplash.png ubuntu-splash.png
```
Just put whatever image you want in there and it should appear.

Wow that looks confusing, care to help me out on how I could change it? Just got a black and red backround and I want everything to match hahaha :lolflag:

---

### Post by Crafty Kisses on 2008-08-15
> **LeetSpeak said:**
> Wow that looks confusing, care to help me out on how I could change it? Just got a black and red backround and I want everything to match hahaha :lolflag:

You technically need to first find your picture (splash screen), and then follow those instructions, and technically there is a easier way, you can go to System>Preferences>Appearance.

---

### Post by LeetSpeak on 2008-08-15
K. Sounds good, thanks everyone! I LOVE THESE FORUMS!:KS

---

### Post by Crafty Kisses on 2008-08-15
> **LeetSpeak said:**
> K. Sounds good, thanks everyone! I LOVE THESE FORUMS!:KS

No problem, remember if you have any other issues be sure to post back.

---

### Post by LiNuXxToOthEMaX on 2008-08-15
Yea, what the guy above me said lol.

---

### Post by ryo1127 on 2008-08-28
> **Codename said:**
> I thought that was GDM.

You are correct about GDM. Now, I was also confused about what was meant with splash screen, thanks a lot!

---

