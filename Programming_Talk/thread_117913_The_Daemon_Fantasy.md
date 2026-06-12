---
title: "The Daemon Fantasy"
date: 2006-01-15
forum: Programming Talk
---

### Post by SuperMike on 2006-01-15
I've had a couple people tell me that in *nix, "everything is a file". However, the way that Linux (and whatever *nix) does daemons does not compute along these same lines. For instance, here's a fantasy:

* Daemons usually have 6 things you usually want to know or do with them:
1. Is it loaded right now in my current run level?
2. Does it usually load in my current run level?
3. Does it usually load in a particular run level?
4. What is the description of the daemon?
5. Can I load, unload, or bounce it now?
6. How can I create my own daemon and execute it at a certain run level?

* For each of these things, it seems these could be easily translated into the file metaphor:

1. Is it loaded right now in my current run level?

ls /dmon/current

-or-

ls /dmon/current | grep -i "<my daemon I'm interested in>"

2. Does it usually load in my current run level?

ls /dmon/load/current

3. Does it usually load in a particular run level?

ls /dmon/load/rl?
(where ? is a # 1-5)

4. What is the description of the daemon?

cat /dmon/load/rl?/desc/*

5. Can I load/reload, unload, or bounce it now?

dload /dmon/load/rl?/<daemon>
dunload /dmon/load/rl?/<daemon>
dbounce /dmon/load/rl?/<daemon>

6. How can I create my own daemon and execute it at a certain run level?

a. Edit a Bash script to load your daemon. No special code needs to be inside. Give the script a name without a file extension on the end.
b. chmod a+x <script file>
c. Copy it to /dmon/load/rl?
d. Edit a small description file by the same name as the script file. It should be in the format, and in human-readable form without <>: 
<daemon short name> <daemon long name>
<tab><short description>
<tab><author(s)>
<tab><version>
<tab><special rules, comments, etc.>
<tab><more special rules, comments, etc.>
e. Copy this description file to /dmon/load/rl?/desc/<file name>
f. Reboot or telinit to a run level and watch your daemon loaded automatically.

P.S. And you probably want to know if the daemon loaded with errors and which daemons loaded and did not load with errors.

This is all speculation. Perhaps one day someone high up in the Linux food chain will say, "Hey, that's a great idea!" and make it happen.

---

### Post by 23meg on 2006-01-15
Hmm,
> 1. Is it loaded right now in my current run level?
```
ps ax |grep daemon_name
```
> 2. Does it usually load in my current run level?

ls /dmon/load/current

3. Does it usually load in a particular run level?

ls /dmon/load/rl?
(where ? is a # 1-5)Distro-specific; in Debian you can do a slocate in /etc/rcX.d to determine this, and I'd be surprised if there isn't a better way
> 4. What is the description of the daemon?

cat /dmon/load/rl?/desc/*```
apt-cache search foo
```comes close; I'm sure there's a more intricate way that will bring it closer
> 5. Can I load/reload, unload, or bounce it now?Your UID compared to the present UID of the daemon via ps and grep can deliver this.
> 6. How can I create my own daemon and execute it at a certain run level?This is distro-specific and can be made easier with a small bash script.

---

### Post by LordHunter317 on 2006-01-15
[QUOTE=SuperMike]I* Daemons usually have 6 things you usually want to know or do with them:
1. Is it loaded right now in my current run level?[/quote]Pretty easy to verify via ps | grep, looking in /var/run, or some init scripts even have the ability to tell you.

> 2. Does it usually load in my current run level?Looking at the /etc/rc.d directory for your runlevel or using a tool like sysv-rc-conf will tell you.

> 3. Does it usually load in a particular run level?I fail to understand what you want by this.

> 4. What is the description of the daemon?There will never be any standard way to provide this.  Technically speaking, a "daemon" is any process that's it's own TTY session leader and has detached from the terminal.  The daemon() library call doesn't require any sort of description, and any relevant Linux standards fail to provide a mechanism for providing it to the sysadmin.

> 5. Can I load, unload, or bounce it now?The initscripts are supposed to be able to safely handle all cases.

> 6. How can I create my own daemon and execute it at a certain run level?In what language?

> * For each of these things, it seems these could be easily translated into the file metaphor:No, not really.  Processes aren't really treated like files for a reason.  Even /proc doesn't let you do all sorts of useful manipulations to processes.

> 6. How can I create my own daemon and execute it at a certain run level?

a. Edit a Bash script to load your daemon. No special code needs to be inside. Give the script a name without a file extension on the end.No, it's far more complicated and special code very well may need to be inside.

> This is all speculation. Perhaps one day someone high up in the Linux food chain will say, "Hey, that's a great idea!" and make it happen.It's more complicated than that, because things like this go all the way back to POSIX and SUS.


[quote=23meg]Distro-specific; in Debian you can do a slocate in /etc/rcX.d to determine this, and I'd be surprised if there isn't a better way[/quote]It isn't distro-specific and ls is the better way.  Only pre-LSB distros will not have /etc/rcX.d runlevels.

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=SuperMike]
6. How can I create my own daemon and execute it at a certain run level?

a. Edit a Bash script to load your daemon. No special code needs to be inside. Give the script a name without a file extension on the end.
[/QUOTE]

I could be wrong, but I think that is what init and /etc/inittab are for.

---

