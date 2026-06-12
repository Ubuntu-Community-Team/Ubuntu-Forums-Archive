---
title: "[SOLVED] 8.04 Upgrade Problem - Boot-Up!!"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-05-04
Hello all. I upgraded my Ubuntu 7.10 to 8.04 and restarted my computer. I than booted into Ubuntu and my monitor turned off. I hot CTRL+ALT+F1 and was at the Terminal. I logged int than typed "sudo apt-get install gdm ubuntu-desktop" and it ran some things.. than said I had to type something else (i forget what it was :( ) so I did that, took awhile. Than it was done and I restarted my computer. Upon entering the GRUB menu, there are now 6 items:

Ubuntu 8.04 22-26
Ubuntu 8.04 22-26 (Recovery Mode)
Ubuntu 8.04 24-22
Ubuntu 8.04 24-22 (Recovery Mode)
Ubuntu 8.04 MemTest
Windows XP Professional

I have NO idea how to boot into the desktop instead of the Terminal!! This happened just as I got done upgrading from 7.10 to 8.04. Any help?

---

### Post by Amstell on 2008-05-04
Can  you get to the desktop with recovery mode?

---

### Post by Cannaregio on 2008-05-04
> **UnknownFear said:**
> Hello all. I upgraded my Ubuntu 7.10 to 8.04 and restarted my computer. I than booted into Ubuntu and my monitor turned off. I hot CTRL+ALT+F1 and was at the Terminal. I logged int than typed "sudo apt-get install gdm ubuntu-desktop" and it ran some things.. than said I had to type something else (i forget what it was :( ) so I did that, took awhile. Than it was done and I restarted my computer. Upon entering the GRUB menu, there are now 6 items:

Ubuntu 8.04 22-26
Ubuntu 8.04 22-26 (Recovery Mode)
Ubuntu 8.04 24-22
Ubuntu 8.04 24-22 (Recovery Mode)
Ubuntu 8.04 MemTest
Windows XP Professional

I have NO idea how to boot into the desktop instead of the Terminal!! This happened just as I got done upgrading from 7.10 to 8.04. Any help?

If you choose the first option: [COLOR="Blue"]Ubuntu 8.04 22-26[/COLOR] what happens?
If you type at the terminal
```
startx
```
what happens?

---

### Post by UnknownFear on 2008-05-04
> **Cannaregio said:**
> If you choose the first option: [COLOR="Blue"]Ubuntu 8.04 22-26[/COLOR] what happens?
If you type at the terminal
```
startx
```
what happens?

Nothing happens. Give me a fatal server error or something. Im REALLY mad!! I just upgraded to 8.04 and installed it and got Ubuntu looking just the way i wanted it!!:mad:

---

### Post by Xerius_fire on 2008-05-04
I have the same issue. I just got finished upgrading from 7.10 to 8.04 and did the mandatory reboot and my monitor blanks out and the power button the monitor flashes orange denoting that it is off. I tried a recovery mode reboot but it gave the same results.

---

### Post by ace007 on 2008-05-04
the monitor turning off like that is usually a sign that your graphics card is not putting out a signal.  This most often occurs because of bad drivers.  It is possible that the upgrade attempted to reinstall a generic driver that comes with the 8.04 release and this is the cause of your problems.  You are going to need boot to a terminal and then install the new drivers from there.

---

### Post by UnknownFear on 2008-05-04
> **ace007 said:**
> the monitor turning off like that is usually a sign that your graphics card is not putting out a signal.  This most often occurs because of bad drivers.  It is possible that the upgrade attempted to reinstall a generic driver that comes with the 8.04 release and this is the cause of your problems.  You are going to need boot to a terminal and then install the new drivers from there.

Ok. How exactly would I go about doing this?

---

### Post by UnknownFear on 2008-05-04
Can I really get support with this? I really don't want to reinstall Ubuntu and than install my drivers.

---

### Post by kansasnoob on 2008-05-04
I did two upgrades from Gutsy. One came off with hardly any problems (basically redefining what program did what, ie: I like Totem, but mplayer took over), the other was a total wash! Nothing worked right! And I had to upgrade Medibuntu!

After several hours I just gave up and did a fresh install! That prompted me to create a seperate "home" partition in the future for all my machines. I'd already done so on some so Windows and Ubuntu could share data easily.

At least 8.04/Hardy is LTS! No sweat till 2011!

---

### Post by zot171 on 2008-05-13
Okay, I had a similar problem in that I could boot to terminal, and if I tried to move to run startx or xinit it spit back an error claiming that an instance of the GUI running. If this is your problem, try:

```
sudo killall5
startx
```

otherwise, or if you just know it's your drivers, try:

```
sudo dpkg-reconfigure xserver-xorg
```

it asks alot of questions, but if you do your best to answer you should get the correct drivers that you can go and test, if they don't work, try again (I tried for 2.5 hours before realizing I needed the LEGACY version of the drivers... then it worked fine)

---

