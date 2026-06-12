---
title: "Eclipse PHPEclipse xampp root"
date: 2005-12-25
forum: Programming Talk
---

### Post by u_b_u_&amp;_i_b_me on 2005-12-25
Firstly I have successfully installed Eclipse 3.1, PHP5, PHPEclipse and xampp in their appropriate directories.  However in order to start and stop xampp within PHPEclipse I need to either be a root user or use the sudo command.  Unfortunately, I can not execute a sudo command within the menu options in the PHPEclipse plugin to start and stop xampp.

In addition I have also uninstalled xampp and install Apache, MySQL and PHP through the Synaptic manager.  Again in order to control Apache, MySQL and PHP you have to be a root user.  However PHPEclipse in running under a non-root user and I need to be able to start, stop and control Apache, MySQL and/or PHP.

I have tried a number of things such as changing permission, etc..  Are there any ideas how to solve this problem?

The instruction at
[http://www.plog4u.org/index.php/Using_PHPEclipse:Installation:XAMPP_Example_Installation](http://www.plog4u.org/index.php/Using_PHPEclipse:Installation:XAMPP_Example_Installation)
are pretty good, however they focus more on Windows than Linux let alone Ubuntu (without a root user)


Thanks
ubu & i b me

---

### Post by geek.de.nz on 2006-02-12
[quote=u_b_u_&_i_b_me]Firstly I have successfully installed Eclipse 3.1, PHP5, ...

...

...

The instruction at
[http://www.plog4u.org/index.php/Using_PHPEclipse:Installation:XAMPP_Example_Installation]("http://www.plog4u.org/index.php/Using_PHPEclipse:Installation:XAMPP_Example_Installation")
are pretty good, however they focus more on Windows than Linux let alone Ubuntu (without a root user)


Thanks
ubu & i b me[/quote] 

Try [http://http://ubuntuforums.org/showthread.php?t=104905&highlight=phpeclipse]("http://http://ubuntuforums.org/showthread.php?t=104905&highlight=phpeclipse")
;)

---

### Post by SreckoMicic on 2006-04-01
I think that u can forget about starting xampp with buttons on php IDE. Just use classic comand.

---

### Post by Riddian on 2006-07-15
It can be done! Well at least this is a simple workaround I came up with anyway but it works none the less.

Just create two shell script, called something like xampp_start.sh and xampp_stop.sh.

In the start script enter:

```
#!/bin/bash
gksudo /opt/lampp/lampp start
```

For the stop script enter:

```
#!/bin/bash
gksudo /opt/lampp/lampp stop
```

You can do the same for all the other buttons if you find you need them.

---

### Post by ednark on 2008-07-11
A small tweak. Create only one extra file with the gksudo. In Eclipse you can now set the Location field to this one file and use the Arguments field to pass through directly to lampp as you would if you didn't use this file.


sudolampp.sh
```

#!/bin/bash
gksudo /opt/lampp/lampp $1

```

Location: /opt/lampp/sudolampp.sh
Arguments: start

Location: /opt/lampp/sudolampp.sh
Arguments: stop

Location: /opt/lampp/sudolampp.sh
Arguments: startapache

Location: /opt/lampp/sudolampp.sh
Arguments: startmysql

---

### Post by cecretnamezone on 2008-08-19
hello! I do everything as u say but I have a problem like this:"You need to start XAMPP as root!"->so how can i start it with root?

---

### Post by intheback on 2010-07-31
I'm literally just started using linux for my website development, and excuse me if this seems stupid, but i just put into terminal:

```
sudo chmod -R 777 /opt/lampp/htdocs/thedirectoythatineededpermissionschanged
```

and that changed the permissions of the folder. After that, Eclipse let me use it no problem.

Sorry if this is stupid, but it seemed to work for me.

---

