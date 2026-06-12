---
title: "Reboot and resume commands"
date: 2008-05-21
forum: Programming Talk
---

### Post by anotherdisciple on 2008-05-21
How can I make a bash script do a series of commands.... then reboot... then continue with another set of commands as soon as the user logs in?

---

### Post by slavik on 2008-05-21
change the user's .profile (or his session file to start your script).

---

### Post by anotherdisciple on 2008-05-21
Maybe I should describe it better... I wrote this script that will first change your sources.list... then update and upgrade. Well.. after that it gives you a warning to restart your computer, so I would like to reboot then continue on with the rest of the script. From there it will uninstall and install a number of programs. Then it gives you a bunch of options to install things like Avant Window Navigator and such... so what I am saying is....

What can I put after 

"sudo aptitude update && sudo aptitude safe-upgrade"

to make it reboot and finish the rest of the script once it reboots?

---

### Post by artir on 2008-05-21
sudo aptitude update && sudo aptitude safe-upgrade && sudo shutdown -h now

---

### Post by anotherdisciple on 2008-05-21
My "Linux in a Nutshell" says -h halts the system... what does that mean?

---

### Post by drubin on 2008-05-21
```
shutdown -h now
```
-h halt as in turns off the power. 
now is the time you would like this to happen


```

 shutdown --help
```

That command gives this result. If you ever get stuck try the --help on the command and will give you some usefull info :) 

> Usage: shutdown [OPTION]... TIME [MESSAGE]
Bring the system down.

Options:
  -r                          reboot after shutdown
  -h                          halt or power off after shutdown
  -H                          halt after shutdown (implies -h)
  -P                          power off after shutdown (implies -h)
  -c                          cancel a running shutdown
  -k                          only send warnings, don't shutdown
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

TIME may have different formats, the most common is simply the word 'now' which
will bring the system down immediately.  Other valid formats are +m, where m is
the number of minutes to wait until shutting down and hh:mm which specifies the
time on the 24hr clock.

Logged in users are warned by a message sent to their terminal, you may include
an optional MESSAGE included with this.  Messages can be sent without actually
bringing the system down by using the -k option.

If TIME is given, the command will remain in the foreground until the shutdown
occurs.  It can be cancelled by Control-C, or by another user using the -c
option.

The system is brought down into maintenance (single-user) mode by default, you
can change this with either the -r or -h option which specify a reboot or
system halt respectively.  The -h option can be further modified with -H or -P
to specify whether to halt the system, or to power it off afterwards.  The
default is left up to the shutdown scripts.


---

