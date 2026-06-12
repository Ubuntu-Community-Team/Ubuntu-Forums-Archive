---
title: "I am asked to install synaptic but I am not allowed"
date: 2014-12-26
forum: New to Ubuntu
---

### Post by whearn on 2014-12-26
I have tried to install new software, and I cannot. I get the following error message: *"It is impossible to install or remove any software. Please use the package manager 'Synaptic' or run 'sudo apt-get install -f' at a terminal to fix this at first"* I am not allowed to install 'synaptic' and the terminal gives 2 errors-something like this: E: could not get lock /var/lib/dpkg/lock.....I have just installed ubuntu 12.04. Any suggestions.

---

### Post by Jonathan Precise on 2014-12-26
Hello whearn, welcome to the forums!

Please do the following:
[s]1) Make sure you have internet connection.[/s]
2) Make sure you typed the command correctly. If possible, use copy/paste (CTRL-V doesn't work in the terminal, use SHIFT-CTRL-V).
3) If the error still occurs, post back with the exact errors, copy-pasted (CTRL-C doesn't work in the terminal either, use SHIFT-CTRL-C)

Make sure you complete those steps in that order so we can see what is the culprit

-Jonathan

---

### Post by flaymond on 2014-12-26
Do you installing any software while in the process?

---

### Post by grahammechanical on 2014-12-26
If I remember correctly, Synaptic Package Manager is installed by default in Ubuntu 12.04. Releases of Ubuntu after 12.04 do not have Synaptic Package Manager installed by default. You can open the Dash and search for Synaptic. Or you can open a terminal (you can find that also by searching the Dash for Terminal) and run

```
sudo apt-get install -f
```

Post any error messages. But my guess is that this message

> [COLOR=#000000]E: could not get lock /var/lib/dpkg/lock[/COLOR]

means that you have more than one utility opened that does updates and installs software. Shut down and restart and try again. And tell us what methods you are using to install software and what the software is and what error messages you get.

Regards.

---

### Post by newb85 on 2014-12-27
As grahammechanical pointed out, that /var/lib/dkpg/lock issue means another install/update utility is running, perhaps in the background.  Ubuntu only allows one to run at a time.  If you just installed 12.04, there will probably be a *lot *of updates to install.  I could be mistaken, but I believe the default in 12.04 is to install security updates automatically.

---

### Post by Bucky Ball on 2014-12-27
Welcome. Close everything. Software Centre and everything else. Open a terminal. Try:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install synaptic
```

Please post any errors you encounter.

---

### Post by whearn on 2014-12-27
error message:

bob@bob-Gateway-450ROG:~$ sudo apt-get autoremove
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Bucky Ball on 2014-12-27
Yep, that's weird. This message should only appear if you have Software Centre or Synaptic already open when you try those commands. We'll need to dig deeper ... :-k

---

### Post by Jonathan Precise on 2014-12-27
Yes apparently you have other programs that manage "APT/DPKG", like software-center, update-manager, synaptic, etc...

If you don't have Ubuntu Software Center, Software Updater, Synaptic, etc. open, try again.

If the problem persists, then run:

```
ps ax | grep -iE "apt|software-center|update-manager|synaptic"
```

Notice I use [noparse]```

```[/noparse] tags for typing commands and giving their outputs.
If nothing is running apt, you should see something similar to:
```
21860 pts/11   S+     0:00 grep --color=auto -iE [COLOR="#FF0000"]apt[/COLOR]|[COLOR="#FF0000"]software-center[/COLOR]|[COLOR="#FF0000"]update-manager[/COLOR]|[COLOR="#FF0000"]synaptic[/COLOR]
```

If there is something, you should see:

```
[COLOR="#800080"]22282[/COLOR] pts/14   Sl+    0:12 /usr/bin/python /usr/bin/[COLOR="#FF0000"]software-center[/COLOR]
[COLOR="#800080"]22352[/COLOR] ?        SNl    0:00 /usr/bin/python3 /usr/sbin/[COLOR="#FF0000"]apt[/COLOR]d
[COLOR="#800080"]22543[/COLOR] pts/14   Rl+    0:14 /usr/bin/python /usr/share/[COLOR="#FF0000"]software-center[/COLOR]/update-[COLOR="#FF0000"]software-center[/COLOR]-channels
[COLOR="#800080"]22557[/COLOR] pts/16   S+     0:00 grep --color=auto -iE [COLOR="#FF0000"]apt[/COLOR]|[COLOR="#FF0000"]software-center[/COLOR]|[COLOR="#FF0000"]update-manager[/COLOR]|[COLOR="#FF0000"]synaptic[/COLOR]
```

In this case, I have Ubuntu software center loading. So try and run:

```
pkexec kill -9 [COLOR="#800080"]<pid>[/COLOR]
```

Replace [COLOR="#800080"]<pid>[/COLOR] with one of the numbers in purple. I recommend going top to bottom.

Finally retry the command(s):

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get autoremove
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install synaptic
```

-Jonathan

---

### Post by schragge on 2014-12-27
I guess reboot should clear any locks. If not, look what process is still accessing */var/lib/dpkg/lock*:
```
sudo lsof -w /var/lib/dpkg/lock
``` or ```
sudo fuser -v /var/lib/dpkg/lock
```
If the list is empty then just remove the file and let dpkg recreate it:
```

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

```

---

### Post by whearn on 2014-12-27
Thanks for the comments. I feel I am a little in over my head, but I will keep trying.

---

### Post by whearn on 2014-12-28
In software center,the only item in the list is an icon followed by “Searching”. Theprogress button above is constantly showing the two arrows chasingeach other. I have tried to stop this, and there is a “Cancelling”below the 'Seaching', but it appears to be unchanging. Even closingsoftware center and/or rebooting does not help. This might be whysoftware center seems to be open.

---

