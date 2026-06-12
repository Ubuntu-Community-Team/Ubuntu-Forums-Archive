---
title: "Can't boot anymore after a series of malfunctions"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by comp3000 on 2012-09-14
The computer has an old version of Ubuntu (11.04) that I need to upgrade, after I do a file backup. Previously, another Absolute Beginner (who's even more green) had been using the machine, and told me that it failed to boot up at some point. 
Instead of booting, it displayed this screen:  
* Starting MTA speech-dispatcher disabled; edit   /etc/default/speech-dispatcher   [OK] 
* Starting Bluetooth * PulseAudio configured for per-user sessions saned disabled; edit    /etc/default/saned 
* Enabling additional executable binary formats  binfmt-support    [OK] Starting smfpd daemon&#8230;done Process smfpd [1511] is running   [OK]
Checking battery state...   [OK] 

(It lags here and doesn't boot.)   

After that, there were several other malfunctions:  
I had to use Ctrl-Alt-Delete and do hard reboots to make it boot.  I don't know if that might have damaged the filesystem.
I couldn't save changes to files. For example, when I tried to edit and save a text file, it said that there wasn't enough disk space to save the file -- "Please free some disk space and try again."
When I looked at the Disk Usage Analyzer, it showed that the directory  /var  was taking up 89% of total filesystem capacity.
I looked at the System Monitor, and the System Status showed  "Available disk space: 0 bytes".  
Whenever I looked at the Properties of files, there was a huge discrepancy between the total size of files Vs. "Size on disk". E.g. the directory  /home  had "Size on disk" listed as 35 GB, but Total size of files was only listed as 4.3 GB.
I ran a Memory test, but after 4+ hours, it still wasn't complete.
At the Recovery Menu, I tried "clean" to try to make free space, but nothing happened. Also, none of the other options on the menu were functional, including failsafeX.
Now, the machine no longer boots.  When I type  Ctrl-Alt-F1 or -F2, I get a screen that allows me to log in and type commands, but I don't know what to type. If anyone can help me out, I'd greatly appreciate it. Thanks.

---

### Post by Bucky Ball on 2012-09-14
Welcome to the forums. 

You may have more luck with this if you edit it for clarity (e.g. paragraphs) because currently nearly unreadable. Cheers and good luck. ;)

Code can be placed in code tags by clicking 'Go Advanced' and using the # icon.

---

### Post by mips on 2012-09-14
Connect a external drive with free space to the pc, boot a livecd, backup all the files you need to the external drive, format & reinstall. 

You do not intent keeping the current OS so I see no point in trying to fix it.

---

### Post by comp3000 on 2012-09-14
Thanks for answering.  
To Bucky: I just realized I had scripting turned off... 
To mips: Thanks for the suggestion, but I don't think my external flash drive has enough space, and I'd like to see if I can boot by entering some commands.

---

### Post by doktorOblivion on 2012-09-14
Can you run:

df -a

Perhaps that will show us where all the space is going?  Oh, cut and paste the results to this thread.

---

### Post by Wim Sturkenboom on 2012-09-14
I suggest that you boot into recovery mode and drop to a root shell. Next run *_apt-get clean_* to clean the cache with updates and installed programs (this does not remove programs or updates, just cleans the cache)
Next run *_fdisk -l_* (lower case L), *_df -h_* and *_du -h --max-depth=1 /_* and post the results (between [noparse]```
 and 
```[/noparse]).

---

### Post by doktorOblivion on 2012-09-14
Be aware, max-depth might not be available in your distro, not sure.  However, df -a will give us more than enough.

```

~$ df -h --max-depth=1
df: Unbekannte Option »--max-depth=1«
„df --help“ gibt weitere Informationen.

```

The apt-get clean is a good idea, definitely try that.

---

### Post by comp3000 on 2012-09-14
Thanks for answering. I tried Wim's suggestion, and  apt-get clean  apparently didn't work-- when I typed it and hit Enter, nothing happened. But the other commands did work.
Just one question: I can't boot, so how do I copy and paste the data output? Is this possible without a CD?
Thank you.

---

### Post by doktorOblivion on 2012-09-14
If you can just type in anything that might look suspicious, e.g.:
```

~$ df -a
Dateisystem      1K-Blöcke  Benutzt Verfügbar Verw% Eingehängt auf
/dev/sda1        278860856278860800        [COLOR="Red"]56   99% /[/COLOR]
proc                     0        0         0     - /proc
sysfs                    0        0         0     - /sys
none                     0        0         0     - /sys/fs/fuse/connections
none                     0        0         0     - /sys/kernel/debug
none                     0        0         0     - /sys/kernel/security
udev               2054784        4   2054780    1% /dev

```
See first line?  This indicates that the root f/s is technically out of space.  Do you see any thing like that?

---

### Post by comp3000 on 2012-09-14
Thanks, for  /dev/sda1 it says:
Size    Used    Use% 
71G    68G      100%

As I wrote in my original post, the computer had indicated that the vast majority of the space was being taken up by  the directory /var  (specifically, /var/log) but I don't know why...

---

### Post by doktorOblivion on 2012-09-14
Try this, if you can obtain a command line, clean up /var/log dir.
```

ls -al /var/log/*

```
This might show you what's eating up all the space.  If you can figure out which log is using all the space, edit it or just delete it.  However, I would take a look at it to see what might be causing the log to fill up.

---

### Post by comp3000 on 2012-09-14
To doktor: Thanks, when I enter that command it outputs a long list, the last 6 entries of which end in a string of red-colored text:
[...] unattended-upgrades.log.1.gz
[...] unattended-upgrades.log.2.gz
[...] unattended-upgrades.log.3.gz
[...] unattended-upgrades.log.4.gz
[...] unattended-upgrades.log.5.gz
[...] unattended-upgrades.log.6.gz

They are all dated from the 1st or 2nd day of each of the last 6 months.
How do I scroll through the list, and what do I look for? 
Again, thanks for the help.

---

### Post by nothingspecial on 2012-09-14
> **comp3000 said:**
> I selected the wrong prefix for a previous thread by mistake and I'd like to change it. Can  you tell me how to do this, or is it something only a moderator can do?  Thanks.

Done.

---

### Post by Wim Sturkenboom on 2012-09-14
> **doktorOblivion said:**
> 
```

~$ df -h --max-depth=1
df: Unbekannte Option »--max-depth=1«
„df --help“ gibt weitere Informationen.

```

max-depth is for du, not for df :)

---

### Post by doktorOblivion on 2012-09-14
I would recommend from the /var/logs directory where you see all those repeated files with small changes to their names:

```

rm -fr unattended-upgrades.log*

```

See if that provides any relief.  Run the df -a or the correct du command mentioned before that I goofed on to see if it worked.  You may have to remove [delete] other stuff as well.

I am guessing this system does not have a lot or storage to begin with...

---

### Post by Wim Sturkenboom on 2012-09-14
> **comp3000 said:**
> 
They are all dated from the 1st or 2nd day of each of the last 6 months.
How do I scroll through the list, and what do I look for? 

```

ls -lS

```
^will sort by size
```

ls -lt

```
^will sort by date/time (newest first)
```

ls -lrt

```
^will sort by date/time (oldest first)

And you can pipe the result through 'less' (see below) so you can scroll up and down

```

ls -lS | less

```

---

### Post by comp3000 on 2012-09-14
> **nothingspecial said:**
> Done.
Thanks, my finger slipped. 
Cheers. ;)

---

