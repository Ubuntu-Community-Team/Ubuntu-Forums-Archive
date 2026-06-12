---
title: "[SOLVED] no panels, no icons, no nuthin except background"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-06-25
I am dual booting with XP and Ubuntu.  Boot from grub gives me the sign in page, then all I get is my background, no panels, no icons, no Alt F2, no way to get to terminal.  It will let me change the background, but that is all.  I have already tried restore of .19, and the previous kernel .18, same thing in all of them.  How can I get my panels back so that I have ways of fixing whatever went wrong ??

---

### Post by iaculallad on 2008-06-25
Press Ctrl+Alt+F1 to get in your TTY: Then issue the command below to reset your GNOME settings.
```

rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Press Ctrl+Alt+F7 again to get back to your GUI.

---

### Post by N.N. on 2008-06-25
Was typing this when there were no replies to the thread, but it's along the lines of iaculallad's reply:

It sounds like something's wrong with your GNOME settings. Try the following: [LIST=1]
[*]Right-click on the desktop and select "Create Launcher". Type in gnome-terminal as the command and click "OK".
[*]Use the launcher to start gnome-terminal.
[*]Issue the following command in the terminal and look for error messages that might indicate what's preventing the panel from being launched: ```
gnome-panel
```
[/LIST]
If the panel refuses to launch when you issue gnome-panel from the terminal, it often helps to reset your GNOME settings, or at least your gnome-panel settings.

Your gnome-panel settings are stored in ~/.gconf/apps/panel. To reset these settings, issue the following command in a terminal: ```
rm -r ~/.gconf/apps/panel
``` Having done that, try starting gnome-panel again.

If that doesn't solve your problem, try resetting all your GNOME settings by deleting or renaming the following hidden directories located in your home directory: [LIST]
[*].gnome
[*].gnome2
[*].gconf
[*].gconfd
[*].metacity
[/LIST]
If you aren't comfortable with doing this from a terminal, you can create a launcher for the graphical file manager, nautilus, the same way you created a launcher for gnome-terminal. In the command field of the launcher just subsitute gnome-terminal with nautilus. Once in nautilus, press CTRL+H to reveal hidden files.

---

### Post by gettinoriginal on 2008-06-25
Did as you said, no luck, just a background. :confused:  I cannot obtain a terminal, that is part of the problem.

---

### Post by N.N. on 2008-06-25
> **gettinoriginal said:**
> Did as you said, no luck, just a background. :confused:

You might have to restart X in order for the changes to take effect. Once you're at the GUI with the background, press CTRL+ALT+BACKSPACE to restart X.

---

### Post by etnlIcarus on 2008-06-25
I think people have jumped the gun a bit. When at GDM (login screen) there should be a, "session", option somewhere. Click it to open up a menu. By default, it uses the, "last used", session. Change it to a fresh Gnome session and login.

if that fails, start doing the following:

$ dpkg-reconfigure gnome-session 
$ dpkg-reconfigure gnome-panel
etc.

---

### Post by gettinoriginal on 2008-06-25
Well, have tried it all, it did give me the default heron background, and an error message that nautilus could not be used, something about needing to stop the bonobo-activation-server, but don't know how to do that either.  I still cannot do anything from the background, and at the sign in page, there is no option for session, only user name, then password.  Sorry this is all taking so long for me to respond, but I have to keep rebooting out of ubuntu back to windows to get to the forums.  I do appreciate all the help.  Any more suggestions ??  and what is meant by the 2 commands and etc. what is etc ??

---

### Post by gettinoriginal on 2008-06-25
Sorry, dummy me, I found the options box and changed the session to gnome default, but still no go, only the background.

---

### Post by Tomatz on 2008-06-25
Press [B]<alt> F2
[/B]
Then in the run dialogue type:
```

gksu users-admin
```


**Add a new user** then **log out** and see if you can log into that account. 

;)

---

### Post by etnlIcarus on 2008-06-25
> **Tomatz said:**
> Press [B]<alt> F2
[/B]
Then in the run dialogue type:
```

