---
title: "Script cannot access external HDD (ntfs)"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by Kjeldgaard on 2012-12-31
Hi all,

I have been trying to setup up a script that copies files/folders to an external hdd when a torrent is finished in Transmission. I did not succeed and I therefore made this dummy/debug script.

```

#!/bin/bash
echo test > /home/xbmc/Complete/test.txt

```

This works perfect. The script is correctly triggered, and the test.txt file is created in the specified folder on the internal hdd.

When I modify the script such that the target folder is on the external hdd, the test.txt file is NOT created.

```

#!/bin/bash
echo test > /media/xbmc/MedieHD/Complete/test.txt

```

If the user "xbmc" executes the script, the test.txt file is created as expected. Based on this, I thought it was the folder permissions that were set incorrect. But the output of
```
ls -l
```
for the two folders are almost the same, at least the permission and owner part:

/home/xbmc/
```
drwxrwxr-x  6 xbmc debian-transmission     4096 Dec 31 12:15 Complete

```

/media/xbmc/MedieHD/
```
drwxrwxr-x 1 xbmc debian-transmission  4096 Dec 31 06:44 Complete

```

The external hdd mount command in /etc/fstab is:
```
UUID=8030C79D30C79914   /media/xbmc/MedieHD     ntfs-3g defaults,uid=1000,gid=117,umask=002 0 0

```

Where the uid and gid are determined from
```
id xbmc
uid=1000(xbmc)
```
and
```
id debian-transmission
gid=117(debian-transmission) 
```

Based on all the above, my conclusion is that I have set the correct ownership and permission. But why is it STILL not working? Is it really because the target is an external hdd and has some "inbuilt" limitations?! Or is the user of the script (when executed upon torrent finish) not "debian-transmission" when accessing the external hdd. But all this is just speculations and way beyond my Ubuntu knowledge, unfortunately.

It has been driving me insane for the last 2 days... And it is the only thing I am missing from having the perfect HTPC setup. Hope you can help me out!

Bonus info:
OS: XBMCbuntu 12.00RC2
HW: Asrock ION 330
Transmission 2.74

Thanks in advance,
Kjeldgaard

---

### Post by sudodus on 2012-12-31
I think that it is a problem with permissions. Maybe you are running the script as another user. Try to insert the following line into the script
```
whoami>/tmp/user
``` and check afterwards with the following command
```
cat /tmp/user
```
and you will find out.

Maybe you can change how you mount the external drive so that everybody gets write access, now only user and group have write access but not others.

---

### Post by Kjeldgaard on 2012-12-31
Hi sudodus.

Thank you very much for your suggestions!

I inserted
```
whoami > /tmp/user
```

in the script and the output for both versions (internal and external hdd target) was:
```
debian-transmission
```

At least that make sense. And again running the
```
ls -l
```
for folder /media/xbmc/MedieHD/Complete gives:
```
drwxrwxr-x 1 xbmc debian-transmission  4096 Dec 31 06:44 Complete

```
which as I understand is correct, so that does still not make sense to me.

I have just given everybody writing right, rebooting now, and I'll be back with the result in 5 minutes.

One more thing, what is the difference of 'ntfs' and 'ntfs-3g' in the /etc/fstab?

Thanks,
Kjeldgaard

---

### Post by sudodus on 2012-12-31
> **Kjeldgaard said:**
> ...
One more thing, what is the difference of 'ntfs' and 'ntfs-3g' in the /etc/fstab?


I guess in the beginning it meant using different drivers for the NTFS file system. The **3g** version allowed writing too. But I think that in some systems today ntfs is an alias for ntfs-3d if that driver is installed, and you will be able to write by default.

Anyway it is should be OK to have ntfs-3g in /etc/fstab.

Good luck :-)

---

### Post by Kjeldgaard on 2012-12-31
Ok, I just changed the /etc/fstab such that everybody has writing permissions in /etc/fstab.

