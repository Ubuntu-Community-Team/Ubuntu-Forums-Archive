---
title: "Setting up an automatic login"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by old-newbie on 2008-08-30
> **pyromanic123boom said:**
> First set up an autologin in an easier way.
click on System -> Administration -> Login Window
Change to the Security tab.
Enable the checkbox for Enable Automatic Login
Select your user account from the drop-down list of users. 

This option is not available on my system and when I tried to install using ```
gksu gdmsetup
```
I get error message
```
GDM is not running.
You might be using a different display manager,
 such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. 
 If you wish to use this feature, then your system will need to be configured
 to use GDM instead.
```

I am using ubuntu 7.10 with gnome on a remote server.

I have also tried the *getty* & the *rungetty* scripts on this page, but can't get either of those to work either. Any suggestions anyone?

---

### Post by aysiu on 2008-08-30
Are you, in fact, running KDM, CDE, or XDM?

---

### Post by old-newbie on 2008-08-30
> **aysiu said:**
> Are you, in fact, running KDM, CDE, or XDM?

No, I am definitely running gnome. I am connecting to a remote server using NX

---

### Post by aysiu on 2008-08-30
You can be running Gnome without running GDM.

---

### Post by old-newbie on 2008-08-30
> **aysiu said:**
> You can be running Gnome without running GDM.

I'm not bothered whether gdm is running or not, I just want to be able to set up automatic login, that is apparently the easiest option.  I am totally new to Linux and am getting on a bit, so learning takes a little longer than it used to. I have been bulding my own windows (sorry to mention that word here):oops: machines for years. Linux takes a bit of getting used to, so any help I get would be truly appreciated.

---

### Post by aysiu on 2008-08-30
Can you do this?

Log out.

Press Control-Alt-F1. This will take you to a full-screen terminal.

Log in.

Type ```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo /etc/init.d/gdm restart
``` and then log in again and try ```
gksu gdmsetup
``` ?

---

### Post by decoherence on 2008-08-30
In my experience, NX appears to function as the display/session manager, bypassing gdm/kdm/whatever.

As auto-login is something handled by the display manager, I would tend to think you should be looking for the NX way of doing this, if there is one. I must say, the idea of automatically logging in to a remote session strikes me as kind of odd, but maybe i just don't undrestand what you're trying to do.

---

### Post by old-newbie on 2008-08-30
If I log out I can't access it as the server is in France and I am in the UK

also Control-Alt-F1 doesnt work

however I tried the commands you said in the terminal and got the login window. I set the auto login on the security tab and rebooted, but the auto login didnt work

---

### Post by old-newbie on 2008-08-30
> **decoherence said:**
> In my experience, NX appears to function as the display/session manager, bypassing gdm/kdm/whatever.

As auto-login is something handled by the display manager, I would tend to think you should be looking for the NX way of doing this, if there is one. I must say, the idea of automatically logging in to a remote session strikes me as kind of odd, but maybe i just don't undrestand what you're trying to do.


I don't want to physically login myself. I am using this server purely for shoutcast servers, and want the "user" to auto login in the event of a server reboot so that the shoutcast servers start up. 

Presently I would have to physically login to make this happen

---

### Post by old-newbie on 2008-08-30
The only other way would possibly add the shoutcast servers as services so that they auto start on boot up, but again I have no idea how to do this

---

### Post by decoherence on 2008-08-30
ah i understand now

> add the shoutcast servers as services so that they auto start on boot up

this is the standard way of doing htis. unfortunately i'm running out the door for a camping trip. someone tell this guy how to start a shoutcast service? ;)

cheers,
sean

---

### Post by old-newbie on 2008-09-26
Bump!

---

