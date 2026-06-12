---
title: "cron and transmission: how to start and stop"
date: 2010-06-13
forum: Programming Talk
---

### Post by wannabegeek on 2010-06-13
hi all,

I've been reading various articles on-line today to learn some
cron basics.

I understand that I should use crontab -e  to edit a crontab.

What doesn't make sense yet, to me, is how would one start and then stop
a cron job ?

The program I want to do this with is Transmission.
Eventually I'll want to get the 'watch directories' command to work for
transmission-daemon too...I didn't really grok those docs either...

thanks in advance for any help and links to good docs,

wbg

---

### Post by soltanis on 2010-06-13
man 5 crontab

The format is

```

minute hour dayofmonth month dayofweek

```

To start transmission at 6:20 and turn it off at 8:40 a.m. everyday add to your crontab:

```

20 6 * * * * cd /home/user/ && transmission
40 8 * * * * pkill -INT transmission

```

Read:
man 1 kill, man 1 pgrep
for usage of pkill to stop a process after a certain amount of time.

---

### Post by wannabegeek on 2010-06-14
cool thanks soltanis

I've used pgrep in a script but never noticed  pkill

seems pretty straight forward will post back with progress...

thanks !
wbg

---

### Post by geirha on 2010-06-14
cron doesn't know about your xserver, so if you intend to start the gui client this way, then I suggest you rather install [gnome-schedule](apt:gnome-schedule) and use that.

If you want to stop/start the daemon that way, edit root's crontab and use the commands
```

/etc/init.d/transmission-daemon start
/etc/init.d/transmission-daemon stop

```
to start/stop.

---

### Post by sandyvong on 2010-06-14
Please, can you point me in the right direction here? I need to run  transmission only when I am asleep. Currently, I run a script using cron  that starts it and kills it. But I don't know if transmission shut  itself down nicely or what kill signals to send.
I did just see a  tidy looking script for starting/stopping the daemon. Any advantages of  using the daemon overnight?

Thanks

---

### Post by geirha on 2010-06-14
Though, why not just run it continuously, and use its temporary speed limits to limit the bandwidth during the hours in question? For the GTK-client: Edit -> Preferences -> [Speed]. The daemon: [https://trac.transmissionbt.com/wiki/EditConfigFiles](https://trac.transmissionbt.com/wiki/EditConfigFiles)

---

### Post by rnerwein on 2010-06-14
> **sandyvong said:**
> Please, can you point me in the right direction here? I need to run  transmission only when I am asleep. Currently, I run a script using cron  that starts it and kills it. But I don't know if transmission shut  itself down nicely or what kill signals to send.
I did just see a  tidy looking script for starting/stopping the daemon. Any advantages of  using the daemon overnight?

Thanks
hi
first - i don't know transmission. - but
may be you can use your ~/.bash_logout to insert a script to start your jobs and use your ~/.bashrc ( or what kind of shell you are using ) when you are awake to stop your script.
and about to stop that job i will try first to use the SIGTERM to stop it ( but this depentds on if the app is
well programmed or not. SIGTERM ( signal 15 ) is normaly designed to tell a job --> make your duty and
finish your work ).
hope this can help you.
ciao

---

### Post by soltanis on 2010-06-14
I'm pretty sure transmission has a daemon mode that you can run in the background, and usually you can stop those with something like

```

daemon start|stop|restart
# or
/etc/init.d/daemon start|stop|restart

```

No need to have an X server running to run transmission, it has a console mode.

---

### Post by wannabegeek on 2010-06-18
@ geirha
> Though, why not just run it continuously, and use its temporary speed limits to limit the bandwidth during the hours in question? For the GTK-client: Edit -> Preferences -> [Speed]. The daemon: [https://trac.transmissionbt.com/wiki/EditConfigFiles](https://trac.transmissionbt.com/wiki/EditConfigFiles)

aweswome....using it now, curious that I didn't see the speed option in the .config/transmission/settings  ?

still interested in crontab...and a program like top and other various command line tools.

thanks all, not done yet with this topic and still reading the great responses and good questions,

wbg

---

### Post by wannabegeek on 2010-06-23
Hi all,
been re-reading this thread and have a few questions.

Supposing that I don't care about a GUI for transmission, only CL, should I use
cron with transmission-daemon   or transmissioncli ?

Is this mainly a matter of foreground vs. background  ?
thanks all,
wbg

EDIT:Found transmission-daemon wiki and  added the schedule options to my config file for the daemon. Having difficulty starting the daemon...
I don't understand  how start-stop-daemon works. I tried
```

start-stop-daemon -Sx transmissio-daemon

```
didn't like that...?

---

### Post by geirha on 2010-06-23
The transmission-daemon package installs an init-script, so you just do ```
/etc/init.d/transmission-daemon start # and stop
``` from the crontab to start and stop it.

The current version in 10.04 has a bug regarding how the daemon handles the config file [https://bugs.edge.launchpad.net/ubuntu/+source/transmission/+bug/571097](https://bugs.edge.launchpad.net/ubuntu/+source/transmission/+bug/571097). A fix is in -proposed, though I'd just add the stable ppa at [https://edge.launchpad.net/~transmissionbt/+archive/ppa](https://edge.launchpad.net/~transmissionbt/+archive/ppa) and install the latest (2.00) from there.

If you want a command-line interface (similar to rtorrent's) to control the daemon with, have a look at fagga's  transmission-remote-cli [http://www.transmissionbt.com/resources.php](http://www.transmissionbt.com/resources.php)

---

### Post by wannabegeek on 2010-06-23
Thanks...

I am using Karmic, but tried to add the ppa to my sources list anyways...it didn't work however.
Should I trouble shoot this, or is Karmic daemon working ok?

Do I put a 'deb' in front of the http address  when adding to sources.list ?
I have the same problem adding a ppa for flash from sevenmachines.

---

### Post by geirha on 2010-06-24
Just run
```
sudo add-apt-repository ppa:transmissionbt/ppa
```

---

