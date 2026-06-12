---
title: "crypt and uncrypt files or directories easy way!"
date: 2007-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by ykpaiha on 2007-05-15
I am not the dev of this piece of software but it look so easy and clever !!
here is the owner:
[http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html](http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html)
and now (my) the how-to:

1)pickup the soft:
[http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper/cryptkeeper_0.5.666-1_i386.deb](http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper/cryptkeeper_0.5.666-1_i386.deb)
and use gdebi to install it (it may take care of the dependencies)
in case of broken system it needs enfs (fuse)

2) when installed
clic on applications=>system-tools=>cryptkeeper
you may have an error message telling you "...no right to open fuse..."

3)manage fuse
system=>admin=>users and group
go to manage group you must find a group named fuse at the bottom
valid it and clic =>property
valid the users group you want using fuse (do not valid root!!!)
close all to valid this.

4') reboot your ubunu 

5)clic on applications=>system-tools=>cryptkeeper
now a small yellow padlock will appear on  your top-menubar
right clic on it and change in preference nautilus as your file-browser

6)left clic now on the padlock to create a new stach
it will create  a directory (name it)  and the password associated to it
nb: the system will create a dir only in your home and refuse to be elsewhere.

7) when done you will have a dir created where you can pass or copy any file or directory with nautilus
when you uncheck the crypted dir it will disapear from nautilus
to mount it just left clic on the padlock valid your dir enter the password and that is it !!

as I said earlier easy and fun!
thanks a lot to the dev of this app and if I can be any help let me know..
(you can see the hidden crypting in your home/.(the-name-of -dir)_encfs)

---

