---
title: "What's the Easiest Way to Make .deb Packages?"
date: 2006-10-02
forum: Packaging and Compiling Programs
---

### Post by hk_2999 on 2006-10-02
I plan on porting some useful apps I found from GnomeFiles and searching the web. Can anyone tell me if there is an easier way to make .deb packages?

---

### Post by pay on 2006-10-02
Checkinstall is probably the most easiest but it isn't exactly the best for sharing on other systems.

---

### Post by hk_2999 on 2006-10-02
I plan on sharing the deb packages on a repository, or even consider uploading it to the main ubuntu packages site.

---

### Post by pay on 2006-10-02
Oh. I remember finding a very through free book somewhere that explains all that sort of stuff. I'll look.

Okay here it is [https://help.ubuntu.com/6.06/](https://help.ubuntu.com/6.06/)  click the package guide

---

### Post by H.E. Pennypacker on 2007-05-13
> **pay said:**
> Oh. I remember finding a very through free book somewhere that explains all that sort of stuff. I'll look.

Okay here it is [https://help.ubuntu.com/6.06/](https://help.ubuntu.com/6.06/)  click the package guide

That page only complicates matters.  So far, I have not a single straight process that requires a single window for creating a .deb file.  As the OP has said, I am trying to help out newbies who don't know how to compile software.

I've created a .deb file before, but the process is far too long and complicated.  You have to switch between several text documents, and do all sorts of stuff.  

Oh God, I wish there was a GUI.

---

### Post by Hendrixski on 2007-05-13
> **H.E. Pennypacker said:**
> 
Oh God, I wish there was a GUI.

I second that.  I did the "create from scratch" example on the Ubuntu Packaging Manual (which is way easier than the Debian New Maintainers guide) and I was exhausted.  I still haven't figured out how to user pbuilder for this stuff (even though, I'm getting good at working in a chroot) and I wish I just had someone explain it to me so that the manuals made more sense.  Like a class I could take.

---

### Post by WW on 2007-05-15
You could try using **epm**.  I gave a simple example in this thread: [http://ubuntuforums.org/showthread.php?t=406069](http://ubuntuforums.org/showthread.php?t=406069)

It doesn't have a GUI, and I don't know enough about .deb files to know if the .deb files created by epm conform to all the standards of an official debian or ubuntu package.  For the few simple packages that I have created, it seems to work fine.

---

