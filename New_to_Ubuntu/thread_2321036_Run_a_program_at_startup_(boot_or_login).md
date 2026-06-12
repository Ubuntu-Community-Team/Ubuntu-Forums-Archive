---
title: "Run a program at startup (boot or login)"
date: 2016-04-19
forum: New to Ubuntu
---

### Post by elpidiovaldez5 on 2016-04-19
I am using Lubuntu 14.04 64 bit.

I want to start programs automatically on booting or on login.  I thought it would be straightforward, but the truth is I can't even work out which directories to use.  I have tried using:
~/.config/lxsession/Lubuntu/autostart
/etc/xdg/lxsession/Lubuntu/autostart

There is also:
~/.config/autostart
/etc/xdg/lxsession/Lubuntu-Netbook/autostart
/etc/xdg/autostart
/etc/xdg/openbox/autostart

Also lxsession configuration tool from system menu offers autostart.  I tried using that but it didn't work.

I read this link [http://lxlinux.com/#4](http://lxlinux.com/#4) which confuses me more.  It says:

Autostart files in an LXDE desktop and/or Openbox can be located in at least 5 places, depending upon the distro. These are

   /etc/xdg/lxsession/LXDE/autostart
   /etc/xdg/openbox/autostart
   ~/.config/openbox/autostart.sh
   ~/.config/autostart
   /etc/xdg/autostart.

The first three are text files that are edited by adding text according to some format, and the last two are directories containing .desktop files for the processes that are to be started. If the lxde-core desktop is installed, then the lxde-autostart usually takes precedence in the command order. In an openbox-only distribution with no session-manager, generally ~/.config/autostart.sh rules. The two autostart files in the user's home directory (~/) only apply to that user; the 3 in the etc directory apply to all users.

The problem is that I don't know how out-of-the-box lubuntu is configured. Is the lxde-core desktop installed ?  I thought it was, but the directory /etc/xdg/lxsession/LXDE/autostart does not exist on my machine.

I have also read that there is a bug which means that if you use startup fies in the home directory they stop files in /etc/xdg from working.

Really I want an answer of the form 'In out-of-the-box Lubuntu 14.04 64 bit startup at login is achieved by a <command-line | .desktop> entry in <dir path>.  Startup before login requires <command linem | some other format> in <dir path>'.  Is there such a simple explanation ?

---

### Post by TheFu on 2016-04-20
End-user programs with a GUI cannot be started until after the userid logs in and X/Windows is started.  Make sense?
Also, it is best to use user-specific startup methods - so that a mistake doesn't prevent the system from working.

I would create a new userid and test each of the options in the ~/ directories. Should take 3 min for each.

I use openbox, but not LXDE. The startup method I use is: 
* ~/.config/openbox/autostart/
* create **any** files in there with the programs to be started after login; just simple bash scripts
* make the permissions executable

Be happy.  I don't have any .desktop files in there.  .desktop files are for menus, not running anything (at least in my mind).  Since I don't have a menu system in my setup, those are pretty worthless.  Remember, do this testing under a new userid, so you don't have any other side-effects from all the other attempts/failures which might have happened.

So - what have you tried? Did it work?

---

### Post by Dennis N on 2016-04-20
What works for me is to use the dialog at **Preferences > Default Applications for LX Session**.

Then in the "Autostart" section, use the "Add" button to add the command to "Manual Autostarted Applications" and check the box of the new entry to activate. If you look, you will also see that the system automatically creates a new entry in ~/.config/lxsession/Lubuntu/autostart for these.

Hasn't failed yet. 

That's all there is to it.

---

### Post by vasa1 on 2016-04-20
Which programs do you want to run when *your* session starts?

I don't use the Lubuntu session now but I remember that their .desktop files should go into *~/.config/autostart*.

---

