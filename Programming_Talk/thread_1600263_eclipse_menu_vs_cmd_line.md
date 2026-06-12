---
title: "eclipse menu vs cmd line"
date: 2010-10-18
forum: Programming Talk
---

### Post by pjmlmas on 2010-10-18
When I am on command line, I can run
eclipse &

everything works fine (hello world etc.)

When I attempt to create a menu item to point to eclipse and run, I receive the following:

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/opt/eclipse/jre/bin/java
java in your current PATH

What would be my next step to get eclipse to launch as menu item?
bashrc not being picked up?

---

### Post by PartickThistle on 2010-10-19
A couple of things;

Make sure your .bashrc is in the right place and is spelt correctly.

It should be in your home folder and be a dot-file - so /home/pjmlmas/.bashrc

It should also contain at least this;

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

You'll want to add the path to your JRE. 

Can post the results of 

$ echo $PATH


Thanks

---

### Post by pjmlmas on 2010-10-19
Maybe this will make it clearer (Probably it is how I am setting up menu item)

/usr/share/applications$ cat myeclipse.desktop 
[Desktop Entry]
Encoding=UTF-8
Name=MyEclipse
Comment=MyEclipse Ganymede IDE
Exec=/usr/local/bin/eclipse
Icon=/opt/eclipse/eclipse-icon-clean.svg
Terminal=false
Type=Application
Categories=GNOME;Application;Programming;
StartupNotify=True


cat /usr/local/bin/eclipse
#!/bin/sh
export ECLIPSE_HOME="/opt/eclipse"
$ECLIPSE_HOME/eclipse $*

which eclipse
/usr/local/bin/eclipse

path has to be fine, otherwise nothing would be working at all?

---

