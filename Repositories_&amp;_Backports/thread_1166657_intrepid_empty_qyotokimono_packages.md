---
title: "intrepid empty qyoto/kimono packages?"
date: 2009-05-22
forum: Repositories &amp; Backports
---

### Post by p_o_x on 2009-05-22
i've been trying to use libkimono4.1-cil (the kimono c# binding package) and libqyoto4.4-cil (the qyoto c# binding package) along with mono and monodevelop to create kde applications.  But when i install these packages i don't get the qt-dotnet.dll and kde-dotnet.dll files that *should* (or at least that is my understanding) come with the packages.  I've looked at packages.ubuntu.com under intrepid backports.  is this the way it is supposed to be?  libqyoto4.3-cil *does* have qt-dotnet.dll which i need, kimono depends on 4.4.  any thoughts on what i should do?  the jaunty packages do have the files, but i can't upgrade to jaunty because it locks up my computer every 10 minutes.

I'm using kubuntu 8.10

---

### Post by directhex on 2009-05-22
There's no Kimono in Intrepid - that's why you're having versioning issues.

The (Debian) KDE team didn't get in contact to improve the .NET packaging until the Jaunty cycle, so it's simply weak in Intrepid - and there's not a lot you can do about it

---

### Post by p_o_x on 2009-05-22
hmm.  well that sucks, but at least nothing is broken.  thanks.

---