```
UUID=8030C79D30C79914   /media/xbmc/MedieHD     ntfs-3g defaults,uid=1000,gid=117,umask=000 0 0

```

And confirming the change with
```
drwxrwxrwx 1 xbmc debian-transmission  4096 Dec 31 13:35 Complete

```

But the script is still not able to create the test.txt file!

Again, to check that I didn't make a typo, I executed the script from  a terminal, and the test.txt file was created. And in the /tmp/user was written xbmc, just as expected.

So I am still VERY confused! 

Cheers,
Kjeldgaard

---

### Post by fdrake on 2012-12-31
can you pleas post the output of the command
```
touch /media/xbmc/MedieHD/test
ls -al /media/xbmc/MedieHD/test
```

---

### Post by sudodus on 2012-12-31
try to cd to the directory on the external drive

```
cd /media/xbmc/MedieHD/Complete
```

and ```
echo test>test.txt
```

This would eliminate some risk typing errors.

Or try copying some file with the cp command or the file browser! Will it work?

---

### Post by Kjeldgaard on 2012-12-31
> **fdrake said:**
> can you pleas post the output of the command
```
touch /media/xbmc/MedieHD/test
ls -al /media/xbmc/MedieHD/test
```

```
touch /media/xbmc/MedieHD/test
```

does not give any output.

```
ls -al /media/xbmc/MedieHD/test
```
outputs
```
-rwxrwxrwx 1 xbmc debian-transmission 0 Dec 31 14:03 /media/xbmc/MedieHD/test


```

---

### Post by Kjeldgaard on 2012-12-31
> **sudodus said:**
> try to cd to the directory on the external drive

```
cd /media/xbmc/MedieHD/Complete
```

and ```
echo test>test.txt
```

This would eliminate some risk typing errors.

Or try copying some file with the cp command or the file browser! Will it work?

This works fine, a test.txt is created. Basically, I can copy files back and forth (internal and external) in file managers and in the terminal. It is only when the dummy script is triggered by transmission daemon that the access to the external hdd is "lost".

I starting to think if it is a Transmission problem...

---

### Post by sudodus on 2012-12-31
> **Kjeldgaard said:**
> This works fine, a test.txt is created. Basically, I can copy files back and forth (internal and external) in file managers and in the terminal. It is only when the dummy script is triggered by transmission daemon that the access to the external hdd is "lost".

I starting to think if it is a Transmission problem...
When you run the script triggered by transmission daemon, what is the user (as shown by whoami>/tmp/user)?

---

### Post by fdrake on 2012-12-31
the mistake is in your fstab options

edit :

```

sudo cp /etc/fstab /etc/fstab.bk
gksudo gedit /etc/fstab

```

change the previous line of the NTFS drive with this one
> UUID=8030C79D30C79914   /media/xbmc/MedieHD     ntfs-3g defaults 0 0
restart pc

---

### Post by Kjeldgaard on 2012-12-31
> **sudodus said:**
> When you run the script triggered by transmission daemon, what is the user (as shown by whoami>/tmp/user)?

```
cat /tmp/user

```

outputs 

```
debian-transmission
```

---

### Post by sudodus on 2012-12-31
> **Kjeldgaard said:**
> ```
cat /tmp/user

```

outputs 

```
debian-transmission
```
... and debian-transmission should have write permissions (at least now, that everybody should have it).

Could there be a problem with path or the other environment variables, that do no exist in the environment, where the script is executed by transmission? If that is the case (as it is with cron, and transmission might use cron), then you should have the complete path to all commands. for example

```
/bin/echo
``` instead of echo etc. You find the path to installed commands with the command which, for example
```
which echo
```

---

### Post by Kjeldgaard on 2012-12-31
> **fdrake said:**
> the mistake is in your fstab options

edit :

```

sudo cp /etc/fstab /etc/fstab.bk
gksudo gedit /etc/fstab

```

change the previous line of the NTFS drive with this one

restart pc

