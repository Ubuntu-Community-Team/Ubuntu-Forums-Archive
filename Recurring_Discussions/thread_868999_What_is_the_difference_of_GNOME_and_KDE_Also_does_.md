---
title: "What is the difference of GNOME and KDE? Also does Xubuntu have any draw backs?"
date: 2008-07-24
forum: Recurring Discussions
---

### Post by S3loth on 2008-07-24
I don't really see a big difference in GNOME and KDE. They seem the same to me. They have the same apps and everything. Also, while reading about Xubuntu, I couldn't find any setbacks with it. Everything I read about it said it went faster, but nothing about the negative points of it.

---

### Post by ChumleyEX on 2008-07-24
search and google are your friends. 

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)


[http://www.google.com/search?hl=en&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=difference+between+gnome+kde+ubuntu&spell=1](http://www.google.com/search?hl=en&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=difference+between+gnome+kde+ubuntu&spell=1)

---

### Post by jimi_hendrix on 2008-07-24
[http://linuxowns.wordpress.com/screenshots/]("http://linuxowns.wordpress.com/screenshots/")

theres ur answer

i believe (i may be wrong) that the difference is simply cosmetic

---

### Post by marshall.robert on 2008-07-24
there is more than appearance involved, there is functionality and resource differences involved, especially since xfce uses half the RAM that either KDE or gnome.

i would recommend trying them, if space is not a real issue then you can install them by putting in
```
sudo apt-get install kde4 xfce4
```
and wait till its done then log out and at the login screen select options and then session and select what you want to try.
i estimate downloading it will be about 242MB (kde being over 200MB) and hard drive space used 585MB (KDE being over 500MB)

---

### Post by jimi_hendrix on 2008-07-24
> **marshall.robert said:**
> there is more than appearance involved, there is functionality and resource differences involved, especially since xfce uses half the RAM that either KDE or gnome.

i would recommend trying them, if space is not a real issue then you can install them by putting in
```
sudo apt-get install kde4 xfce4
```
and wait till its done then log out and at the login screen select options and then session and select what you want to try.
i estimate downloading it will be about 242MB (kde being over 200MB) and hard drive space used 585MB (KDE being over 500MB)

wait

so if i wanted to without downloading and intalling it i could run xubuntu simply by installing xfce and picking it when i log in?

---

### Post by CEB2nd on 2008-07-24
This site is worth a look.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by snowpine on 2008-07-24
> **jimi_hendrix said:**
> wait

so if i wanted to without downloading and intalling it i could run xubuntu simply by installing xfce and picking it when i log in?

'sudo apt-get install xfce4' will give you the basic xfce windows manager. 'sudo apt-get install xubuntu-desktop' will give you the whole xubuntu experience (and it is a larger package). Yes, it really is that simple. :)

Xubuntu contains fewer applications by default than Ubuntu or Kubuntu. However, you can manually install any application that you feel it's missing. :)

---

### Post by jimi_hendrix on 2008-07-24
and then if i wanted to switch back to my good old gnome ubuntu i could without file loss?

---

### Post by marshall.robert on 2008-07-24
yeah, basically...

i do the same sort of thing, since i like variation and to try new things

you will notice a few other things in your menus and stuff, such as abiword and mousepad if you install xubuntu-desktop, but it set everything up for you rather than manually having to sort out the layout of things such as panels with plain xfce4

---

### Post by jimi_hendrix on 2008-07-24
and how would i switch in between desktops

then im done hijacking this post

---

### Post by snowpine on 2008-07-24
> **jimi_hendrix said:**
> and then if i wanted to switch back to my good old gnome ubuntu i could without file loss?

You can switch between Xfce or Gnome every time you use the computer by selecting Sessions at the login screen. It's that easy.

Actually, if you are going to do that, I have heard (no direct experience) it is better to use 'sudo aptitude install xubuntu-desktop' rather than apt-get, because if you change your mind and want to remove xubuntu later, 'sudo aptitude remove xubuntu-desktop' does a better job cleaning things up.

---

### Post by marshall.robert on 2008-07-24
you would select your session by clicking Options or Session at the login screen depending on your current login theme

Also: a couple of side notes, XFCE is like Gnome, as in it uses GTK, KDE is completely different from gnome, and installing a new desktop environment does take a little while, its mainly the downloading that takes a while.

---

### Post by jimi_hendrix on 2008-07-24
hi all

im posting this from the xubuntu livecd

other then a few different icons i cant see the difference from ubuntu

---

### Post by cardinals_fan on 2008-07-24
> **jimi_hendrix said:**
> hi all

im posting this from the xubuntu livecd

other then a few different icons i cant see the difference from ubuntu
It's lighter and more configurable.  Welcome to Xfce :)

---

### Post by marshall.robert on 2008-07-24
there isnt much of a visual difference since both gnome and xfce use the same theming engine (GTK) if you are really after a visual difference, go for KDE

so basically xfce is just like gnome but it uses less resources...

---

### Post by cardinals_fan on 2008-07-24
> **marshall.robert said:**
> 
so basically xfce is just like gnome but it uses less resources...
...and is more modular and customizable :)

