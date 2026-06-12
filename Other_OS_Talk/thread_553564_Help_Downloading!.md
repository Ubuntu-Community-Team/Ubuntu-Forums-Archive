---
title: "Help Downloading!"
date: 2007-09-17
forum: Other OS Talk
---

### Post by ES_EF_EX on 2007-09-17
I know this is the Ubuntu forum [I use Puppy], but the Puppy forums are nothing compared to these!  

I have managed to download Firefox 2.0.0.6, and have extracted the files from the tar.gz file to a new folder located at /usr/local/src/Firefox

From here, how to I make Firefox appear on the Start menu and add a shortcut on the desktop? So far the only way I've been able to run it is by opening up the terminal and typing in this code: /usr/local/src/Firefox/Firefox &

Also, after I launch Firefox via Terminal, if I close the terminal, Firefox closes. I would really like to know how to make Firefox behave like a normal Windows program [on the start menu and with a shortcut].

Any help is MUCH appreciated : )

---

### Post by bsharp on 2007-09-17
I've never used Puppy, but in Ubuntu to add it to the "Start Menu" you would right click on the menu and click add to panel and do a custom program launcher.  To create a shortcut ```
sudo ln -s /usr/local/src/Firefox/Firefox ~/Desktop
```

When you launch it from a terminal with the "&" symbol at the end you need to do Control C before you close the terminal.

---

### Post by ES_EF_EX on 2007-09-17
Thanks for the reply.  After entering the code: 

sudo ln -s /usr/local/src/Firefox/Firefox ~/Desktop

I got this message, code:  

sudo: can't stat /etc/sudoers: No such file or directory
Broken pipe

I have no clue what that means.  [HELP!!]

---

### Post by alienexplorers on 2007-09-18
That could mean your sudoers file is busted. Check your sudoers file using visudo:> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by ravenwere on 2007-09-18
Try entering the code without the sudo at the beginning. Puppy is different to ubuntu.

---

### Post by nonewmsgs on 2007-09-18
> **ES_EF_EX said:**
> I know this is the Ubuntu forum [I use Puppy], but the Puppy forums are nothing compared to these!  

I have managed to download Firefox 2.0.0.6, and have extracted the files from the tar.gz file to a new folder located at /usr/local/src/Firefox

From here, how to I make Firefox appear on the Start menu and add a shortcut on the desktop? So far the only way I've been able to run it is by opening up the terminal and typing in this code: /usr/local/src/Firefox/Firefox &

Also, after I launch Firefox via Terminal, if I close the terminal, Firefox closes. I would really like to know how to make Firefox behave like a normal Windows program [on the start menu and with a shortcut].

Any help is MUCH appreciated : )

i have actually had this same problem under puppy with the dissapearing firefox.  my fix was to pup get opera or was it....i might have downloaded opera...

---

### Post by Midwest-Linux on 2007-09-18
While we are on the subject on Puppy, did anyone ever have any luck installing the blessed thing? It works great, I love the desktop, minimal at its best but top notch in its approach. So did anyone have any luck installing Puppy or DSL?

---

### Post by notwen on 2007-09-18
I have installed Puppy many times w/o issue, I like to keep a copy of DSL & Puppy in my laptop bag at all times.  Who knows when they will be useful. =]

---

