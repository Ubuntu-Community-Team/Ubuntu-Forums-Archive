---
title: "SCID install failed"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by gigenieks on 2011-12-22
Hi guys once again need some help. :D

I am trying to install [SCID]("http://scid.sourceforge.net/index.html") software.

1st tried to do that via Ubuntu Software Center - the only thing which changed after (not 100% sure) is in Games there is new item called XBoard. ([What is XBoard?]("http://www.gnu.org/software/xboard/"))
When I try to lauch it - absolutely nothing happens!

O.K. - since easy method didn't work I had to try "hard" - compilation stuff (which I'm doing first time). 

So tar.bz2 file - [http://scid.sourceforge.net/download.html]("http://scid.sourceforge.net/download.html")

According to README and guys in #ubuntu channel I tried following: [http://paste.ubuntu.com/778900/](http://paste.ubuntu.com/778900/)

I got this error:
> src/misc.h:22:17: fatal error: tcl.h: No such file or directory
**compilation terminated**.

Also there is mentioned by author in README:
> 
On Unix-ish operating systems (such as Linux, Solaris, BSD, etc) you
should just be able to type "./configure" then "make" to compile the
programs. The configure script tries to determine the appropriate
Makefile settings for your computer. [B]If it is not successful,[COLOR="DarkRed"] you
may need to edit[/COLOR] the file "Makefile" [COLOR="Blue"]before[/COLOR] typing "make".[/B]


=> I have no clue what to edit or why....

As for README content it is here: [http://paste.ubuntu.com/778985/](http://paste.ubuntu.com/778985/)


The big question is how do we fix this issue? (I really need that software for improving my chess game) :confused:

---

### Post by Toz on 2011-12-22
SCID doesn't seem to create a menu item when you install it. Try running it from the command line:
```
scid
```
If it works and you want a menu item, create a desktop file:
```
gksu gedit /usr/share/applications/scid.desktop
```
...with the following content:
```
[Desktop Entry]
Name=Shane's Chess Information Database
Comment=Chess Information Database
Exec=scid
Icon=xboard
Terminal=false
Type=Application
Categories=GNOME;GTK;Game;BoardGame;
StartupNotify=true
X-Ubuntu-Gettext-Domain=gnome-games

```
...and save the file.

Xboard should work. Do you get any error messages when you run it from the command line:
```
xboard
```

You shouldn't need to compile anything.

---

### Post by gigenieks on 2011-12-22
Indeed SCID is installed and even working! As I tried with Application Finder search "scid" it didn't find anything I concluded that wasn't successful installation..

Anyway your second command didn't work - nothing happens. I type my password and thats all. (I'm using Xubuntu)

That desktop item would be really awesome. :)

This is what I got when I typed xboard in terminal:
```

gigenieks@juris-study-pc:~$ xboard
xboard: no fonts match pattern -*-helvetica-bold-r-normal--*-*-*-*-*-*-*-*

```
weird.

P.S. I dont remember installing XBoard. Did it install "together" with SCID? :confused:

---

### Post by Toz on 2011-12-22
> **gigenieks said:**
> Indeed SCID is installed and even working! As I tried with Application Finder search "scid" it didn't find anything I concluded that wasn't successful installation..

Anyway your second command didn't work - nothing happens. I type my password and thats all. (I'm using Xubuntu)
oops, sorry. Try this:
```
gksudo mousepad /usr/share/applications/scid.desktop
```
...then copy the contents into the file.

> That desktop item would be really awesome. :)

This is what I got when I typed xboard in terminal:
```

gigenieks@juris-study-pc:~$ xboard
xboard: no fonts match pattern -*-helvetica-bold-r-normal--*-*-*-*-*-*-*-*

```
weird.

P.S. I dont remember installing XBoard. Did it install "together" with SCID? :confused:
Try this:
```
sudo apt-get purge xboard && sudo apt-get install xboard
```

---

### Post by gigenieks on 2011-12-22
> **Toz said:**
> oops, sorry. Try this:
...then copy the contents into the file.

Did the job! :) Thanks.

> 
Try this:
```
sudo apt-get purge xboard && sudo apt-get install xboard
```
Still nothing happens when I click on XBoard. Whatever - SCID is working and that is what I needed thank you for your time! :)

---

