---
title: "rc.local doesnt run on boot"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by matthew1670 on 2013-12-24
hi all i cant seem to get my rc.local file to run when the system is booted any ideas why 

```
  GNU nano 2.2.6                 File: etc/rc.local


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
su  matthew -c "screen -d - m -S minecraft -c '~/minecraft/craftbukkit.sh'"


exit 0

```

---

### Post by ajgreeny on 2013-12-24
What do you expect the command in the file to do?

Ubuntu does not use the **su** command like most other Linux OSs, though I am not sure if this is the case when running commands in rc.local.

Can you also show the output of **ls -l /etc/rc.local** to make sure the file is marked as executable.

---

### Post by sisco311 on 2013-12-24
Ubuntu uses [Upstart]("http://upstart.ubuntu.com/"). While Upstart is backward compatible with the old init system, the rc.local file is often executed too soon (for example before the filesystems are mounted) during the boot process.

As a dirty fix you could add `sleep 10' command in the rc.local file to delay a bit the execution of your own command, but the proper way to run your command during boot would be to write an upstart job for it.

---

### Post by The Cog on 2013-12-24
I don't like the tilde '~' in there. I would suggest you try using the full path for any filenames, folder names and executable names. You can't rely on all the environment path settings being the same as when you log in normally.

EDIT:
There should not be a space between "- m".
You may need to change directory in that script too.
You may need to wait until networking is working too - minecraft may sulk if it can't open the network.

Because of these things, I think it may be best to make a small launcher script that rc.local can call. Somethign like this perhaps (don't forget to make it executable):
```
#!/bin/sh
cd /home/matthew
sleep 10
/usr/bin/screen -d -m -S /wherever/minecraft -c /home/matthew/minecraft/craftbukkit.sh
```

---

### Post by ian-weisser on 2013-12-24
rc.local *does* run at boot.
That's the problem.

"screen -d" reattaches a session to a working display. At boot, you don't have a working display yet.
Displays are assigned at login (not startup).

You should add the script to your login jobs, not to your startup jobs.

---

