---
title: "Start-up-problem in Ubuntu. Can't get to the Sign-in-screen or the Desktop"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by MarkusIggy on 2008-06-10
Hi!
I am fairly new to the Linux-world, but I have managed to install Ubuntu 8.04 and Windows XP Pro on my computer, so I'm not completely idiot ... :P

I think I have a problem with my graphics card, but I am not sure if it is the graphics card, or something else, so I would like to ask her if there is someone who can help me.

When I start up Ubuntu, everything seemingly goes smooth until I see the Ubuntu-logo, and loading-bar beneath the logo, then something that may resemble the terminal in Ubuntu shows on my screen, only that it's a little described about what it is, as opposed to what you see in the terminal. I can then type in commands to the computer. A list of commands is printed on the screen, when I enter "help", featuring "ls", "cd", "wget", "help", and a lot of other commands. Is there someone who can help me to get you to and the desktop, so that I can use Ubuntu the way I want to use it?

The computer my name is HP Compaq nx6325, and the graphics card is called the ATI Radeon Xpress 1150.
[Link to the list of all the components in my computer](http://developer.novell.com/yes/84948.htm)

---

### Post by diablo75 on 2008-06-10
What was the last thing you did before this started happening?

---

### Post by ukripper on 2008-06-10
Can you run this command when you see that terminal window:
```
startx
```

and post any output if you get.

---

### Post by MarkusIggy on 2008-06-10
> **diablo75 said:**
> What was the last thing you did before this started happening?

I'm sorry, I forgot to include that in my first post.

The last thing I did before this started happening was installing the restricted driver for my wireless network-card. I also tried to click to download and install the restricted driver for the graphics-card (I forgot to mention that the card needs the restrcted driver), but it didn't seem to download at all, so I just restarted my computer, thinking I could install the graphics-card later.

> **ukripper said:**
> Can you run this command when you see that terminal window:
```
startx
```

and post any output if you get.

I'll try later...

---

### Post by MarkusIggy on 2008-06-10
UPDATE: I don't know what happened, but this time (third time) I started Ubuntu, I did not get the weird screen I thought I would get. Thank you for your time. I will aska again if the problem comes up again. :)

---

### Post by ukripper on 2008-06-11
> **MarkusIggy said:**
> UPDATE: I don't know what happened, but this time (third time) I started Ubuntu, I did not get the weird screen I thought I would get. Thank you for your time. I will aska again if the problem comes up again. :)

no problem. if it happens again try startx to restart the xserver.

:)

---

### Post by MarkusIggy on 2008-06-11
> **ukripper said:**
> no problem. if it happens again try startx to restart the xserver.

:)

Okay! Thank you! But what is the xserver?

---

### Post by ukripper on 2008-06-11
> **MarkusIggy said:**
> Okay! Thank you! But what is the xserver?

Xserver handles all your desktop GUI side in simple terms. Basically, if you have no X window system you won't be able to use GNOME or KDE at all, only thing you will have is console (only command line) no GUI. Good example is Ubuntu server which is only console based unless you manually install ubuntu-desktop(gnome).

For details check this link - [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