gksu users-admin
```


**Add a new user** then **log out** and see if you can log into that account. 

;)
If I remember correctly, the keybondings are tied into either metacity or gnome-panel.

You'll have to start up a recovery session from grub; use the command, "startx", to log into a graphical session as root and then create a new user account.



If you only get a background when you star a graphical session, you might have to use the command:

$ startx && gnome-session

If that still doesn't work as it should, I'm guessing gnome is broken. At which point I'd suggest logging into a shell; opening up aptitude and installing Xfce pacakges so you can log into the Xfce desktop environment instead.

---

### Post by gettinoriginal on 2008-06-25
Ok, I have tried everyones suggestions, and still no change, so am assuming I am going to have to do a fresh install.  Thanks everyone for your attempts, if nothing else, I have learned alot of code  LOL

---

### Post by etnlIcarus on 2008-06-25
> **gettinoriginal said:**
> Ok, I have tried everyones suggestions, and still no change, so am assuming I am going to have to do a fresh install.  Thanks everyone for your attempts, if nothing else, I have learned alot of code  LOL

You couldn't install Xfce though either apt-get or aptitude? Something must be seriously wrong with your system then.

---

### Post by gettinoriginal on 2008-06-25
Sorry, I was responding with the fresh install reply when you posted that, I am going to try your advice.  Thanks

---

### Post by etnlIcarus on 2008-06-25
- Boot up.
- Ctrl Alt F1 at login screen.
- Login in text mode.
- sudo apt-get install xfce4

Once you restart, you should be able to choose an Xfce4 session from the session chooser on the login screen.

---

### Post by gettinoriginal on 2008-06-25
Ok, I did that, but still no panels or icons, just background.  But now I get an error message that nautilus cannot launch due to bonobo-activation-server problem.

---

### Post by Tomatz on 2008-06-25
> **gettinoriginal said:**
> Ok, I did that, but still no panels or icons, just background.  But now I get an error message that nautilus cannot launch due to bonobo-activation-server problem.

You need to change your session to xfce in the login screen ;)

---

### Post by lswest on 2008-06-25
hit <ctrl>+<alt>+F1 at the login screen, sign in to that virtual terminal and do:
```
sudo apt-get install --reinstall libbonobo2-bin
``` seems the problem is to do with the package, so try re-installing it.

---

### Post by etnlIcarus on 2008-06-25
Natilus shouldn't be trying to launch. You're supposed to choose an Xfce-session; not a Gnome-session.

Once you've got a working desktop environment other than gnome, you can then go about comfortably investigating why gnome isn't working.

---

### Post by gettinoriginal on 2008-06-25
Thank you all so much for the help, I now have a working desktop in ubuntu, now if I can only figure out why gnome will not work, cause I sure can't figure out how to set up this xfce thing, :lolflag:

---

### Post by etnlIcarus on 2008-06-25
You'll probably find Xfce easier to learn than Gnome. Until you open up synaptic and install a bunch of extra packackages for Xfce (mcs-plugins-extra, xfce4-goodies, etc), onyl expect basic functionality, though.

With regards to Gnome, have you created a second user account yet and tried to log into a fresh Gnome desktop? And have you reinstalled all your bonobo components yet?

---

### Post by gettinoriginal on 2008-06-25
I did as above with bonobo ie: sudo apt-get install --reinstall libbonobo2-bin, but that is all I did with it, is there more ??  I tried a new account, and it still wouldnt give me a working desktop.  I also have no idea what I need to install in this new one.  I can't find terminal, all of the help buttons just tell me it "can't find page", and icons cannot be rearranged on the panel, they just snap back to where they were.  I hate to mess with the synaptic manager, as that is what I think got me in trouble in gnome, I tried to uninstall evolution, and everything went pooof.

---

### Post by etnlIcarus on 2008-06-25
Son of a...


$ sudo apt-get install ubuntu-desktop



Granted, it's possible that with all the screwing around we've boned some of the files in your home directory so you'll probably have a bit of work ahead of you getting Gnome back the way you want it.

Edit: I guess I should explain that a little better.

Introduction: **Welcome to dependency hell**

The problem: Evolution is, for lack of a better analogy, "tied", to many other apps it really shouldn't be. When you uninstalled it, it took many dependant packages with it - including half the stuff needed by Gnome.


Edit again: Also, not blaming you but you really should have told us what you were doing before the problem occurred. I should have asked as well, except I've personally had parts of Gnome die for no good reason so I assumed it was an error at Gnome's end. Funnily enough, though, the first major mistake I ever made with *nix was trying to remove a stock application and clicking, "ok", when it asked to uninstall 50 other packages. :p

---

### Post by gettinoriginal on 2008-06-25
well, if you could explain to me where I can find the terminal in xfce, I could try to repair it.  But seriously, despite anything else I have to deal with, you have been excellent help !!:KS

---

### Post by etnlIcarus on 2008-06-25
Ctrl Alt F1

Or you can open gnome-terminal from the /usr/bin directory or you can try Ctrl F2 and just type in *gnome-terminal*.

---

### Post by gettinoriginal on 2008-06-25
well, I found the "konsol"  and installed that, but it won't let me install ubuntu desktop, error says 
"Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

---

### Post by etnlIcarus on 2008-06-25
*sudo* apt-get install ubuntu-desktop

You need to su (set user) to root so you've got admin rights.

---

### Post by Tomatz on 2008-06-25
> **etnlIcarus said:**
> *sudo* apt-get install ubuntu-desktop

You need to su (set user) to root so you've got admin rights.

Its because he has synaptic running while trying to use apt.

Close synaptic ;)

---

### Post by etnlIcarus on 2008-06-25
> **Tomatz said:**
> Its because he has synaptic running while trying to use apt.

Close synaptic ;)Ahh damnit, it's almost the same error message. :p

---

### Post by gettinoriginal on 2008-06-25
Hate to tell you this, but no, I dont have synaptic running, but I did a reboot just to make sure something wasn't running that I cant find on this new xfce, and guess what, I get a background only even with the session set on xfce !!!

---

### Post by Tomatz on 2008-06-25
> **gettinoriginal said:**
> Hate to tell you this, but no, I dont have synaptic running, but I did a reboot just to make sure something wasn't running that I cant find on this new xfce, and guess what, I get a background only even with the session set on xfce !!!

I suggest you backup all your files and reinstall. Its either half hour max installing or possibly hours of pain ;)

---

### Post by etnlIcarus on 2008-06-25
Yeah, I think it's time to admit defeat.

---

### Post by gettinoriginal on 2008-06-25
Well, I did get xfce desktop back :lolflag:  But in case I have to reinstall, do I erase the partition and reinstall from the ISO I have, or is there an easier way ??

---

### Post by Tomatz on 2008-06-25
> **gettinoriginal said:**
> Well, I did get xfce desktop back :lolflag:  But in case I have to reinstall, do I erase the partition and reinstall from the ISO I have, or is there an easier way ??

You can reformat (erase) the disc/partition from the install disc.

Just put it in the drive and reboot ;)

---

### Post by Tomatz on 2008-06-25
> **etnlIcarus said:**
> Yeah, I think it's time to admit defeat.

We live to fight another day :)

---

### Post by Tomatz on 2008-06-25
Let us know how you got on.

:guitar:

---

### Post by etnlIcarus on 2008-06-25
And if you uninstall an application which, in turn, tried to uninstall any more than about 5 dependencies, click, "cancel".

However, just try apt-get again. For old time's sake.

---

### Post by gettinoriginal on 2008-06-25
Now this is gonna floor ya, after all the "repairs" you all have helped me with, I decided to try one more time, so I did a sudo install evolution, sudo install ubuntu-desktop, then sessioned into gnome, and I'M BACK !!!  THANK YOU, THANK YOU, THANK YOU !!!:KS:KS:KS

---

### Post by etnlIcarus on 2008-06-25
25th hour hail-marry **SAVE!**

---

