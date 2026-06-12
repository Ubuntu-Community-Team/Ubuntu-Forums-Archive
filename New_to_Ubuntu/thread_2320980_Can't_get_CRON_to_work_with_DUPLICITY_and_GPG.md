---
title: "Can't get CRON to work with DUPLICITY and GPG"
date: 2016-04-19
forum: New to Ubuntu
---

### Post by Stef2016 on 2016-04-19
Hello! 

I'm pretty new to the whole linux thing and trying to learn by setting up little local headless server using Ubuntu Server 14.04.

One of the things that i need is a automatic backup to external HDD every couple of hours. I also want the files to be encrypted in some way. 
After some research i figured the best way to do this would be Duplicity. So i followed [this]("https://www.digitalocean.com/community/tutorials/how-to-use-duplicity-with-gpg-to-securely-automate-backups-on-ubuntu") guide, skipping the SSH thing.

I ended up with this script:  (located in */home/stef2/scripts/backup_notes.sh*)
```

#!/bin/sh

test -x $(which duplicity) || exit 0
. /root/.passphrase

export PASSPHRASE
$(which duplicity) --encrypt-key 8BA9D028 /server/temp/_Notes file:///media/transcend/backup/

```

The *passphrase* file is just 
```

PASSPHRASE="[COLOR=#ffa07a]<my_passphrase_here>[/COLOR]"

```
As the guide said, i made it only readable by root:
```
$sudo ls -la /root
...
-rwx------ 1 root root   22 Apr 18 16:56 .passphrase
...

```

Also following the instructions, i've created a key:
```
$ sudo gpg --list-keys
/home/stef2/.gnupg/pubring.gpg
------------------------------
pub   2048R/8BA9D028 2016-04-19
uid                  Butt Pirate (aaa) <[COLOR=#ffa07a]my_email[/COLOR]>
sub   2048R/96870DC1 2016-04-19


```
The passphrase i used creating the key is the same as in the *passphrase* file.

[SIZE=3]**And the script works!**
[SIZE=2]When i run it from the shell, it does the backup:[/SIZE]
[/SIZE]```
$ sudo ./backup_notes.sh
Synchronizing remote metadata to local cache...
Deleting local /home/stef2/.cache/duplicity/db36b31bd40a4143dea5e32e2b87af6b/duplicity-full-signatures.20160419T112620Z.sigtar.gz (not authoritative at backend).
Deleting local /home/stef2/.cache/duplicity/db36b31bd40a4143dea5e32e2b87af6b/duplicity-full.20160419T112620Z.manifest (not authoritative at backend).
Deleting local /home/stef2/.cache/duplicity/db36b31bd40a4143dea5e32e2b87af6b/duplicity-inc.20160419T112620Z.to.20160419T115851Z.manifest (not authoritative at backend).
Deleting local /home/stef2/.cache/duplicity/db36b31bd40a4143dea5e32e2b87af6b/duplicity-inc.20160419T115851Z.to.20160419T122040Z.manifest (not authoritative at backend).
Deleting local /home/stef2/.cache/duplicity/db36b31bd40a4143dea5e32e2b87af6b/duplicity-new-signatures.20160419T112620Z.to.20160419T115851Z.sigtar.gz (not authoritative at backend).
Deleting local /home/stef2/.cache/duplicity/db36b31bd40a4143dea5e32e2b87af6b/duplicity-new-signatures.20160419T115851Z.to.20160419T122040Z.sigtar.gz (not authoritative at backend).
Last full backup date: none
No signatures found, switching to full backup.
--------------[ Backup Statistics ]--------------
StartTime 1461068463.72 (Tue Apr 19 15:21:03 2016)
EndTime 1461068463.78 (Tue Apr 19 15:21:03 2016)
ElapsedTime 0.06 (0.06 seconds)
SourceFiles 18
SourceFileSize 1978115 (1.89 MB)
NewFiles 18
NewFileSize 1978115 (1.89 MB)
DeletedFiles 0
ChangedFiles 0
ChangedFileSize 0 (0 bytes)
ChangedDeltaSize 0 (0 bytes)
DeltaEntries 18
RawDeltaSize 1977435 (1.89 MB)
TotalDestinationSizeChange 88880 (86.8 KB)
Errors 0

```
Not sure about the *cache* thing, but it does the job.
One thing the guide doesnt mention though, is that the script only works if run by *root.* Other users can't open the *passphrase* file.

[SIZE=3]**However, i can't get it to work with *cron.   ***[/SIZE]
As the script only works for *root*, i figured i need to use the *root*'s crontab. I've also set for it to run every minute, instead of couple hours, just so i can test it faster, and tried to log the process to file.

Heres *root*'s crontab (*/tmp/crontab.WX2EPC/crontab*):
```
# m   h  dom mon dow   command
  */1 *  *   *   *     /home/stef2/scripts/backup_notes.sh > /var/log/backup_test/log1.log 2>&1


```

From the log i can guess that this is the *gpg* problem, but i have no idea how to fix it. The script doesn't have any problems with keys when run manually.
```
$ cat /var/log/backup_test/log1.log
Synchronizing remote metadata to local cache...
Copying duplicity-full-signatures.20160419T122103Z.sigtar.gpg to local cache.
GPGError: GPG Failed, see log below:
===== Begin GnuPG log =====
gpg: encrypted with RSA key, ID 96870DC1
gpg: decryption failed: secret key not available
===== End GnuPG log =====


```

