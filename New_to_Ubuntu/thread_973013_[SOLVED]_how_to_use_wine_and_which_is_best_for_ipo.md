---
title: "[SOLVED] how to use wine and which is best for ipod music transfer"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by jaswinder on 2008-11-06
i buddy, i am new in linux and just installed ubuntu 8.10, updates and some packages but i am unable to use wine....
please help me out..

and i am also have an ipod and want to load some more songs in it, so which package should i download and how to use it...

please help

---

### Post by jpoRS on 2008-11-06
Hey,

Have you installed wine?  Ubuntu doesn't come with wine automatically, you have to open a Terminal (Applications>Accessories>Terminal) and put in

```
sudo apt-get install wine
```

After that you should just be able to click on any .exe files and they should work, but no guarantees. 

As for iPod updating, I suggest the program Amarok.  It is a little different from iTunes but I think most people will agree that it is an excellent music player and very user friendly.  To get Amarok run

```
sudo apt-get install amarok
```

Then go to Applications>Sound and Video>Amarok.  It will run you through some basic start up questions, and then you should be ready to roll.

Both wine and Amarok are very popular, and if you have any issue with them, you should try the forum search function at the top of the page.  Chances are you aren't the first person with that problem, and you will get answers faster than waiting for other people to help you.

Good luck, and welcome to the community,
jim

---

### Post by roger_1960 on 2008-11-06
Hi

Read this for using wine

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Dont have an ipod, so cant help there.

---

### Post by SuperSonic4 on 2008-11-06
> **jpoRS said:**
> As for iPod updating, I suggest the program Amarok.  It is a little different from iTunes but I think most people will agree that it is an excellent music player and very user friendly.  To get Amarok run

```
sudo apt-get install amarok
```

Then go to Applications>Sound and Video>Amarok.  It will run you through some basic start up questions, and then you should be ready to roll.

Both wine and Amarok are very popular, and if you have any issue with them, you should try the forum search function at the top of the page.  Chances are you aren't the first person with that problem, and you will get answers faster than waiting for other people to help you.

Good luck, and welcome to the community,
jim

I agree, amarok is awesome although I prefer 1.4.10 to 2.0 beta. You might want to try rhythmbox if you want to avoid KDE dependencies though (although amarok is good and k3b is unparalleled for CD/DVD tasks). Some people here have found gtkpod to work for them but I've never tried it

```
sudo apt-get install gtkpod
```

---

