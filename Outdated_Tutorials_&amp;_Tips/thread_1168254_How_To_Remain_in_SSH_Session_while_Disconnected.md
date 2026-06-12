---
title: "How To: Remain in SSH Session while Disconnected"
date: 2009-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by BslBryan on 2009-05-23
Hello, everyone. :-)

This is a how-to I am writing because I see a lot of questions like this over at Launchpad. 

This tutorial will teach you how to keep your SSH session active while disconnected.

**1. ** The first thing that you need to do is install Screen.
```
sudo apt-get install screen
```
Screen is the equivalent of a window manager for your shell that will let you keep multiple shell sessions running.  **Make sure that you install Screen on the server you are connecting to.**

**2. ** Now, you are able to start a new sessions by typing ```
screen
``` in your shell.  The first thing you see will be information about the program.  Don't freak out, it's just a string of words to help you get more comfortable with the software. :-)  To skip this, just press Enter.

**3. ** That's it!  The Screen programmers have done all of the hard work for you!  Here is how to leave the session running while disconnected, plus some other helpful key bindings.  :-)

**Leave the system running and disconnect** by pressing Ctrl + A, followed by Ctrl + D immediately.  You will see the message ```
[detached]
``` :-)

**To reconnect to an existing session, or create a new session**, simply type ```
screen -D -r
```

**If you'd like to reconnect to a session that is already active**, type ```
screen -r
```

**Listing open Screen windows** is possible by pressing CTRL + A, immediately followed by W.

**Create a new window inside of an existing Screen session** by pressing Ctrl + A, immediately followed by C.  Yes, a new prompt is supposed to appear. :lol:

**Switch from one Screen window to another** by pressing Ctrl + A twice rapidly.

And there are tons of other cool key bindings and commands, but these are certainly good to get everyone familiar with the program.

I hope that I've helped some of you! :-)

---

### Post by lavinog on 2009-05-24
Isn't screen installed by default now in jaunty?

Any idea how to detach a screen from within a screen?
ex: I ssh into server1, open a screen and ssh into server2, and open a screen on server 2. If I ctrl-A D, I close server1's screen and not server2.
Kind of a minor issue since opening a screen on server1 can wait until I disconnect from server2, but it was an afterthougt and required backing out completely.

---

### Post by phinullfermata on 2009-05-24
I beleive you can press CTRL-a a D.

Explaination: Ctrl-a a inserts a literal Ctrl-a into the screen program you have running, which is screen, then D detatches.

I tested this and it works.  Keep in mind, though, that Ctrl-a is the escape key for your local screen session, and a is the escape for the server - if you've modified your escape keys on either, you'll need to change this.

---

### Post by lavinog on 2009-05-24
> **phinullfermata said:**
> I beleive you can press CTRL-a a D.

Cool, that makes sense.

---

### Post by BslBryan on 2009-05-28
> **lavinog said:**
> Isn't screen installed by default now in jaunty?
Yep! :-)  But not in Hardy or Intrepid, I think.

---