Being new to cron, i've tried different commands seen around the internet, but all of them are failing, for one reason or another:
```
#  */1 *  *   *   *     /bin/sh /home/stef2/scripts/backup_notes.sh > /var/log/backup_test/log1.log 2>&1
#  */1 *  *   *   *     root /home/stef2/scripts/backup_notes.sh/ > /var/log/backup_test/log1.log 2>&1
#  */1 *  *   *   *    cd /home/stef2/scripts && sudo ./backup_notes.sh > /var/log/backup_test/log1.log 2>&1


```

I've also made sure that i have empty lines at the end of the *crontab* file.

I've been stuck on this for many hours and could not find any more ideas on google, so please help a noob out! It feels like the solution i'm missing is very simple one, but i just can't get it!
Also, sorry for any mistakes, i'm not a native speaker and don't use forums much.

- Stef

---

### Post by TheFu on 2016-04-19
Others can't open the passphrase file by design.  This is normal, expected, behavior based on the file ownership and permissions.  The guide has to assume "some" level of knowledge.

Running system-level backups as root is pretty standard. After all, most userids cannot even view the entire file system containing the most important files which need to be backed up.  There are techniques to avoid this - you'll understand those when you are ready and more familiar with Unix. Some books document these different backup techniques.  I use a root-equiv userid, but my backups are network-based, so ssh is a core part of them.  Running the backups on a single system, there really isn't anything to be gained by doing that.

Don't run a job that takes over a minute, every minute.  Try 1.5x the amount of time it requires to complete to start.  Make certain you don't try to write backups to the same locations at the same times too.  I suspect (but do not know) that duplicity expects only 1 backup task to be running at a time.  Really, when using duplicity, hourly should be able the shortest backup interval.  If you want quicker backups, use LVM snapshots. Shouldn't be too hard to make them every 5 minutes, plus they are nearly instantaneous.  They don't move any data to backup media, but they are useful to freeze a file system for 24 hrs while the duplicity backup is run. There are different techniques for how to handle multiple LVM snapshots for backups - I'd probably take a snapshot hourly and remove them when the duplicity backup is finished with the snapshot.  24 snapshots in a day shouldn't take very much storage.

Sub-daily backups are usually handled using block-storage replication, BTW. Did you look into that?  Or did you look into a clustered file system with built-in network redundancy?  The right tool for the right job.  Not that duplicity isn't a workable option, just ... all those backups to keep track about would get unwieldily quick.  Heck, even the weekly-full vs daily incremental had me running away from duplicity for a different tool that only needs 1 "full" backup, then builds diffs off that forever.  Not to day that duplicity doesn't check all the boxes for a "best practices" backup tool - it does and I think it is the only tool which can with everything all-in-one.  The tool I use doesn't store files encrypted - but running encfs solves that completely.  The power of Unix is that small tools can be put together to make a total solution.  The kitchen-sink model of application design isn't needed.

Next, understand that cron doesn't come with much environment.  The script needs to setup any required environment needed. An interactive/shell environment is different, as you've seen.  Pretty much every program in your scripts needs to be fully specified in the path to run it.  "duplicity" should be ... "/usr/bin/duplicity" - for example. NEVER assume a PATH environment exists in cron.  This is a scripting "best practice." For a few more:  [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

sudo should not be used inside a cron script.  Run the entire script as root and chagne userids as needed with /bin/su - specify the full-path-to every program in the scripts.

To increase confusion (or provide more flexibility), root has a few different places where crontabs can be created.  There are different file formats, which can be confusing too.  There's the **sudo crontab -e** way, there's the /etc/crontab file and there's the /etc/cron.d/ directory. Each has a different purpose, but can be used for backups.

You've done well to get this far, BTW.   Guess I've shared enough.  Well done.  Hopefully something above will get you passed the issues.

---

### Post by Stef2016 on 2016-04-19
Thank you TheFu for your kind words and suggestions.

I did correct my script as you've suggested, this truly a good idea. I do realise that my backup is not the most efficent, since i don't even use network (SHH part), but i wanted to start with something simple.
I've also looked into LVM snapshots, and this is definitely something that i will try to do later. I actually *did *set up a LVM partition spread across 3 drives when i was installing this system, but right now its 99% full and i need more time to clean it up.

But i'm glad to say that after a couple more hours i've actually [SIZE=3]**found the solution**[/SIZE] myself!

One thing that i've noticed accidently, is that the script did not ran when i was *logged in *as root. Which i thought was odd, since it worked when i was logged in as user and used sudo.
As far as i understand, after some research, the *root *and *stef2 *userids had separate... "keyrings"? i guess?
```
# gpg --list-keys
```
when run under *root* userid returned empty list. So when cron ran my script under root, and tried to use public key, it simply wasn't there.

Using [gpg commands]("http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/gpg-cs.html"), i've exported keys under my userid, imported them to *root*'s "keychain", and made them "trusted".

And it did the trick! The cron job gets executed, files get backed up, and the log confirms it!

I've figured i should post the solution here, since i myself couldn't find it online. 

Thank you again!

---

### Post by TheFu on 2016-04-19
Thanks for posting the solution.  It makes complete sense.  Unix/Linux is multi-user and programs running as root would try to access settings known to root, not some other userid.  Takes some time to get used to that.

Also, the default environment for root is **very** different from that of a normal userid.  The root account must work when other accounts don't, so this is smart.  KISS.

---

