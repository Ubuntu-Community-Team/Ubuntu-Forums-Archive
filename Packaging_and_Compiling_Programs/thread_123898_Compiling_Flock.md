---
title: "Compiling Flock"
date: 2006-01-31
forum: Packaging and Compiling Programs
---

### Post by [Nirvana] on 2006-01-31
I've been trying to compile flock for a while now, and always receive an error when it comes to building Mozilla. I have checked the mozilla build pre-req page, but it wasn't clear. I did what I could though. I downloaded their libIDL, and aliened it, I made sure I had all that gcc, pkgconfig, fontconfig, etc, and I get an error because (of what I believe is) the gtk files. Now, I am on Kubuntu, so I have to download all gtk dev files, which I don't know much about. I've tried this so far:
```

sudo apt-get install libgtk2.0-dev libgtk1.2-dev
-------------------
sudo apt-get build-dep mozilla-browser
-------------------
sudo apt-get build-dep firefox

```

And none of them eased the error. I only thought of using the apt-get build-dep  because I figured if I was building from source, it might be smart to get the build dependancies...

error I receive: [http://kubuntu.pastebin.com/532048](http://kubuntu.pastebin.com/532048)

---

### Post by [Nirvana] on 2006-02-02
**bump**

Anyone know anything?

---

### Post by lotu5 on 2006-07-03
Has anyone been able to do this? or is there a binary package for ppc anywhere? i really dig flock, but i couldn't get it to compile either. it also took up a ton of disk space ot try to get it to build, so i removed it because i needed the space.

---

