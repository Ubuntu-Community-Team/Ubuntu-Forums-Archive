---
title: "Need help to get script to run on startup"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by dustin_wielenga32 on 2008-11-23
Hello, I am attempting to get the following script to run on startup:
```
./fah6 -verbosity 9 < /dev/null > /dev/null 2>&1 &
```
The script is under /home/dustin/fah/fah.

When I type "home/dustin/fah/fah", the program starts, as I can see under System Monitor.

My crontab currently looks like:
```
@reboot /home/dustin/fah/fah
```

However, it does not begin on startup.  Any idea what I am doing wrong here?

Thanks in advance, Dustin

---

### Post by shifty_powers on 2008-11-23
could you just not use sessions to start that on startup?

---

### Post by dustin_wielenga32 on 2008-11-23
How is that done?  I've been doing some searching, and there's a bunch of stuff about /etc/init.d, or /etc/rc.5 and stuff like that.  What would I put there?

Thanks, Dustin W.

---

### Post by shifty_powers on 2008-11-23
system>preferences>sessions

startup items tab, add item, fill out name, command comment, press add.

reboot.

should be ok :D

---

### Post by binbash on 2008-11-23
> **shifty_powers said:**
> system>preferences>sessions

startup items tab, add item, fill out name, command comment, press add.

reboot.

should be ok :D

If this does not work, you can write the script to etc/rc.local

---

### Post by hyper_ch on 2008-11-23
if you want to add scripts to the boot routine have a look at the
```

update-rc.d

```
command

---

### Post by lswb on 2008-11-23
Does your script really need to run at boot, or just whenver you log in? If the latter, you can add it to .profile in your home directory, or to Main Menu/System/Preferences/Sessions like shifty_powers suggested.

If you really do want it to run at system boot time, then you can call it from /etc/rc.local.

Both /etc/rc.local and your home/username/.profile should have explanatory comments. For /etc/rc.local make sure anything you add is before the "exit" line.

---

### Post by dustin_wielenga32 on 2008-11-23
I'm not sure if it needs to run at boot, but the idea is to have it run once per computer load-up, and if possible, to not stop even when the user logs out. That's not a huge deal however, so long as it auto-starts when I log in, I'll be happy.

It's still not working, and I'm not sure why.  Here's the current setup:

/usr/local/bin/startfah
```
#! /bin/sh
FoldDir=/home/dustin/fah
cd $FoldDir
./fah6 -verbosity 9 < /dev/null > /dev/null 2>&1 &
```

When I run "startfah" from a regular directory, it starts, according to the System Monitor.

I copied the same file to"/etc/init.d/startfah", so it also looks like:
```
#! /bin/sh
FoldDir=/home/dustin/fah
cd $FoldDir
./fah6 -verbosity 9 < /dev/null > /dev/null 2>&1 &
```

Next, I ran
```
 sudo ln -s /etc/init.d/startfah /etc/rc5.d/S99starfah
```

Doing a cat on /etc/rc5.d/S99startfah produces:
```
#! /bin/sh
FoldDir=/home/dustin/fah
cd $FoldDir
./fah6 -verbosity 9 < /dev/null > /dev/null 2>&1 &
```

However, after trying to restart a bunch of times, it still fails to show up in System Monitor.  I then can run "startfah" to start it, and it shows up.

So all I need to do is to get something to run the commands in "startfah" on startup.  Any idea where I'm messing up now?

Thanks for all your advice so far.

---

### Post by lswb on 2008-11-23
ubuntu by default starts in runlevel 2, so maybe try making your link from /etc/rc2.d 
Or, you could put the contents of your "startfah" script in /etc/rc.local and it would run for all runlevels except single-user/recovery. Also make sure the copy in /etc/init.d has executable permissions set.

---

### Post by hyper_ch on 2008-11-24
just use update-rc.d to link to according levels...

---

