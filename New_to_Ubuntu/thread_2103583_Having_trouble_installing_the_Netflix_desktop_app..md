---
title: "Having trouble installing the Netflix desktop app."
date: 2013-01-10
forum: New to Ubuntu
---

### Post by poeticink626 on 2013-01-10
Hey guys, 
so, I did the terminal commands to install it. I get this error message. I've tried changing mirror servers, and tried main server. I also tried installing wine itself then trying the patch. No clue what to do further. Thanks so much for your time! 

ubuntu:~$ sudo apt-get install netflix-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 netflix-desktop : Depends: wine-compholio (>= 1.5.19~quantal1) but it is not installable
                   Depends: ttf-mscorefonts-installer but it is not going to be installed
                   Depends: mesa-utils but it is not installable
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to correct problems, you have held broken packages.
km13@ubuntu:~$

---

### Post by LuciferRex on 2013-01-10
have you tried running apt-get update as shown in the error?

```
sudo apt-get update
```

---

### Post by Dodeca on 2013-01-10
[http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/](http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/)

---

### Post by poeticink626 on 2013-01-10
Yes, I tried that after adding in the compholio ppa.

---

### Post by unheatedgarage on 2013-03-17
I'm having the same problem as the OP, and haven't been able to find any help on the web. Finally decided to come here and ask the same question.   poeticink626, were you ever able to get Netflix working?

---

### Post by Curtis6767 on 2013-03-17
> **unheatedgarage said:**
> I'm having the same problem as the OP, and haven't been able to find any help on the web. Finally decided to come here and ask the same question.   poeticink626, were you ever able to get Netflix working?


When you check your software sources, do you see the compholio PPA in there? 

Sometimes you have to install it twice. That happened to me. Try that.

---

### Post by rainbowtastical on 2013-03-22
Also in the same boat here. Uninstalled and reinstalled everything 3 times now. Super frustrated. Does anyone have an answer to this?

The desktop runs, goes to shows and whatnot, but when I try to actually play anything all I get is sound with the title-screen of whatever I'm trying to watch as the picture. I'm about to go try the suggestions in this thread, and seriously hoping that one of them works. I'm getting really tired of watching Netflix on my phone.

Edit: Still no luck. Tried the link posted above.

---

