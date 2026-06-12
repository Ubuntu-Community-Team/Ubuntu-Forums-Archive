---
title: "Setting up an xorg.conf file to force software cursor"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-05-16
I don't think xorg.conf is in use anymore, but it used to let you specify a hardware or software cursor to handle mouse problems.  In one case, the use of certain NVidia video drivers was the problem.

[http://www.pendrivelinux.com/mouse-pointer-disappears-after-switching-users/](http://www.pendrivelinux.com/mouse-pointer-disappears-after-switching-users/)

Can one still create an xorg.conf file and place it in /etc/X11?  Would that be the correct directory with the latest Ubuntu releases?

I'm trying to help a friend and thought I would see what I could learn.

Thanks for any information.

---

### Post by Luke M on 2014-05-17
> **KAWill70 said:**
> 
Can one still create an xorg.conf file and place it in /etc/X11?  Would that be the correct directory with the latest Ubuntu releases?


Yes and yes.

---

### Post by KAWill70 on 2014-05-18
Thanks for the help.

I just discovered that you can't simply copy xorg.conf into the desired directory.  It appears that I need to drop into console mode, stop the video service, copy or move the file, and then restart the stopped service.  However, my console mode gives a black screen so I need to resolve that first.

I also saw reference that the command sudo Xorg -configure might get me started.

---

### Post by Luke M on 2014-05-18
> **KAWill70 said:**
> 
I just discovered that you can't simply copy xorg.conf into the desired directory.  It appears that I need to drop into console mode, stop the video service, copy or move the file, and then restart the stopped service.  However, my console mode gives a black screen so I need to resolve that first.


That sounds unnecessarily hard. You can edit xorg.conf while it's running, it just won't take effect until you reboot (actually logging out might be enough).

---

### Post by KAWill70 on 2014-05-19
> **Luke M said:**
> That sounds unnecessarily hard. You can edit xorg.conf while it's running, it just won't take effect until you reboot (actually logging out might be enough).
Glad to hear that xorg.conf can easily be edited.  However, it doesn't appear easy to get that file into /etc/X11 in the first place.  I have tried several things and all attempts to copy or paste the file into the directory have been rejected.  That is when I ran across the link below.

[http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file](http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file)

It seems that others have had the same problem and used Console Mode to stop services before being able to copy the file.  It's also possible I misunderstood the information in that link.  Maybe services are only stopped so they can run sudo X-configure.

If anyone has more information please pass it along.

---

### Post by Luke M on 2014-05-19
> **KAWill70 said:**
> Glad to hear that xorg.conf can easily be edited.  However, it doesn't appear easy to get that file into /etc/X11 in the first place.

It's the same as any system modification, you need administrator privileges (doesn't matter whether Xwindows is running or not), e.g.:
gksudo gedit /etc/X11/xorg.conf

---

### Post by KAWill70 on 2014-05-20
> **Luke M said:**
> It's the same as any system modification, you need administrator privileges (doesn't matter whether Xwindows is running or not), e.g.:
gksudo gedit /etc/X11/xorg.conf
Thanks once again for the help.  I was able to create and store an xorg.conf file in both Lubuntu 14.04 and Mint 13 using sudo gedit and sudo leafpad.  The gksudo command did not seem to be required.  Now I need to play with the file contents.

The odd thing is that earlier I had tried copying an xorg.conf file on the desktop using the sudo cp command and it would not work.  Also tried sudo mv.  In Terminal mode I had changed to the correct directory and as I recall used the command sudo cp xorg.conf /etc/X11.  It was rejected.  I wonder if Linux treats the sudo text editor command differently from a terminal move or copy command.

---

### Post by Luke M on 2014-05-20
> **KAWill70 said:**
> 
The odd thing is that earlier I had tried copying an xorg.conf file on the desktop using the sudo cp command and it would not work.  Also tried sudo mv.  In Terminal mode I had changed to the correct directory and as I recall used the command sudo cp xorg.conf /etc/X11.  It was rejected.  I wonder if Linux treats the sudo text editor command differently from a terminal move or copy command.

No, I don't think so...probably just made a typing error.

---

### Post by KAWill70 on 2014-05-21
> **Luke M said:**
> No, I don't think so...probably just made a typing error.
I tried the sudo cp and sudo mv commands again and both worked.  Also did a few other operations for practice.  It's possible I failed to type a capital D for the Desktop designation.  You really need to be alert when entering terminal commands.

It looks like my xorg.conf is indeed being accessed at boot.  I discovered that there is an xorg log file in /var/log/.  Near the end I saw my attempt to enable a software cursor.  The log said the HWCursor and SWCursor entries were "not used".  It's possible my drivers are not set up for those features.

I also discovered desktop commands such as Ctl Alt F2 and Ctl Alt F7 to return.  There is a command defined as Xinit--:2 but it did not work on my system.  I was hoping to check changes to xorg.conf without having to reboot.

---

### Post by Luke M on 2014-05-21
> **KAWill70 said:**
> 
I also discovered desktop commands such as Ctl Alt F2 and Ctl Alt F7 to return.  There is a command defined as Xinit--:2 but it did not work on my system.  I was hoping to check changes to xorg.conf without having to reboot.

Doesn't logging out work? Or try
sudo restart lightdm

---

