---
title: "KDE issue"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by bgast1 on 2008-05-25
I have Hardy Heron installed. Switched to KDE desktop. My computer will not shut down, and I cannot log out by ctrl -> Alt -> Backspace. 

Also, what is the command to issue if I want to install KDE 4.

---

### Post by .nedberg on 2008-05-25
Did you install keytouch?
There is a bug in it preventing Kubuntu from shuting down.
[https://bugs.launchpad.net/bugs/186713](https://bugs.launchpad.net/bugs/186713)

To install KDE4 issue:
```
sudo apt-get install kubuntu-kde4-desktop
```in a terminal

---

### Post by bgast1 on 2008-05-25
> Did you install keytouch?

I don't know I did 

```
sudo apt-get install kde-desktop
```

---

### Post by CPImmanuel on 2008-05-25
I have a somewhat more serious problem with KDE. I cannot get it to start. I have tried to install, remove (purge) and reinstall KDE, but no avail, Perhaps I messed up when I tried to install KDE4 and then tried to go back to KDE 3, I do y tt know. I have noticed that I cannot shutdown, even from my GNOME desktop if I ever try to run a KDE  application from there I have to use sudo shutdown -r now.  Any way to completely delete and purge KDE (both 3 and 4) and then reinstall either KDE 3 or KDE 4????
While I prefer the GNOME desktop, I do like some of the KDE apps...... 
Any suggestions?

Paul

---

### Post by CPImmanuel on 2008-05-25
I have also tried disabling the NIVIDA restricted drivers...just in case it was a problem with KDE and not with GNOME... That did not help either.....

Paul

---

### Post by bgast1 on 2008-05-25
Paul -- I am still pretty inexperienced with Linux, but I am getting there. My suggestion to you would be to start with a new installation and add the KDE applications that you want. I use Amarok, and prefer K3b for burning CD's as well. If you like the Gnome desktop then you can install what you want and have the best of both.

---

### Post by CPImmanuel on 2008-05-26
Thanks. I am reluctant to stsrt all over again, since I have everything working under GNOME now, including USB support, palm pilot support, a virtualbox with windowsxp for a couple of applications that i could not get to run under WINE etc. In addition, I have already activated the windows stuff...and I only have a couple of activations on those things.... And the last complete backup of the system that I did had the non-working KDE.....

So, I did the next best thing....I remove and purged ALL kde applications, kubuntu desktop, KDE 4 etc. and started over again  with kde. I did not have any success..Then I installed KDE4 late last night.... I have very very limited progress. I now can get the KDE4 desktop to come up.. However, I cam run only a handful of GNOME applications under KDE4.(abiword and a spreadsheet) That does not bother me, since what I really want is to run KDE applications under GNOME. The problem that I now have is i still cannot run ANY KDE applications---even from the KDE desktop. The one clue that I have is that when I am on the KDE desktop, I cannot connect to the web, and when I try to set up the network card, I get an error message about sudo not being set up...Does KDE need to be configured, or user access need to be configured in some way for KDE before the KDE applications run????
Any ideas?

Paul

---

### Post by CPImmanuel on 2008-05-26
I just found out something else..... Under GNOME, it appears that applications for KDE4 work, but not applications for KDE3...Does that make any sense? Is there a clue here? 

Paul

---

### Post by .nedberg on 2008-05-26
Try to remove all your KDE related settings:
```

rm -rf ~/.kde
rm -rf ~/.kde4

```
You might want to make a backup of those before you remove them...

---

### Post by CPImmanuel on 2008-05-26
Thank you soooo much!! :)
:)
It appears to have solved my problems.  I can now run KDE and GNOME programs under the GNOME desktop. I have not yet tried to bring up KDE3 or KDE4 yet, but I only have academic interest in that... I got what i wanted....

Paul

---

