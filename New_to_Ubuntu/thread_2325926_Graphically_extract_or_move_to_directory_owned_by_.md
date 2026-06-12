---
title: "Graphically extract or move to directory owned by root and give user permissions."
date: 2016-05-26
forum: New to Ubuntu
---

### Post by slomobile on 2016-05-26
Similar questions have been asked repeatedly by beginners.  But invariably experienced linux users chose to answer similar but different questions.
This is not a windows user expects windows features problem.  It is a basic workflow problem.  A graphical tool is frustrating and inefficient if you have to jump to the terminal for frequently used operations.

My example problem is for a regular user with sudo rights to install a program prog.tar.gz from ~/Downloads into /opt and have it executable by all local users. Do this without touching a terminal, remembering obtuse option names, or typing much more than my user password.  Alt-F2 is a cheat for the terminal.

Acceptable answers may be to use a specific graphical tool or combination of graphical tools,
 modify the configuration of a default graphical tool or the environment,
add a "extract as root" right click menu option when ~/Downloads/prog.tar.gz is graphically selected in file browser, but remain ordinary user for other operations.
 
I am NOT asking how to ```
sudo tar -zxvf $HOME/Downloads.prog.tar.gz -C /opt
``` despite how easy it may seem to you.

I am also specifically NOT asking how to use gksudo to launch a graphical file manager with root privileges, unless the instructions include how to make that replace the default file manager for typical methods that launch it(from menu and when clicking directory), and it still offers some warning before accessing system files.

This may seem a silly question, you may even think I am asking the wrong question and should just get used to the Linux way of doing things.  Anything is possible in Linux.  I hear that a lot.  As long as you are a good typist and remember all the right commands, or have network access and time to look them up.  Well I don't.  Like more and more people injured in war zones or car accidents, I have both a physical impairment that limits my range of motion(mouse instead of keyboard) and a brain injury that limits executive function, including ability to memorize new things and perform symbolic manipulation.  Oddly, my limitations are similar to many windows converts, so helping me out will also help them.

I assume that since the file manager can produce a "Permission denied" dialog box when trying to do this on /opt, it could just as easily produce a dialog asking for my sudo password to complete the operation instead.  Does that violate some kind of principal?

If there are no ready answers, please tell me what the implementation barriers are, or point me to any developers that may be working on it.
I'm using Ubuntu MATE 16.04 64bit, and Mythbuntu. 
Thank you.

---

### Post by QIII on 2016-05-26
Hello!

Your question is a bit difficult to parse.  Let me see if I am distilling it properly:

Is there a GUI method to take an arbitrary .tar.gz and install a package it contains in /opt or another location in such a way that the application will be available to all users?

---

### Post by slomobile on 2016-05-26
Yes, that is the specific representative case I chose.  Ideally the same or similar method would work with other compressed types, or moving files and directories, or just changing permissions graphically, or opening for editing.  Any of the usual file management functions that get stopped in their tracks when doing them graphically onto a portion of the root filesystem.

I want to know how to do it, if the method exists.  If it does not exist, I want to inspire some kind developer to invent it.  It seems odd that a properly packaged very complex program on a website like eclipse can be installed with a single click(or 2) within the browser, but a tiny utility requires me to descend into the blackness of the terminal.  Even the name sounds like death.

I understand why this would be difficult under Linux with the permission system, but with most non server machines being single user laptops, the whole thing seems like pointless busy work, and its time to make a change to the way things get done.  Think about it.  The root account is protecting the filesystem, a generic group of files that can and do get replaced on a regular basis by updates, upgrades, and fresh reinstalls anyway, so who really cares if they get a little trashed once in a while by ham fisted authorized users as long as system access is denied to unauthorized users.  In fact, most system files that get messed up are because an inexperienced user (me) finds some instructions online, gets frustrated with permission denied, so starts throwing sudo at everything under the sun until either something works, or they get frustrated and give up.  Or worse, they unlock the root account and really start mucking about in dangerous ways.

---

