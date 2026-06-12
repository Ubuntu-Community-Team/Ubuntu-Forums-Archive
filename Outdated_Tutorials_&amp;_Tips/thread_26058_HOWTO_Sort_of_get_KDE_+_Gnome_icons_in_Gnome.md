---
title: "HOWTO: Sort of get KDE + Gnome icons in Gnome"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Gianni Exile on 2005-04-11
If you've run "apt-get install kubuntu-desktop" on a clean Ubuntu install, all kinds of KDE programs show up in the Gnome menus without icons.  I use for example  the (Gnome) Clearlooks icon theme, set in System->Preferences->Theme
Theme->Theme Details (button on right) ->Icon (tab on top).  Now select Clearlooks.

Now run your favourite editor, vim etc:
```
sudo gedit /usr/share/icons/Clearlooks/index.theme
```

Edit the line 
```
Inherits=gnome
```
to read as follows.
```
Inherits=crystalsvg,gnome
```

And voila! The icons for both appear properly in the menus.  I'm sure there's a better way, but this is the only one that's worked well so far, and other users of the system are happy.  It's not obvious to others what e.g. a program called Kooka does, but with the correct icon, a scanner, it is.

---

### Post by Topper on 2005-04-13
Nice, although to get the KDE icons I also had to do a 
```
$ sudo killall gnome-panel
```.

and everything was fine.

---

### Post by NeTo on 2005-05-05
I was searching on the net for a way to make that change in all the gnome themes without manually editing but I got a bit confused.

Would this work?

```
find /usr/share/icons/ -name "*.theme" -exec sudo sed -i 's/Inherits=gnome$/Inherits=crystalsvg,gnome$/g' {} \;
```

My ubuntu setup is badly damaged, so I can't test it right now, but I have the feeling there isn't something right in that line.

---

### Post by arnieboy on 2005-05-05
there is also another way to do it. You can copy all 32x32 images from one of the icon directories of KDE like crystal etc (search for kooka.png for example and u will know which directory am referring to) into /usr/share/pixmaps which is the default image directory for GNOME. You might choose not to overwrite any existing file. if /usr/share/pixmaps has an image referenced by any .desktop file in /usr/share/applications or /usr/share/applications/KDE, then u will see it in the gnome menu, provided the .desktop file allows the item to be shown in the GNOME menu.

---

### Post by maspro on 2005-05-11
[QUOTE=arnieboy]there is also another way to do it. You can copy all 32x32 images from one of the icon directories of KDE like crystal etc (search for kooka.png for example and u will know which directory am referring to) into /usr/share/pixmaps which is the default image directory for GNOME. You might choose not to overwrite any existing file. if /usr/share/pixmaps has an image referenced by any .desktop file in /usr/share/applications or /usr/share/applications/KDE, then u will see it in the gnome menu, provided the .desktop file allows the item to be shown in the GNOME menu.[/QUOTE]
I tried this method and after rebooting I can't login anymore and it gives me a bunch of errors recommending me to check my install and saying something about d_cop_server??? and errors somewhere in the /etc/.. Very strange.

---

### Post by arnieboy on 2005-05-11
[QUOTE=maspro]I tried this method and after rebooting I can't login anymore and it gives me a bunch of errors recommending me to check my install and saying something about d_cop_server??? and errors somewhere in the /etc/.. Very strange.[/QUOTE]
 the errors that are showing have nothing to do with copying a few image files from one directory to the other. Something else is messed up which u have to give details about so that we can analyze the problem and try and help you.

---

### Post by maspro on 2005-05-11
[QUOTE=arnieboy]the errors that are showing have nothing to do with copying a few image files from one directory to the other. Something else is messed up which u have to give details about so that we can analyze the problem and try and help you.[/QUOTE]
Well this happend to me once before, I also found it a bit strange that this happens just after I copied some images, so after a re-install of Ubuntu  :-#  I made a back-up image and then I tried again with the same errors. I just restored from my back-up so I don't have access to the error messages anymore, but tomorrow I will simulate the problem again and then post the errors here.  ;-)

---

### Post by maspro on 2005-05-12
[QUOTE=arnieboy]the errors that are showing have nothing to do with copying a few image files from one directory to the other. Something else is messed up which u have to give details about so that we can analyze the problem and try and help you.[/QUOTE]
Well here goes:

