---
title: "How to Force Remove a package (bandwidthd)"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by Antonorsi on 2012-02-25
Hello, I tried to install "bandiwdth' from their page bandwidthd.sourceforge.net/ but in the middle of the installation it gave me an error and now I can't either remove it o reinstall it.

This is what happens if I do sudo dpkg --force-all -P bandwidthd

carlosf@CarlosF-HP:~$ sudo dpkg --force-all -P bandwidthd
[sudo] password for carlosf: 
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 180101 files and directories currently installed.)
Removing bandwidthd ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing bandwidthd (--purge):
 subprocess installed pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bandwidthd

help?

---

### Post by HeroOfCanton on 2012-02-25
> **Antonorsi said:**
> Hello, I tried to install "bandiwdth' from their page bandwidthd.sourceforge.net/ but in the middle of the installation it gave me an error and now I can't either remove it o reinstall it.

This is what happens if I do sudo dpkg --force-all -P bandwidthd

carlosf@CarlosF-HP:~$ sudo dpkg --force-all -P bandwidthd
[sudo] password for carlosf: 
dpkg: warning: overriding problem because --force enabled:
 [SIZE=3][B]Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.[/B][/SIZE]
(Reading database ... 180101 files and directories currently installed.)
Removing bandwidthd ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing bandwidthd (--purge):
 subprocess installed pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bandwidthd

help?

Did you try reinstalling first like the error message suggested? You seem to be doing it correctly.

---

### Post by Antonorsi on 2012-02-26
Yep, I tried to (well, I think that I tried haha)

LONG post, sorry

**aptdcon --reinstall bandwidthd**
```


The following package will be upgraded (1):                                     
  bandwidthd
The following package will be reinstalled (1):
  bandwidthd
After this operation, 86.0 kB of additional disk space will be used.
Do you want to continue [Y/n]?y
Preconfiguring packages ...                                                     
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Selecting previously deselected package bandwidthd.
(Reading database ... 180102 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20090917-4.1_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-4.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-4.1_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an err[-]  50% Cleaning up Run[+] 100% Failed                                                                 
ERROR: Package operation failed
The installation or removal of a software package failed.

installArchives() failed: Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Selecting previously deselected package bandwidthd.
(Reading database ... 180102 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20090917-4.1_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-4.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-4.1_i386.deb
Error in function: 
dpkg: error processing bandwidthd (--configure):
 [B]Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.[/B]

```
:confused:

---

### Post by audiomick on 2012-02-26
> **Antonorsi said:**
> 
LONG post, sorry

There is a button above the posting window marked with a hash
#

click on that and it will give you a set of code tags. Put output like that between those, and it will appear in a nice box with a scroll bar on the side.

If you want to be as fussy as I am ;) , you can add them to your existing post by clicking on the "edit" button on your post, and selecting "go advanced". Select the text you want to have between the tags, then click on the # button.

---

### Post by Antonorsi on 2012-02-28
So, nobody?

---

### Post by matt_symes on 2012-02-28
Hi

Open a terminal and type

```
sudo touch /usr/share/doc/bandwidthd/bandwidthd.conf
```

This will create an empty file that may get rid of the first error.

For the second error, type this into a terminal and post back the output using copy and paste.

```
sed -n '19p' /etc/init.d/bandwidthd
```

Kind regards

---

### Post by Antonorsi on 2012-03-07
```
carlosf@CarlosF-HP:~$ sed -n '19p' /etc/init.d/bandwidthd
function checkconfig () {

```

---

### Post by Antonorsi on 2012-03-08
Anyone?

---

### Post by matt_symes on 2012-03-09
Hi

Press ALT + F2 together. Type 

```
gksudo gedit /etc/init.d/bandwidthd
```

Scroll down to line 19 and edit it so it looks like this

```
function checkconfig 
{
```

Save the file.

Kind regards

---

### Post by Antonorsi on 2012-03-16
With ALT+F2 didnt do anything, so I tried from the teminal and this is what happened:

```

carlosf@CarlosF-HP:~$ gksudo /etc/init.d/bandwidthd

(gksudo:19067): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:19067): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:19067): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:19067): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

---

### Post by raja.genupula on 2012-03-16
[http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line](http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line)

EDIT : its always better to start new thread for your own issues .

---

### Post by matt_symes on 2012-03-16
Hi

You need to open the file in gedit.

```
gksudo gedit /etc/init.d/bandwidthd
```

Then look for that line and change it.

Kind regards

---

### Post by Antonorsi on 2012-03-21
Thank you all for your time, it worked!

:)

---

