---
title: "software install issue [TEAMVIEWER]"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by windowsfree on 2014-04-22
Hello,

I am attempting to install Teamviewer on Xubuntu 14.04.  I could not find it in the synaptic package manager or the Ubuntu software center.  I downloaded the 32 bit version from the website and attempted to install it with the software center and received the errors shown in the attached screenshots.  Please advise on how to install this package.

Thank you.

---

### Post by windowsfree on 2014-04-22
attachments failed on upload.

---

### Post by Christmas on 2014-04-22
Can you try opening a terminal and see if **cd ~/Downloads && sudo dpkg -i teamviewer_linux.deb** works, and if not, what is the output you get?

---

### Post by windowsfree on 2014-04-23
Sorry I haven't responded sooner.  I hope to have the opportunity to try this later today.  Thank you for your input and I will post results when attempted.

---

### Post by windowsfree on 2014-04-23
thanks, that w0rked!!!  why doesn't the other method work?

---

### Post by Vladlenin5000 on 2014-04-23
> **windowsfree said:**
> thanks, that w0rked!!!  why doesn't the other method work?

The issue you experienced is unrelated with the package you were trying to install. I had to reinstall it recently because after upgrading to 14.04 it refused to start - missing library error - and suggested reinstalling. I opened it - multiarch - directly from the browser and installed with software center.

I suggest you note what happens next time you try to install a deb file...

---

