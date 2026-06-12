---
title: "GTK#, monodevelop and Hardy Heron"
date: 2008-08-05
forum: Programming Talk
---

### Post by nter_user2 on 2008-08-05
Hello,

I've build a small app using GTK#. I've installed the standard Hardy Heron packages for GTK#, mono and monodevelop. The app also runs under that configuration but under any other config it doesn't. I've tried XP/MS CLI, Vista/MS CLI, Vista/Mono, Ubuntu Gutsy Gibbon.

The error messages of course vary when it comes to the format of the output. However it seems that the problem is, that Hardy Heron has a very strange GTK# version. 

Anyway here is the relevant part of the error msg on Gutsy Gibbon:
> ** (app.exe:6737): WARNING **: The following assembly referenced from /home/my_name/app.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/my_name/).


** (app.exe:6737): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

What is exactly causing this problem? Is there some way to solve this on Hardy Heron? I suppose I could always do the final build under Windows if it is really necessary.

I don't want to upload my app and I don't have access to my Hardy platform until end of the week to make a minimal demo. However as I'm using vanilla packages I don't think that this would be of any help.

---

### Post by nter_user2 on 2008-08-06
Does nobody have an idea?

---

### Post by Kadrus on 2008-08-06
There aren't lots of .NET programmers around here,a better way to get your problem solved is by asking at the Mono Project Forums

---

### Post by lakersforce on 2008-11-13
Excactly the same problem here. I'm using x64 version of Ubuntu.

---

### Post by directhex on 2008-11-13
Hardy comes with GTK# 2.12, and MonoDevelop will compile against it by default (libgtk2.0-cil package). Gutsy has 2.10, Windows has 2.10 or 2.8 depending on what you install

If you want to increase compatibility with other distros, especially older ones, then look in the MonoDevelop Addin-Manager, which should allow you to download older GTK# versions to compile apps against. You can change the target GTK# in the project options (remember to change it for every single project in a solution, and that you may need to change the setting twice the first time you use it)

---

