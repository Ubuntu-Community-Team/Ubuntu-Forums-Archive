---
title: "Counter strike for Ubuntu ????"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Urvish on 2008-09-13
How can I get counter strike 1.6 for Ubuntu 8.04 ???

---

### Post by acidsolution on 2008-09-13
Dont know if linux version is available 
but 
install wine and than use it from wine 
it must work with wine 
or else you would like to play this game Tremulous 
```
 sudo apt-get install tremulous

```

---

### Post by wineman on 2008-09-18
dude, tremulous is nothing like CS1.6/Source.

Acid, you are truely a newbie. Welcome to the club, we have jackets.

CS is capable on ubuntu, but only if you have mozill'a ActiveX control (google MOZCONTROL) and a lot of packages installed. 
In synaptic, search for html. Inside the results show be the following packages: (obviously install them)

xulrunner
gtkhtml (or something relative to that)
(all the other things that are lib--- and have HTML or Gecko in the description)

In xterm or gnome-terminal, go to the folder where you extracted mozcontrol. then register the following:
mozctrlx.dll
shdocvw.dll
..
(all the .dll and .ocx files)
i must go. I'll post a full CS/Source/War3 guide later

check u.

---

### Post by Pas_sa on 2008-09-18
Wow don't... scare the guy.

To the TC, head over to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and install Wine (they'll explain how to set it up on Ubuntu).

Once you've done that, go to here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554) and follow the guide to install Steam under Wine.

Once you've done all that.. log in as usual, and either download your CS 1.6 files through Steam normally or copy them over from your Windows partition if you know how. Once that's done, it should work without needing to tinker with more settings.

Good luck man.

---

### Post by Urvish on 2008-09-18
How can I register

mozctrlx.dll
shdocvw.dll
..
Is It needs code in terminal ???

---

### Post by Nepherte on 2008-09-18
You will have to download those dll files or get them from an existing windows installation. Then run
```
winecfg
```
there should be a tab where you can 'override' dll files. Add those two to the override list.

---

### Post by Mornedhel on 2008-09-18
> **wineman said:**
> Inside the results show be the following packages: (obviously install them)

xulrunner
gtkhtml (or something relative to that)
** (all the other things that are lib--- and have HTML or Gecko in the description)**


Oh just great. Have him install all HTML-related packages, yeah, right.

I want you to perform the search you described and take a closer look at everything that starts with libhtml. Oh HEY, it's Perl and Ruby modules ! Nothing to do at all whatsoever with Counter Strike or Wine or ActiveX controls ! Why, see for yourself : [http://packages.ubuntu.com/search?keywords=libhtml&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=libhtml&searchon=names&suite=hardy&section=all)

Seriously, next time you try to help, try what you recommend first.

---

### Post by LowSky on 2008-09-18
Wine is available from the repos, from add/remove or type the install yourself in a terminal
```
sudo apt-get install wine
```

follow these instructions for steam
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554&iTestingId=30896](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554&iTestingId=30896)

then follow these instructions for CS1.6
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507)

---

### Post by syms on 2008-09-18
> **wineman said:**
> dude, tremulous is nothing like CS1.6/Source.

Acid, you are truely a newbie. Welcome to the club, we have jackets.

CS is capable on ubuntu, but only if you have mozill'a ActiveX control (google MOZCONTROL) and a lot of packages installed. 
In synaptic, search for html. Inside the results show be the following packages: (obviously install them)

xulrunner
gtkhtml (or something relative to that)
(all the other things that are lib--- and have HTML or Gecko in the description)

In xterm or gnome-terminal, go to the folder where you extracted mozcontrol. then register the following:
mozctrlx.dll
shdocvw.dll
..
(all the .dll and .ocx files)
i must go. I'll post a full CS/Source/War3 guide later

check u.

i should say that you need to respect people more. be aware of these posts.

---

### Post by Perfect Storm on 2008-09-18
Please keep it civil people, thanks.


regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by eldragon on 2008-09-18
not CS, but quite similar in gameplay. and native on linux, based on quake3, called urban terror. give it a shot.

---

### Post by billgoldberg on 2008-09-18
> **eldragon said:**
> not CS, but quite similar in gameplay. and native on linux, based on quake3, called urban terror. give it a shot.

I am a CSS player myself and can tell you Urban Terror has nothing on CSS.
 
If you are used to counter strike, UT will suck.

---

### Post by wineman on 2008-09-19
i'm sorry for seeming to blast everyone, but i honestly didn't mean to:(. Installing wine alone isn't enough, you have to install some HTML and game supporting things too. that post from the wineDB was probably the best you can get.

---

### Post by Urvish on 2008-09-20
Thank U to all of U man........

---

### Post by acidsolution on 2008-09-20
> **wineman said:**
> dude, tremulous is nothing like CS1.6/Source.

Acid, you are truely a newbie. Welcome to the club, we have jackets.

CS is capable on ubuntu, but only if you have mozill'a ActiveX control (google MOZCONTROL) and a lot of packages installed. 
In synaptic, search for html. Inside the results show be the following packages: (obviously install them)

xulrunner
gtkhtml (or something relative to that)
(all the other things that are lib--- and have HTML or Gecko in the description)

In xterm or gnome-terminal, go to the folder where you extracted mozcontrol. then register the following:
mozctrlx.dll
shdocvw.dll
..
(all the .dll and .ocx files)
i must go. I'll post a full CS/Source/War3 guide later

check u.

Well Well wineman 
I guess you are very old to ubuntu but i m not the newbie ..
well that doesn't matter me 
and if you read mine post clearly than i have never written that tremelous is alternative to CS 1.6 . 
Dear I used to play CS lot b4 when i used windows . but i shifted to linux and was trying some linux games. since tremelous is shooter game and i have written that u can give a try not that its alternative to cs 1.6 ..
Better read the post clearly 

thanks 
acidsolution

---