---

### Post by marshall.robert on 2008-07-24
im guessing that the modular and less resources go hand in hand... only loading what it needs etc....

---

### Post by cardinals_fan on 2008-07-24
> **marshall.robert said:**
> im guessing that the modular and less resources go hand in hand... only loading what it needs etc....
Sort of.  Because Xfce is modular, the user can customize and choose which components they want.  I use a minimal Xfce with no panels and no desktop.

---

### Post by LaRoza on 2008-07-24
> **cardinals_fan said:**
>  I use a minimal Xfce with no panels and no desktop.

Amazing! It levitates your computer?

---

### Post by cardinals_fan on 2008-07-24
> **LaRoza said:**
> Amazing! It levitates your computer?
Kind of funny that you mention that.  My keyboard tray collapsed on Monday, and I spent a while typing from the floor looking up.  On Tuesday I put my budding engineering skills to work and got the wretched thing back on pretty good.

---

### Post by jimi_hendrix on 2008-07-25
define modular in context withe xfce

---

### Post by cardinals_fan on 2008-07-25
> **jimi_hendrix said:**
> define modular in context withe xfce
I don't use panels, and I prefer to manage my wallpaper with xsri.  So, I just disable xfdesktop and xfce4-panel.  These apps aren't tied into Xfce.  You pick and choose which components you want to create the environment that's best for you.

---

### Post by michlt on 2008-07-28
> **jimi_hendrix said:**
> and how would i switch in between desktops

then im done hijacking this post
Jimi_H  -- I'm a relative newbie but I've been test driving Gnome, KDE, Xfce4, Fluxbox.
All are 'window managers' not 'desktops'. Gnome and KDE are the most highly developed, loaded, polished, etc. Xfce4 might become my favorite though because it is light-weight AND compatible with elements from both Gnome & KDE. Fluxbox is strictly barebones and may be frustrating. The more I play with it the more I like it though. Just remember that with Xfce4 & Fluxbox the right mouse click is your quick access to your applications before you create your own launchers for convenience's sake. Switching between them has to be done by logging out then selecting a different 'session' before entering user & password from your login screen.

---

### Post by RiceMonster on 2008-07-28
> **michlt said:**
> Jimi_H  -- I'm a relative newbie but I've been test driving Gnome, KDE, Xfce4, Fluxbox.
All are 'window managers' not 'desktops'. Gnome and KDE are the most highly developed, loaded, polished, etc.

Actually, Fluxbox is the only one in that list that's a Window Manager. Gnome, KDE and Xfce are desktop environments. That's why they seem "the most highly developed, loaded, polished, etc."  and Fluxbox seems so bare-bones. Fluxbox can be used inside Gnome, KDE or Xfce because it's just a window manager, so you'd be replacing the window manager for the desktop environment you're using, aka. Metacity (GNOME), Kwin (KDE), and Xfwm4 (Xfce4). A desktop environment is a Window Manager coupled with a number of other tools such as a file browser, panels, etc.

---

