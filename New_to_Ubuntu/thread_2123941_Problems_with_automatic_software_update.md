---
title: "Problems with automatic software update"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by rounder8 on 2013-03-09
I just installed Ubuntu 12.10 (64bit) to my laptop. The first thing I did was to run automatic update after it reported I had 293 updates to install. It downloaded all the packages in about 30 minutes but during the first couple of minutes of the actual installation the system suddenly was shat down. It wasn't reboot, it was complete shut down. After turning my computer back on I tried to open Ubuntu software center but got an error popup:

"Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?" -> cancel/repair

I clicked repair and after a while I got an error dialog showing lots of dependency errors.

As it is I cannot use the package manager anymore. How can I fix this problem? Do I need to reinstall Ubuntu? What if something like this happens on a system that cannot be easily formatted/reinstalled? There must be a way to deal with installer errors like this...

Only thing I was doing while auto updater was running was that I had 2 terminal windows open, one showing top and one showing ping [www.google.com]("http://www.google.com") to check connection status. I was resizing the auto-update-window with the details view turned on when computer decided to shut down.

Edit:

I have ran Ubuntu on multiple computers before and this was the first time I ran against problems using auto-update.
Not sure if this is the right forum, perhaps installation/upgrade would have been better?

Update:

I tried:
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install

And ran into dependency errors that canceled the process

---

### Post by ptn107 on 2013-03-09
```
sudo dpkg --configure -a
```

---

### Post by ibjsb4 on 2013-03-09
--configure -a is a good call.  You can also try:

```
sudo apt-get dist-upgrade
```

[Apt-get #3]("https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands")

Can you post the errors?

How bout posting the output of:

```
cat -n /etc/apt/sources.list
```

and

```
cat /etc/apt/sources.list.d/*
```

---

### Post by rounder8 on 2013-03-09
Thanks for the answer guys!

 I'm not sure whether the proposed solution would have worked or not but I went ahead and reinstalled Ubuntu and this time auto-update finished successfully.

---

### Post by fiodev on 2013-03-09
I personally don't prefer auto-update
try manually open terminal
sudo -s
apt-get update && apt-get upgrade -y 
apt-get dist-upgrade (optional)
apt-get autoremove && apt-get autoclean -y

the terminal is much faster and uses less resources, also if you dont use the -y it will ask before doing installs and give you a chance to review what will happen and what will be done

---

### Post by ibjsb4 on 2013-03-09
Don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

