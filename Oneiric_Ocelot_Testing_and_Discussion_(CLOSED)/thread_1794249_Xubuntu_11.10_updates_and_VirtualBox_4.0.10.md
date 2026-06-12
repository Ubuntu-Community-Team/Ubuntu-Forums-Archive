---
title: "Xubuntu 11.10 updates and VirtualBox 4.0.10"
date: 2011-06-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by loukingjr on 2011-06-30
Just installed a number of updates including the 3.0.2 kernel. Now Xubuntu will no longer boot. It hangs right after it checks the battery state.

---

### Post by lucazade on 2011-06-30
> **loukingjr said:**
> Just installed a number of updates including the 3.0.2 kernel. Now Xubuntu will no longer boot. It hangs right after it checks the battery state.

battery-state check, if i'm not wrong, is one of the last thing before starting X.
Have you tried to switch to another virtual terminal, login, and to start X manually? 
sudo service lightdm restart (or stop and start)

maybe drivers for the gpu are not compiled against new kernel 3.0.2 and X doesn't start.

---

### Post by loukingjr on 2011-06-30
hmmm, I can login to my user acct from the cli and get to my desktop by typing startx but once there I can't mount drives, open users & groups etc. I can log in as root. I'm going to make a new user from there and see what happens.

edit: downloaded today's daily build. It doesn't boot either. oh well lol

---

### Post by Bowmore on 2011-06-30
One reason where this happens atm is if one use lightdm's autologin. If so, try switching to non-autologin by commenting out the *default-user* line in the lightdm config file */etc/lightdm/lightdm.conf*.

---

### Post by loukingjr on 2011-06-30
> **Bowmore said:**
> One reason where this happens atm is if one use lightdm's autologin. If so, try switching to non-autologin by commenting out the *default-user* line in the lightdm config file */etc/lightdm/lightdm.conf*.
actually every line in the lightdm.conf file is commented out except for...
[GuestAccount]
enabled=true
username=guest
setup-script=/usr/share/lightdm/guest-session/guest-session-setup.sh
cleanup-script=/usr/share/lightdm/guest-session/guest-session-cleanup.sh

---

### Post by jerrrys on 2011-06-30
so is mine.  thats an option during install that i passed on.

---

### Post by loukingjr on 2011-06-30
> **jerrrys said:**
> so is mine.  thats an option during install that i passed on.
well, I can't boot today's live cd either.
edit: is there something I should uncomment in my hard drive install that might work?

---

### Post by jerrrys on 2011-06-30
can't even get to a terminal?  guest you got a new coaster...

---

### Post by loukingjr on 2011-06-30
> **jerrrys said:**
> can't even get to a terminal?  guest you got a new coaster...
I can get to a terminal. It's easier for me to connect the virtual drive to another vm and edit things from there. I'm just not sure what to change. as it is, both the live cd and my Xubuntu guest boot to a black screen.

---

### Post by jerrrys on 2011-06-30
myself, i just updated both guest and host.  a couple of things in guest now work.  the host is no different.  i am going to burn a copy this weekend and do a total reinstall.  hopefully lose some bugs...

EDIT: didnt see your post till now

---

### Post by jerrrys on 2011-06-30
ok, i quicky read thru things.  cant startx, how bout sudo gdm

---

### Post by loukingjr on 2011-06-30
> **jerrrys said:**
> myself, i just updated both guest and host.  a couple of things in guest now work.  the host is no different.  i am going to burn a copy this weekend and do a total reinstall.  hopefully lose some bugs...

EDIT: didnt see your post till now

well, I guess i will wait for the next builds. It's not like I have a shortage of guests :)

---

### Post by jerrrys on 2011-06-30
i started with 3, but now down to using just one and a clone drive

---

### Post by loukingjr on 2011-06-30
> **jerrrys said:**
> ok, i quicky read thru things.  cant startx, how bout sudo gdm
actually I can start x. it takes me to root though. running sudo gdm gave me a failed to acquire org.... something something gnome... etc...

---

### Post by jerrrys on 2011-06-30
we are having a one step ahead conversation

---

### Post by Yellow Pasque on 2011-06-30
I'm pretty sure the vboxvideo module doesn't build with the updated kernel. Change your /etc/X11/xorg.conf to use vesa driver.

---

### Post by loukingjr on 2011-06-30
well it seems I can only startx randomly. I'll just wait a few days for another build. thank you for trying to help for the help .

---

### Post by jerrrys on 2011-06-30
nice tip.  have to keep it in mind this weekend...

---

### Post by loukingjr on 2011-06-30
> **Temüjin said:**
> I'm pretty sure the vboxvideo module doesn't build with the updated kernel. Change your /etc/X11/xorg.conf to use vesa driver.
I don't have a /etc/X11/xorg.conf file... I thought ubuntus stopped using xorg files

---

### Post by Yellow Pasque on 2011-06-30
> **loukingjr said:**
> I don't have a /etc/X11/xorg.conf file... I thought ubuntus stopped using xorg files
Usually, the vbox guest additions installer creates one automatically.

---

### Post by Bowmore on 2011-06-30
Ok, tried the daily built and was left with a blank screen.

First I commented out *default-user=ubuntu* and *default-user-timeout=5* in the lightdm.conf followed by *sudo restart lightdm* to get to the login screen.

Then logging in still gave a blank screen. Restarted lightm again and **selected** a session which then logged in successfully!

It seems here that the session is kind of undefined and has to be manually set.

---

### Post by jerrrys on 2011-06-30
i am soooo glad i stopped here.  any your right, no xorg.conf.

---

### Post by cariboo on 2011-06-30
I'm not sure about AMD/ATI, but Intel and Nvidia don't need an xorg.conf any more, and haven't for the last couple of releases.

---

### Post by jerrrys on 2011-07-01
and guest additions will not create them

---

### Post by cariboo on 2011-07-01
And I didn't pay attention to the title of this thread. :)

---

### Post by loukingjr on 2011-07-02
> **Bowmore said:**
> Ok, tried the daily built and was left with a blank screen.

First I commented out *default-user=ubuntu* and *default-user-timeout=5* in the lightdm.conf followed by *sudo restart lightdm* to get to the login screen.

Then logging in still gave a blank screen. Restarted lightm again and **selected** a session which then logged in successfully!

It seems here that the session is kind of undefined and has to be manually set.

interesting but as I mentioned everything in my copy of lightdm.conf was commented out so not much point in me re-commenting them out. And I'm not sure how to comment anything out in the .iso I'm trying to install :(

edit: well, I'm back in business. Today's daily build works although I am having a few issues, like the notification applet just says no indicators, and when I try and launch users and groups I get this...

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported

---

### Post by Bowmore on 2011-07-02
> **loukingjr said:**
> interesting but as I mentioned everything in my copy of lightdm.conf was commented out so not much point in me re-commenting them out. And I'm not sure how to comment anything out in the .iso I'm trying to install :(Anyway, it seems to be a session issue. Actually Xubuntu tries to launch the gnome session that does not exist instead of the xubuntu session.

I found out a workaround to enable autologin as well by creating a gnome softlink to the xubuntu session.
```
cd /usr/share/xsessions/
sudo ln -s xubuntu.desktop gnome.desktop
```

> **loukingjr said:**
> Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supportedThat's what you get if you try to launch this using the obsolete command u*sers-admin*. Same happened to Ubuntu during the transitions from gnome2 to gnome3. I guess Xubuntu goes for gcc too using the command *gnome-control-center user-accounts*.

---

### Post by loukingjr on 2011-07-02
thanks for the info. I just added myself to the vboxsf group in the terminal. Things seem to be running ok for an alpha release.

---

