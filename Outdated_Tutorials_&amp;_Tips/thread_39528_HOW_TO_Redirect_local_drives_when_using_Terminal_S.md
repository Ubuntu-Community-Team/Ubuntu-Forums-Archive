---
title: "HOW TO: Redirect local drives when using Terminal Services/Remote Desktop Connection"
date: 2005-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Darrena on 2005-06-05
This was asked in the application support forum, so I figured that I would slap together a how-to to make it easier for people to find.   Under windows,  Terminal Services (Also called remote desktop in XP) allows a user to map a local drive back to the terminal server so they can transfer files back and forth.  rdesktop 1.4 also supports this feature, this howto describes how to do this from Ubuntu (Or any other linux distro).

First of all to do this you will need to install version 1.4.1 of rdekstop, Hoary ships with 1.3.

You can download a package from Debian unstable at:
[http://packages.debian.org/unstable/x11/rdesktop](http://packages.debian.org/unstable/x11/rdesktop)

Assuming that you download the package to your home directory, open a terminal and type the following:
```
sudo dpkg -i rdesktop_1.4.1-1_i386.deb 
```

Replace the filename with the one appropriate to your achitecture.

None of the current front-ends to rdesktop support drive redirection so you will need to run it from a command line.  An example is shown below:
rdesktop -g1024x768 -a15 -r 'disk:linux=/home/' -p- 10.10.10.10

I haven't figured out how to map more than one drive, so I usually just map my home drive since that contains all my data anyway.

Some common command switches are:
-g for size of the window, this is in the format HorizontalxVertical, ie 1024x768 or 800x600.  
-a for desktop color depth, by default rdesktop uses 256 colors, to use 15 bit color use 15 and for 16 bit color use 16.
-u to pass a username to fill in for you
-p to pass the password for the username above
-x to set the speed to the remote host: m for modem, b for broadband and l for lan.
-r is the switch to redirect something from the local PC, to see all the options for this just type rdesktop from a terminal.

So using my example above, I am connecting to the server 10.10.10.10, using a resolution of 1024x768 and a 15bit color depth and creating a share on the windows box that points back to /home on my Linux PC.

---

