---
title: "GNOME login session doesn't show up after installing"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by User_ on 2012-01-07
I am trying to install Gnome Shell as a seperate login session in Ubuntu 11.10. I have tried installing it through the Ubuntu Software Center and also through the terminal by using the command "sudo apt-get install gnome-shell". Although the installation is completed successfully each time it still doesn't show up as a login session at the login screen. 

One thing worth mentioning is that I also installed MATE a few days ago in order to test it out. To my surprise, when I logged out and went to select MATE in the Ubuntu login screen, I saw that the GNOME and GNOME-Classic (fallback) sessions were there as well. Since I didn't like MATE that much, I removed it manually through terminal and also since I didn't have any use for the GNOME and GNOME-Classic sessions I removed them as well. Note that I only removed the sessions and not the files/packages of each one.

I tried removing and re-installing the Gnome Shell package again today to see if that would do the trick but it still won't show up as a seperate session. Any help would be much appreciated!

---

### Post by BlinkinCat on 2012-01-07
What you deleted, "gnome" IS "gnome shell" as far as I know.

Sorry I can't be of assistance re fixing your problem - :(

---

### Post by User_ on 2012-01-07
It was the session (the text if you want) that I removed in the login screen not the actual shell itself. I just need to find a way to make it to show up again in lightdm.

---

### Post by Frogs Hair on 2012-01-07
Make sure Advanced Settings is installed , I reinstalled this once and lost my Gnome sessions while it was absent . Try the command also . ```
sudo apt-get install gnome-session-fallback
```

---

### Post by User_ on 2012-01-07
> **Frogs Hair said:**
> Make sure Advanced Settings is installed , I reinstalled this once and lost my Gnome sessions while it was absent . Try the command also . ```
sudo apt-get install gnome-session-fallback
```


I tried that but it didn't work... What I just did was to install the "gnome" package which also automatically installed the "gnome-shell" one. I proceeded to log out and I got a message saying that "Some software updates will not apply until the computer is restarted" or something among these lines. So I restarted my computer instead of logging out. What I noticed is that now there are two new login sessions, one named "Recovery Console" and the other "User Defined Session". And still no Gnome session.

p.s: After restarting, I was greeted by a debian background on the grub menu which means that  it obviously installed the "desktop-base" package, that I uninstalled (after unchecking the GNOME desktop add-on in the Ubuntu Software Center) and noticed that it prompted me to remove a "gnome-core" package (which  may explain why theres no GNOME session in lightdm).

---

### Post by BlinkinCat on 2012-01-11
It is now four days since your last post - have you got any further in your efforts to rectify the situation?
By my bumping this thread, an answer may be forthcoming - If not I suggest that you may try "ask ubuntu" for the possible solution - I have received help there in the past.

[http://askubuntu.com/](http://askubuntu.com/)

Good luck - :)

---

