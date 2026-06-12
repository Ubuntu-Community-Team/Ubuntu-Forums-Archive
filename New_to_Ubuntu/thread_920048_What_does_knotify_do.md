---
title: "What does knotify do?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by The ragman on 2008-09-14
I was playing a game on the computer - patience - and on winning, the computer tried to open 'knotify', presumably did, some modem activity occurred, and the cursor stopped the busy thing. 

What happened, what was the modem action all about? Anyone know?

---

### Post by appier on 2008-09-15
Knotify is part of KDE and does system notifications.  The following link should take you to an article on how to configure it:

[http://lukeplant.me.uk/articles.php?id=3](http://lukeplant.me.uk/articles.php?id=3)

---

### Post by The ragman on 2008-09-15
Interesting. How do I uninstall it - I don't like programs that do anything I don't ask them to.

---

### Post by appier on 2008-09-15
The short answer to uninstalling it is to go into Synaptic or Adept Package Manger, uncheck it, and then apply the changes.  However, it may not be that easy.  I do not know what programs are dependent upon it so I would not recommend doing so until you hear from someone else who knows if this action is safe or not.

---

### Post by Bush_Roo on 2008-09-15
Knotify is part of the KDE, and cannot be uninstalled without the whole of KDE being uninstalled. Dangerous move to try to remove it.

When I did my homework on this, I didn't see anywhere where it actually sends stuff over the Internet. This can be easily tested if you use Firestarter as a firewall--it will be listed there if it used the Internet. If it did, then just tell Firestarter to block it ;)

---

### Post by Bush_Roo on 2008-09-15
Something you can try:

If you are using GNOME, install kcontrol

sudo apt-get install kcontrol

run kcontrol

To the left there is something like "Sound & Multimedia" there. Under that there is "System notifications"

Try disabling anything or everything in there and see if it pops up with knotify again.

Let us know what happens.

---

### Post by sdibaja on 2013-03-10
> **Bush_Roo said:**
> Something you can try:

If you are using GNOME, install kcontrol

sudo apt-get install kcontrol

run kcontrol

To the left there is something like "Sound & Multimedia" there. Under that there is "System notifications"

Try disabling anything or everything in there and see if it pops up with knotify again.

Let us know what happens.

I got this:
Package kcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kinfocenter:i386 kde-workspace-bin:i386 kinfocenter kde-workspace-bin
  kde-runtime-data

not sure what that means...now what?

---

### Post by oldos2er on 2013-03-10
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

