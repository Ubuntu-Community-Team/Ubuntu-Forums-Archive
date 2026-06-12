---
title: "I'm a newbie to Ubuntu, please help!"
date: 2006-01-26
forum: Repositories &amp; Backports
---

### Post by dsokus on 2006-01-26
Hi,

After a few days of struggling with installing drivers on Fedora Core 4 I have switched to Ubuntu today and found out with great pleasure that it recognizes all my drivers, sound, touchpad, wireless net, that Fedora did not! :D 

However, for some reason I do not seem to be able to install any new packages on my system. First I tried to install AMSN from the website and nicely clicking on the links etc - but the Archive Manager shouted at me saying that it is not a supported file type. :( I got the same error message when I tried to install KDE in the same way. 

Then I decided to use the command line apt-get, but unfortunately it doesn't work either. AMSN failed because of a package dependancy called tcltls. Then I attempted to install that package and that failed too. I then tried with KDE but that too breaks down... Then I read about Automatix here and tried to install using the exact instructions that were here and that failed as well. :confused: 

I am thinking I may be doing something wrong since I am not used to Debian-derived versions. Please could someone help me by giving a detailed description of what I should do to install these packages on my system, or to find out what is wrong? [-o< 

Please note that I am not an expert at all, I am generally new to Linux and absolutely new to Ubuntu so please say stuff that even an Absolute Beginner (from which I am not far) would understand. In fact I considered posting in the Absolute Beginners place first but then I have actually used command line at least once in my life :p so I decided to try it here. 

Any help will be greatly appreciated... 

Thanks,
Zs.

---

### Post by Derek Djons on 2006-01-26
Based on your stories and missing the application "Synaptic Package Manager" I suggest you try installing your application using it. System -> Administration

If possible you should always use the Package Manager. All the software in it has been thorough tested and will be installed without you bashing your head over CLI errors. 

The problems about missing dependancies could be related to not using Synaptic. Some applications require additional files or libararies. The Package Manager takes care of this problem by automatically adding them.

---

### Post by dsokus on 2006-01-26
Ah, I found it, thanks!!!! :D Gonna try it right now and report how it works. :cool:

---

### Post by dsokus on 2006-01-26
Ahh I am running the new KDE now... WOW, soooo beautiful!!! :D :D :D

Thanks a lot. :D

---

