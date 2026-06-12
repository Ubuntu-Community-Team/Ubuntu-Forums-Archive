---
title: "[SOLVED] Amarok won't start, please help"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by jlbr on 2008-10-10
I installed Amarok a couple of weeks ago, it was working perfectly, I was loving it as a matter of fact. This morning I get up and the thing won't start, I uninstalled it and installed it again using Synaptic Package Manager, the thing still won't work. I took a screenshot of the error window.

I tried doing what the error window said, to no avail...

Any ideas anybody?

Thanks.

---

### Post by Pro-reason on 2008-10-10
The instructions in the dialogue are generic Linux instructions, non suitable for Ubuntu.  Whenever you see instructions to enter “su -c *[COLOR="Silver"]"some command"[/COLOR]*”, type “sudo *[COLOR="Silver"]some command[/COLOR]*” instead.

No promises that the instructions will work though, of course.

General advice: if a program doesn't start up properly, try starting it from a terminal instead.  That way, there will be some text output that you can copy and paste on to the forums, for us to help you more.

---

### Post by jlbr on 2008-10-10
Hi pro-reason,

OK, I will try and do that as soon as I get home (working now) :-)

---

### Post by jlbr on 2008-10-10
> juanluis@juanluis-laptop:~$ amarok
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/juanluis/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/juanluis/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809be28 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809be28 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QPainter::begin: Cannot paint null pixmap


OK, this is what i get when i try to run amarok from a terminal window, any ideas??

Could this be a memory issue? my disk is pretty full and I have noticed some pretty strange behavior in other applications such as Firefox and openoffice...

---

### Post by nowshining on 2008-10-10
try running it as root sudo amarok - does it work??

---

### Post by SteveNorman on 2008-10-10
If you have low ram loading the libraries would be a problem if you have a bunch of songs. typing ```
free
``` at the terminal will give you a memory report.

Try and remove it via synaptic and post the results of a search for amarok

The search:

```
$ sudo updatedb
$ locate amarok 
```

If you removed all the of amarock you shouldnt get anything,,and this search will tell you if there are leftover files. If you dont get anything in the search you should restart the desktop (ctrl-alt-backspace) and then reinstall amarock.

---

### Post by Pro-reason on 2008-10-10
What happened when you tried the commands it suggested?

---

### Post by taladan on 2008-10-10
might also want to check:

```
ps -ef|grep amarok
```

I know sometimes Amarok & evolution (don't know why just these two) hang in memory and won't allow another instance to start.  if it's in memory still you can kill it and try opening it.

Probably won't work, but worth a shot ;)

Tal

---

### Post by jlbr on 2008-10-11
Thanks to everybody who gave me hints. OK I got it solved, I did as SteveNorman said, I went, uninstalled all components, rebooted, then installed back again, BUT it was a memory issue as well, I freed some RAM and some hard disk space as well and now it works fine, it takes a long time to start and load my library but it works :)

Thanks again!

---

### Post by SteveNorman on 2008-10-11
sweet

---

