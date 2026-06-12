---
title: "hostname not found in lastlog"
date: 2024-03-29
forum: New to Ubuntu
---

### Post by atik-mahedvi on 2024-03-29
We have installed 22.04 LTS , We did not find the hostname in lastlog. Is it possible to modify lastlog parameter to add hostname columns


Also  hostname not found in btmp logs.

Anyone knows how to get this both parameters displayed  together in logs.

---

### Post by MAFoElffen on 2024-03-31
Welcome to Ubuntu Forums and Ubuntu...

That is not what the command 'lastlogin' is about... RE: [https://manpages.ubuntu.com/manpages/jammy/en/man1/last.1.html](https://manpages.ubuntu.com/manpages/jammy/en/man1/last.1.html)
```

DESCRIPTION

       last searches back through the /var/log/wtmp file (or the file designated by the -f
       option) and displays a list of all users logged in (and out) since that file was created.

```
And the command format had no filters ... more useful would have been
```

lastlogin | grep -v 'Never logged in'

```
To show those who have logged in. But there is no facility to add a hostname in that util/log. That just shows show stats about when users logged in last and from what type of device session.

Not sure what you are asking... I saw your output showing update-motd... That is something different... For that, if you did this
```

grep . /var/run/motd.dynamic

```
It would display the motd banner of what was displayed at the last login. That is a dynamic file, so is rewritten with login.

I modify my motd banner... RE: [https://manpages.ubuntu.com/manpages/jammy/en/man5/update-motd.5.html](https://manpages.ubuntu.com/manpages/jammy/en/man5/update-motd.5.html)
```

sudo apt install update-motd

```
Which uses scripts inside folder /etc/motd.d/

If you create this script file (modify as needed) inside that folder as /etc/motd.d/01-stats
```

#!/bin/sh
# Add the following stats to the motd

echo -e ""
date
echo -e ""
who
echo -e ""
uptime
echo -e ""
hostname
echo -e ""

```
And make it executable 
```

sudo chmod +x /etc/motd.d/01-stats

```
Then wait 10 minutes for it to pick up the changes... Then logout, and log back in to see the changes. (See attachment)

Modify that script to display what you want seen in the motd. Or add scripts with a higher or lower number to show before or after that. The first 2 numbers in the file name determine the order shown. 

You could use 'tee' to the output of those to send output to a log file, and track what you want from a login...

---

### Post by atik-mahedvi on 2024-04-05
[COLOR=#000000]We have installed 22.04 LTS, We did not find the hostname in anaconda log file. just to make sure it really doesn't exist or any way to print hostname in the anaconda logs.

    
[/COLOR]

---

### Post by MAFoElffen on 2024-04-05
??? I see you chaged your title. I fear that you are chasing ghosts.

I think you might be confused. "Anaconda" is the installer for Fedora. The "Anaconda Log" is the installer log for Fedora.

What exactly are you looking for, and where?

Because, the installer variables in the 22.04.x installer (subiquity) only exist in a file in memory during the install, they are not logged. So not there.

If you check the install syslog:
```

sudo grep 'hostname changed from' /var/log/installer/syslog
[sudo] password for mafoelffen: 
Sep 23 11:46:22 ubuntu NetworkManager[1450]: <info>  [1632397582.5656] hostname: hostname changed from (none) to "ubuntu"

```
Which is what the installer LiveUSB changes the L.I.E. during the boot of the environment... but no-where there is a record of what the user changed the hostname to during the installation. At least not in the older 22.04 subiquity installer.

In the Newer Installer, from 23.04 and newer (thru 24.04)... It's installer logs that and stores the user-data in a cloud-init file... ad in the curtin debug logs. But again, the newer installer uses a different process to do all that.

So what you are looking for in 22.04.x will be found in 24.04 in a few weeks when it is released.

---

