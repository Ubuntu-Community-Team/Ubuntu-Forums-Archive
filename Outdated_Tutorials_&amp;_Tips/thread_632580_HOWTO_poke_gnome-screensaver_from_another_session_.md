---
title: "HOWTO: poke gnome-screensaver from another session (via ssh)"
date: 2007-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by explicitly ambiguous on 2007-12-05
I wanted to share my solution to a problem that has been bugging me for a while now...

Set-up:
        I have a laptop that I have been using as a remote-control for watching movies on a PC the other side of the room.  I ssh into the PC and can play / pause / load movies in totem via the command line.  However, sometimes the screensaver is active and I want to poke it so I can see totem.  I had tried naively
```
gnome-screensaver-command --poke
``` to no availe.

Solution:
        The problem is when I tried the above command after ssh'ing in to my account I was met with the error message:
```
 ** Message: Failed to connect to the D-BUS daemon: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
```
After searching around for some time I came across a post ( [http://lists.debian.org/debian-user/2007/05/msg00434.html](http://lists.debian.org/debian-user/2007/05/msg00434.html) ) describing a solution to a similar problem.  The solution is to set the variable DBUS_SESSION_BUS_ADDRESS.

So here's what I did:

        -on the host PC I wrote a small script "write_DBUS.sh" ( included below ) and added it to the start-up sessions ( System  > Preferences > Sessions )
        -I added the line
        ```
alias poke="source /home/yourusername/.DBUS_temp ; export DBUS_SESSION_BUS_ADDRESS ; gnome-screensaver-command -p"
```
         to ~/.bash_aliases ( after uncommenting the lines in ~/.bashrc to allow ~/.bash_aliases to be read -- see e.g. [http://ubuntuforums.org/showpost.php?p=2222465&postcount=7](http://ubuntuforums.org/showpost.php?p=2222465&postcount=7) )

Now whenever I ssh into the PC I can type the command "poke" and gnome-screensaver will return me the screen :-) 


Hope this is of use to someone,

Andy


#Comments welcome!

------------------------------------------------

Put the following into a file "write_DBUS.sh" 

```
#!/bin/bash
# wait for 2 mins (wasn't sure if I would need to wait for gnome-screensaver to come on-line)
sleep 120 
# export the variable DBUS_SESSION_BUS_ADDRESS to the file .DBUS_temp so we can pick it up later 
set | grep DBUS > /home/yourusername/.DBUS_temp

```

Now run:
 
```
chmod +x write_DBUS.sh
```

---

### Post by arbrandes on 2008-05-30
Excellent tip!  I'm using it to suspend a machine remotely by use of:

```

dbus-send --session --dest=org.freedesktop.PowerManagement --type=method_call --print-reply --reply-timeout=2000 /org/freedesktop/PowerManagement org.freedesktop.PowerManagement.Suspend

```

Thanks!

---

### Post by PinkFloyd102489 on 2008-05-30
I know that if you dont specify a display, you'll get DBUS errors. I always use:

```
export DISPLAY=:0 && gnome-screensaver-command --poke
```


Well not anymore, since I removed gnome-screensaver in favor of xscreensaver. Apparently gnome-ss doesnt play nice with cron and my wake up alarm script wasnt unblanking the screen.

---

### Post by svensandberg on 2009-06-17
Thanks for the information! Based on your scripts, I wrote the following so that I can run gnome-screensaver-command from a cronjob:

```
#!/bin/bash
#Synopsis: cron-gnome CMD [ARGS]
#
#Purpose: run gnome-screensaver-command from a cronjob.
#
#Usage:
#1. in ~/.bashrc, add the following line:
#
#   set | grep DBUS_SESSION_BUS_ADDRESS > ~/.DBUS_temp
#
#2. in crontab, use a line like this:
#
#   * * * * * gnome-cron gnome-screensaver-command FLAGS
#
#   instead of:
#
#   * * * * * gnome-screensaver-command FLAGS
#
#Background: To execute a gnome-screensaver-command, the environment
#variable DBUS_SESSION_BUS_ADDRESS must be set properly.  This is done
#automatically by bash but not by cron.  The code in .bashrc saves the
#environment variable to a file, and this script reads the file and
#sets the environment variable to the saved value before executing the
#command.

source /home/YOUR_USER_NAME/.DBUS_temp
export DBUS_SESSION_BUS_ADDRESS
$*

```

---

### Post by YaronSh on 2010-12-28
I found another nice way to do it,
I SSHed into my other computer and I was facing the same problem.

Since the command needs an X screen in order to work I simply did:
$ DISPLAY=:0 gnome-screensaver-command -p

Assuming there are no seperate X displays for your screen and projector or the bigger screen you were watching on this might work as well, if you do you just need to change the display number from 0 to whatever display you are trying to wake (although I guess all screens are awakaned in this process anyway but I don't have the required tools to approve that)

---

