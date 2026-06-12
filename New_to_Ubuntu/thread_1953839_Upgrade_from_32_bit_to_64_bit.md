---
title: "Upgrade from 32 bit to 64 bit"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by quarkhirad on 2012-04-07
I have a dell l502x laptop. However, i am using ubuntu 11.10 32 bit. 

1) Can i upgrade to 64 bit just like i upgraded from 11.04 to 11.10 or do i need a fresh install. 

2) If i do a fresh install then do i have to sit and reconfigure all my compiz settings or can i copy the settings.

3) If i do a fresh install then will the same packages that i downloaded for ubuntu 11.10 32 bit work on 64 bit or will i have seperately download the 64 bit version packages.

---

### Post by codemaniac on 2012-04-07
Have been discussed earlier .Please refer the thread .
[http://ubuntuforums.org/showthread.php?t=1764571](http://ubuntuforums.org/showthread.php?t=1764571)

---

### Post by d4m1r on 2012-04-07
Just to add to the topic, I have 8GB and I am still running 32 bit to avoid any issues....I hear 64 bit Ubuntu is much more compatible these days so I might spring to it when I upgrade to 12.04 LTS, but nothing I currently do under linux will ever use enough RAM to make any difference between 32 bit and 64 bit...

Only 2 things I can think of that do use a lot of RAM (gaming and video editing), I use Windows exclusively for which is 64 bit.

---

### Post by 3rdalbum on 2012-04-07
> **quarkhirad said:**
> I have a dell l502x laptop. However, i am using ubuntu 11.10 32 bit. 

1) Can i upgrade to 64 bit just like i upgraded from 11.04 to 11.10 or do i need a fresh install. 

2) If i do a fresh install then do i have to sit and reconfigure all my compiz settings or can i copy the settings.

3) If i do a fresh install then will the same packages that i downloaded for ubuntu 11.10 32 bit work on 64 bit or will i have seperately download the 64 bit version packages.

A fresh install is necessary, but here's a tip for you. Select the "Something Else" option in the installer, to bring up the partitioning screen. Tell the installer to use your existing partition as / (the root file system) but DO NOT click the box to tell it to format the partition.

Your files and settings will be retained, including your Compiz settings, all of which will work no different to when you were using 32-bit.

Your 32-bit packages will need replacing with 64-bit packages.

**Here's a better suggestion though.** Download Ubuntu 12.04 64-bit. Even the current beta will do. In the installer, tell it you want to do an "Upgrade" instead of a "Something Else". Your existing files and configuration will be saved as I mentioned before, your existing package list will be remembered and the installer will automatically re-download the packages, this time for 12.04 and 64-bit.

---

### Post by shuttleworthwannabe on 2012-04-07
> **3rdalbum said:**
> A fresh install is necessary, but here's a tip for you. Select the "Something Else" option in the installer, to bring up the partitioning screen. Tell the installer to use your existing partition as / (the root file system) but DO NOT click the box to tell it to format the partition.

Your files and settings will be retained, including your Compiz settings, all of which will work no different to when you were using 32-bit.

Your 32-bit packages will need replacing with 64-bit packages.

**Here's a better suggestion though.** Download Ubuntu 12.04 64-bit. Even the current beta will do. In the installer, tell it you want to do an "Upgrade" instead of a "Something Else". Your existing files and configuration will be saved as I mentioned before, your existing package list will be remembered and the installer will automatically re-download the packages, this time for 12.04 and 64-bit.

Marking this to remember for next time I am in this pickle.

---

### Post by rmil on 2012-04-07
@3rdalbum

great suggestion. Is it possible to do the same with servers versions also?

---

### Post by UnknownFearNG on 2012-04-07
> **3rdalbum said:**
> 
**Here's a better suggestion though.** Download Ubuntu 12.04 64-bit. Even the current beta will do. In the installer, tell it you want to do an "Upgrade" instead of a "Something Else". Your existing files and configuration will be saved as I mentioned before, your existing package list will be remembered and the installer will automatically re-download the packages, this time for 12.04 and 64-bit.

Definitely doing this when 12.04 gets released :)

---

