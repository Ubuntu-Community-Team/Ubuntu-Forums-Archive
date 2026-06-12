---
title: "Can't unlock system management programs"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by jlrubin on 2008-06-05
I started using Xubuntu (Hardy 8.04) a few days ago. I am trying to use it headless -- no keyboard, no monitor -- by logging in with SSH from a windows box and starting the tightvnc server. It all looks great, but when I try System > Services, the "unlock" button won't let me.:confused: The same goes for other system management programs like Users and Groups.

No monitor and keyboard are connected now, so I can't tell if the problem is due to the way I log in.

---

### Post by Oldsoldier2003 on 2008-06-05
> **jlrubin said:**
> I started using Xubuntu (Hardy 8.04) a few days ago. I am trying to use it headless -- no keyboard, no monitor -- by logging in with SSH from a windows box and starting the tightvnc server. It all looks great, but when I try System > Services, the "unlock" button won't let me.:confused: The same goes for other system management programs like Users and Groups.

No monitor and keyboard are connected now, so I can't tell if the problem is due to the way I log in.

traditionally servers are administered via ssh and the command line. however since you are trying to admin via VNC I'll ask the obvious question: Does your user have the right to administer the system?

---

### Post by jlrubin on 2008-06-05
> **Oldsoldier2003 said:**
> traditionally servers are administered via ssh and the command line. however since you are trying to admin via VNC I'll ask the obvious question: Does your user have the right to administer the system?
I'm a linux newbie.

Sure I have the right to administer the system, I installed it, and I'm the only user. I will no doubt use the command line more as I learn more.

---

### Post by Oldsoldier2003 on 2008-06-05
in your remote session open a terminal and do the following command:

id

and see if your user shows up in the "admin" group. I don't use VNC to administer but if you have questions i can help you with the command line.

---

### Post by jlrubin on 2008-06-05
I started a terminal window while connected through vnc.
The id and groups commands show that I belong to 'admin' and 'adm'

---

### Post by Oldsoldier2003 on 2008-06-05
> **jlrubin said:**
> I started a terminal window while connected through vnc.
The id and groups commands show that I belong to 'admin' and 'adm'

then clicking the unlock should bring up a password dialog for you to enter your password. (effecively they are launching the gui tools via gksu to give you admin rights...)

---

### Post by jlrubin on 2008-06-05
> **Oldsoldier2003 said:**
> then clicking the unlock should bring up a password dialog for you to enter your password. (effecively they are launching the gui tools via gksu to give you admin rights...)
That's what I expected, but it doesn't even bring up the password dialog.

I next tried doing
  gksudo services-admin
This pops up the window, asks for my password, and I'm *still* locked.

---

### Post by jpryor68 on 2008-06-06
That's strange. On my own machine (using directly connected keyboard/monitor), I can Unlock the services-admin dialog. (But not if I run gksudo services-admin, which is odd). I don't know why you aren't able to. But here's how to enable/disable the services via the command line. In the services-admin dialog, you'll see a description of a service followed by the name of the daemon in parenthesis: for example "Actions scheduler (atd)". These daemons are located in /etc/init.d/. You can turn one on with the command:
     sudo invoke-rc.d DAEMONNAME start
and turn it off with the command:
     sudo invoke-rc.d DAEMONNAME stop
These changes won't survive a reboot. I don't know, off the top of my head, how to make the changes in a way that survives reboot, via the command line.

---

### Post by jlrubin on 2008-06-06
Here's more information about the problem; I think I might be starting the desktop environment wrong. Please note that I am simultaneously a newbie at linux, ubuntu, x windows, and xfce. You can't say I'm lacking in Chutzpah. (i do have 30 years experience, just not in unix/linux).

When I power up the box, I connect with ssh and run tightvncserver from my home directory (no sudo or anything). It displays the usual messages about creating display :1 and running programs in ~/.vnc/xstartup. This file contains:

```

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
# I removed
# x-terminal-emulator -geometry ..... &
x-window-manager &
# I added
xfce4-panel &

```

I connect with tightvncviewer from windows xp, and my desktop looks fine, with the panel as I configured it. I can disconnect vnc and reconnect to the same session. But when tools requiring root are run from the menus, the "unlock" button doesn't work, and I am not prompted for my password. No problem using a terminal window started from the desktop.

Am I starting the right stuff in the right environment?

---

### Post by bsh on 2008-06-06
i have had the same problem (but with vnc4server, if that matters), couldn't find a solution (and no-one answered my question either... :/ ). since 8.04 has way too many bugs for me, i have wiped it and happily using 7.04 now.

---

### Post by jarlz0r on 2008-07-04
Run **ck-list-sessions**. You should get something along the lines of
```
$ ck-list-sessions 
Session1:
	uid = '1000'
	realname = 'jarlz0r,,,'
	seat = 'Seat1'
	session-type = ''
	active = TRUE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2008-07-04T07:16:50Z'
```
If your user does not appear, run **ck-launch-session**, and then try **ck-list-sessions** again. Does it now list stuff about your user? Check if the unlock-button works now before closing that terminal.

---

### Post by soaringaa on 2008-07-14
I am having the same problem.  I executed ck-list-sessions as suggested in this thread.  This showed that for my ssh session the field "active = TRUE" and for the vnc session "active = FALSE", which looks to be indicative of the problem.

I searched around some more based on this and found the following  bug report discussion:
[https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/238800](https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/238800)
titled:
"policykit not available over NX sessions"

The first entry notes:

[I]Binary package hint: policykit

Policykit is not available over NX sessions. The unlock button
in the admin utilities is greyed out.[/I]

At the end of the thread (as of today) is the following messgae:

[I]It seem that Marcelo Boveto Shima had a temp fix for NX sessions
[https://bugs.launchpad.net/ubuntu/+bug/221363](https://bugs.launchpad.net/ubuntu/+bug/221363)
[https://bugs.launchpad.net/ubuntu/+bug/221363/comments/23](https://bugs.launchpad.net/ubuntu/+bug/221363/comments/23)[/I]

[I]At least it work in my environment.
[/I]

I am using vnc4server and this thread regards freeNX.  I am wondering if this provides any hint to the problems here since it seems to relate to a policykit issue.  I don't know enough about vnc4server to know if it could be having the same problem.  Does anyone following this thread know more?

---

### Post by csogilvie on 2008-11-10
I too am having a similar problem:

Ubuntu 64-bit 8.04 LTS (server)
Ubuntu 64-bit 8.04 LTS (desktop)

tightvnc server on both

ssh tunnel to vnc session using any vnc program.

Admin buttons in gnome are all greyed out.

I'd love to know if anybody has any ideas for us folks not using NX session.

---

### Post by ijakings on 2009-04-19
Just incase anyone is still struggling on this problem the following entered into a terminal window works.

sudo ck-launch-session users-admin

---

