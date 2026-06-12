---
title: "Enlightened XFCE: Or, How to allow your XFCE to achieve Satori"
date: 2005-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Iandefor on 2005-12-09
_**Enlightened XFCE4**_
    
 ____________________________________________
|1.16.06: Added a screenshot of EXCE running E17  |
|1.15.06: I added a fix which adds the Debian menu.|
|___________________________________________|

After reading poofyhairguy's excellent [Enlightened GNOME]("http://www.ubuntuforums.org/showthread.php?t=54476&") howto, I got the idea 
of attempting to apply Enlightenment as the window manager for XFCE. I sat
on the idea after a few unsuccessful attempts; however, after reading karma's 
thread "XFCE with Enlightenment?" I decided to give it a go again. Mhancoc7 
and I both came up with individual ways of applying E as the window manager 
for XFCE. In this howto, I'm going to cover the various ways of getting Enlightened XFCE 
that we came up with.
    
_**I. Getting Enlightenment**_
    
This is the primary step, of course. To obtain Enlightenment, you've got a couple options; there 
are currently two versions available. First, you have available Enlightenment DR16, 
which is fairly lightweight, looks good, and is currently more stable than the other 
version, E17. E17 is heavier, looks pretty fine, but I've had bad luck running it. 
My suggestion is to go with DR16 for the time being; it crashes less often. To 
get DR16, ensure you have the Universe repository enabled .Open up Synaptic, 
find the package named "enlightenment" and choose to install it. Getting E17 
is slightly more complicated, but still easily achieved; to do so, may I suggest 
[ Aboe's Howto]("http://www.ubuntuforums.org/showthread.php?t=79155&")? Enlightenment also has several great utilities available for it, which 
are all available via Shadoi's repository (Covered in Aboe's howto).
    
_**II. Autosta****rt**_
    
Mhancoc7 came up with this one. He's a genius for coming up with it; it's simpler 
than both my methods and works better than the next one I came up with, which 
is why I put it first. This one uses the stock XFCE setup, but makes a few slight
changes. Open up a terminal and type in
    
**cd ~/Desktop**
    
Which will bring you to the Desktop directory. once there, type in
    
**mkdir Auto****start**
    
The directory Autostart is used by XFCE and runs any executables it finds in there 
on start up; hence the name. Once this has been completed, enter the directory 
by entering into the terminal
    
**cd Autostart**
    
    and create a new file. It doesn't particularly matter what it's called, since XFCE 
will run *any* executable file in the Autostart directory. For this example, I chose
to call it starte. Put the following into the file:
    
**#****!/bin****/s****h**
    
    **enlightenment &**
    
    and save it. Make it an executable script with the following:
    
    **chmod 0775 starte**
    
    Now, enter the following command into the terminal:
    
    **killall xfwm4 ****xfdesktop**

    Which will kill the XFCE window manager and the XFCE desktop manager; these 
both interfere with the proper functioning of Enlightenment. Log out and save 
session. Enjoy your newly Enlightened XFCE!
    
    _**III. ****Siddarth****a**_
    
    I made this one up as a stopgap for until I could get Enlightenment working properly 
with XFCE. Really, this is the worst of all the methods listed, but it is the next 
simplest, so will be given the honour of being listed as the second. This method 
completely eschews the session manager and starts up each component individually; 
this has the drawback of giving you a new session each time you login and it 
disables the logout button on the XFCE panel menu (Since that goes through
 the XFCE session manager). 
     First, make a new file and put the following in it:
    
    **#!/bin****/sh**
    
    **xfce4-panel ****&**
    **xfce4-ico****nbox &**
    **enlightenment**
    
    Save it with a name that you like. For this example, I called mine buddha.
    Enter
the following:
    
    **chmod 0775 budd****ha**
    
    Move your script to the folder /usr/bin with the following command:
    
**sudo mv ****buddha**** /usr/bin**
    
It will ask you for your password; this is necessary to move it to that folder.
                Now, create a new file in the folder /usr/share/xsessions. It doesn't particularly 
matter the name, but it does need to end in .desktop. Put the following in that
file:

    [LEFT]**[Desktop Entry]**[/LEFT]
                                                [LEFT]**Encoding=UTF-8**[/LEFT]
                                                [LEFT]**Name=Enlightened X****FCE****4**[/LEFT]
                                                [LEFT]**Comment=**[/LEFT]
                                                [LEFT]**Exec=buddha**[/LEFT]
                                                [LEFT]**Icon=**[/LEFT]
                                                [LEFT]**Type=Application**[/LEFT]
                                                
    [LEFT]Save the file, log out, and at the login screen, check under "Sessions" for a new 
session called Enlightened XFCE4. Select it and run it. Do a little dance and enjoy
the newfound wisdom of your computer :smile:.[/LEFT]
                                                
    [LEFT]_**IV. ****Poison Ivy**_[/LEFT]
                                                
                          [LEFT]This is the last, and most complicated, method available. I've listed it last because 
it is the most complex. I've named it Poison Ivy for no good reason other than it seemed 
appropriate. The only merit over the Autostart method is that it's faster. [/LEFT]
                                                [LEFT]First, 
