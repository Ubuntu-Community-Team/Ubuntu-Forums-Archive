---
title: "Video Thumbnails won't load"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by ralphygarfield on 2008-05-27
I'm having a problem where I enter a folder with video files in it, and only a few of them load to show thumbnails. Other times, all of the thumbnails will load to show the contents, but it takes like five minutes or more for them all to load.

On Windows, they load super fast. I don't know what could be wrong. 

I also need to know how to cache the thumbnails so they are automatically loaded the next time I enter the folder. 

Can anyone help?

---

### Post by Paqman on 2008-05-27
They do get cached (take a look in ~/.thumbnails to see them)

IIRC the default settings for thumbnails in Nautilus excludes most remotely-hosted files and files under (over?) a certain size. I tend to set that to allow everything.

---

### Post by ralphygarfield on 2008-05-27
> **Paqman said:**
> They do get cached (take a look in ~/.thumbnails to see them)

IIRC the default settings for thumbnails in Nautilus excludes most remotely-hosted files and files under (over?) a certain size. I tend to set that to allow everything.


So that's just how Linux is then? 

It might keep taking them forever to load no matter what?

---

### Post by Paqman on 2008-05-27
> **ralphygarfield said:**
> 
It might keep taking them forever to load no matter what?

Depends why they're taking ages. Are they massive files? Do you have a slow processor? Either way, they should only need to be loaded once, after that they're cached.

---

### Post by ralphygarfield on 2008-05-27
> **Paqman said:**
> Depends why they're taking ages. Are they massive files? Do you have a slow processor? Either way, they should only need to be loaded once, after that they're cached.



I have a very average processor. And yes, some are big files, but on Windows they load fast.

Is it normal for Linux to load slower?

---

### Post by Paqman on 2008-05-27
> **ralphygarfield said:**
> 
Is it normal for Linux to load slower?

Only the first time they're viewed. After that they're cached. Where are the actual files located? Another partition? A network share?

---