- After the install of Ubuntu I downloaded the Kubuntu-desktop through Synaptic.
- I then opened a terminal-windows and typed: sudo konqueror to open konqueror as root. 
- I then browsed to /usr/share/icons/crystalsvg/32x32/apps
- I then selected all images
- I copied all images to /usr/share/pixmaps skipping all existing images.
- I them logged-off and when I try to log back on in Gnome I get the following errors and then I'm returned to the login-screen:

-----start error----
[b]~/.xsession-errors:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "dennis"
/etc/gdm/Xsession: Beginning session setup...
gpg-agent[10796]: directory ' /home/dennis/.gnupg/private-keys-vl.d' created
** (gnome-session:10751): WARNING **: Uable to read ICE authority file: /home/dennis/.ICEauthority[/b]
-----end error----

When I  try to start a KDE session, I get the following error and are them returned to the login-screen:

-----start errors----
[b]There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list.
/home/dennis/.DCOPserver_laptop_0

Please check that the "dcopserver" program is running!

-----------

Will not save configuration.
Configuration file "/home/dennis/.kde/share/config/ksplashrc" not writable.
Configuration file "/home/dennis/.kde/share/config/kdeglobals" not writable.

Please contact your system administrator. 

----------

The following installation problem was detected while trying to start KDE:
No write access to '/home/dennis/.ICEauthority'.

---------

KDE is unable to start.
Could not start ksmserver. Check your installation.[/b]
-----end errors----

If I try to run Gnome-safe mode I'm returned straight back to the login-screen without being logged-in, I get no errors, so safe mode doesn't work either.
Xterm safe mode however does work.

Anyone know a solution?

---

### Post by maspro on 2005-05-13
*bumb*

---

### Post by arnieboy on 2005-05-13
maspro,
            I researched about your problem and found the following thread:
[http://www.linuxquestions.org/questions/archive/60/2005/04/1/254177](http://www.linuxquestions.org/questions/archive/60/2005/04/1/254177)
It seems that the only solution that has been found till now is to log in as root. Obviously that is not a permanent solution. However, you can try the things that some experts have suggested in the above thread and see if it works for you or not.
Good Luck!

---

### Post by arnieboy on 2005-05-13
and this one as well:
[http://www.linuxquestions.org/questions/archive/26/2003/12/2/122748](http://www.linuxquestions.org/questions/archive/26/2003/12/2/122748)

---

### Post by maspro on 2005-05-13
[QUOTE=arnieboy]and this one as well:
[http://www.linuxquestions.org/questions/archive/26/2003/12/2/122748](http://www.linuxquestions.org/questions/archive/26/2003/12/2/122748)[/QUOTE]
Thx for doing some research, I did some research myself but no luck. So I'm going to restore my back-up and I ain't going to copy any images to and from those specific directories listed in previous posts.  :smile: 

But it does remain strange that this only happens when I copy those images.  :-? 

Thx again.  :smile:

---

### Post by feight on 2005-10-19
I have a strange problem as well. The above-mentioned steps work for me, but not with the Human theme. I'm apparently in the minority for liking the earth-tones of the Human theme (although I wish there were a less rough-edged alternative). If I change themes to Clearlook the icons all appear, but if I switch back to Human, even after a restart... nothing.

EDIT: I think I know why, it looks like the problem is based upon the directories used by the theme; any suggestions on how to fix this problem universally or at least in the human theme? I noticed this isn't a problem in Breezy and has apparently been fixed, but breezy has been causing lots of strange problems for my java apps.

---

### Post by NeTo on 2005-10-19
You could try editing the /usr/share/icons/Human/index.theme file as Gianni Exile's described, as that file constains the icon information for the human theme.

---

### Post by feight on 2005-10-19
Sorry, I failed to mention that I did that already. I did indeed alter the folder to the command from Clearlooks to Human and put the crystalsvg,gnome in the line. I even tried taking it back out, switching to another theme, altering the file and changing back without luck. Even stranger was the fact that soon after making these changes gnome began to randomly and mysteriously fail and go to a nonresponsive black screen, other TTYs were unavailable for error messages.

Oh well, someone helped me figure out what I was doing wrong with my java apps in Breezy and I'm switching back so this is all moot for me, hopefully it will help others in some way though.

---

### Post by bugmenot on 2006-02-11
to solve all you .ICEauthority and .DCOPserver problems when logging in, login with root in the "Failsafe Terminal" session and do:

chmod 777 /home/your_user_name/.ICEauthority
chmod 777 /home/your_user_name/.DCOPserver

and try logging in again with gnome or kde

---

