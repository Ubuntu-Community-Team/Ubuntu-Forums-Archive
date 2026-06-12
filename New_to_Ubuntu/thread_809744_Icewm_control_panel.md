---
title: "Icewm control panel"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-27
Hi everybody.
How can i install and use (a tutorial would be nice) Icewm control panel?
Thanks in advance.

---

### Post by sayakb on 2008-05-27
Check these out:

[http://www.scribd.com/doc/289012/IceWM-FAQ-and-Howto](http://www.scribd.com/doc/289012/IceWM-FAQ-and-Howto)
[http://www.phrozensmoke.com/projects/icewmcp/](http://www.phrozensmoke.com/projects/icewmcp/)

---

### Post by cristo-father on 2008-05-27
> **LinuxIsInnovation said:**
> Check these out:

[http://www.scribd.com/doc/289012/IceWM-FAQ-and-Howto](http://www.scribd.com/doc/289012/IceWM-FAQ-and-Howto)
[http://www.phrozensmoke.com/projects/icewmcp/](http://www.phrozensmoke.com/projects/icewmcp/)
Thanks for the info but i don't know how to install the file from the download. Can anyone please tell me.
Thanks for the help.

---

### Post by eriqjaffe on 2008-05-27
> **cristo-father said:**
> Thanks for the info but i don't know how to install the file from the download. Can anyone please tell me.
Thanks for the help.[http://www.phrozensmoke.com/projects/icewmcp/installation.php](http://www.phrozensmoke.com/projects/icewmcp/installation.php)

---

### Post by dannybuntu on 2009-01-07
> The document "IceWM FAQ and Howto" has been removed from Scribd


This content has been removed due to suspected copyright infringement

For more information, please send questions to [email]support@scribd.com[/email]. Note that we cannot provide you with a copy of the document, as it has been permanently deleted.

So I tried this:

> .TAR.BZ2 Packages:
As of version 0.2 of IceWM Control Panel, tarball (.tar.bz2) packages include a new installation method based around PyInstallShield. After downloading a tarball package, extract the package to a directory of your choice, with the command 'tar -xjf [tar_ball_file_name]' or 'tar -xIf [tar_ball_file_name]'. You can also use a GUI utility such as GnoZip or File-Roller to extract the tarball. **_After you have extracted all files from your downloaded tarball, install the application by running either 'PyInstallShield' or 'INSTALL-ME.sh' in the directory you extracted the files to. That's it!_**.

```
dan@ubuntu:~/Downloads/system/INSTALL-IceWMCP$ sh INSTALL-ME.sh
./PyInstallShield:214: DeprecationWarning: use gtk.UIManager
  itemf=ItemFactory(MenuBar,"<main>",ag)
./PyInstallShield:249: Warning: unsupported arithmetic operation for flags type
  table1.attach( Label(_("Installation Directory:")),0,1,0,1,(EXPAND+FILL),(EXPAND+FILL),0,0)
Traceback (most recent call last):
  File "./PyInstallShield", line 1468, in <module>
    runbabel()
  File "./PyInstallShield", line 1464, in runbabel
    mybabel=installwin()
  File "./PyInstallShield", line 249, in __init__
    table1.attach( Label(_("Installation Directory:")),0,1,0,1,(EXPAND+FILL),(EXPAND+FILL),0,0)
TypeError: flag values must be strings, ints, longs, or tuples
dan@ubuntu:~/Downloads/system/INSTALL-IceWMCP$ 
```

Thanks in advanced :)

---

### Post by Terl on 2009-01-07
> **cristo-father said:**
> Hi everybody.
How can i install and use (a tutorial would be nice) Icewm control panel?
Thanks in advance.

Have you checked via synaptic to see if this is available via the repositories?  That would be the easiest fix.  (I am at work so I cannot check the repos right now.  IIRC, everything is there for ICE WM)

---

### Post by dannybuntu on 2009-01-07
The strange thing is, it is not in the repositories.

---

### Post by Fragadelic on 2010-11-12
I know this is old but some folks may be looking into it for Ubuntu.  I was doing some tinkering with icewm and found icewmcp so I found this thread since I had the error as well.  I know a bit about python and pygtk so I thought I'd take a look.

What you need to do is edit the PyInstallShield script with gedit.  You may need to set encoding for Western or something so it opens the file.

Once it is open, replace the following:

,(EXPAND+FILL)

with a blank

To do this, either hit CTRL-H or Click on Search-Replace.

Save the file now and run it with sudo.

sudo ./INSTALL-ME.sh

That will install it for you.

You can then run IceWMCP to run the Control Panel and it isn't that bad actually.  Still works on Ubuntu 10.04.

---

