---
title: "Updating SDL 1.2 to 2.0 on 12.04"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by Coffeetree on 2013-08-19
Hi, i wanted to compile Warzone 2100 3.1 and can an error after i did ./configure. The error was SDL  >= 1.2  pachage requirements were not met. Needless to say, i searched around and found that SDL 1.2 is linked with the video display and i did want to find a faliure in an upgrade to 2.0. I'm looking for a clean way for the upgrade from 1.2 to 2.0 SDL. My system is ubuntu 12.04  64 bit for my OS.

---

### Post by Coffeetree on 2013-08-21
I've been looking at differnt sources and found out you can safely remove the  early 1.2 version with the Ubuntu Software Center with the search SDL 1.2. From there, i have gone to  [http://www.libsdl.org](http://www.libsdl.org) to get the latest verson and after that the only way to download it is via the source code and complie it..((this is the page where I'm getting the install info [http://hobnobsandcheese.blogspot.com/2013/01/upgrading-from-sdl-12-to-sdl-20.html](http://hobnobsandcheese.blogspot.com/2013/01/upgrading-from-sdl-12-to-sdl-20.html))) When compiling i get the error like this  "WARNING: 'aclocal-1.13' is missing on your system" when i have already installed automake from apt-get.  So, this is where i'm at now if there is questions relating to how i've explaned things just let me know and i will clarify on that point.

---

