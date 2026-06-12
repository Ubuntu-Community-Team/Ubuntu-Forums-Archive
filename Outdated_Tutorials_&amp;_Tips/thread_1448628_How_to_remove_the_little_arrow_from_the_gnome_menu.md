---
title: "How to remove the little arrow from the gnome menu applet"
date: 2010-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Sporkman on 2010-04-06
The gnome menu applet has a little arrow pointing towards the desktop, indicating that it's a menu to be opened as opposed to being a launcher.

I find the arrow to be a blemish on an otherwise attractive panel, so I've always wanted to get rid of it.

There's a bug filed to make the arrow optional ([https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/291463](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/291463)), however for the time being the gnome panel source code has to be hacked.

Here's how to do it:

First download the source & dependencies:

```

sudo apt-get source gnome-panel
sudo apt-get build-dep gnome-panel

```

Then open up the applicable source file (as root):

```

sudo gedit /home/<your_login_name>/gnome-panel-2.30.0/gnome-panel/panel-menu-button.c

```

Note #1: Replace <your_login_name> with your login name,
Note #2: The gnome panel version might have changed by the time you read this - if so, change the path to the source file accordingly

In the source file, search for the term (including the quotes):

"has-arrow"

As of this writing, there is only one occurrence of this in this source file. Next to it, there's a "TRUE":

```

			       "has-arrow", TRUE,

```

Change the TRUE to a FALSE. Then save & exit.

Back to the command line, do:

```

cd /home/<your_login_name>/gnome-panel-2.30.0/
sudo ./configure
sudo make
sudo make install

```

Finally, restart the gnome panel to put the change in effect:

```

killall gnome-panel

```

And voila. :)

---

### Post by rhydian on 2011-01-14
Thank you, that worked a treat! That arrow was annoying me too!

---

### Post by rhydian on 2011-01-14
:-)

---

### Post by angelcleff on 2011-01-16
Now you are my new hero... hahaha

thanks a lot my friend!! :D

---

### Post by Sporkman on 2011-01-20
Note: There appears to be a problem with the build on Ubuntu 10.10.

The workaround described by bdforbes in the link below works for me:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/655205](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/655205)

---

