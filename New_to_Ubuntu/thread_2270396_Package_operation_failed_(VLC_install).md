---
title: "Package operation failed (VLC install)"
date: 2015-03-22
forum: New to Ubuntu
---

### Post by jwn-2 on 2015-03-22
Ubuntu 14.04 LTS

I am trying to install VLC media player, but the installation keeps failing with the following message. What am I suppose to do to rectify this?

//
The installation or removal of a software package failed.

Details
installArchives() failed:  Extract templates from packages: 76% Extract templates from packages: 100% 
 Extract templates from packages: 76% Extract templates from packages: 100% 
 Extract templates from packages: 76% Extract templates from packages: 100% 
dpkg: unrecoverable fatal error, aborting: 
 syntax error: unknown group 'root' in statoverride file 
Error in function:  
//

---

### Post by ajgreeny on 2015-03-22
How are you installing (or trying to install) VLC?  It does not sound like a normal repository installation, so are you building it from source?

---

### Post by jwn-2 on 2015-03-23
Sorry, yes I should have mentioned that I am trying to install from the Software Centre (I assume that is the normal repository you are refering to), from where I have installed many other packages succesfully before.

---

### Post by bardo2 on 2015-03-23
Just tried the same thing on my old computer running XUbuntu Trusty (installed vlc through software center). Went fine and is properly installed.
If i had to find the problem source, i'd be interested in more information, thus i would install from commandline, where more outputs are generated, like
sudo apt-get install vlc
You/We will have to find out, what is unusual in your configuration...

btw: EVERY Ubuntu system should have a user(id) root (uid 0) and that user has a group. The question therefor could be: Did you remove that one?

For example, if i ask:
head -n 1 /etc/group

i get:
root:x:0:

indicating root is in fact a group with uid 0.
And on your system?

---

### Post by jwn-2 on 2015-03-23
Thanks bardo2. I did not remove anything that I know of.

I get: croot:x:0:

Does that mean anything to you?

---

### Post by jwn-2 on 2015-03-23
.

---

### Post by jwn-2 on 2015-03-23
Okay, I seem to have solved the problem. I just changed the "croot" group in /etc/group back to "root" and then installed VLC again succesfully. I might have accidentally changed it to "croot" when I eddited the file to add myself to the VBoxusers group. Thanks bardo2. I will mark as solved.

---

