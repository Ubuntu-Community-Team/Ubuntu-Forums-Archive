---
title: "[SOLVED] Progress of dd"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by rbc on 2008-08-08
I love the dd command. I use it frequently to zero out hard drives and flash drives, but when i issue the command, the cursor just sits there until it is done. I have no way of knowing how far along the process is. Is there something I can include in the command to tell me how much progress the dd command has made?

---

### Post by cdtech on 2008-08-08
No. You would have to hack the code to include a progress bar.....

---

### Post by tamoneya on 2008-08-08
> **rbc said:**
> I love the dd command. I use it frequently to zero out hard drives and flash drives, but when i issue the command, the cursor just sits there until it is done. I have no way of knowing how far along the process is. Is there something I can include in the command to tell me how much progress the dd command has made?

Yep it is even in the help file.  I just ran dd --help and found this at the bottom:```
  $ dd if=/dev/zero of=/dev/null& pid=$!
  $ kill -USR1 $pid; sleep 1; kill $pid
  18335302+0 records in
  18335302+0 records out
  9387674624 bytes (9.4 GB) copied, 34.6279 seconds, 271 MB/s

```
After running the kill -USR1 command it will resume the transfer.

---

### Post by cdtech on 2008-08-08
> **tamoneya said:**
> Yep it is even in the help file.  I just ran dd --help and found this at the bottom:```
  $ dd if=/dev/zero of=/dev/null& pid=$!
  $ kill -USR1 $pid; sleep 1; kill $pid
  18335302+0 records in
  18335302+0 records out
  9387674624 bytes (9.4 GB) copied, 34.6279 seconds, 271 MB/s

```
After running the kill -USR1 command it will resume the transfer.

Thats not verbose, you have to stop the process to see the status....

---

### Post by tamoneya on 2008-08-08
> **cdtech said:**
> Thats not verbose, you have to stop the process to see the status....

i never said it was the same as a verbose option.  The OP just wanted a status and that is how dd --help says you should get the status.  I realize it stops thing but considering that it starts itself up automatically right afterwards it is okay.

---

### Post by rbc on 2008-08-08
Yeah. I saw that in the "man dd". I would have preferred the progress without stopping dd, but that's still extremely useful. Thanks all

---

### Post by runesvend on 2008-10-11
You don't have to stop *dd* in order to see its progress. Just type in the command:

```
sudo kill -USR1 (PID)
```

and *dd* will output its progress in the same terminal window where it had just been sitting with a blinking cursor prior to you issuing the command.

You can get the PID of the *dd* process by issuing the command *ps -A | grep dd* and finding dd in that list. For example:

```
rune@runescomp:~$ ps -A | grep dd
    2 ?        00:00:00 kthreadd
 5396 ?        00:00:00 dd
 5745 ?        00:00:00 winbindd
 5814 ?        00:00:00 winbindd
 5896 ?        00:00:01 hald-addon-usb-
 5903 ?        00:00:00 hald-addon-inpu
 5910 ?        00:00:00 hald-addon-cpuf
 5911 ?        00:00:00 hald-addon-acpi
 5980 ?        00:00:00 btaddconn
 7959 pts/1    00:04:36 dd
```

The last process is *dd* and its PID is the number in the leftmost column (7959).

Issuing the command *sudo kill -USR1 7959* makes *dd* output its status in the terminal where it is running:

```
rune@runescomp:~$ sudo dd if=/dev/zero of=/dev/sdb
[sudo] password for rune: 
141955993+0 records in
141955993+0 records out
72681468416 bytes (73 GB) copied, 2802,29 s, 25,9 MB/s
```

---

### Post by wltj on 2011-03-01
in case ppl happen upon this post via google.

```
sudo dd if=/dev/zero bs=2048 | pv -s 500G | sudo dd bs=2048 of=/dev/sdb
```

set pv -s to the size of the disk you are zeroing out.

see [http://www.commandlinefu.com/commands/view/6177/dd-with-progress-bar-and-statistics](http://www.commandlinefu.com/commands/view/6177/dd-with-progress-bar-and-statistics)

---

### Post by jsavga on 2012-11-10
How To: Monitor the progress of dd
[http://www.serenux.com/2011/02/howto-monitor-the-progress-of-dd/](http://www.serenux.com/2011/02/howto-monitor-the-progress-of-dd/)

Even provides info on using the watch command to get regular updates of dd status while it's running.


Basically, once dd is running you open a second temrinal and type
```
[COLOR=#000080]sudo kill -USR1 `pgrep ^dd`[/COLOR]
```
and the output pops up in the dd terminal without halting the process.

To get regular updates, use
```
[COLOR=#000080]watch -n5 'sudo kill -USR1 `pgrep ^dd`'
```
where -n equals the number of seconds between updates (-n5 equal 5 second updates)
[/COLOR]

---

### Post by oldfred on 2012-11-10
Thread Closed - Necromancy

But  from another really old thread.

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)
[http://www.anti-forensics.com/disk-wiping-with-dcfldd](http://www.anti-forensics.com/disk-wiping-with-dcfldd)

---

