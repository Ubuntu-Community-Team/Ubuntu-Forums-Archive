---
title: "adding Blackbox 0.70 to gdm menu after compiling"
date: 2005-03-07
forum: Outdated Tutorials &amp; Tips
---

### Post by landotter on 2005-03-07
I compiled the new Blackbox and it was absolutely painless, but it didn't get added to gdm so after much googling, I found this to work:

create a file, /etc/X11/gdm/Sessions/Blackbox:

 ```
 #!/bin/sh
#
exec /usr/local/bin/blackbox
``` 

make it executable

create another file: 

/usr/share/xsessions/blackbox.desktop

```
 [ Desktop Entry]
Encoding=UTF-8
Name=BlackBox
Comment=Black and Boxy
Exec=/etc/X11/gdm/Sessions/Blackbox
Terminal=False
TryExec=blackbox
Type=Application

[Window Manager]
SessionManaged=true

``` 

restart x (ctrl alt backspace) and Blackbox should show up in gdm.

Then I opened /etc/X11/blackbox/blackbox-menu, edited it to my liking and saved in my home directory as .blackboxmenu.

To make blackbox use this menu I edited my .blackbox.rc file and changed the "session.menuFile" line:

session.menuFile:    /home/username/.blackboxmenu

I wanted some startup apps, but couldn't find a clean way to do this that wouldn't bork my Gnome or XFCE, so I made a shell script: 

 ```
#!/bin/sh
#
xscreensaver --quiet & 
gnome-volume-manager &
fbpanel -p default &
wmnd -I ppp0 &
wmweather -s kbna &
gnome-settings-daemon &
chbg -scenario .scenario &
wmix $
``` 


saved it as ~.blackboxstartup.sh

and added it to my blackbox menu

Now I can run a plain blackbox menu, or simply right click and run a whole gang of fanciness at once.

:D

I highly recommend fbpanel. It only takes around 2mb to run and has a windowlist, pager, clock, tray, and even launchers!

Check it out in this screenie:

[img]http://photos5.flickr.com/6169234_4d4be49270_o.jpg[/img]

---

### Post by bored2k on 2005-03-09
For some weird reason its not working for me  :-( 

I compiled it, and I can run it through Failsafe Terminal, but it does not show up on GDM  :oops: 

I tried twice and even copied/pasted from you're How-To .

Thoughts on where I could have made a mistake?


btw, i had to create the Sessions dir /etc/X11/gdm/Sessions

---

### Post by landotter on 2005-03-09
[QUOTE=bored2k]For some weird reason its not working for me  :-( 

I compiled it, and I can run it through Failsafe Terminal, but it does not show up on GDM  :oops: 

I tried twice and even copied/pasted from you're How-To .

Thoughts on where I could have made a mistake?[/QUOTE]
 Well, I'm a complete boob when it comes to this kind of stuff, but it does work for me with the provided scripts. I'm on Warty btw.

Did you restart X? Do a crl alt backspace, perhaps you just need GDM to restart to have it show up.

---

### Post by bored2k on 2005-03-09
[QUOTE=landotter]Well, I'm a complete boob when it comes to this kind of stuff, but it does work for me with the provided scripts. I'm on Warty btw.

Did you restart X? Do a crl alt backspace, perhaps you just need GDM to restart to have it show up.[/QUOTE]
 I restarted X, i even restarted the computer, and its not there, It installed correctly cuz i am able to run it in FS Terminal .
edit >> im listening to an mp3 on it thru xnest ... so it works :P

btw , also on warty .

---

### Post by landotter on 2005-03-09
[QUOTE=bored2k]I restarted X, i even restarted the computer, and its not there, It installed correctly cuz i am able to run it in FS Terminal .

btw , also on warty .[/QUOTE]

I'm at a loss.

did you make /etc/X11/gdm/Sessions/Blackbox executable by changing the permissions?

---

### Post by bored2k on 2005-03-09
[QUOTE=landotter]I'm at a loss.

did you make /etc/X11/gdm/Sessions/Blackbox executable by changing the permissions?[/QUOTE]
 I had to also make the Sessions directory.

> root@noir:/usr/share/xsessions # ls -l /etc/X11/gdm/Sessions/Blackbox
-rwxr-xr-x    1 root     root           42 2005-03-09 02:34 /etc/X11/gdm/Sessions/Blackbox


What else?

---

### Post by bored2k on 2005-03-09
> root@noir:/usr/share/xsessions # cat blackbox.desktop
 [ Desktop Entry]
Encoding=UTF-8
Name=BlackBox
Comment=Black and Boxy
Exec=/etc/X11/gdm/Sessions/Blackbox
Terminal=False
TryExec=blackbox
Type=Application

[Window Manager]
SessionManaged=true
root@noir:/usr/share/xsessions #

That's my file . With same permissions gnome and xfce one have

---

### Post by bored2k on 2005-03-09
> Then I opened /etc/X11/blackbox/blackbox-menu, edited it to my liking and saved in my home directory as .blackboxmenu.

Even tho i logged to it , I do not have blackbox dir., thus i dont have blackbox-menu.

---

### Post by landotter on 2005-03-09
[QUOTE=bored2k]Even tho i logged to it , I do not have blackbox dir., thus i dont have blackbox-menu.[/QUOTE]
 if you compiled blackbox successfully, you should have a /etc/X11/blackbox/blackbox-menu file. 

you can copy, edit, and save it where you like (~.blackboxmenu works for me) but you have to point ~.blackboxrc at it by editing that as well.

:P

Now running Gnome will be uber-impressive. It just works. LOL

---

### Post by bored2k on 2005-03-09
Dunno why it didnt show but thanks anyway, I'm just apt-getting fluxbox blackbox, though I will be getting 0.65 not 0.7 . I'm thinking of re-doing the operation after apt-get configures it correctly.

edit > Funny lol, even by doing apt-get blackbox fluxbox , flux appeared on GDM while blackbox didn't . 

Maybe it has something against me from the days I dumped it on Mandrake :-\

At least I can run it thru terminal, and get rid of the aterm screen by doing screen blackbox .


edit >  Now i noticed everything in correct place, so I just open flux from gdm and switch 2 blackbox . I still have to tamper both to see wich one I like the most .

---

### Post by bored2k on 2005-03-09
By the way sorry for starting you're thread with this crappy error because of my s2pid box (codenamed Noir) has a mind of its own and it does what it wants :S .

---

### Post by landotter on 2005-03-09
[QUOTE=bored2k]By the way sorry for starting you're thread with this crappy error because of my s2pid box (codenamed Noir) has a mind of its own and it does what it wants :S .[/QUOTE]
 no worries.

Be happy.

:)

---

### Post by chrisw on 2005-03-18
Hi There

OK, I think I found a couple of problems...... with the first script you might want to change the line:

[COLOR=DarkGreen]exec /usr/local/bin/blackbox[/COLOR]

to:

[COLOR=DarkGreen]exec /usr/bin/blackbox[/COLOR]

and with the second script, the first line of:

[COLOR=DarkGreen] [ Desktop Entry][/COLOR]

needs to be corrected by removing a space so that it reads:

[COLOR=DarkGreen] [Desktop Entry][/COLOR]

---

### Post by landotter on 2005-03-18
/usr/local/bin/blackbox if you compile it yourself, /usr/bin/blackbox if via apt-get. ;)

---

### Post by william_nbg on 2006-02-02
Got it installed up and running fine. Played with .xsession and realized it doesn't work that easy in Ubuntu. Found your thread and now am working on my bbstartup.sh and have one noob question:

What will: gnome-settings-daemon get me???


Thanks

---

