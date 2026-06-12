---
title: "Feedback Needed"
date: 2005-06-05
forum: Packaging and Compiling Programs
---

### Post by Gtaylor on 2005-06-05
I just finished my first attempt at making a .deb package and need some feedback on it. I have packaged TinyFugue ([http://tf.tcp.com/~hawkeye/tf/](http://tf.tcp.com/~hawkeye/tf/)) which is a console based MU* client. I've verified that it runs on my box and the man page works as directed, but I'd be curious to see how it runs on someone else's. 

Install it and run the 'tf' command. There will probably be warnings about a tiny.world file missing. This is perfectly normal and is just there to remind you that things could be easier for the user if they read the manual :)

You can get the .deb from:
[http://squishywaffle.com/debs/tf_50b7-1_i386.deb](http://squishywaffle.com/debs/tf_50b7-1_i386.deb)

Someone who's been packaging a while please take a look at this and tell me if I've got it half right!

---

### Post by Gtaylor on 2005-06-05
Here's another, maneditor-0.6.1, opposed to the 0.5 that is currently included in the normal repositories. You will need libgcc1 (>= 1:4.0.0-7) for this.

[http://squishywaffle.com/debs/manedit_0.6.1-1_i386.deb](http://squishywaffle.com/debs/manedit_0.6.1-1_i386.deb)

---

