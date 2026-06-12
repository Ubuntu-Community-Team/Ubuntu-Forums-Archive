---
title: "How to remove compiz and restore Xubuntu?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by ferral-cat on 2008-11-02
Hi,  

I have screwed up my Xubuntu real bad and have followed many different posts to get my window manager back to xfwm4 but I cannot.  

I cant drag windows anymore and even terminal wont let me type into it anymore.  

I removed every single compiz package and also ran these commands:

```
sudo dpkg-reconfigure -phigh xserver-xorg

xfwm4 --replace &

xfwm4 --replace


```

i also tried to reinstall the package: xubuntu-desktop

Is there anything else I can do before i just backup my /home directory and reinstall?  I am so PISSED about this.  I wish someone had warned me there was no going back and I would never have even tried Compiz.

Im unhappy because I have searched for over an hour on how to fix this and have tried so many things and I hate to ask questions but it would be great if someone could write up a "How to revert back to original Xubuntu after removing Compiz" tutorial.

---

### Post by diablo75 on 2008-11-02
Click on the options button in the lower left corner of your login screen and change your session to xfce before logging in.  If you have your system setup to auto-login to your account, log out by hitting CTRL-ALT-BACKSPACE, then log back in with xfce selected and tell it to save your session preferences too.

---

### Post by ferral-cat on 2008-11-02
I did not have the opportunity to do what you suggested. 

I had rebooted into Windows XP and then when I restarted my PC to boot into Xubuntu I ran into a big problem.  

I see all the verbose lines scrolling by like normal and no errors but then the screen turns black and i can see the hourglass but it is not animated.  I can move the hourglass around but the screen is pitch black and the hourglass animation is frozen.  

I then rebooted and tried Xubuntu recovery mode and I choose "Fix X server" after the teask completed i rebooted back into normal Xubuntu.  

but the problem persists.  I cannot get to the login splash screen at all now.  It looks like a reinstall is inevitable now.  I should send a thank you card to the developers of Compiz Fusion along with a bouquet of roses.

---

### Post by ferral-cat on 2008-11-02
But what frustrates me to no end is that still i do not see a tutorial on the proper way to remove compiz fusion and revert back to standard Xubuntu.  

Has any human being alive ever successfully accomplished this task?  

There are tutorials galore on how to install it but what about how to remove it properly?  Compiz is a virus as far as i am concerned.

---

### Post by cardinals_fan on 2008-11-02
How about (as root):
```
aptitude purge compiz
aptitude clean
aptitude update
aptitude install xubuntu-desktop
reboot
```
What do you end up with?

---

### Post by diablo75 on 2008-11-02
If you want to uninstall compiz, restart the computer and go back into recovery mode.  Instead of selecting "Fix X Server", tell it to send you to a root prompt.  Once there, you should be able to type:

```
sudo apt-get –purge remove compiz* libcompizconfig*
```

---

### Post by ferral-cat on 2008-11-03
Thanks Guys,

I had never done the "purge compiz"  that was probably what i was  missing

Sadly i did not read your replies in time and ended up saving my /home and personal files and then i wiped the hdd and reinstalled ubuntu 8.10

Yes an upgrade from Xubuntu 8.04  so far so good and this time I will be careful not to add anything crazy.

---

