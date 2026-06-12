---
title: "Confused about .xinitrc"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by horatio_alger on 2011-10-18
I am trying to change window managers from openbox to awesome.  I'd like awesome to start when I turn my computer on.  

The awesome wiki suggested that I go to ~/.xinitrc, look for "exec openbox" (or something like that) and replace with "exec awesome".

No sign of ~/.xinitrc.  (And I'm pretty sure I know how to view hidden files; ls -a right?)  Looks like when there is no ~/.xinitrc, startx uses /etc/X11/xinit/xinitrc, so I opened that up.  It reads

#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

No sign of "exec anything" so I looked in /etc/X11/Xsession.  This one is long so I am hesitant to just quote the whole thing, but I can't make head or tail of it.  Looks like most of it is devoted to error messages, besides setting some variables like USERXSESSION=$HOME/.xsession (which is another minor mystery actually, since I cannot find the file ~/.xsession either).

Given that 'openbox' has not appeared in any of these scripts, how does it get started?  And what should I change to make it not start, and make awesome start instead?

Thanks!

Forgot to say earlier:  I am using lubuntu, and have not changed anything from the defaults since I installed it aside from upgrading to oneiric.

---

### Post by meatytaco on 2011-10-18
At your login screen, once you click on your username, at the bottom of the screen there should be a box where you can choose awesome to load up. And I believe it should remember your choice. That's how I did it anyway. :P
Cheers :)

Edit: If this doesn't help, someone more adept at this will have to help :S lol

---

### Post by horatio_alger on 2011-10-18
Heh I do not have a log in screen in fact.  Another job for another day maybe....

I went to [http://wiki.lxde.org/en/LXDE:Questions#How_can_I_use_a_window_manager_other_than_Openbox_with_LXDE.3F](http://wiki.lxde.org/en/LXDE:Questions#How_can_I_use_a_window_manager_other_than_Openbox_with_LXDE.3F)
which says "Simply edit /etc/xdg/lxsession/LXDE/desktop.conf with a text editor, and replace openbox with your favorite window manager"

So I did that, changing "window_manger=openbox-lubuntu" to "window_manager=awesome".  But this does not appear to have had any effect.

---

### Post by bodhi.zazen on 2011-10-18
> **horatio_alger said:**
> Heh I do not have a log in screen in fact.  Another job for another day maybe....

I went to [http://wiki.lxde.org/en/LXDE:Questions#How_can_I_use_a_window_manager_other_than_Openbox_with_LXDE.3F](http://wiki.lxde.org/en/LXDE:Questions#How_can_I_use_a_window_manager_other_than_Openbox_with_LXDE.3F)
which says "Simply edit /etc/xdg/lxsession/LXDE/desktop.conf with a text editor, and replace openbox with your favorite window manager"

So I did that, changing "window_manger=openbox-lubuntu" to "window_manager=awesome".  But this does not appear to have had any effect.

That is because you are not using lxsession (or GDM), I assume you are using startx ?

Simply write a ~/.xinitrc

For details see: [http://awesome.naquadah.org/wiki/Autostart](http://awesome.naquadah.org/wiki/Autostart)

awesome is fantastic, but you are going to have to learn do do some reading and learn some lua if you wish to customize the interface.

Here is my awesome desktop:

[http://zenix-os.net/screenshots/awesome.html](http://zenix-os.net/screenshots/awesome.html)

---

### Post by horatio_alger on 2011-10-18
No luck.

First I created a file in my home directory, naming it .xinitrc, and including a single line, "exec awesome".  That had no effect, so I added the line "exec awesome" to /etc/X11/xinit/xinitrc. This had no effect either, as far as I could see.


Nice desktop by the way!

---

### Post by bodhi.zazen on 2011-10-18
make it executable

exec u+x or a+x ~/.xinitrc

---

### Post by horatio_alger on 2011-10-20
I did had indeed not done that, but I now have done that and I still do not see any effects.

To make sure I got this right, here are the permissions I see next to it when I use ls -al: -rwxrwx--x

In case I am missing anything else, here is the entire text of .xinitrc:

#!/bin/sh
exec awesome

---

### Post by bodhi.zazen on 2011-10-20
Not sure why it is not working. Is it awesome or awesomewm ?

See

[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

[http://manpages.ubuntu.com/manpages/hardy/man1/xinit.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/xinit.1.html)

If that fails , post to the awesome mailing list.

---