enter a different desktop environment/window manager than XFCE4. I suggest 
Windowmaker for those on old hardware. Open up a terminal and type in [/LEFT]
                                                
                          [LEFT]**rm ****~/.cache/****sessions/*******

 Which will completely remove all the session data for XFCE4. Now, log in to the XFCE4 
environment, and open up the "run program" dialog. Enter into it 
[B]
killall xfwm4
[/B]
and as soon as you can verify xfwm4 is no longer running (I'd suggest running 
this in a terminal; when the terminal window goes crazy, type in exit), save session 
and log out. Now, log back into your alternative DE. Navigate to the directory 
~/.cache/sessions in whatever way pleases you most. It should be empty save 
for a single file. The one on my computer was named "xfce4-session-brownie:0" 
Whatever file you get should at least *look* something like that. If it doesn't, cross 
your fingers and hope for the best. Open up the file for editing. it should look 
like this:

 [B][Session: Default]
[/B]
**Client0_UserId=ian**[/LEFT]
                                                [LEFT]**Client****0****_ClientId=10af783ad2000113376999500000128550002**[/LEFT]
                                                [LEFT]**Client****0****_Hostname=unix/brownie**[/LEFT]
                                                [LEFT]**Client****0****_CloneCommand=xftaskbar4,--sm-client-id,10af783ad2000113376999500000128550002,--display,:0.0Client1_CurrentDirectory=/home/ian**[/LEFT]
                                                [LEFT]**Client****0****_Priority=30**[/LEFT]
                                                [LEFT]**Client****0****_Program=xftaskbar4**[/LEFT]
                                                [LEFT]**Client****0****_RestartCommand=xftaskbar4,--sm-client-id,10af783ad2000113376999500000128550002,--display,:0.0**

 **Client1_UserId=ian**[/LEFT]
                                                [LEFT]**Client****1****_ClientId=10af783ad2000113376999500000128550001**[/LEFT]
                                                [LEFT]**Client****1****_Hostname=unix/brownie**[/LEFT]
                                                [LEFT]**Client****1****_CloneCommand=xfce4-panel,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client****1****_CurrentDirectory=/home/ian**[/LEFT]
                                                [LEFT]**Client****1****_Priority=40**[/LEFT]
                                                [LEFT]**Client****1****_Program=xfce4-panel**[/LEFT]
                                                [LEFT]**Client****1****_RestartCommand=xfce4-panel,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client****1****_UserId=ian**[/LEFT]
                                                
    [LEFT]**Count=****2**[/LEFT]
                                                [LEFT]**LegacyCount=0**[/LEFT]
                                                
    [LEFT]Keep in mind your file shouldn't look *exac**t**l**y* like this; just close. Copy and paste 
the last segment of "Client[num]_[something]" groups to right past itself. What 
you should get is this (The first section has been omitted):

**Client1_UserId=ian**[/LEFT]
                                                [LEFT]**Client1_ClientId=10af783ad200011337699950000012855  0001**[/LEFT]
                                                [LEFT]**Client1_Hostname=unix/brownie**[/LEFT]
                                                [LEFT]**Client1_CloneCommand=xfce4-panel,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client1_CurrentDirectory=/home/ian**[/LEFT]
                                                [LEFT]**Client1_Priority=40**[/LEFT]
                                                [LEFT]**Client1_Program=xfce4-panel**[/LEFT]
                                                [LEFT]**Client1_RestartCommand=xfce4-panel,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client1_UserId=ian**[/LEFT]
                                                
    [LEFT]**Client1_UserId=ian**[/LEFT]
                                                [LEFT]**Client1_ClientId=10af783ad200011337699950000012855  0001**[/LEFT]
                                                [LEFT]**Client1_Hostname=unix/brownie**[/LEFT]
                                                [LEFT]**Client1_CloneCommand=xfce4-panel,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client1_CurrentDirectory=/home/ian**[/LEFT]
                                                [LEFT]**Client1_Priority=40**[/LEFT]
                                                [LEFT]**Client1_Program=xfce4-panel**[/LEFT]
                                                [LEFT]**Client1_RestartCommand=xfce4-panel,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client1_UserId=ian**[/LEFT]
                                                
    [LEFT]**Count=2**[/LEFT]
                                                [LEFT]**LegacyCount=0**[/LEFT]
                                                
            [LEFT]With the new section, go through and change every instance of "Client1_[something]" 
to "Client2_[something]". On the line that says "Client2_CloneCommand=xfce4-panel, [stuff]" 
change 
it to read "Client2_CloneCommand=enlightenment, [stuff]", change the line that 
reads "Client2_Program=xfce4-panel"  to "Client2_Program=enlightenment", and
change the line that reads "Client2_RestartCommand=xfce4-panel, [stuff]"
to 
"Client2_RestartCommand=enlightenment, [stuff]". Update "count=2" to count="3" 
(Or whatever the appropriate number is).[/LEFT]
                                                
    [LEFT] If you've done all that, the final file should look like

 [B][Session: Default]
[/B]
**Client0_UserId=ian**[/LEFT]
                                                [LEFT]**Client0_ClientId=10af783ad200011337699950000012855  0002**[/LEFT]
                                                [LEFT]**Client0_Hostname=unix/brownie**[/LEFT]
                                                [LEFT]**Client0_CloneCommand=xftaskbar4,--sm-client-id,10af783ad2000113376999500000128550002,--display,:0.0Client1_CurrentDirectory=/home/ian**[/LEFT]
                                                [LEFT]**Client0_Priority=30**[/LEFT]
                                                [LEFT]**Client0_Program=xftaskbar4**[/LEFT]
                                                [LEFT]**Client0_RestartCommand=xftaskbar4,--sm-client-id,10af783ad2000113376999500000128550002,--display,:0.0**[/LEFT]
                                                
    [LEFT]**Client1_UserId=ian**[/LEFT]
                                                [LEFT]**Client1_ClientId=10af783ad200011337699950000012855  0001**[/LEFT]
                                                [LEFT]**Client1_Hostname=unix/brownie**[/LEFT]
                                                [LEFT]**Client1_CloneCommand=xfce4-panel,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client1_CurrentDirectory=/home/ian**[/LEFT]
                                                [LEFT]**Client1_Priority=40**[/LEFT]
                                                [LEFT]**Client1_Program=xfce4-panel**[/LEFT]
                                                [LEFT]**Client1_RestartCommand=xfce4-panel,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client1_UserId=ian**[/LEFT]
                                                
    [LEFT]**Client****2****_UserId=ian**[/LEFT]
                                                [LEFT]**Client****2****_ClientId=10af783ad2000113376999500000128550001**[/LEFT]
                                                [LEFT]**Client****2****_Hostname=unix/brownie**[/LEFT]
                                                [LEFT]**Client****2****_CloneCommand=****enlightenment****,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client****2****_CurrentDirectory=/home/ian**[/LEFT]
                                                [LEFT]**Client****2****_Priority=40**[/LEFT]
                                                [LEFT]**Client****2_****Program=****enlightenment**[/LEFT]
                                                [LEFT]**Client****2_****RestartCommand=****enlightenment****,--sm-client-id,10af783ad2000113376999500000128550001,--display,:0.0**[/LEFT]
                                                [LEFT]**Client****2****_UserId=ian**[/LEFT]
                                                
    [LEFT]**Count=****3**[/LEFT]
                                                [LEFT]**LegacyCount=0**[/LEFT]
                                                
    [LEFT]If you've got all that, save the file, and try logging into XFCE. If all went well, 
it should stop and load Enlightenment somewhere in the process of starting up. 
Enjoy your new, Unburdened XFCE![/LEFT]
                                                [U]
**V. Removing the Splash Screen**[/U] 

This is an optional step. I've gotten a few complaints that on startup, the splash screen is
interrupted by the Enlightenment startup screen, which just looks kinda bad. To fix this, go 
to the XFCE settings dialog, and open up the splash screen settings dialog. Set the 
splash screen to "none" and then close. You're set!

_**VI. Getting Debian Menus**_

Some people had issues getting the Debian menus working under Enlightenment, 
but here's a fix, care of superprotta. Thanks, superprotta! Open up a terminal and run:

**sudo aptitude install menu && update-menus**

open up the following file as root using your preferred text editor: /usr/share/enlightenment/config/menus.cfg.
Look around for a line that looks similar to this:
[B]
BEGIN_NEW_FILE_MENU("DEBIAN_MENU","ROOT","/var/lib/enlightenment/debian.menu")

[/B]Change it to point to where your debian.menu file is- if it isn't in /var/lib/enlightenment, 
then it's probably in ~/.enlightenment/menus_debian/. After changing it, it should look like 

**BEGIN_NEW_FILE_MENU("DEBIAN_MENU","ROOT","/home/<username>/.enlightenment/menus_debian/debian.menu****")**

Regenerate the menu by going to Maintenance--> Regenerate Menus under the Enlightenment 
menu. Hope this works!

NOTE: Constructive criticism of this howto is encouraged, but only on the conditions 
that if you find you dislike something or find an area confusing, point it out politely 
and perhaps propose a solution. It's no good to me to have you to say that it sucks 
without saying why, and there's no profit in being rude.

---

### Post by poofyhairguy on 2005-12-11
Brilliant!

---

### Post by kairu0 on 2005-12-11
Screenshots, anyone?

---

### Post by Iandefor on 2005-12-11
added a screenshot.

> Brilliant! You're only saying that because I complemented your howto in the first sentence... jk

---

### Post by tseliot on 2005-12-11
1) Could you open gnome-system-monitor and tell me how much the "user memory" is (as soon as you have booted)?
2) Could you post the settings of your menu of enlightenment (so that I can access all those applications), please?
3) Is there a way to see the battery status of my laptop (in xfce there is)?

Thanks in advance

P.S. Nice howto!

---

### Post by kairu0 on 2005-12-11
Brilliant!

...and I am only saying that because my post is in the screenshot. ;)

---

### Post by Iandefor on 2005-12-11
> **tseliot]1) Could you open gnome-system-monitor and tell me how much the "user memory" is (as soon as you have booted)?
2) Could you post the settings of your menu of enlightenment (so that I can access all those applications), please?
3) Is there a way to see the battery status of my laptop (in xfce there is)?

P.S. Nice howto![/quote] 
!) I know this isn't right after bootup, but after being logged in for about 20 minutes, I get a user memory reading of about 39.4 MB (Keep in mind that I only have 64 MB of RAM said:**
> 
Brilliant!

...and I am only saying that because my post is in the screenshot. Yeah, I know your type.. *glower* :-D

---

### Post by sapo on 2005-12-11
The Autostart way worked, but the thing that i hat in enlightenment is still bugging me.. is there a way to put the opened windows in the taskbar? my taskbar is there, but the windows just dont go there.. the xfce tray is working, but the taskbar dont!

btw.. thanx for the howto, my desktop now is kinda pretty :D

here a screenshot:
[[IMG]http://img118.imageshack.us/img118/5245/enlightenedxfce8lm.th.jpg[/IMG]](http://img118.imageshack.us/my.php?image=enlightenedxfce8lm.jpg)

---

### Post by Iandefor on 2005-12-11
[quote=sapo]The Autostart way worked, but the thing that i hat in enlightenment is still bugging me.. is there a way to put the opened windows in the taskbar? my taskbar is there, but the windows just dont go there.. the xfce tray is working, but the taskbar dont!

btw.. thanx for the howto, my desktop now is kinda pretty :D[/quote] That's the first I've heard of it. You could use the Iconbox for XFCE. To do so, run ```
xfce4-iconbox
``` and if that still doesn't work, Enlightenment has an iconbox. To get it, middle-click (Or do whatever it is you have to do to get the menu in the screenshot) and go to the Desktop menu. Select "Create New Iconbox" Hope this helped!

---

### Post by sapo on 2005-12-11
[QUOTE=Iandefor]That's the first I've heard of it. You could use the Iconbox for XFCE. To do so, run ```
xfce4-iconbox
``` and if that still doesn't work, Enlightenment has an iconbox. To get it, middle-click (Or do whatever it is you have to do to get the menu in the screenshot) and go to the Desktop menu. Select "Create New Iconbox" Hope this helped![/QUOTE]
none worked, i was already using the iconbox, but i dont like that :(, btw thanx.

---

### Post by tseliot on 2005-12-11
> **Iandefor]!) I know this isn't right after bootup, but after being logged in for about 20 minutes, I get a user memory reading of about 39.4 MB (Keep in mind that I only have 64 MB of RAM said:**
> 
You can run Ubuntu with 64MB of RAM? Impressive.

[QUOTE=Iandefor]2) Sorry if I'm being thick, but for the second, can you explain a litte more what you're looking for?
I mean: when you click with the mouse pointer in order to access the menu with all your application you seem (according to the screenshot) to have the Debian menu available. I can't see it in my Enlightenment.
Is there a configuration file (of the menu) I can use? If that exists, could you post me yours?

---

### Post by sapo on 2005-12-11
[QUOTE=tseliot]You can run Ubuntu with 64MB of RAM? Impressive.


I mean: when you click with the mouse pointer in order to access the menu with all your application you seem (according to the screenshot) to have the Debian menu available. I can't see it in my Enlightenment.
Is there a configuration file (of the menu) I can use? If that exists, could you post me yours?[/QUOTE]
here you go:


[http://sourceforge.net/projects/e17genmenu](http://sourceforge.net/projects/e17genmenu)

Download the tar.gz, install it and run e17genmenu -g from the terminal, after that you will have you deb menu in the right click, like mine here:

[[IMG]http://img118.imageshack.us/img118/8489/enlightenedxfcemenu1kr.th.jpg[/IMG]](http://img118.imageshack.us/my.php?image=enlightenedxfcemenu1kr.jpg)

enjoy :)

---

### Post by tseliot on 2005-12-11
[QUOTE=sapo]here you go:


[http://sourceforge.net/projects/e17genmenu](http://sourceforge.net/projects/e17genmenu)

Download the tar.gz, install it and run e17genmenu -g from the terminal, after that you will have you deb menu in the right click, like mine here:

[[IMG]http://img118.imageshack.us/img118/8489/enlightenedxfcemenu1kr.th.jpg[/IMG]](http://img118.imageshack.us/my.php?image=enlightenedxfcemenu1kr.jpg)

enjoy :)[/QUOTE]
Thanks but do you know something like that for E16 (which is more stable than E17)?

---

### Post by Iandefor on 2005-12-11
[quote=tseliot]Thanks but do you know something like that for E16 (which is more stable than E17)?[/quote] It's accessible using the Enlightenment menu. Can you post a screenshot so we can see your Enlightenment menu as it is?

> 
You can run Ubuntu with 64MB of RAM? Impressive. Yeah; my next computer going to have 1 GB of RAM. Go figure :)

---

### Post by tseliot on 2005-12-11
[QUOTE=Iandefor]It's accessible using the Enlightenment menu. Can you post a screenshot so we can see your Enlightenment menu as it is?

 Yeah; my next computer going to have 1 GB of RAM. Go figure :)[/QUOTE]
Here's my screenshot:
[http://img367.imageshack.us/my.php?image=desktopenlfce12fc.png]("http://img367.imageshack.us/my.php?image=desktopenlfce12fc.png")

EDIT: fixed

---

### Post by sapo on 2005-12-11
[QUOTE=tseliot]Here's my screenshot:
[[IMG]http://img514.imageshack.us/img514/1228/desktopenlfce1mr.th.png[/IMG]](http://img514.imageshack.us/my.php?image=desktopenlfce1mr.png)[/QUOTE]
your link is kinda broken, it goes to the imageshack.us index :(

---

### Post by tseliot on 2005-12-11
[QUOTE=sapo]your link is kinda broken, it goes to the imageshack.us index :([/QUOTE]
it should work now

---

### Post by Iandefor on 2005-12-11
That's not the Enlightenment menu. If you have a mouse with a scroll-wheel, try clicking it. That's what I did to get that menu.

---

### Post by tseliot on 2005-12-11
[QUOTE=Iandefor]That's not the Enlightenment menu. If you have a mouse with a scroll-wheel, try clicking it. That's what I did to get that menu.[/QUOTE]
Ok, here's the right one:
[http://img476.imageshack.us/my.php?image=enlitalb4uf.png]("http://img476.imageshack.us/my.php?image=enlitalb4uf.png")

Under user application list I've got only 9 applications

P.S. Of course Debian menu is installed but I can't use it from Enlightenment menu

---

### Post by Iandefor on 2005-12-11
[quote=tseliot]Ok, here's the right one:
[http://img476.imageshack.us/my.php?image=enlitalb4uf.png]("http://img476.imageshack.us/my.php?image=enlitalb4uf.png")

Under user application list I've got only 9 applications

P.S. Of course Debian menu is installed but I can't use it from Enlightenment menu[/quote] That's really quite weird. I'm at a loss as to how to help you. Sorry. The Debian menu just showed up one day after I installed XFCE; as to how it got there, I don't know :-D.

---

### Post by tseliot on 2005-12-11
[QUOTE=Iandefor]That's really quite weird. I'm at a loss as to how to help you. Sorry. The Debian menu just showed up one day after I installed XFCE; as to how it got there, I don't know :-D.[/QUOTE]
Ok, no problem. I'll let you know if I find a solution

---

### Post by tseliot on 2005-12-11
Can you post your "./enlightenment/file.menu" and "./enlightenment/gnome.menu" and "./enlightenment/userapps.menu" , please?

---

### Post by Iandefor on 2005-12-11
[quote=tseliot]Can you post your "./enlightenment/file.menu" and "./enlightenment/gnome.menu" and "./enlightenment/userapps.menu" , please?[/quote]

~/.enlightenment/file.menu:
```

"User Menus"
"User Application list" NULL menu "user_apps.menu"
"KDE" NULL menu "kde.menu"
"GNOME" NULL menu "gnome.menu"
"GNOME User Menu" NULL menu "gnome_user.menu"
"Enlightenment Epplets" NULL menu "epplets.menu"
"Restart Enlightenment" NULL exec "/usr/bin/eesh -e 'restart'"
"Log Out" NULL exec "/usr/bin/eesh -e 'exit'"
```

~/.enlightenment/gnome.menu:
```

"GNOME Menu"
"Multimedia" "" menu "/home/ian/.enlightenment/menus_gnome/Multimedia.menu"
```

~/.enlightenment/user_apps.menu [userapps.menu doesn't exist]:
```
"User Application List"
"Eterm" NULL exec "Eterm"
"XTerm" NULL exec "xterm"
"RXVT" NULL exec "rxvt"
"KTerm" NULL exec "kterm"
"Gnome Terminal" NULL exec "gnome-terminal"
"Netscape" NULL exec "netscape"
"TkRat" NULL exec "tkrat"
"Netscape Mail" NULL exec "netscape -mail -no-about-splash"
"Balsa" NULL exec "balsa"
"Exmh" NULL exec "exmh"
"Electric Eyes" NULL exec "eeyes"
"The GIMP" NULL exec "gimp"
"XV" NULL exec "xv"
"GQView" NULL exec "gqview"
"XMag" NULL exec "xmag"
"XawTV" NULL exec "xawtv"
"Imlib Settings" NULL exec "imlib_config"
"X-Chat" NULL exec "xchat"
"XMan" NULL exec "xman"
"TkMan" NULL exec "tkman"
"GnomeICU" NULL exec "gnomeicu -a"
"eMusic" NULL exec "emusic"
"X11Amp" NULL exec "x11amp"
"XMMS" NULL exec "xmms"
"FreeAmp" NULL exec "freeamp"
"Civilization" NULL exec "civctp"
"Myth 2" NULL exec "myth2"
```

Don't think this is gonna be of much help, though.

---

### Post by karma 23 on 2005-12-11
I'd like to thank everyone, especially Iandefor for this HOWTO.  When I started the original thread about XFCE + Enlightenment, I was originally going to experiment myself and post my findings, but Iandefor and the others did that for me and went as far as creating and contributing to this HOWTO.

Anyway, I did some comparisons between EXFCE (Enlightened XFCE) and Elive (a Debian-based distro using Enlightenment as default), and I must say that Elive is zippier than EXFCE, though not as easy to use.  Both XFCE and Elive only require less than 120 Mhz and 64 MB RAM to run (though XFCE recommends 128 MB).  I'd actually recommend Elive over EXFCE for raw speed but if you're unfamiliar and uncomfortable with Debian, EXFCE is better.  Not only that, you'd have a harder time finding support for Elive since their forums aren't nearly as populated as ours here.

Has anyone else tried Elive?  If so, what were your thoughts?  Iandefor, I believe I've found something else that runs on weaker hardware and still looks awesome.  If you haven't already, please see how Elive runs on your 64 MB machine and post your comments if you have time.  I'd love to hear what you have to say.

---

### Post by Iandefor on 2005-12-11
Hmm.. I hadn't given Elive much thought. I'll try it out tomorrow (Seeing as how I've got finals to study for, final projects to work on, and a bunch of homework I gotta atch up on tonight).

---

### Post by tseliot on 2005-12-12
[QUOTE=Iandefor]~/.enlightenment/file.menu:
```

"User Menus"
"User Application list" NULL menu "user_apps.menu"
"KDE" NULL menu "kde.menu"
"GNOME" NULL menu "gnome.menu"
"GNOME User Menu" NULL menu "gnome_user.menu"
"Enlightenment Epplets" NULL menu "epplets.menu"
"Restart Enlightenment" NULL exec "/usr/bin/eesh -e 'restart'"
"Log Out" NULL exec "/usr/bin/eesh -e 'exit'"
```

~/.enlightenment/gnome.menu:
```

"GNOME Menu"
"Multimedia" "" menu "/home/ian/.enlightenment/menus_gnome/Multimedia.menu"
```

~/.enlightenment/user_apps.menu [userapps.menu doesn't exist]:
```
"User Application List"
"Eterm" NULL exec "Eterm"
"XTerm" NULL exec "xterm"
"RXVT" NULL exec "rxvt"
"KTerm" NULL exec "kterm"
"Gnome Terminal" NULL exec "gnome-terminal"
"Netscape" NULL exec "netscape"
"TkRat" NULL exec "tkrat"
"Netscape Mail" NULL exec "netscape -mail -no-about-splash"
"Balsa" NULL exec "balsa"
"Exmh" NULL exec "exmh"
"Electric Eyes" NULL exec "eeyes"
"The GIMP" NULL exec "gimp"
"XV" NULL exec "xv"
"GQView" NULL exec "gqview"
"XMag" NULL exec "xmag"
"XawTV" NULL exec "xawtv"
"Imlib Settings" NULL exec "imlib_config"
"X-Chat" NULL exec "xchat"
"XMan" NULL exec "xman"
"TkMan" NULL exec "tkman"
"GnomeICU" NULL exec "gnomeicu -a"
"eMusic" NULL exec "emusic"
"X11Amp" NULL exec "x11amp"
"XMMS" NULL exec "xmms"
"FreeAmp" NULL exec "freeamp"
"Civilization" NULL exec "civctp"
"Myth 2" NULL exec "myth2"
```

Don't think this is gonna be of much help, though.[/QUOTE]
Can you post your "gnome_user.menu"?

Thanks

---

### Post by Iandefor on 2005-12-12
[quote=tseliot]Can you post your "gnome_user.menu"?[/quote]

No files by that name on *this* hard drive. Interesting.

---

### Post by Iandefor on 2005-12-14
Sorry. Took me longer than I thought it would take
to get a copy of Elive. I'm typing this post on it 
right now, and my first impression is: awesome!
Were it not for the fact that it doesn't get my 
display settings right (It's running at 640x480 on a 
1024x768 monitor), I might consider using Elive on a 
more regular basis.

---

### Post by karma 23 on 2005-12-14
I'm actually having the same problem with Elive; the resolution is a little off, but I'm sure I can work around it.  To me, it's faster, more beautiful, and has all the video codecs I need to view online videos.  With EXFCE I had a hard time running Automatix, and it got annoying.  With Elive, everything I need just works.  I also like the fact that Enlightenment has numbers to prove its superior speed, and also only requires less than 120 MHz and 64 MB RAM.  Though XFCE has the same requirements, Elive just ran faster for me.

I'm still doing tests between EXFCE and Elive and will start coming up with numbers.  My goal is to find the least resource hungry and fastest distro/combo and I must say that, at the moment, Elive is it.  On top of that, E is pleasing to the eye.  The creator of E ran tests, and numbers placed XFCE as the slowest of WM's.  I'm planning to test XFCE vs. EXFCE vs. Elive to see which is really the fastest.

Please keep your comments coming, as you seem to know what you're doing .

---

### Post by Iandefor on 2005-12-14
[quote=karma 23]I'm actually having the same problem with Elive; the resolution is a little off, but I'm sure I can work around it.  To me, it's faster, more beautiful, and has all the video codecs I need to view online videos.  With EXFCE I had a hard time running Automatix, and it got annoying.  With Elive, everything I need just works.  I also like the fact that Enlightenment has numbers to prove its superior speed, and also only requires less than 120 MHz and 64 MB RAM.  Though XFCE has the same requirements, Elive just ran faster for me.&#12288;I'm still doing tests between EXFCE and Elive and will start coming up with numbers.  My goal is to find the least resource hungry and fastest distro/combo and I must say that, at the moment, Elive is it.  On top of that, E is pleasing to the eye.  The creator of E ran tests, and numbers placed XFCE as the slowest of WM's.  I'm planning to test XFCE vs. EXFCE vs. Elive to see which is really the fastest.&#12288;Please keep your comments coming, as you seem to know what you're doing .[/quote]

I used E17 for less than ten minutes with Elive and I fell in love with it.
It has all the eyecandy that more modern DE's can currently only use with some pretty ugly hacks (compositing, anyone?) and does it faster. Elive was built from the ground up to be a lightweight desktop system, and it does it pretty well. Enlightened XFCE simply cannot compete with E17's beauty and light step, IMHO. Such a shame it can't get my resolution right nor can E17 run properly on my computer as of the time of this writing; I hit a segmentation fault in six minutes of using it. I'm going to stick to EXFCE for the time being because I just don't like DR16 on it's own and E17 doesn't like me.

I look forward to seeing what numbers you come up with. Also: it might be interesting to test Metacity and Kwin alongside E/XFCE and Elive. My thought is that people more used to those WM's might find the tests more relevant if their own WM's were compared to E/XFCE and Elive.
But I'm not pushing anything here; just a suggestion.

---

### Post by karma 23 on 2005-12-14
I see what you mean about Elive.  I just can't wait until it's officially released with E17 AND an American keyboard (don't know if you noticed it's not there).  As far as resolution, you can set it by pressing F4 when it asks you to choose a keyboard.  But, of course, if it's crashing on you, then wait for the official release with E17.

Other WM's have been tested also on the E page, and I believe they're way too behind to even compare to E/XFCE and E17.  Not only that, they require at least 128 MB of RAM.  Again, my goal is to find a WM/DE that will promptly run on 64 MB and about 100 Mhz.  Both XFCE and E fit the bill so it's really a head to head battle between them two.  I realize Fluxbox and IceWM also require low memory but their speeds don't compare.  

I personally believe E17 is THE DE/WM for low end machines.  It's the "fastest" (don't have numbers yet), requires pretty much just a motherboard that turns on, and is beautiful.  E/XFCE is close but, to me, is difficult to have just the way I want it.  I have a hard time installing Automatix or all the codecs needed to view videos online, and OpenOffice isn't included like Elive.  What I recommend now for stable usage is E/XFCE but for the more adventurous ones out there, check out Elive!

---

### Post by Iandefor on 2005-12-14
[quote=karma 23]I see what you mean about Elive.  I just can't wait until it's officially released with E17 AND an American keyboard (don't know if you noticed it's not there).  As far as resolution, you can set it by pressing F4 when it asks you to choose a keyboard.  But, of course, if it's crashing on you, then wait for the official release with E17.&#12288;Other WM's have been tested also on the E page, and I believe they're way too behind to even compare to E/XFCE and E17.  Not only that, they require at least 128 MB of RAM.  Again, my goal is to find a WM/DE that will promptly run on 64 MB and about 100 Mhz.  Both XFCE and E fit the bill so it's really a head to head battle between them two.  I realize Fluxbox and IceWM also require low memory but their speeds don't compare.  

I personally believe E17 is THE DE/WM for low end machines.  It's the "fastest" (don't have numbers yet), requires pretty much just a motherboard that turns on, and is beautiful.  E/XFCE is close but, to me, is difficult to have just the way I want it.  I have a hard time installing Automatix or all the codecs needed to view videos online, and OpenOffice isn't included like Elive.  What I recommend now for stable usage is E/XFCE but for the more adventurous ones out there, check out Elive![/quote]

I was never asked to choose a keyboard layout. Weird. I most definitely am waiting for E17 to become stable. I've had the same experience with Fluxbox/icewm- low footprint just doesn't guarantee speed. I also agree that E17 is "THE DE/WM" for legacy hardware. However, keep in mind that Elive is an entire distribution, whereas EXFCE is just a DE with identity issues :), so it's not really fair to expect EXFCE to come with an office suite of some kind.

---

### Post by kairu0 on 2005-12-14
[QUOTE=Iandefor]I also agree that E17 is "THE DE/WM" for legacy hardware.[/QUOTE]

I agree that E17 is a very good WM for legacy hardware, but I struggle to call Enlightenment a DE yet.

Granted, this all depends on your definition of "DE." For me, XFCE is a DE. Gnome is a DE. Enlightened XFCE is a DE. Enlightenment is a WM.

---

### Post by Iandefor on 2005-12-14
[quote=kairu0]I agree that E17 is a very good WM for legacy hardware, but I struggle to call Enlightenment a DE yet.

Granted, this all depends on your definition of "DE." For me, XFCE is a DE. Gnome is a DE. Enlightened XFCE is a DE. Enlightenment is a WM.[/quote]

My definition of DE is pretty broad; so long as I can easily launch my favorite applications and have a systemtray/taskbar, I'll call it a DE without complaint :). I can do all that with E17, ergo, by my definition, it's a DE. What definition do you use for DE? Oh, and BTW, I "accidentally" killed your slug caught in a vat of molasses... too bad he never worried about his sodium intake :-D </irrelevant to rest of thread>

---

### Post by kairu0 on 2005-12-15
[QUOTE=Iandefor]My definition of DE is pretty broad; so long as I can easily launch my favorite applications and have a systemtray/taskbar, I'll call it a DE without complaint :). I can do all that with E17, ergo, by my definition, it's a DE. What definition do you use for DE? Oh, and BTW, I "accidentally" killed your slug caught in a vat of molasses... too bad he never worried about his sodium intake :-D </irrelevant to rest of thread>[/QUOTE]

You killed Charles?? I'll never forgive you. That was the best slug on this side of the Pacific. Your trout is next! Hear me!?! Your trout is on the list! (completely irrelevant to rest of thread)

Anyway, for my definition of DE: I take for granted that my desktop will have a window manager, program menus, a window list to see what's running, a system tray (or WindowMaker-stylie dock), a file manager, and a desktop icon manager. This is the minimum amount of elements for me. The best combination of these elements that I've found so far in Ubuntu is Gnome + xfwm. Your trout is mine, Iandefor!

---

### Post by Iandefor on 2005-12-15
[quote=kairu0]You killed Charles?? I'll never forgive you. That was the best slug on this side of the Pacific. Your trout is next! Hear me!?! Your trout is on the list! (completely irrelevant to rest of thread)

Anyway, for my definition of DE: I take for granted that my desktop will have a window manager, program menus, a window list to see what's running, a system tray (or WindowMaker-stylie dock), a file manager, and a desktop icon manager. This is the minimum amount of elements for me. The best combination of these elements that I've found so far in Ubuntu is Gnome + xfwm. Your trout is mine, Iandefor![/quote]

**Gasps in shock** How dare you threaten Reuben? As though he had ever done anything to you... Kill my computer, kill the chef who cooked the unnamed high-sodium dish that killed Charles, kill Bill, even, but not poor Reuben! </Completely irrelevant to rest of thread>

Anywho... all those elements you listed as necessary, I believe, are actually all available for Enlightenment in one form or another. You get the Enlightenment Window Manager, the User Applications menu (And the Debian menu if you're lucky), and a window list (for me, it's [ctl]+[middle click]) with Enlightenment. You can also get, from other DE's, a panel with systemtray (xfce-panel), a filemanager (Rox-filer, and if you don't like that, then you can try Thunar), and a desktop icon manager (idesk or Rox-pinboard). However, you're right that E17, on it's own, (Using your definition) isn't really a DE.

---

### Post by kairu0 on 2005-12-15
Reuben is as good as gone. And if the coppers find out about dis, I send Jimmy to whack youz, too! (symbolically relevant to thread)

OK. Point taken that the Enlightenment window manager can be combined with other elements to make a (good) DE. So, a Enlightenment DE is possible.

But let me derail from the main point ("God forbid!") by saying that I am also a fan of integration. KDE is beautifully-integrated and if it was half as good at handling multiple locales and keyboard layouts as Gnome is, I would probably use it.

Gnome and xfwm integrate into a good DE and the beauty of it is that if I change my WM to xfwm, the rest of the DE (Nautilus, Gnome Volume Manager, etc.) will work without any extra configuration. Configuring XFCE to use Enlightenment, Enlightenment to use Debian menus, the menus to include Thunar, etc. is a lot of configuration. For the time being, I prefer the Gnome "it just works" approach. It just feels more congruent.

---

### Post by karma 23 on 2005-12-15
[QUOTE=kairu0]Gnome and xfwm integrate into a good DE and the beauty of it is that if I change my WM to xfwm, the rest of the DE (Nautilus, Gnome Volume Manager, etc.) will work without any extra configuration. Configuring XFCE to use Enlightenment, Enlightenment to use Debian menus, the menus to include Thunar, etc. is a lot of configuration. For the time being, I prefer the Gnome "it just works" approach. It just feels more congruent.[/QUOTE]

Well you must have a powerful system to be able to run that.  Of course, if everyone had high end machines, KDE or GNOME would be the easiest way to go.  Some people, like myself, just want speed though and I find that Elive gives me just that.  I have a P4 2.4 with 1G RAM and see no need to run GNOME or KDE because, being a newbie, I don't see a need to use their extra features.  XFCE and Elive get the job done for me and they require less resources at the same time.  Maybe as I become a more seasoned Linux user I'll find the need for what GNOME and KDE have to offer but, for now, it's E/XFCE or Elive all the way!

UPDATE: I ran some tests and E/XFCE is, indeed, slower than Elive.  Numbers are coming up!

---

### Post by kairu0 on 2005-12-15
[QUOTE=karma 23]Some people, like myself, just want speed though and I find that Elive gives me just that.[/QUOTE]

All the more power to you. You prefer Elive, I prefer Gnome+xfwm. There are many possible DE's in Linux and I'm glad that we can both find something that suits our preferences.

---

### Post by karma 23 on 2005-12-15
[QUOTE=kairu0]All the more power to you. You prefer Elive, I prefer Gnome+xfwm. There are many possible DE's in Linux and I'm glad that we can both find something that suits our preferences.[/QUOTE]

Exactly!

I'd like to ask you why you use XFWM instead of the default Metacity in GNOME.  Is there something that XFWM does that Metacity can't do?  Or is there something that it does better?

---

### Post by kairu0 on 2005-12-15
[QUOTE=karma 23]I'd like to ask you why you use XFWM instead of the default Metacity in GNOME.  Is there something that XFWM does that Metacity can't do?  Or is there something that it does better?[/QUOTE]

XFWM is less resource-intensive, let's me define the buttons that go on my titlebar (without editing theme files), has better themes, and just feels more responsive. Now that I think of it, it's more of a speed tweak than a feature addition.

So, what are your reasons for liking Elive so much? :)

---

### Post by Iandefor on 2005-12-15
> But let me derail from the main point ("God forbid!") by saying that I am also a fan of integration. KDE is beautifully-integrated and if it was half as good at handling multiple locales and keyboard layouts as Gnome is, I would probably use it.

Gnome and xfwm integrate into a good DE and the beauty of it is that if I change my WM to xfwm, the rest of the DE (Nautilus, Gnome Volume Manager, etc.) will work without any extra configuration. Configuring XFCE to use Enlightenment, Enlightenment to use Debian menus, the menus to include Thunar, etc. is a lot of configuration. For the time being, I prefer the Gnome "it just works" approach. It just feels more congruent.

I'm also a fan of integration, and I agree that if there's such a thing as "integration" in EXFCE, it's probably hidiing in a small corner somewhere out of everyone's sight. I definitely miss the congruence available using a DE like GNOME or KDE, but my computer simply cannot run them properly; It's too old, which is partially why I spend my time mixing elements of light-weight WM/DE's; so far, I've not found any lighter or more attriactive mix than E17 on it's own. Pity it won't run without hitting segmentation faults on my computer.

You killed Reuben's family! He just barely managed to escape with his life, and is now fleeing to Austria, for fear of you! Oh, the humanity! When will it end?

---

### Post by karma 23 on 2005-12-15
[QUOTE=kairu0]So, what are your reasons for liking Elive so much? :)[/QUOTE]

Simply put, Elive just works right out of the box.  And besides, all I really do is use my computer for internet purposes and Elive comes with all codecs I need for streaming videos.  I originally tried Ubuntu (GNOME) but it was so hard to get  win32 codecs, so I downloaded Automatix and it was fine, I guess.  Then I was introduced to lightweight desktops...XFCE, to be exact, and gave it a go.  It had most of the features I needed and required less resources so I kept it, but couldn't run Automatix to get everything I needed.  Then I came across Rasterman's WM speed tests which "proved" that E was the fastest so I wanted to know if combining XFCE and E was possible, and Iandefor came up with this HOWTO.  After playing with E/EXFCE, I tried Elive which was more lightweight and did pretty much all of what XFCE did for me, except for a couple taskbars here and there.  

I'm still very new to Linux and the setup I have is more of a logical approach.  Since I'm not yet familiar with everything, I base the setup I choose on what I read online and benchmark tests, but I'm sure that as I get more experienced, like you guys, I may find that different components from different DE's/WM's combined work best.  

Tell me this though, have you tried XFCE?  You talk about XFWM being less resource intensive so it tells me that it is somewhat important to you.  XFCE is known to be the lightest, so why not choose it?

---

### Post by LaSSarD on 2005-12-15
wonderful!!

the autostart method worked perfect with me :)
i just had to set xfce splash to none in order to see only the enlightenment splash screen, not both :P

now i have a perfect desktop... functional, nice and quick. thanks a lot ;D

---

### Post by kairu0 on 2005-12-15
> **Iandefor]I definitely miss the congruence available using a DE like GNOME or KDE, but my computer simply cannot run them properly said:**
> 
Okay, so we are working in different computer environments. Your situation is different from mine in that you must run a very tight ship. In that case, E17 is a good choice, I think. I'm tempted to use E17 instead of xfwm from time to time and maybe some day I will. It certainly looks nice for its small footprint!

I have a new machine, but I also like to be efficient with my resources. That's why I pulled metacity for xfwm.

[QUOTE=Iandefor]You killed Reuben's family! He just barely managed to escape with his life, and is now fleeing to Austria, for fear of you! Oh, the humanity! When will it end?

Austria? Oh reeealllllyy. Then I've got news for you! Right now, Reuben is hanging in an aquarium above a vat of sharks in a Chicago warehouse! And, let me tell YOU, these sharks are itchin' to fix Reuben up like you fixed up my favorite slug! UWA HAH HAH HAH

---

### Post by Iandefor on 2005-12-16
> Okay, so we are working in different computer environments. Your situation is different from mine in that you must run a very tight ship. In that case, E17 is a good choice, I think. I'm tempted to use E17 instead of xfwm from time to time and maybe some day I will. It certainly looks nice for its small footprint! I have a new machine, but I also like to be efficient with my resources. That's why I pulled metacity for xfwm. Austria? Oh reeealllllyy. Then I've got news for you! Right now, Reuben is hanging in an aquarium above a vat of sharks in a Chicago warehouse! And, let me tell YOU, these sharks are itchin' to fix Reuben up like you fixed up my favorite slug! UWA HAH HAH HAH

Yeah, we *are* working in different environments... for the moment. I'm going to be getting a new computer for the new year. But now, I'm beginning to wonder at the wisdom of using the full GNOME desktop (or even XFWM+GNOME) because of the resource draw. I might just go with E17 once it comes out of development, because I've gotten into this minimalist mindset with all this playing with E. 

Reuben! Nooo...! he was the best dancer in the state! Darn you to heck, I'm going after your dancing monkey! Even now, I've got assassins preparing on the way to "Liquidate" the poor monkey... muahaha... revenge is so sweet.

> 
wonderful!!
the autostart method worked perfect with me :smile:
i just had to set xfce splash to none in order to see only the enlightenment splash screen, not both :P now i have a perfect desktop... functional, nice and quick. thanks a lot ;D Good suggestion. I hadn't seen it as much of a problem, but I'll add that to the original howto soon. Thanks for the praise :)

---

### Post by kairu0 on 2005-12-17
[QUOTE=Iandefor]But now, I'm beginning to wonder at the wisdom of using the full GNOME desktop (or even XFWM+GNOME) because of the resource draw. I might just go with E17 once it comes out of development, because I've gotten into this minimalist mindset with all this playing with E. [/QUOTE]

Okay. So, you have a point that Gnome is memory hoggish (for the time being.) I hope that all of that talk about working to reduce memory usage materializes into a notable difference in a near release.

I think I have a point that Enlightenment is not a complete DE (as in with a file manager, volume manager, icon handler, etc.) without adding extra stuff.

Do you have anything against a pure XFCE configuration (xfce + xfwm)? It's a complete desktop, yet it's not a memory hog. Why do you prefer Enlightenment to it? (and by the way, I'm not suggesting there's anything wrong with Enlightenment. I just want your opinion.)

---

### Post by Iandefor on 2005-12-17
[quote=kairu0] Do you have anything against a pure XFCE configuration (xfce + xfwm)? It's a complete desktop, yet it's not a memory hog. Why do you prefer Enlightenment to it? (and by the way, I'm not suggesting there's anything wrong with Enlightenment. I just want your opinion.)[/quote]

Not really. I just like to experiment, and E is pretty novel for me right now.
I'm also pleased with the alacrity of E as compared to XFCE on legacy hardware such as mine. Enlightened XFCE is just striking a balance between usability and light weight. I do, however, prefer Enlightenment to XFCE because it's incredibly configurable, but it doesn't get in the way of having a clean interface.

---

### Post by karma 23 on 2005-12-17
[QUOTE=kairu0]Do you have anything against a pure XFCE configuration (xfce + xfwm)? It's a complete desktop, yet it's not a memory hog. Why do you prefer Enlightenment to it? (and by the way, I'm not suggesting there's anything wrong with Enlightenment. I just want your opinion.)[/QUOTE]

Let's also not forget the eye candy that E provides at such a small footprint!  Also, I think you may have missed my question to you in my earlier post, why do you use GNOME/XFWM instead of XFCE?

---

### Post by kairu0 on 2005-12-17
[QUOTE=Iandefor]Not really. I just like to experiment, and E is pretty novel for me right now.
I'm also pleased with the alacrity of E as compared to XFCE on legacy hardware such as mine. Enlightened XFCE is just striking a balance between usability and light weight. I do, however, prefer Enlightenment to XFCE because it's incredibly configurable, but it doesn't get in the way of having a clean interface.[/QUOTE]

Does Enlightenment perform that much better on older, legacy hardware than XFCE? I don't have any old machines, so I can't check.

[QUOTE=karma 23]Let's also not forget the eye candy that E provides at such a small footprint! Also, I think you may have missed my question to you in my earlier post, why do you use GNOME/XFWM instead of XFCE?
[/QUOTE]

In post #41 I said why I like xfwm more than metacity. Were you asking why I liked Gnome/XFWM more than XFCE/XFWM?

Well, I have two reasons. One is that the Gnome panel has better plugins. For example, the XFCE keyboard selector plugin didn't work with my Japanese layout until I manually patched it. Also, the XFCE mixer plugin is really clumsy and easy to miss with the mouse. (I change the volume all the time.)

My other reason is that I like Gnome's Applications, Places, and System menu. I use all three menus frequently and I navigate them more quickly than XFCE's program menu.

---

### Post by Iandefor on 2005-12-17
>  Does Enlightenment perform that much better on older, legacy hardware than XFCE? I don't have any old machines, so I can't check.

It's a dramatic difference on my hardware.

---

### Post by kairu0 on 2005-12-17
Exactly what are the specs for your machine?

---

### Post by karma 23 on 2005-12-17
[QUOTE=kairu0]Does Enlightenment perform that much better on older, legacy hardware than XFCE? I don't have any old machines, so I can't check.[/QUOTE]

I'll second what Iandefor said.  You could also try Enlightened GNOME since you're so used to the way GNOME works.  I did some tests and, on "powerful" systems, Enlightened GNOME is just as fast as Enlightened XFCE.  The only thing is you need better hardware.  For legacy hardware, though, E/EXFCE beats E/GNOME.

[QUOTE=kairu0]In post #41 I said why I like xfwm more than metacity. Were you asking why I liked Gnome/XFWM more than XFCE/XFWM?

Well, I have two reasons. One is that the Gnome panel has better plugins. For example, the XFCE keyboard selector plugin didn't work with my Japanese layout until I manually patched it. Also, the XFCE mixer plugin is really clumsy and easy to miss with the mouse. (I change the volume all the time.)

My other reason is that I like Gnome's Applications, Places, and System menu. I use all three menus frequently and I navigate them more quickly than XFCE's program menu.[/QUOTE]

Yes, I was asking why you liked GNOME/XFWM better than XFCE, and I can see those are good reasons.

---

### Post by Iandefor on 2005-12-17
[quote=kairu0]Exactly what are the specs for your machine?[/quote]

An AMD Duron rated at 700 mhz and 64 MB RAM are the two specs I know of that are relevant to speed.

I guess there's nothing like legacy hardware to test the efficiency of code :-D.

---

### Post by kairu0 on 2005-12-17
[QUOTE=Iandefor]An AMD Duron rated at 700 mhz and 64 MB RAM are the two specs I know of that are relevant to speed.

I guess there's nothing like legacy hardware to test the efficiency of code :-D.[/QUOTE]

You have some willpower, man. I would have "shelled out" the 25$ for another 64MB of RAM. :)

---

### Post by kairu0 on 2005-12-17
[QUOTE=karma 23]I'll second what Iandefor said.  You could also try Enlightened GNOME since you're so used to the way GNOME works.[/QUOTE]

Can I do that and keep my Nautilus menus when I right-click on the desktop? I use it all the time.

---

### Post by Iandefor on 2005-12-17
[quote=kairu0]You have some willpower, man. I would have "shelled out" the 25$ for another 64MB of RAM. :)[/quote] I'd forgotten all about this computer up until last January. At that point, I'd long since lost the hardware specifications. I'dve looked it up online, but it was built by one of the local computer stores, and I can't recall whatever silly name they gave it. It's not like I can call up and ask them for the spec sheet on a computer whose name I forgot, that they probably stopped supporting three years ago. lol, I'd have happily shelled out $25 for another 64MB, but at this point, I'm just gonna drop ~$500 for a decent computer when I get the money.

---

### Post by kairu0 on 2005-12-18
Okay. Gnome panel crashed on me today twice when my CPU load got to about 95%. So, I am now living a XFCE+XFWM desktop.

I like it so far. In particular, it just feels many more super fasterest.

---

### Post by Iandefor on 2005-12-18
What's the name of that window decoration, and where did you get your filthy little claws on it :-D? I really like it.

---

### Post by kairu0 on 2005-12-18
[QUOTE=Iandefor]What's the name of that window decoration, and where did you get your filthy little claws on it :-D? I really like it.[/QUOTE]

It's BlendedSmallDoubleRound and I got my filthy little claws on it at:

[http://www.xfce-look.org/content/show.php?content=28805](http://www.xfce-look.org/content/show.php?content=28805)

---

### Post by karma 23 on 2005-12-18
[QUOTE=kairu0]Can I do that and keep my Nautilus menus when I right-click on the desktop? I use it all the time.[/QUOTE]

I haven't been able to do that, but then again I haven't really experimented since my destop of choice is E/EXFCE at the moment (Elive started to crash on me).

[QUOTE=kairu0]Okay. Gnome panel crashed on me today twice when my CPU load got to about 95%. So, I am now living a XFCE+XFWM desktop.

I like it so far. In particular, it just feels many more super fasterest.[/QUOTE]

Have you enlightened your XFCE yet?  It'll feel even more super duper fasterests.

---

### Post by kairu0 on 2005-12-18
[QUOTE=karma 23]Have you enlightened your XFCE yet?  It'll feel even more super duper fasterests.[/QUOTE]

Actually, yes! I tried it yesterday. It was a nice breather to have a beautiful desktop again.

However, I got frustrated and came back to xfwm. So, I am running xfce right now.

Enlightenment, was very fast. The drop shadow module was genius. There were a few things that made it difficult to use, though:

[LIST=1]
[*]The right-click menu on the Desktop was useless to me. It didn't load my applications automatically, like Gnome and XFCE.
[*]Choosing my own background image from a jpeg file was too much work. (I quickly get tired of my wallpaper and change it at least 3 times a week.)
[*]It crashed on me. (XFWM has never crashed on my machine.)
[*]There aren't very many themes for it yet.
[*]The menu editor tool (from the eutils package) either wasn't functional yet or I couldn't figure out how to use it.
[*]*The most important* I opened a site in Firefox that maximized the browser window to cover the screen. I wanted to make the window virtually-shorter, but I couldn't for the life of me do it. There are no handles at the top of the window for vertical resizing and the bottom handles were off the screen. If anyone knows how I could have solved this, I'd like to know.
[/LIST]

Of course, E17 is still in development, and I'm sure that many of these things will get ironed out before it is finalized.

---

### Post by Iandefor on 2005-12-20
For that last one (This is more a tip for other people, really), you can right-click the titlebar, go to the "Window Size" menu, then select whichever dimension you want to adjust (be it height or width) and, from the relevent sub-menu, select "absolute max-height toggle" which will resize it to the size of the full screen. Really, this howto is more suited towards people who have older hardware and want to keep system stress low. It's not necessary for someone who has actually modern hardware.

---

### Post by kairu0 on 2005-12-20
Oh. Thanks. I read that menu up and down but didn't see the option for some reason. If I try Enlightenment again, I'll remember to try that.

I wouldn't necessarily say that the HOWTO is only for people will old hardware. Well, your wrote it and so I'm not gonna re-define it, but for powerusers and the resource-conscious it's pretty useful as well, I think.

---

### Post by Iandefor on 2005-12-20
> I wouldn't necessarily say that the HOWTO is only for people will old hardware. Well, your wrote it and so I'm not gonna re-define it, but for powerusers and the resource-conscious it's pretty useful as well, I think. Good point.

---

### Post by superprotta on 2006-01-15
hi..i had the same problem as tseliot with debian menus but i think i found a solution...at least it worked for me.
I had to open file /usr/share/enlightenment/config/menus.cfg and edit this line:
```
BEGIN_NEW_FILE_MENU("DEBIAN_MENU","ROOT","/var/lib/enlightenment/debian.menu")
``` 
and change the path were debian.menu is located wich , in my case, was  ```
/home/<username>/.enlightenment/menus_debian/debian.menu
```
Then i had to save changes, right-click on the desktop (or whatever you use to get the enlightenment menu) ->Maintenance->Regenerate Menus
I hope this helped

---

### Post by Iandefor on 2006-01-16
[quote=superprotta]hi..i had the same problem as tseliot with debian menus but i think i found a solution...at least it worked for me.
I had to open file /usr/share/enlightenment/config/menus.cfg and edit this line:
```
BEGIN_NEW_FILE_MENU("DEBIAN_MENU","ROOT","/var/lib/enlightenment/debian.menu")
``` 
and change the path were debian.menu is located wich , in my case, was ```
/home/<username>/.enlightenment/menus_debian/debian.menu
``` Then i had to save changes, right-click on the desktop (or whatever you use to get the enlightenment menu) ->Maintenance->Regenerate Menus
I hope this helped[/quote] Excellent. Will add to main guide.

---

### Post by superprotta on 2006-01-16
sorry i forgot a step i did in order to have the debian.menu file in /home/<username>/.enlightenment/menus_debian directory.
I did :
```
sudo apt-get install menu
update-menus
```
and then i edited the /usr/share/enlightenment/config/menus.cfg file as described in the post above. Sorry for the confusion but i struggled a lot with enlightenment menus so i forgot the step i had taken..

---

### Post by Iandefor on 2006-01-16
[quote=superprotta]sorry i forgot a step i did in order to have the debian.menu file in /home/<username>/.enlightenment/menus_debian directory.
I did :
```
sudo apt-get install menu
update-menus
``` and then i edited the /usr/share/enlightenment/config/menus.cfg file as described in the post above. Sorry for the confusion but i struggled a lot with enlightenment menus so i forgot the step i had taken..[/quote] Excellent. Fixed.

---

### Post by capink on 2007-01-17
I've found a way to easily change xfce WM and filemanager. I used it to change to openbox as WM and pcmanfm as filemanager. i dont know if this method will work with enlightenmet as i have not installed it yet. Anyway here it is:

- Delete any saved sessions: 

```
rm ~/.cache/sessions/*
```

- Copy xfce4-session global config file to your home directory

```
cp /etc/xdg/xfce4-session/xfce4-session.rc ~/.config/xfce4-session/xfce4-session.rc
```

- Edit the file you have just copied:

```
mousepad ~/.config/xfce4-session/xfce4-session.rc
```

replace the parts that read:

```
Client0_Command=xfwm4
Client0_PerScreen=False
Client1_Command=xfce4-panel
Client1_PerScreen=False
Client2_Command=Thunar,--daemon
Client2_PerScreen=False
Client3_Command=xfdesktop
Client3_PerScreen=False
```

with:

```
Client0_Command=openbox
Client0_PerScreen=False
Client1_Command=xfce4-panel
Client1_PerScreen=False
Client2_Command=pcmanfm
Client2_PerScreen=False
Client3_Command=xfdesktop
Client3_PerScreen=False
```

- Add the following line under [General]:

```
[General]
SaveOnExit=false
```

- Save and exit

- Logout, you should see the box saying "save sessions for future logins" unchecked. if not, uncheck it and press logout.

- Login and choose change session and choose xfce4

N.B this will work only if you have both openbox and pcmanfm installed. if not install them first before doing any of the above steps

I am new to linux. So use this method at your own risk. Feel free to correct me if anything is wrong.

---

