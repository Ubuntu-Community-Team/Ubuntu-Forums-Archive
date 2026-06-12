---
title: "HOWTO: Beagle 0.2.16 on Edgy"
date: 2007-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by kelbizzle on 2007-02-17
[SIZE="2"]According to [/SIZE][Kevin Kubasik]("http://kubasik.net/blog")[SIZE="2"] over at [/SIZE][http://beagle-project.org/](http://beagle-project.org/)
[QUOTE=Kevin Kubasik] Ok, Ubuntu Edgy ships Beagle 0.2.9, that sucks. Beagle 0.2.16 is way better,[/QUOTE]

[SIZE="2"]Beagle is a search tool that ransacks your personal information space to find whatever you're looking for. More technically, Beagle is a Linux desktop-independent service which transparently and unobtrusively indexes your data in real-time. For example:
    * Files are immediately indexed when they are created, are re-indexed when they are modified, and are dropped from the index upon deletion.
    * E-mails are indexed upon arrival.
    * IM conversations are indexed as you chat, a line at a time.
    * Web pages are indexed as you view them (with a browser extension). [/SIZE]

[SIZE="3"] In this Guide/Howto we will Update your sources.list, Install Beagle, Install evolution-backends(optional), 
Install Beagle Firefox extension(optional). I have tested this on 6.10 Edgy. Kernel Version 2.6.17-11-386[/SIZE]

[SIZE="3"]
If you want Beagle 0.2.16, Edit Sources.list. In Terminal type:[/SIZE]
```
sudo gedit /etc/apt/sources.list
```

[SIZE="3"]Add this line at the bottom.[/SIZE]
```
#Beagle
deb http://beagle-project.org/files/ubuntu/edgy/ ./
#Beagle
```
[SIZE="3"]save, and close this.[/SIZE]
[SIZE="3"]
Update your sources.[/SIZE]
```
sudo apt-get update
```

[SIZE="3"]Install Beagle. In Terminal type:[/SIZE]
```
sudo apt-get install beagle
```
[SIZE="3"]
If you use Evolution install evolution-backend to index your evolution mail.[/SIZE]
```
sudo apt-get install beagle-backend-evolution
```
[SIZE="3"]
If you want the web pages you view in Firefox to be indexed. Download and install This extension in Firefox.[/SIZE]
[SIZE="2"][http://primates.ximian.com/~joe/beagle-firefox-extension-0.6.xpi](http://primates.ximian.com/~joe/beagle-firefox-extension-0.6.xpi)[/SIZE]
[SIZE="3"] Install it by going to File > Open then select the XPI. The extension will be installed after you restart firefox[/SIZE]
 
[SIZE="3"]Once everything is installed your ready to run Beagle. [/SIZE]
```
beagled
```
[SIZE="2"]There should be Menu Items in Applications > Accessories or System > Preferences[/SIZE]
[SIZE="3"]
You can see exactly what beagle is doing. In Terminal type:[/SIZE]
```
beagle-status
```

or Indexing
```

beagle-index-info

```
[SIZE="3"]
There is also a log located[/SIZE]
```
~/.beagle/Log/current-Beagle
```
[SIZE="3"]
If you want to make it index at full throttle (note this will really increase beagles priority)
In Terminal with *beagled* running type:[/SIZE]

```
beagle-shutdown
export BEAGLE_EXERCISE_THE_DOG=1
beagled
```

[SIZE="3"]IF YOU WANT TO REMOVE BEAGLE[/SIZE]
Shutdown Beagle 
```
beagle-shutdown
```
Remove Beagle (Note This will also remove the evolution-backend)
```
Sudo apt-get remove beagle
```
Remove the packages that beagle automatically installed.
```
sudo apt-get autoremove
```

If you installed the Firefox Extension to remove it..In Firefox goto Tools > Addons and click the uninstall button for the extension

---

### Post by jackn on 2007-02-20
Thank you kindly, Kelbizzle.

Been at it for two days now, and Beagle works a treat. It's come a long way since last time I tried to install it, when it was a mess, and that was only 6 months ago.

I did not install the Evolution or Firefox backends, as I prefer web-based mail and bookmarks.

It installs only the /home path for filesystem searches. 
```
beagle-settings
```, however, launches an easy GUI, from which I could add the whole filesystem, and exclude /bin, as I mean to use it also as a source of help (man pages and other doc files searched by content).

This is, at this early stage, a highly functional and user-friendly app.
A big thank you to the Beagle team.

Jackn

---

### Post by Bossieman on 2007-02-20
Do I have to put beagled in the sessionmanager(startup program)?

---

### Post by jackn on 2007-02-20
I'm not sure I understand the question, Bossieman, but for what it's worth:

Yes, 'beagled' does figure in my 'startup program' list.

I think it was there by default, but I'm not sure.

```
Beagle-settings


```, to launch the config window, was set up by default, I'm quite sure, in Applications -> Accessories as 'search & indexing' (as opposed to old 'search').

Is that the issue?

Jackn

---

### Post by Bossieman on 2007-02-20
I installed it accordingly to your howto. After a while my compute whent up tu 100% cpu. I kill the process and after that with beagled in the startskrivt I still only got about 65 hits on .mp3.

---

### Post by kelbizzle on 2007-02-20
> **Bossieman said:**
> I installed it accordingly to your howto. After a while my compute whent up tu 100% cpu. I kill the process and after that with beagled in the startskrivt I still only got about 65 hits on .mp3.

If you issued the exercise the dog command. Then Beagle will index using all the resources it can until it's finished. After it's finished it's initial indexing..It should return to normal. If you killed the process theres a possibility is hasn't finished indexing. To check it's status with **beagled** running. Type:  **beagle-status** into terminal.

---

### Post by jackn on 2007-02-20
I have a hard time understanding what help you need, Bossieman. In the future, if you have a problem, please ask a clear question, and please try to give specific details about what's going on. Separate sentences are easier to understand. You may also want to preview your post first.

1. 100% CPU is probably due to initially setting Beagle to its intense indexing mode.

I don't know whether you did that, but this is what it would take to get what you've 100% CPU used.
```
$ beagle-shutdown
$ export BEAGLE_EXERCISE_THE_DOG=1
$ beagled
```

You ***shouldn't*** usually do the above.

Why is it important that beagle is in the start menu still? Do you mean that it's still working?

'Only' 65 mp3's might be due to incomplete indexing. Beagle's efficiency and speed derive from indexing the whole filesystem, every word in it. Contrary to the old search method, it doesn't need to go through everything again every time you have a query. It has an index of everything, and when you query, it just finds a match in the index.
Since it's just the beginning, it probably wasn't done indexing when you queried for mp3, especially if you killed it.

Since then, it's probably been indexing as you have it in the startup list. It should tell you if indexing is not over when you launch a query by clicking on the magnifying glass in the top righthand corner.

If it's done indexing, you should get the right number of mp3's by repeating the search now.

Study the [beagle site]("http://beagle-project.org/Main_Page").
Study,```
 beagled --help
```
Study the man pages on ```
beagle-query
```, ```
beagle-status
``` and ```
beagle-shutdown
```.

---

### Post by Bossieman on 2007-02-20
I did the easy way.

sudo aptitude remove beagle

then removed .beagle folder in my home directory

then did a 

sudo aptitude install beagle

it works like a charm now, still indexing

---

### Post by kelbizzle on 2007-02-20
That works too. As long as you got it working right?

---

### Post by jackn on 2007-02-20
The how-to, Kelbizzle, doesn't mention extended attributes.

Yet, according to [the beagle site]("http://beagle-project.org/Enabling_Extended_Attributes"):

> Extended attributes are used by Beagle to keep track of which files have been indexed and which need to be re-indexed. There is an sqlite-based fallback which is **_very slow, so it is highly recommended that you do use extended attributes_**.

...Your kernel will need support for extended attributes on the filesystem you are indexing... For Reiser3, ext2 and ext3 filesystems, the default kernel config does not enable the attributes.

In spite of the above, the search works like lightning in my hands. I guess it is rather the indexing which they mean is slow.

In my system, the kernel option ```
CONFIG_EXT3_FS_XATTR
``` is set to =y.
It's the default kernel.
In my fstab file, on the other hand, no filesystem has extended attributes.

I assume, therefore, that I could easily enable it. 

So, should I enable 'extended attributes'? 

Jackn

---

### Post by kelbizzle on 2007-02-20
You can enable Extended Attributes. The reason I didn't mention it was because I had some issues with beagle not reindexing data right away so recently modified files wouldn't show up in the search until beagle decided to reindex it. I just didn't want to deal with that head ache. The spotlight feature had the same issue and you would have to force it to reindex data. I didn't know how to solve the issue.

---

### Post by anandi on 2007-02-22
Nice howto. I enabled the extended attributes as well.

However i see the problem with this version of beagle as with the version shipped with edgy. It takes the temp of both the cpus of my laptop to 55 deg C, which is very high. And this stays on like this for a very long time, eventually i go and kill the process and the temp comes down.

I can understand beagle is indexing stuff on my hdd (which is like 40GB of documents files etc), however it should run on a low priority and avoid taking the cpu to such high temps for prolonged intervals.

The following is the default priority of beagle processes

beagle-search  0
beagled 0
beagled-helper 12

I am using renice to change the priority of the processes. Now this is not a 100% working solution as i have repeat the same process everytime i boot up my laptop.

Now is there a way to force this everytime my laptop boots ? And someway to lower the cpu utilisation of beagle ? I don't mind it slowly indexing stuff (its as it is very slow indexing), however the high cpu temp is killing.

---

### Post by jackn on 2007-02-22
> **anandi said:**
> 

I am using renice to change the priority of the processes. Now this is not a 100% working solution as i have repeat the same process everytime i boot up my laptop.

Now is there a way to force this everytime my laptop boots ? And someway to lower the cpu utilisation of beagle ? 

Don't know, Anandi, if this is what you're looking for, but here's what comes to mind:

In order to have commands execute on every startup, you can put said commands in ```
.bashrc
```
.bashrc is a shell script in your home directory which is executed automatically every time the shell starts (upon *your* login).

In your case, I guess you'd prefer a system-wide change, applying to all users. In that case, modify 
```
/etc/bash.bashrc 
```


First, you would do well to back up the file you're modifying:
```

$ sudo cp file_name file_name_backup
```

Then, open the file:
```
~$ sudo gedit file_name
```

Add in your renice command. Save.

Upon your next login, your renice should be effective.

Is that what you're looking for?

Could you please detail the renice command and how you go about using it?
How do you know what the priorities are and whether they've changed?

Thanks,
Jackn

---

### Post by anandi on 2007-02-22
> **hroit said:**
> Don't know, Anandi, if this is what you're looking for, but here's what comes to mind:

In order to have commands execute on every startup, you can put said commands in ```
.bashrc
```
.bashrc is a shell script in your home directory which is executed automatically every time the shell starts (upon *your* login).

In your case, I guess you'd prefer a system-wide change, applying to all users. In that case, modify 
```
/etc/bash.bashrc 
```


First, you would do well to back up the file you're modifying:
```

$ sudo cp file_name file_name_backup
```

Then, open the file:
```
~$ sudo gedit file_name
```

Add in your renice command. Save.

Upon your next login, your renice should be effective.

Is that what you're looking for?

Could you please detail the renice command and how you go about using it?
How do you know what the priorities are and whether they've changed?

Thanks,
Jackn

Thanks for the information about .bashrc. I am aware of that. However i was looking for more in terms of doing something in beagle startup scripts which will force it to launch the processes with low priority.

Right now this is what i do to lower the priority of beagled and its processes

```

get all beagle procesess

```
```

ps aux | grep beagle
anand     5037  0.0  2.4  51996 24860 ?        SNsl 12:22   0:01 beagle-search --debug /usr/lib/beagle/Search.exe --icon
anand     5038  0.3  2.4  83008 25460 ?        SNl  12:22   0:52 beagled /usr/lib/beagle/BeagleDaemon.exe --bg
anand    14368 75.1  3.6 105244 37604 ?        SNl  15:34  49:05 beagled-helper /usr/lib/beagle/IndexHelper.exe
anand    17339  0.0  0.0   2800   768 pts/3    S+   16:40   0:00 grep beagle

```
Now the pids i need are 5037, 5038, 14368.

Now i issue the renice command to change their priorities

```

sudo renice 19 -p 5037 5038 14368
Password:
5037: old priority 0, new priority 19
5038: old priority 0, new priority 19
14368: old priority 12, new priority 19

```

According to man page for renice, this will make it run in lowest priority.

```

What is renice?

NAME
     renice - alter priority of running processes

SYNOPSIS
     renice priority [[-p] pid ...] [[-g] pgrp ...] [[-u] user ...]

DESCRIPTION
     Renice alters the scheduling priority of one or more running processes.  The following who parameters are
     interpreted as process ID&#8217;s, process group ID&#8217;s, or user names.  Renice&#8217;ing a process group causes all pro&#8208;
     cesses in the process group to have their scheduling priority altered.  Renice&#8217;ing a user causes all processes
     owned by the user to have their scheduling priority altered.  By default, the processes to be affected are
     specified by their process ID&#8217;s.

```

Please let me know if i was clear enough.

Even now beagled-helper process is taking 99% cpu thereby taking my cpu temp upto 60 deg C. All i want to do is cut it down, and let it index slower perhaps.

Just had another thought/ way to do the above (ofcourse manually again)

```

renice 19 -p `pidof beagled beagled-helper`

```

```

5038: old priority 19, new priority 19
14368: old priority 19, new priority 19

```

---

### Post by jackn on 2007-02-22
> **anandi said:**
>  

Please let me know if i was clear enough.


Plenty clear. Thank you.

My beagle-helper takes up much less CPU:
```
5318  7.0  3.6  89204 19020 ?        SNl  06:30  27:58 beagled-helper /usr/lib/beagle/IndexHelper.exe
```

I don't know what the 'cumulative' (man pages) means in the CPU figures given here, and how it differs from what 'top' gives. Is it from the beginning of the session?

I think you may want to look at the [Beagle troubleshooting pages]("http://beagle-project.org/Troubleshooting_CPU").

One thing they say:> 
Generally speaking, however, if the beagled-helper process is using 100% CPU for a few minutes uninterrupted (and with the screensaver off), this is a bug.

They say that beagle will sometimes get into trouble with proprietary file formats. They go on to describe a simple procedure to pin down the culprit. This sounds useful to me.
You can then exclude some stuff from the indexing, until the bug is sorted out.

I have also applied extended attributes.

Jackn

---

### Post by anandi on 2007-02-22
Thanks for the pointer to the beagle website.

As for the buddy part, i am already using 0.2.16 as per this tutorial, so the question of old versions don't arise.

I had a look at it and tried to grep inside the file it mentions. However wasn't able to get anything much out of it. It doesn't seem to be stuck at any specific document.

Lot of my files obviously include word documents, excel sheets, some are in MS format, and some are in OO format. And sitting and trying to exclude stuff won't be a easy job.

Anyways looks like all i can do right now is wait until all such bugs are ironed out of beagle.

---

### Post by anandi on 2007-02-22
Ok i caught beagled-helper process with 100% cpu for a very long time. Killed the process, and looked at the logs, i found it was stuck at a jpg file which was an invalid jpg file.

Now theoretically beagle should have skipped the file and went ahead. I hope this part of the new version.

---

### Post by kelbizzle on 2007-02-22
> **anandi said:**
> Ok i caught beagled-helper process with 100% cpu for a very long time. Killed the process, and looked at the logs, i found it was stuck at a jpg file which was an invalid jpg file.

Now theoretically beagle should have skipped the file and went ahead. I hope this part of the new version.

I haven't had the high cpu issue. I've seen the issue arise in cases like yours.

---

### Post by jackn on 2007-02-23
Anandi, what did you do? Delete the file? Exclude it from indexing?

Was it enough to get Beagle to behave?

Jackn

---

### Post by anandi on 2007-02-23
> **hroit said:**
> Anandi, what did you do? Delete the file? Exclude it from indexing?

Was it enough to get Beagle to behave?

Jackn

Couple of files / directories i exclude, some i deleted. For balance, can't think of anything else, but let beagled handle it whatever way it does. If it gets stuck at 100% cpu again, i can always kill it.

---

### Post by jackn on 2007-02-23
Actually, I got the clogged CPU problem, too, I just realized.

It happens infrequently, so I thought it was the usual freak freeze, but it's definitely happened more often than usually, and, above all, last time it happened, indeed, upon 'top', beagled-helper was high up there, hogging the CPU.

I'm going to try and troubleshoot this as described above, and will keep you guys posted.

I still prefer beagle with these snags to unindexed search, and every app has its growing pains.

Jackn

---

### Post by jamesrose on 2007-02-23
Thanks a lot, this was very helpful.

---

### Post by kelbizzle on 2007-02-25
I don't know how you guys keep having the cpu issue. I havn't had it once. what kinds of files are they getting stuck at?

---

### Post by jackn on 2007-02-25
OK, Kelbizzle, an example that occurred just now. 
This by no means happens often, but it does.

The machine froze, at least Firefox.
I followed the [instructions for troubleshooting]("http://beagle-project.org/Troubleshooting_CPU") on Beagle.


Unfortunately, I did not fish any file:
```
IndexH  WARN: Filtering status (18s ago): no document is currently being filtered.
```
Yet, beagled-helper was clearly free-wheeling intensely (high CPU, '18s ago' and 'warn'.

Upon restarting Firefox, everything settled down. It must be noted that I've also killed beagled-helper, as part of the diagnostic process above.

I'll be watching this.

Jackn

---

### Post by anandi on 2007-02-27
> **kelbizzle said:**
> I don't know how you guys keep having the cpu issue. I havn't had it once. what kinds of files are they getting stuck at?

It happens at random files. Couple of files i saw where currupt, meaning there weren't openable in any manner and problems associated with it. But then ideally beagle should ignore these files, however it gets stuck with it, consuming 90-95% of the cpu, sometimes even 100%.

---

### Post by hornett on 2007-02-27
@hroit & others having lock up problems:

Are you using the FS extended attributes to store the metdata, or the sqlite database?

---

### Post by anandi on 2007-02-28
> **hornett said:**
> @hroit & others having lock up problems:

Are you using the FS extended attributes to store the metdata, or the sqlite database?

I am using FS extended attributes.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5ea53dbc-7ce8-4ab4-94f2-02df93cfbdb1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=a7172222-ca73-4ac9-bcdb-2e020f36a248 /home           ext3    defaults,user_xattr        0       2
# /dev/sda2
UUID=3953e2fb-2e04-4ec3-9da8-ff7bb5725699 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by mshlin on 2007-02-28
Many thanks for tutorial, seems to be indexing fine. I am not using FS extended attributes.

---

### Post by jackn on 2007-03-01
OK, now serious, persistent trouble.

For some reason, beagle is forever running 'beagle-build-in'.
'beagle-build-in' takes up anywhere between 30% and 80% of the CPU all the time.
Bbeagle is indeed indexing all the time (meassage on GUI), it has been for a few days now.

Found nothing on the net, except others complaining of the same problem.

beagle-build-in cannot be killed:
```

$ sudo kill 5340
Password:
$ ps aux |grep beagle-build-in
110       5339  0.0  0.1   2540   804 ?        SN   04:46   0:00 su -s /bin/bash beagleindex -c MONO_SHARED_DIR=/tmp/.beagleindexwapi.RYHGdp5294 /usr/sbin/beagle-build-index --target /var/cache/beagle/indexes/documentation --disable-directories --recursive --allow-pattern *.xml,*.html,*.docbook /usr/share/doc /usr/local/share/doc /opt/kde3/share/doc /opt/gnome/share/gnome/help /usr/share/gnome/help /opt/gnome/share/gtk-doc/html /usr/share/gtk-doc/html /usr/share/gnome/html
110       5340 49.3  4.5  78696 23360 ?        SNl  04:46  51:17 beagle-build-index --debug /usr/lib/beagle/BuildIndex.exe --target /var/cache/beagle/indexes/documentation --disable-directories --recursive --allow-pattern *.xml,*.html,*.docbook /usr/share/doc /usr/local/share/doc /opt/kde3/share/doc /opt/gnome/share/gnome/help /usr/share/gnome/help /opt/gnome/share/gtk-doc/html /usr/share/gtk-doc/html /usr/share/gnome/html

```

As you can see, process 5340 is still there, and, of course, comes up upon 'top'.

Here's the output of beagle-status:
```

Scheduler:
Count: 1021
Status: Waiting for next task at 3/1/2007 6:18:57 AM

Pending Tasks:
1 Delayed 0 (3/1/2007 6:18:31 AM)
File Crawler

2 Delayed 0 (3/1/2007 6:18:32 AM)
Tree Crawler
Pending directories: 627

3 Maintenance 100 (3/1/2007 6:18:33 AM)
Final Flush for FileSystemIndex


Future Tasks:
Maintenance 0 (3/1/2007 6:18:37 AM)
Optimize FileSystemIndex
Hold until 3/1/2007 6:28:37 AM
```

I'm afraid I don't know very well what this means.

Help?

Jackn

---

### Post by dbera on 2007-03-03
According to [https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/88751](https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/88751)

beagle recently had a maintenance release 0.2.16.2 which fixes a lot of looping/100% CPU problems on svg, jpeg and pdf files. Backporting these fixes to Fiesty would definitely fix a lot of the problems above.

---

### Post by anandi on 2007-03-07
> **hroit said:**
> OK, now serious, persistent trouble.

For some reason, beagle is forever running 'beagle-build-in'.
'beagle-build-in' takes up anywhere between 30% and 80% of the CPU all the time.
Bbeagle is indeed indexing all the time (meassage on GUI), it has been for a few days now.

Found nothing on the net, except others complaining of the same problem.

beagle-build-in cannot be killed:
```

$ sudo kill 5340
Password:
$ ps aux |grep beagle-build-in
110       5339  0.0  0.1   2540   804 ?        SN   04:46   0:00 su -s /bin/bash beagleindex -c MONO_SHARED_DIR=/tmp/.beagleindexwapi.RYHGdp5294 /usr/sbin/beagle-build-index --target /var/cache/beagle/indexes/documentation --disable-directories --recursive --allow-pattern *.xml,*.html,*.docbook /usr/share/doc /usr/local/share/doc /opt/kde3/share/doc /opt/gnome/share/gnome/help /usr/share/gnome/help /opt/gnome/share/gtk-doc/html /usr/share/gtk-doc/html /usr/share/gnome/html
110       5340 49.3  4.5  78696 23360 ?        SNl  04:46  51:17 beagle-build-index --debug /usr/lib/beagle/BuildIndex.exe --target /var/cache/beagle/indexes/documentation --disable-directories --recursive --allow-pattern *.xml,*.html,*.docbook /usr/share/doc /usr/local/share/doc /opt/kde3/share/doc /opt/gnome/share/gnome/help /usr/share/gnome/help /opt/gnome/share/gtk-doc/html /usr/share/gtk-doc/html /usr/share/gnome/html

```

As you can see, process 5340 is still there, and, of course, comes up upon 'top'.

Here's the output of beagle-status:
```

Scheduler:
Count: 1021
Status: Waiting for next task at 3/1/2007 6:18:57 AM

Pending Tasks:
1 Delayed 0 (3/1/2007 6:18:31 AM)
File Crawler

2 Delayed 0 (3/1/2007 6:18:32 AM)
Tree Crawler
Pending directories: 627

3 Maintenance 100 (3/1/2007 6:18:33 AM)
Final Flush for FileSystemIndex


Future Tasks:
Maintenance 0 (3/1/2007 6:18:37 AM)
Optimize FileSystemIndex
Hold until 3/1/2007 6:28:37 AM
```

I'm afraid I don't know very well what this means.

Help?

Jackn

The process is beagle-build-index and NOT beagle-build-in. You can kill the process by using kill command or trying to shutdown beagle by beagle-shutdown.

After you have issued the kill/ beagle-shutdown, wait for couple of secs and then check in memory, the process should have gone. Now if you want you can restart beagle by running 'beagled'.

---

### Post by anandi on 2007-03-07
> **dbera said:**
> According to [https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/88751](https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/88751)

beagle recently had a maintenance release 0.2.16.2 which fixes a lot of looping/100% CPU problems on svg, jpeg and pdf files. Backporting these fixes to Fiesty would definitely fix a lot of the problems above.

Thats nice to hear.

I am using the repository located at 'http://beagle-project.org/files/ubuntu/edgy/' for beagle packages, and it still doesn't have the maintenance release packages in it. I guess i will wait till the time author releases those packages.

The reason i use them is because they are much better than the edgy shipped packages.

---

### Post by jackn on 2007-03-07
Thank you, Anandi. Indeed, I confused beagle-build-in and beagle-build-index.

But, 'beagle-build-in' I got from issuing 'top'. Then, upon 'ps' and 'grep' for the same, I only got 'beagle-build-index', as you pointed out. So, could they be one and the same? Where is the process which 'top' refers to as 'beagle-build-in' if not?!

Since then, this has calmed down. No more 'beagle-build-in' upon 'top'.

About two weeks after having installed Beagle, however, while I love its power, I'm still worried about its hogging of resources. 
It is almost always indexing. Is that as it should be? 
In addition, my informal impression is that the system has slowed down. I mostly spend my time surfing, and it seems to me that things have become sluggish. I'm pretty sure I've had the system freeze on me more than ever before. 
None of this would lead me to drop Beagle, but it's worth knowing about.

I run it with extended attributes and, perhaps more importantly, I have it index almost the whole filesystem, not only /home.

Finally, I'd appreciate instructions on how to use the repository you referred to in order to get the latest. I would need step-by-step instructions, and what package to use from teh several listed there. Thank you kindly in advance.

Jackn

---

### Post by anandi on 2007-03-08
> **hroit said:**
> Thank you, Anandi. Indeed, I confused beagle-build-in and beagle-build-index.

But, 'beagle-build-in' I got from issuing 'top'. Then, upon 'ps' and 'grep' for the same, I only got 'beagle-build-index', as you pointed out. So, could they be one and the same? Where is the process which 'top' refers to as 'beagle-build-in' if not?!

Since then, this has calmed down. No more 'beagle-build-in' upon 'top'.

About two weeks after having installed Beagle, however, while I love its power, I'm still worried about its hogging of resources. 
It is almost always indexing. Is that as it should be? 
In addition, my informal impression is that the system has slowed down. I mostly spend my time surfing, and it seems to me that things have become sluggish. I'm pretty sure I've had the system freeze on me more than ever before. 
None of this would lead me to drop Beagle, but it's worth knowing about.

I run it with extended attributes and, perhaps more importantly, I have it index almost the whole filesystem, not only /home.

Finally, I'd appreciate instructions on how to use the repository you referred to in order to get the latest. I would need step-by-step instructions, and what package to use from teh several listed there. Thank you kindly in advance.

Jackn

Well beagle takes a lot of resources at times.

For a howto on the repository, see the first post on this thread.

---

### Post by jackn on 2007-03-11
I'm pretty sure that the sluggishness occasioned by Beagle, and its CPU hogging are due in my box to the indexing of the root filesystem.

Immediately after installing Beagle, it only indexed /home by default, and was well-behaved.
Shortly thereafter, I started indexing my whole filesystem basically, and this gave rise to the trouble described above.

When I finally limited it to the /home partition again, it went back to behaving itself.

Though I can't vouch for it, my guess is that the difference between indexing / and indexing /home is not so much about the size of the target. 'df' tells me that /home weighs 2.1Gb, while / weighs 3.3Gb (separate partition, not including /home). 

There may be something in the system files, and not in the home files that Beagle stumbles upon.

In any case, I'd like to grab a package with 0.2.16.2 when it becomes available, and try indexing the whole of / again, to see if things are any better.

At this point, I don't permanently see Beagle indexing as it used to, and I don't see it upon 'top' all the time...

Jackn

---

### Post by anandi on 2007-03-13
> **hroit said:**
> I'm pretty sure that the sluggishness occasioned by Beagle, and its CPU hogging are due in my box to the indexing of the root filesystem.

Immediately after installing Beagle, it only indexed /home by default, and was well-behaved.
Shortly thereafter, I started indexing my whole filesystem basically, and this gave rise to the trouble described above.

When I finally limited it to the /home partition again, it went back to behaving itself.

Though I can't vouch for it, my guess is that the difference between indexing / and indexing /home is not so much about the size of the target. 'df' tells me that /home weighs 2.1Gb, while / weighs 3.3Gb (separate partition, not including /home). 

There may be something in the system files, and not in the home files that Beagle stumbles upon.

In any case, I'd like to grab a package with 0.2.16.2 when it becomes available, and try indexing the whole of / again, to see if things are any better.

At this point, I don't permanently see Beagle indexing as it used to, and I don't see it upon 'top' all the time...

Jackn

There is a cron entry at /etc/cron.daily/beagle-crawl-system which directs beagle to index parts of system. This is probably what was causing you to see the beagle-build-index process in memory. If you have ionice on your system, it runs the process with a low priority otherwise the process runs at a normal priority (i am not sure on this).

So i think you should remove the index part of / file system.

P.S. : Even though my beagle is only setup to index default file system location (i.e. my home directory), i still see lot of processing happening and most of the time its beagle helper process. I really wish i could make it less intensive by default.

---

