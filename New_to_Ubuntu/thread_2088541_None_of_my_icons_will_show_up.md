---
title: "None of my icons will show up"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by JSF16 on 2012-11-26
This is a very urgent issue for me considering how often I use my laptop. I was going through the updated library, and was notified that some of the updates could not be installed -presumably because they were for ubuntu 12.10- but the rest where. I installed the rest, and was told to restart my computer to apply them. I did so, and when I signed back on after it powering up, nothing appeared. My wallpaper was there, but nothing else. No sidebar, no icons, NOTHING for which to operate my computer with. If I insert a DVD or something of the like, the program to play it will power up and I may use that, but can't minimize/maximize the window and still cannot access any of my icons or my sidebar.

I do need to use this computer tomorrow, and would be most obliged if help could come quickly.

---

### Post by newb85 on 2012-11-26
I don't understand.  Are you not running 12.10?  Why would updates for 12.10 come up?

---

### Post by evilsoup on 2012-11-26
Press ctrl+alt+t ; this should bring up a terminal. Copy and paste the following (paste into a terminal with ctrl+shift+v)
```
sudo apt-get install -f
```
Then press enter. You'll have to put in your password - there'll be no visual feedback - and then press enter again.

The update manager will never try to install packages for another version, unless you're using backports or some other voodoo magic; sometimes things just go wrong, for whatever reason (are you using any PPAs or other custom repositories?), and this command will try to fix things.

---

### Post by JSF16 on 2012-11-26
ctrl+alt+t is not bringing up terminal. Nothing is happening. I have a cursor on the screen, but nothing else.

---

### Post by evilsoup on 2012-11-26
Ah, OK then. press ctrl+alt+F1; this will bring up a full-screen terminal (try ctrl+alt+F2 if that doesn't work). You'll have to enter your username and password, but then just use the command in my above post.

To reboot the computer from there when the apt-get install -f is finished, use
```
sudo shutdown -r now
```

---

### Post by JSF16 on 2012-11-26
Alright, I did that. No change however. I entered in the code you gave me, then restarted using the code. Upon reboot, no changes.

---

### Post by JSF16 on 2012-11-26
I mean not to irritate with such a hasty bump, but straits are most dire for me, and I need my computer operational again ASAP.

---

### Post by arpanaut on 2012-11-26
Just a shot in the dark here...
Have you tried to login to Ubuntu 2d ?
It might get you to a usable desktop so you can try to correct things.

HTH

---

### Post by JSF16 on 2012-11-26
I know not what Ubuntu 2D is nor how to log in to it.

---

### Post by JSF16 on 2012-11-26
Update: I am unsure if I am running 12.04 or 12.10. When I use ctrl+alt+F1 to use the fullscreen terminal, it says I am using 12.10, however when I log on the writing at the bottom-corner of my screen says ubuntu 12.04

---

### Post by arpanaut on 2012-11-27
When you are at the logon screen click on the gear by the name and choose the ubuntu 2d session.

From what I see in this thread and your other it seems that you have suffered a partial upgrade to 12.10 and may have mixed repositories, this may be hard to correct.

What I would suggest is to back up your personal data, your email, your bookmarks from firefox and then do a fresh install with your 12.04 iso, overwriting the install you have now.
In the installer select "something else" and install to the partition(s) you used originally.
This will give you a pristine system that you can build on from there.
In the future if the update manager offers a partial update, Do Not accept, this usually indicates something wrong with the repositories or something misconfigured with update manager, cancel the upgrade and investigate why the partial upgrade is being offered..

Fresh installs are not fun, and not necessarily the "Linux" way, but sometimes quicker and easier than trying to solve complex problems and breakages.

I still can't understand how you got 12.10 parts wanting to be installed unless you explicitly told the system to do that.

---

### Post by LuisGMarine on 2012-11-27
This could be linked to your video card drivers being updated.  If possible can you verify that one of the updates was a video driver update?

1. First you need to check if this package is installed.  Simply type this into the terminal window.  It should spit out two entries, one being the kernel, and two the actual package linux-headers-generic, let me know the output of if it says the package is installed, and what version. :
```

apt-cache policy linux-headers-generic
```

2. Do you have an nVidia or ATI graphics card?  Also do you know what driver the card is currently using?  For example, if you are running an nvidia card, type this command into a terminal and post the output to see what driver package you have installed.
```

apt-cache policy nvidia-current-*
```

Post back what the name of the driver is if installed, if you are using something else, try this command and post the output:
```

sudo lshw -c video
```

---

### Post by newb85 on 2012-11-27
> **JSF16 said:**
> I know not what Ubuntu 2D is nor how to log in to it.

When prompted for your password at the login screen, click the little Ubuntu icon next to your name and select the Ubuntu 2D option.  Then proceed normally and see if your system is at least usable.

Edit: Oops, should have turned the page...

---