Changed the line to
```
UUID=8030C79D30C79914 /media/xbmc/MedieHD ntfs-3g defaults 0 0
```

Still the same problem, no file is created. And debian-transmission is written to /tmp/user.

---

### Post by Kjeldgaard on 2012-12-31
> **sudodus said:**
> ... and debian-transmission should have write permissions (at least now, that everybody should have it).

Could there be a problem with path or the other environment variables, that do no exist in the environment, where the script is executed by transmission? If that is the case (as it is with cron, and transmission might use cron), then you should have the complete path to all commands. for example

```
/bin/echo
``` instead of echo etc. You find the path to installed commands with the command which, for example
```
which echo
```

Updated script to
```
#!/bin/bash
whoami > /tmp/user
/bin/echo test > /media/xbmc/MedieHD/Complete/test.txt

```

still the same... :(

Again, executed in terminal, and as usual that worked perfectly.

---

### Post by fdrake on 2012-12-31
> **Kjeldgaard said:**
> Updated script to
```
#!/bin/bash
whoami > /tmp/user
/bin/echo test > /media/xbmc/MedieHD/Complete/test.txt

```

still the same... :(

Again, executed in terminal, and as usual that worked perfectly.

Can you boot into the oldest kernel you have and try if the scrip works

Is it neccessary for you that the driver is ntfs can you reformat it to ext2/3/4?

---

### Post by sudodus on 2012-12-31
This is a hard nut!

1. Are you sure that the script is run by Transmission at all? When run by Transmission, is it writing the info about the user to /tmp? In that case it has been running.

2. Can the script (run by Transmission) write a redirected echo to /tmp ?
```
/bin/echo test > /tmp/test.txt
```

If this is the case, there is still something with the permissions to write to the external drive, maybe some limit set by Transmission. In that case, maybe you can let it write to your internal drive and later on (manually or with a script) move it to your external drive.

*Edit*: or switch to an ext file system as suggested by fdrake

---

### Post by Kjeldgaard on 2012-12-31
> **fdrake said:**
> Can you boot into the oldest kernel you have and try if the scrip works

Is it neccessary for you that the driver is ntfs can you reformat it to ext2/3/4?

Did a clean install two days ago, this is the oldest kernel I have.

Reformat the drive is absolutely last option, unfortunately. I really don't understand such a simple task gives me such a headache :)

---

### Post by Kjeldgaard on 2012-12-31
> **sudodus said:**
> This is a hard nut!

1. Are you sure that the script is run by Transmission at all? When run by Transmission, is it writing the info about the user to /tmp? In that case it has been running.

2. Can the script (run by Transmission) write a redirected echo to /tmp ?
```
/bin/echo test > /tmp/test.txt
```

If this is the case, there is still something with the permissions to write to the external drive, maybe some limit set by Transmission. In that case, maybe you can let it write to your internal drive and later on (manually or with a script) move it to your external drive.

*Edit*: or switch to an ext file system as suggested by fdrake

1
As the /tmp/user contains debian-transmission it must be run by the transmission daemon, at least according to my logic.

2
Not following you here. Scripting is kind of new to me...

3 
I would really like to avoid reformating the hdd.

Background info.
Basically what I am trying to accomplish is to make a "one-time-copy"of all files/folders in the /home/xbmc/Complete to /media/xbmc/MedieHD/Complete. I thought this would be very easy with transmission triggering the script upon completion, I was wrong.
I you know of an easier way, I am all ears :)
In Matlab I could easily program it! But I am looking for a more light weight solution :) And beside Matlab, my coding skills are rather limited...

PSEUDO CODE:
-init empty file/folder list (only do once)

DO every 30 minutes or so
-compare "file/folder list" with "file/folder" currently in source folder
-all entries which are not in "file/folder list" copy to target folder
-after successful file/folder copy, add file/folder entry to "file/folder list"
-remove file/folder entries in "file/folder list" if deleted from source folder.
\DO
/PSEUDO CODE

