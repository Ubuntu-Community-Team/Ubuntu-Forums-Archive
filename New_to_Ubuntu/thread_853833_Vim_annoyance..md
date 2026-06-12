---
title: "Vim annoyance."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by systemintheglitch on 2008-07-08
I hate how when I press escape to enter command mode.. It moves the cursor back one! What is the logic behind this. I don't ever see it being useful. 

Try this: press escape, i, escape, i, escape, i.. repeat..

How can i turn this off?

---

### Post by ChameleonDave on 2008-07-08
Vim is very annoying.  Unless you are used to it, or have some strong reason to use it, simply go for GNU *nano* instead.

---

### Post by Hooya on 2008-07-08
> **ChameleonDave said:**
> Vim is very annoying.  Unless you are used to it, or have some strong reason to use it, simply go for GNU *nano* instead.

yeah... except if you have to visudo.  I tried doing that and had a lot of trial and error because I couldn't find a good guide on how to use the darned interface.

How does one carriage return at the end of a line without pushing the last character on the previous line to that next line, for instance.  Just a really annoying interface.

Know of a good user manual?  man visudo doesn't really help me.

---

### Post by sdennie on 2008-07-08
For a vim tutor, just type the following in a terminal:

```

vimtutor

```

To change the editor that visudo uses, see this thread: [http://ubuntuforums.org/showthread.php?t=779902](http://ubuntuforums.org/showthread.php?t=779902)

---

### Post by systemintheglitch on 2008-07-09
> **Hooya said:**
> yeah... except if you have to visudo.  I tried doing that and had a lot of trial and error because I couldn't find a good guide on how to use the darned interface.

How does one carriage return at the end of a line without pushing the last character on the previous line to that next line, for instance.  Just a really annoying interface.

Know of a good user manual?  man visudo doesn't really help me.


It's not that bad except for the one thing that I posted about.. The solution to your problem:

    Go to the end of the line.. Press lower case a. Press return..
OR when in command mode.. just press lower case o!!! Even if you are in the middle of the line it will always work.

---

### Post by original_jamingrit on 2008-07-09
definitely sit down with vimtutor for a half hour sometime.  I hated vim for about a month before trying vimtutor, and it really made a difference in how I used it.

---

### Post by ChameleonDave on 2008-07-09
> **Hooya said:**
> yeah... except if you have to visudo.  I tried doing that and had a lot of trial and error because I couldn't find a good guide on how to use the darned interface.

Ah, yes.  Visudo is a very stupid command.  Its purpose is error checking, but there is no reason why a certain editor ought to be hard-coded into the command.

To force visudo to use another editor, do this:

```

sudo -i     # This is not just to get root access, but also to switch the shell to root settings

export EDITOR=nano

visudo

```

I imagine that you could put "export EDITOR=nano" in some config file to make the setting persist.

---

### Post by txcrackers on 2008-07-10
*visudo* doesn't execute Vim by default - it executes "vi" by default. This is because for many years *vi* (or *vim*) was just about the only screen editor that would be installed by default with a minimal footprint (Emacs is enormous by comparison). As most distributions still ship with a "vi" editor, there hasn't been any need to change this behavior. Besides, as noted, there's an easy way to use another editor in place of "vi" with the environment variables.

---

