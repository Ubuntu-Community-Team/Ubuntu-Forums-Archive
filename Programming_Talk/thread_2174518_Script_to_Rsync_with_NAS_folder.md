---
title: "Script to Rsync with NAS folder"
date: 2013-09-14
forum: Programming Talk
---

### Post by Herbon on 2013-09-14
I was working on the script to backup files on my laptop to my "NAS", with it connection to my network

The following is what I came up with:

> #!/bin/bash
# Checks for NAS drives when connected to 10.10.1.0 network with ping, and starts ssh Resync with folder

ping -c 2 10.10.1.5; 
    if [ $? -eq 0 ]; then 

    notify-send "Machine is giving ping response, attempting to connect.";            # Use of "espeak"#
    var=10.10.1.5 ;while ! nc -zw 1 $var 22;do sleep 1; done ; ssh TOM@$var      # Automatically connect to a host with ssh once it is online#
    cd /media/imhotep/ISIS                                                                               # CD path to folder and syncs data on my PC with NAS#
    rsync -n ssh 10.10.1.5 TOM@peanuttwo: /media/RONIN/                               # folder location on NAS drive. "n" used for testing#

    sleep 10
else 
    espeak "Machine is offline, no reply." 2>/dev/null;                                         # Test use of "espeak" will use a email address later for failed updating#

    sleep 10

fi

I’m getting the following errors when I remove the "n" and use "a" in "rsync -n ssh"

> 

rsync: mkdir "/media/imhotep/ISIS" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(605) [Receiver=3.0.9]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9]



Another issue is how  do I get the script to run on its own when port Eth0 comes up??

Thanks

---

### Post by nerdtron on 2013-09-14
which computer is 10.10.1.5? and which is peanuttwo?
why is it "ssh 10.10.1.5"?

---

### Post by Herbon on 2013-09-14
> **nerdtron said:**
> which computer is 10.10.1.5? and which is peanuttwo?
why is it "ssh 10.10.1.5"?

The NAS = 10.10.1.5

I wanted to back up a folder from my laptop to network drive.

---

### Post by nerdtron on 2013-09-14
> TOM@$var      # Automatically connect to a host with ssh once it is online#
Why do you need to ssh on the NAS computer?
    > cd /media/imhotep/ISIS                                                                                # CD path to folder and syncs data on  my PC with NAS#
After your ssh to the NAS computer you change folder? I think this folder is on your computer and not on NAS computer so it will return "directory not found".
    > rsync -n ssh 10.10.1.5 TOM@peanuttwo: /media/RONIN/                                # folder location on NAS drive. "n" used for testing#
Does this even work standalone? The rsync syntax is
```
rsync [options] {source folder/file} {destination folder/files}
```

Anyway here's my recommendation:
After testing if the NAS computer is alive. Run the rsync command and don't ssh or cd to other folders.
I think the rysnc command should be like this, and this should work standalone (test it/run it directly on the terminal) before you put it in the script.
This will copy the contents of your computer folder "/media/imhotep/ISIS/" to the remote NAS computer with folder "/media/RONIN/" 
```
rsync -e ssh /media/imhotep/ISIS/ TOM@10.10.1.5:/media/RONIN/
```
The "-e ssh" can be optional. You can add --progress to the command to see the progress of copying.

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **Programming Talk**.*

---

### Post by Herbon on 2013-09-15
Thanks I will update when I get home later today

---

