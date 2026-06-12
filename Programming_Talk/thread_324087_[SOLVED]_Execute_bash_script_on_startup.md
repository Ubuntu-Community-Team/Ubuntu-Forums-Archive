---
title: "[SOLVED] Execute bash script on startup"
date: 2006-12-23
forum: Programming Talk
---

### Post by mogliii on 2006-12-23
Hi,

I already posted once here:
[http://www.ubuntuforums.org/showthread.php?t=279723]("http://www.ubuntuforums.org/showthread.php?t=279723")

The point is:
I wrote a backup script for my dad, including deleting of the oldest backup (so at least one backup is present at anytime), backing up, noting everything in a log file and sending this file via mutt to me, so I can see if he backed up and if it was successful.

But, I still didnt find a way to start the script after startup. rc.local is not the right place.
reason? 
The script shuts down the computer at the end, and the script in rc.local can not be stopped with Ctrl+C. So: the only way to access the system is actually to use a live cd.

Now I am not sure if it is possible to set up a cron-job that executes once as soon as the computer is booted?

Please help me. Would increase the acceptance by my father extremely if he only has to choose another boot menue option for a full system backup!

---

### Post by rowanparker on 2006-12-23
You can make it execute on login by adding it to start up programs in System > Preferences > Sessions.

---

### Post by studiesrule on 2006-12-23
Another way, which I now do not recommend (but was earlier the only way I knew, Thanks rowan), is modify the /etc/rc.local file. This will run a script only after all other scripts have been loaded.

---

### Post by thomasaaron on 2006-12-23
Add it to your /etc/anacrontab file.

Then it will run at whatever interval you want (including daily)

---

### Post by mogliii on 2006-12-31
Hi,

How do I do this with Cron. I havent used cron before, but as far as I could look over it on the intertet, I have to specify a minute or hour. But I cannot say once at startup?!?

Can anyone help me with that?

---

### Post by phossal on 2007-01-01
You can execute bash commands via .bash_profile on startup, which is executed once at login.

---

### Post by winch on 2007-01-01
> **phossal said:**
> You can execute bash commands via .bash_profile on startup, which is executed once at login.

That requires a login though.

From [http://en.wikipedia.org/wiki/Init#Skipping_init](http://en.wikipedia.org/wiki/Init#Skipping_init)
> In Linux systems, with most modern bootloaders (such as LILO or GRUB), users can change which process the kernel spawns at the end of its initialization from the normal default of /sbin/init. This is generally done by typing init=/foo/bar at the bootloader's prompt. Appending init=/bin/bash, for example, will bring up a single root shell, without a password. If the system administrator feels that this is insecure, they may setup a BIOS password. Or in the case of GRUB, MD5 hashed boot passwords.

You should be able to create a grub menu item that runs your script instead of init.

I think you can also use the bootloader to configure which runlevel to boot into. Runlevel 4 is typically unused so you could use that runlevel for your script.Then it's just a matter of editing the contents of /etc/rc4.d/ to run what you want.

---

### Post by mogliii on 2007-11-15
Hi,

I found a way to do what I asked above. *Using Ubuntu 7.10 by now.*

What I found out is, that grub is passing its parameters it used for booting to ```
/proc/cmdline
```

So here is the way I used. I am sure it is not clean, but it works:


**Step 1:**
Change the script you wish to execute and add the following lines in the beginning:
```
#/bin/bash
if grep -q -v "identifier" /proc/cmdline;
then 
    exit 0;
else 
    echo "Starting backup";
fi
..
..
..

```


**Step 2:**
Edit /boot/grub/menu.lst. 
Duplicate the default ubuntu entry, and rename it in a meaningful way. For example "Backup and shutdown".
Append "identifier"(or whatever you want to name it. Has to match the script) to the kernel line:
```
kernel		/vmlinuz-2.6.22-14-generic root=UUID=xxxxxxx ro quiet splash [COLOR="Red"]identifier[/COLOR]
```


**Step 3:**
Its best to copy the script to /etc/init.d and don't forget to make it executable. Then, create a symlink in /etc/rc2.d to that script. e.g.
```
# ln -s /etc/init.d/backupscript S99backupscript 
```
Note: I am not 100% sure about this command. I used midnight commander.

Done.


Your backup script is executed every time you start. But only if you start with the backup menu entry in grub, "identifier" (or whatever you chose) will be written in /proc/cmdline. And only then your script will actually do the backup. If it can't find the identifier it will just exit.

---