Sorry for the dirty pseudo code, but this was how I would create a script (not triggered by Transmission) if I had the skills.

---

### Post by haqking on 2012-12-31
You could just use a different torrent client like qbittorrent or ktorrent which has a tick box which says "move completed torrents to" ;-)

And i thought transmission had that feature too ? [https://trac.transmissionbt.com/ticket/3754](https://trac.transmissionbt.com/ticket/3754)

---

### Post by sudodus on 2012-12-31
Maybe Transmission wants the downloaded files to stay where they were downloaded, so that they are available as seeds for others using Transmission. That could be a reason that the script gets limited write access.

Another option might be that you start a script yourself and that script in turn runs Transmission. And when Tranmission has finished, the script moves the files to the external drive. (Did I get it right, that a script started by you can write to the external drive?)

Disadvantage: You need workspace for the files to be stored temporarily on the internal drive.

---

### Post by Kjeldgaard on 2012-12-31
> **haqking said:**
> You could just use a different torrent client like qbittorrent or ktorrent which has a tick box which says "move completed torrents to" ;-)

I am already using that option in Transmission as well, and it works. What I would like to have is two copies of the completed file(s). 1 copy on the internal hdd and 1 copy one the external hdd. The "move completed torrent to" only leaves 1 copy.

---

### Post by haqking on 2012-12-31
> **Kjeldgaard said:**
> I am already using that option in Transmission as well, and it works. What I would like to have is two copies of the completed file(s). 1 copy on the internal hdd and 1 copy one the external hdd. The "move completed torrent to" only leaves 1 copy.


ahhhh ok, gotcha.

---

### Post by sudodus on 2012-12-31
> **Kjeldgaard said:**
> I am already using that option in Transmission as well, and it works. What I would like to have is two copies of the completed file(s). 1 copy on the internal hdd and 1 copy one the external hdd. The "move completed torrent to" only leaves 1 copy.
Oh, well, this info will help.

I suggest that you make a separate script, that you run manually or from cron. And in this script you run

***rsync***

It is well documented, see ```
man rsync
``` to copy new files from the internal drive to the external one. For example

```

rsync -av /home/xbmc/Complete/ /media/xbmc/MedieHD/Complete

```

---

### Post by Kjeldgaard on 2012-12-31
> **sudodus said:**
> Maybe Transmission wants the downloaded files to stay where they were downloaded, so that they are available as seeds for others using Transmission. That could be a reason that the script gets limited write access.

Another option might be that you start a script yourself and that script in turn runs Transmission. And when Tranmission has finished, the script moves the files to the external drive. (Did I get it right, that a script started by you can write to the external drive?)

Disadvantage: You need workspace for the files to be stored temporarily on the internal drive.

I don't think this is the case. When transmission trigger this script it works as long as the target folder is on the internal hdd:

```
#!/bin/sh
if [ -e "$TR_TORRENT_DIR/$TR_TORRENT_NAME" ]; then
cp -R "$TR_TORRENT_DIR/$TR_TORRENT_NAME" "/your/path/to/copies/" 2>/dev/null
fi
```

And I just realized that this is probably the best solution.
1: Call above script with temp-target folder on internal hdd.
2: In the temp-target folder everything is moved to the target folder on the external hdd.

Disadvange, double amount of space required for some time.

Anybody knows a "move-everything" script that runs every X minutes/hours?

Thanks,
Kjeldgaard

---

### Post by sudodus on 2012-12-31
> **Kjeldgaard said:**
> 
Anybody knows a "move-everything" script that runs every X minutes/hours?

Thanks,
Kjeldgaard

See post # 24.

Copy directly from the original download using rsync. No need for another temporary copy.

---

### Post by Kjeldgaard on 2012-12-31
Thanks a lot guys, really appreciate the help.

I won't have time to test it today, but I'll get back with the outcome.

Happy New Year,
Kjeldgaard

---

