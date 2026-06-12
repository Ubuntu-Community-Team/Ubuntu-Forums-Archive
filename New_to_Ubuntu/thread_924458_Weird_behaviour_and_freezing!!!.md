---
title: "Weird behaviour and freezing!!!"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-09-19
First I thought it was a Ubuntu only related error, from a few days on, my computer mysteriously freezes, I might be working on a document or browsing internet or just got up for a cup of coffee and when I return, everything is frozen unresponsiveness and the caps lock light tilting. The times that has done this with me in front of the screen, sometimes can be seen something weird, as if there were some corrupted data (TV like) and then it freezes. 
I have Xubuntu installed on the same computer, so believing that maybe I broke something, used the Xubuntu installation, and it happened the same thing.
What is going on? Is it the OS or the computer? It's not the temp is at 60ºC and when it shuts down because of the heat, it shows a message. This is just freezes and the only button that works is the power button.:confused:
HELP

---

### Post by nowshining on 2008-09-19
it's prob. a kernel panic :/

have you done an fsck lately...

---

### Post by HellNoire on 2008-09-19
my desktop has been randomly freezing too, don't have a clue what's causing it

---

### Post by nowshining on 2008-09-19
now that i think about it? do u both use compiz?? turn that off and see if the freezing still continues...

---

### Post by arashiko28 on 2008-09-19
I do use compiz-fusion, about a month ago, it stopped running automatically at startup and have to run it by myself but, on Xubuntu, I don't have compiz-fusion and yet it did the same thing. Right now, I'm trying it, I'm on Ubuntu and didn't ran compiz-fusion, though this might take a while since it's not always, just sometimes and I have failed to find the trigger...

---

### Post by HellNoire on 2008-09-19
I never installed Compiz so if it's running by default, then yes. If not, no.

---

### Post by gjoellee on 2008-09-19
There are several solutions for this...here a few:

1. Some process might take a lot of CPU
2. If you have WINE, Cedega or Crossover or any other Windows emulator you might have got a "forkbomb" or "virus" etc....
3. There is a lot of dust in your computer
4. Lot of RAM is taken somehow
5. Might have been a bad update
6. You may have installed a package from a website that contains virus for Linux.

NOTE: No worries about getting viruses people! If you download packages from official and/or safe places you will not get viruses. Viruses in Linux must in most cases somehow by launched manually. However there is a little risk in getting viruses that takes a lot of CPU and other recourses if you are using a windows emulator.

---

### Post by FiremanEd on 2008-09-19
Also, read about the bug that had been reported. [https://bugs.launchpad.net/bugs/204996]("https://bugs.launchpad.net/bugs/204996")
I had that problem when I was running Ubuntu/XP dual boot.  I reformatted, nixed XP (really was not using it)  and did a clean Ubuntu only install on my Dell Dimension 4550.  Problem stopped.

---

### Post by arashiko28 on 2008-09-19
> **gjoellee said:**
> There are several solutions for this...here a few:

1. Some process might take a lot of CPU
2. If you have WINE, Cedega or Crossover or any other Windows emulator you might have got a "forkbomb" or "virus" etc....
3. There is a lot of dust in your computer
4. Lot of RAM is taken somehow
5. Might have been a bad update
6. You may have installed a package from a website that contains virus for Linux.

NOTE: No worries about getting viruses people! If you download packages from official and/or safe places you will not get viruses. Viruses in Linux must in most cases somehow by launched manually. However there is a little risk in getting viruses that takes a lot of CPU and other recourses if you are using a windows emulator.

1-Except when on web pages with a lot of flash images, doesn't happen.
2-Might be possible, but the antivirus shows nothing
3-Fresh cleaned not so long (it used to overheat)
4-I have system monitor, it's not the same on everytime, but memory was not taken to 100% nor CPU processes
5-It did the same thing in Xubuntu which I haven't updated since... 2-3 months ago
6-Could be possible too, have no idea of what, but it could be...

How do I work to find it? Also, I have compiz-fusion off, it seems to be more stable without it. :confused: after 5 months without a flaw since installation on 8.04, no upgrade, fresh install

---

### Post by arashiko28 on 2008-10-15
I have found a little realtion, though not so accurate since it still happens even when left alone with all programs closed. It has come to do it more often when scrolling up or down on a document, I work with large documents usually over 100 pages long, and when scrolling, tends to freeze, independently if on compiz fusion or not.

---

