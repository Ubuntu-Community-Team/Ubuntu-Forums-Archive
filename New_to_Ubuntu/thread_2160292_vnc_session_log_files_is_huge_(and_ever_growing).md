---
title: "vnc session log files is huge (and ever growing)"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by R0BiN on 2013-07-06
Hi all!

So, I've recently begun taking advantage of my server running ubuntu 13.04 and using vncserver to connect (and use VNC).

However, my /root/.vnc/HOSTNAME:1.log file gets larger and larger and larger until it fills up my entire HDD (currently it's 701.81, but it has gone higher than 1 TB).

Killing the vncsession and rebooting the system does get the disk space back.  However, as soon as I start another session with "vncserver -geometry 1600x1100", that file starts exploding in size again.  If I'm not doing anything, "vino-server" is the most active process (when I type "top" into SSH), so I'm somewhat inclined to blame it.

How can I get this to stop?  Can I disable logginng?  Some posts I found seemed to suggest the logs were caused by people trying to bruteforce in; but they didn't really tell me how to use that information to fix the problem.

I'd like to thank everyone who tries to help in advance (I'll make sure to do it again after, as well).

Thank you!
x

---

### Post by steeldriver on 2013-07-06
Can you tell us what message(s) the log is filling with? to avoid trying to open the whole big file in a text editor you can use the 'tail' command e.g.

```
tail -n 25 /root/.vnc/HOSTNAME:1.log
```

BTW are you really remoting in to a root desktop session? if so that sounds like a bad idea

---

### Post by R0BiN on 2013-07-07
Why does it sound bad?  Should I be creating a second user to use as the remote?  What does that get me (security wise)?

> 
07/07/2013 11:37:39 AM      173-162-224-189-NewEngland.hfc.comcastbusiness.net
07/07/2013 11:37:39 AM      173-162-224-189-NewEngland.hfc.comcastbusiness.net
07/07/2013 11:37:39 AM      173-162-224-189-NewEngland.hfc.comcastbusiness.net
07/07/2013 11:37:39 AM      tor-exit.burratino.net
07/07/2013 11:37:39 AM      tor-exit.burratino.net
07/07/2013 11:37:39 AM Client Protocol Version 3.3

** (vino-server:22542): WARNING **: Deferring authentication of 'fresno099.server4you.de' for 5 seconds


** (vino-server:22542): WARNING **: VNC authentication failure from 'fresno099.server4you.de'

07/07/2013 11:37:45 AM rfbAuthPasswordChecked: password check failed

(vino-server:22542):  GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)'  but the given value has a type of `(a{sv})'

(vino-server:22542): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:22542):  GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)'  but the given value has a type of `(a{sv})'

(vino-server:22542): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:22542):  GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)'  but the given value has a type of `(a{sv})'

(vino-server:22542): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

By the way, I can no idea what/who 173-162-224-189-NewEngland.hfc.comcastbusiness.net, tor-exit.burratino.net, or fresno099.server4you.de are.

Thanks for trying to help me out!

---

### Post by ljwobker on 2013-08-13
Someone (maybe not you???) is trying to authenticate to your VNC session from the fresno099.server4you.de machine.  If it's not you, someone is probably just port-scanning your machine.  Running as root opens your machine to anyone who can authenticate to it.  are you *really* sure you want to do this?  

The GLib error I can't help you with, but given that it's happening constantly, it's going to continue to fill your log until you solve it.

---

### Post by R0BiN on 2013-09-26
So I can deal with the people trying to access my machine.

I can't find anything that tells me how to keep all these "(vino-server:3090): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `(a{sv})'" errors from ruining my life.

Does anyone know how I make them stop?  Does anyone know how to change where the log file is kept, how verbose it is, etc. (with vncserver)?  I've been looking in files all over the place, and mostly don't understand what is going on in the files (I'm a bit of a duffer with Python, but outside of that I'm basically just a fool with a search engine).  I basically wouldn't mind being able to have all this logging ******** go to /dev/null.

---

### Post by DuckHook on 2013-09-26
You really need to read [this]("http://ubuntuforums.org/showthread.php?t=510812") excellent sticky on security by one of the best security gurus on this forum. The 2 simplest and most abused ways for bad guys to compromise systems are poor SSH setups and VNC, and you are using one of them.

I would never, never, never, allow root access to anything or anyone either through VNC or SSH. In fact, I leave the root account disabled (as it is by default on all pristine Ubuntu installs) and use sudo to get temporary root privileges only when absolutely necessary. You must cultivate the same good habits. Anything else is playing with fire, and your setup in particular is just an invitation to getting owned.

The idea of doing everything as root is a stupid nasty Windows convention that is simply awful computing practice. Once a bad guy guesses your VNC password, it's game over and at best your computer will become just one of the millions of spambots that infest the internet. At worst, some Russian mafia network will have all of your bank accounts, private e-mails and critical web passwords. It is a simple matter for a cracker to install a keylogger or rootkit once he has root access. I trust that this answers your question about what's so bad with your current setup.

The security sticky already referenced will link to instructions for setting up VNC properly. The steps are too complex to describe here, but it generally amounts to:

1. Disable password access altogether in SSH
2. Enable and allow *only* certificate access in SSH
3. Access VNC *only* through an SSH tunnel

This will prevent any brute force password dictionary attack from succeeding. If you want further protection, then make sure your router is set to accept/allow SSH connections only on high non-standard ports.

---

### Post by R0BiN on 2013-09-27
So, thinking (and reading) about DuckHook's advice here, I think I'll be taking it (setting everything up now).

Having said that, this still doesn't solve my log size problem.  The log is filling up mostly with error messages about GLIB
> (vino-server:22542):  GLib-CRITICAL **: the GVariant format string `(u)'  has a type of `(u)'  but the given value has a type of `(a{sv})'

(vino-server:22542): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

and then (it seems like this happens towards the end), by the server repeating the following message 1,000,000 times (basically until the log file takes up all the space and things start crashing).
> 27/09/2013 12:21:41 PM Authentication deferred - ignoring client message

---

### Post by bweinel on 2013-09-27
I beleive this may be a bug in vino. See the following launchpad bug report:

[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1047679](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1047679)

cheers
bill

---

### Post by DuckHook on 2013-10-02
Have you solved your logging issue? I noticed that the latest update included a new *vino*. You may be able to solve your matter by installing latest updates.

---

