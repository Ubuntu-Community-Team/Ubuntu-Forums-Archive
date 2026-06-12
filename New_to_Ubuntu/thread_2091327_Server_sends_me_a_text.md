---
title: "Server sends me a text"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by ITProInTraining on 2012-12-04
Hi there community.  This is my first post, but not my first time on the forums or on Ubuntu.

I have a great dell desktop I'm using to mainly play around with Linux, and I seem to have hit a speed bump.

I was recently impressed that an IT pro had different pieces of equipment send him emails and even text messages when certain backups finished, events occurred, etc.  I thought it could not be too hard so I set out to do it.  Long story short, I can send a pre made text from Ubuntu by double clicking a file.  I have taken it that far.

PROBLEM:  I should think it was easy enough to run the file at startup, but I have a complication.  The box runs plugged into nothing but power.  That is the only cable.  It starts up, loads up somewhat "messed with" drivers and ndiswrapper to make my wireless card work, connects to my network, and starts TeamViewer.  I started up the box tonight, and I was surprised to get a text (it had not done this before), so I shut it off and tried again, and lo and behold, no text.

MY THEORY:  The machine takes some time to connect to the network because of ndiswrapper.  By the time the box is actually online, it has already run the "text sender"

MY GOAL:  Can I delay the action by 20 seconds?  I have the code directly in the "Startup Applications" program, so is there something I can add to the code to make it wait?

Any help is greatly appreciated.

---

### Post by Hadaka on 2012-12-04
Hi,use code

```
 sleep 20
```man sleep for information on the sleep command

you can also use crontab...to set things in motion at given times and send you an
e-mail when complete.

here is a nice link to get you started with crontab if you dont already know how to use it.

[http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/](http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/)

and...if you use gedit as your editor you can make gedit the default editor in crontab by
adding the following code to the end "last line" of your .bashrc file.

code:
#sets gedit as default for crontab
export EDITOR=gedit



have fun !

---

### Post by StinkySQL on 2012-12-05
You'll want to work through cron to schedule things like this. Eventually it will be an administrative nightmare and you can minimize that by having a central location to work on changes and additions.

---

