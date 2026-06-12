---
title: "Virtualbox"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by Deniz343 on 2012-08-06
Does somebody help me to figure out how to install virtualbox to Ubuntu 12.04. I want to play windows games on virtualbox. 

PLEASE HELP

Best Regards

---

### Post by CharlesA on 2012-08-06
Virtualbox is not really that good with games.

Read this:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by mlentink on 2012-08-06
Virtualbox works by setting up a virtual computer on your system. A virtual computer with basic, generic hardware, like a harddisk, and a very generic videocard, without all of the sophisticated circuitry needed to play most modern games. I understand Virtualbox can do some basic 3D-accelaration, this will not be enough to run any of the modern graphics-intensive games.

You would be much bettter off with a dual-boot system. There's ample information on setting up such a system in these forums.

---

### Post by mastablasta on 2012-08-06
> **Deniz343 said:**
> Does somebody help me to figure out how to install virtualbox to Ubuntu 12.04. I want to play windows games on virtualbox. 

 
aside form what others already said... what widnows based games do you want to play? perhaps they work in Wine (or the GUI frontend Play on Linux)?

---

### Post by Deniz343 on 2012-08-06
Okey then what can I do for play windows games in Ubuntu. Except for wine.

---

### Post by Deniz343 on 2012-08-06
> **mastablasta said:**
> aside form what others already said... what widnows based games do you want to play? perhaps they work in Wine (or the GUI frontend Play on Linux)?

I want to play world of subways vol. 3, tropico 4, Cities XL 2012, Empire Earth 2

---

### Post by mlentink on 2012-08-06
You might try PlayOnLinux (I have no experience with it, am no gamer).

Please remember that Ubuntu, and linux in general, is a completely different operating system than Windows, just like OSX is different. Software designed for one OS does not ordinarily run on another. The Wine developers, and those of derivatives like CrossOver en perhaps PlayOnLinux, do exceptional jobs in making some software run on Linux, but that doesn't mean you should expect everything to run.

Take a look here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Deniz343 on 2012-08-06
> **mlentink said:**
> You would be much bettter off with a dual-boot system. There's ample information on setting up such a system in these forums. Can you post a link for it.

---

### Post by mlentink on 2012-08-06
A simple search on these forums (use the 'Search' function above) wit the words 'dual boot' will return e.g. this: [http://ubuntuforums.org/search.php?searchid=87260879](http://ubuntuforums.org/search.php?searchid=87260879)

Or you might look here: [http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu)

or google this: ubuntu dual boot how to

---

### Post by Deniz343 on 2012-08-06
> **mlentink said:**
> A simple search on these forums (use the 'Search' function above) wit the words 'dual boot' will return e.g. this: [http://ubuntuforums.org/search.php?searchid=87260879](http://ubuntuforums.org/search.php?searchid=87260879)

Or you might look here: [http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu)

or google this: ubuntu dual boot how to

Dual-boot is too complicated for me. Is there any other way to play windows games in Ubuntu. Except for wine, PlayOnLinux or dual-boot.

---

### Post by Cheesemill on 2012-08-06
You could take a look at Crossover but it's just a commercial version of Wine with support for slightly more programs.
[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)
 
Apart from that then there are no other options.
 
Basically if you want to run Windows games then you should use Windows.

---

### Post by Deniz343 on 2012-08-06
You right I did a little google search and i founded CrossOver Linux.

---

### Post by mlentink on 2012-08-06
Crossover Linux and PlayonLinux are both based on Wine. 
I read from your posts that:
1. You do not want to dual boot
2. Virtualbox is not an option
3. You do not want to use Wine

If you still want to play Windows games, the obvious conclusion is that you need to use a Windows computer.

---

### Post by uRock on 2012-08-06
Depending on your system's specs you may be able to play your games in a virtual machine. Do you have an install disk and key for Windows? If yes, then what version?

---

### Post by Deniz343 on 2012-08-06
> **mlentink said:**
> Crossover Linux and PlayonLinux are both based on Wine. 
I read from your posts that:
1. You do not want to dual boot
2. Virtualbox is not an option
3. You do not want to use Wine

If you still want to play Windows games, the obvious conclusion is that you need to use a Windows computer.

You are right but my other pc is not good as my Ubuntu pc. In this topic I learned two other application to run windows games; CrossOver Linux, PlayOnLinux. I did a little google search about PlayOnLinux and this program is not enough to run my games. But CrossOver Linux's Application Support is more greater than other programs (wine etc.)

---

### Post by Cheesemill on 2012-08-06
> **Deniz343 said:**
> You are right but my other pc is not good as my Ubuntu pc. In this topic I learned two other application to run windows games; CrossOver Linux, PlayOnLinux. I did a little google search about PlayOnLinux and this program is not enough to run my games. But CrossOver Linux's Application Support is more greater than other programs (wine etc.)
As mlentink said above, Playonlinux and Crossover ***are*** Wine.

Playonlinux is basically a set of helper scripts that make sure that your applications are using the version of Wine that is most compatible for that application.

Crossover is again just basically Wine but with a few tweaks to ensure greater compatibility. All of Crossover's tweaks make there way into the free version of Wine.

---

