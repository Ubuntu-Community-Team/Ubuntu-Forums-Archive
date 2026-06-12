---
title: "I love it, but need dial up help."
date: 2008-06-21
forum: New to Ubuntu
---

### Post by frogdude on 2008-06-21
Hello, I just recieved my free copy of the Ubuntu Hardy heron, and I am trying to learn to navigate through it, I am getting there, but I have a couple questions.

1.Love that this is the first OS to actually run as a virtual machine :)

2.  This is the main reason I came to the forums here.  I am trying to connect to the internet from Ubuntu, and I installed al the packages that came with the disc, as well, I have done a little reasearch n the subject, but I can;t find anything that helps me specifically.

I have the ISP dial up number, I need help getting the internet to work on my Ubuntu OS.  Right now I am on my Win XP AOL, but I need to start moving all my stuff over to Ubuntu.  If someone could please help with that, I would be greatly apreciative.

Also, I have a couple more questions.

I need a c++ compiler as I am starting my programming career.  But to do that, I need help trying to get programs installed onto my Ubuntu.

Is there a way to run .exe files?  Or a way to install from Windows program discs?  And how do I get my music player to run mp3's?  Doi I need a working connection on my Ubuntu OS to dowload the packages for it?

Thanks again, talk to you guys later.

---

### Post by adewale on 2008-06-21
For your c++ complier ubuntu comes preinstalled with gcc.  
For dialup open the terminal and type sudo wvdialconf and post the response here or better still follow this guide [www.ubuntunigeria.wordpress.com](www.ubuntunigeria.wordpress.com)             
To run .exe files you'd have to install wine

---

### Post by frogdude on 2008-06-21
1.I installed that g++ package, now how do  Iinitiate/start it.  I can't seem to find it anywhere.
2.How do I install wine?
3.I will get the response to you asap.

---

### Post by Sarah L on 2008-06-21
1. To compile C++ source code, go into the directory with the Makefile and type "make" (in a console). You might need extra packages for this - you can install basic compiler necessities by typing the following into a console: ```
 sudo apt-get install build-essential
```

2. To get wine, simply run this command in a console: ```
sudo apt-get install wine
```

Be aware that software installation using aptitude requires an active internet connection. If you haven't gotten your internet to work in Ubuntu yet, you can download the packages here: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Then move them to your Ubuntu partition and install them using ```
sudo dpkg -i *.deb
``` in the directory that you stored them in.

---

### Post by adewale on 2008-06-21
Its about 9:30pm my time here, i'd almost be going to bed now, i'd wait for maybe an hour more.

---

### Post by frogdude on 2008-06-29
Sorry, I've been a little busy lately., but I have the modem info ...on my linux, i still gotta transfer it over here, and get it to whoever, and I have been running a few little tests for stuff, and I have to download a few more things before I get moving, I'll get back soon, I hope.

---

