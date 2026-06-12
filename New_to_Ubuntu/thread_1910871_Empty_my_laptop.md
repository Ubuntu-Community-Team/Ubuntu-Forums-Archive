---
title: "Empty my laptop"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by Ron156 on 2012-01-17
Hi all,
I am a newbie trying to make head or tail of this great system.
I have downloaded Ubuntu 11.10 on to my laptop with it sitting alongside Windows.

It runs very slowly and the forums have taught me to look more closely at my system, so I now realise I don't have enough grunt to run it this way(Toshiba Tecra 1.73GHz 795 MHz, 504  MB of RAM).

I have concluded that I need to run one of the Puppy versions.

Now for my questions. I want to clear out the laptop and install only the Lynux system, so how do I do it without killing off the Toshiba tools and other stuff I might need? Or is it OK to wipe the whole hard drive? If so, what is the process and, if I have cleaned the drive out, how can I give commands to the computer to load the Puppy?
I am a very naive about changing code, so if that is necessary, please be gentle.
Many thanks.

---

### Post by corrytonapple on 2012-01-17
Dude, Puppy is a little extreame for your specs.  You can run many other DE (Desktop Enviroments) on that laptop.
Fire up that terminal.  Go to the Ubuntu Logo, click it, and type terminal.
```
sudo apt-get install xubuntu-desktop
```
When all is done, logout.  Then, click your username, and where you see that little gear next to your username, click it.  The menu will pop up, and you can click "XFCE" or something like that.
Try it out and see how you like it.  We can get even lighter if we need to.

---

### Post by papibe on 2012-01-17
Is that a Pentium 3? If so, take a look at Lubuntu.

If it's a P4, as corrytonapple mentioned, Xubuntu will fit just fine.

Just my thoughts.
Regards.

---

### Post by Bucky Ball on 2012-01-17
Mods please remove this post. ;)

---

### Post by Bucky Ball on 2012-01-17
> **corrytonapple said:**
>  Go to the Ubuntu Logo, click it, and type terminal.
```
sudo apt-get install xubuntu-desktop
```

I wouldn't advise this as it will install all Xubuntu apps also. You only need to install the desktop environment, Xfce4. It can be found in the software centre. Then log out and in the 'Sessions' menu choose Xfce Session. Log in. Done. 

Don't need to clag that little baby anymore than necessary. ;)

*** NOT sure why this posted twice. Could mods remove one above, please. ;)

---

### Post by corrytonapple on 2012-01-17
> **papibe said:**
> Is that a Pentium 3? If so, take a look at Lubuntu.

If it's a P4, as corrytonapple mentioned, Xubuntu will fit just fine.

Just my thoughts.
Regards.

Googilng reveals the pentinum m is what is in that laptop.  It is (in their higher range) equal to a P4.  I'd say it can do it.  The M's were for mobile, the P4's for desktops.

BTW, Bucky:
If he wanted this to be a full replacement, he may as well get everything.
But if he has a slow internet connection, then replacing "xubuntu-desktop" with "xfce4" should work.  IDK packages names anymore, I'm a Debian guy.

---

### Post by Ron156 on 2012-01-17
Thanks so far.
I got the message E: Unable to locate package xbuntu-desktop.
Any ideas?

---

### Post by Ron156 on 2012-01-17
When you said fire up that terminal, did you mean start UBUNTU? Please forgive my naivety.

---

### Post by Mark Phelps on 2012-01-18
> **Ron156 said:**
> Thanks so far.
I got the message E: Unable to locate package xbuntu-desktop.
Any ideas?

You misspelled it.  It's "xubuntu" not "xbuntu".

---

### Post by corrytonapple on 2012-01-18
> **Ron156 said:**
> When you said fire up that terminal, did you mean start UBUNTU? Please forgive my naivety.
That is me being redneck :P

I mean launch the terminal, as described.  Ubuntu must be started though to launch the Terminal.

---

### Post by sudodus on 2012-01-18
> **Ron156 said:**
> Hi all,
I am a newbie trying to make head or tail of this great system.
I have downloaded Ubuntu 11.10 on to my laptop with it sitting alongside Windows.

It runs very slowly and the forums have taught me to look more closely at my system, so I now realise I don't have enough grunt to run it this way(Toshiba Tecra 1.73GHz 795 MHz, 504  MB of RAM).

I have concluded that I need to run one of the Puppy versions.

Now for my questions. I want to clear out the laptop and install only the Lynux system, so how do I do it without killing off the Toshiba tools and other stuff I might need? Or is it OK to wipe the whole hard drive? If so, what is the process and, if I have cleaned the drive out, how can I give commands to the computer to load the Puppy?
I am a very naive about changing code, so if that is necessary, please be gentle.
Many thanks.
If your hard drive is big enough, you can have a dual boot system, otherwise I suggest that you wipe the drive completely and dedicate it to Lubuntu or Xubuntu. Try them both from a live CD or USB drive, so that you know that it works, before you install.

---

