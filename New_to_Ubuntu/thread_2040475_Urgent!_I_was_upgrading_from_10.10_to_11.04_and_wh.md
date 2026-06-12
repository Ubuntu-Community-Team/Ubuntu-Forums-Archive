---
title: "Urgent! I was upgrading from 10.10 to 11.04 and when I restarted it's just a terminal"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by f1ndingwalden on 2012-08-11
I have spent all night upgrading from and 8.04 disk I have to the new 12.04. I was running the update manager on 10.10 and everything was golden; all the update where installed, obsolete packages removed, and it just had to restart. When I clicked O.K. and it restarted a black screen came on and I had to log in through  the terminal. When I did it says 
> Welcome to Ubuntu 11.04m(GNU/Linux 2.6.38-15-generic-pae i686)
*Documentation: [http://help.ubuntu.com/](http://help.ubuntu.com/)
System information as of Sat Aug 11 03:34:35 EDT 2012
System load: 0.49                   Memory usage: 1%         Processes:   89
Usage of /:   0.9% 0f 914.11GB        Swap Usage: 0%     Users logged in: 0

Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

New release 'oneiric' avaliable.
Run 'do-release-upgrade' to upgrade it.
When I run 'do-release-upgrade' all I get is
> Checking for a new ubuntu release
No new release found And when I run 'sudo apt-get upgrade' all I get is
> Reading package lists... Done
Building dependency tree
Reading state information...Done
0 upgraded, O newly installed, 0 to remove and 0 not upgraded.I have seriously spent the past 7 hours upgrading from 8.04 and I dont want to do that again, especially since I don't know what caused this and might just run into the same problem again. Please help.:confused:

---

### Post by Kalanac on 2012-08-11
Have you done a

```
sudo apt-get update
```

not upgrade.  That'll update the package lists.

Also check /etc/apt/sources.list (post it up here :))

---

### Post by f1ndingwalden on 2012-08-11
When I run 'sudo apt-get update' I get a list of things similar to;
> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg) Could not resolve 'us.archive.ubuntu.com' 

 and it ends with;
> W: Some index files failed to download. They have been ignored, or old ones used instead. 

And when I checked '/etc/apt/sources.list' it said 'Permission denied.'
So I tried 'sudo /etc/apt/sources.list' and it said 'command not found'
I also tried 'cd /etc/apt/sources' so I could just enter 'ls', but it says 'No such file or directory'

Thank you for helping, and I will try to respond ASAP.

---

### Post by Kalanac on 2012-08-11
Hi there, sorry I should have given clearer instructions to view the file:

```
sudo nano /etc/apt/sources.list
```

It's a text file.  Is that computer connected to the net?  Try running a ping:

```
ping ubuntu.com
```

---

### Post by f1ndingwalden on 2012-08-11
Oh my bad. And it's cool, Im really new to ubuntu, but I'm trying to learn and I only have some of the really basic stuff. 
In reply to 
sudo nano /etc/apt/sources.list I got;us.archive.ubuntu.com/ubuntu/ natty main restricted
>  #deb cd rom:{ubuntu 8.04 _Hardy Heron_ -Release i386 (20080423)}/ hardy main restricted
# See [http://help.ubuntu.com/UpgradeNotes](http://help.ubuntu.com/UpgradeNotes) for how to upgrade to newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/ubuntu](http://us.archive.ubuntu.com/ubuntu/ubuntu) natty main restricted

##Major bug fix updates produces after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com//ubuntu/](http://us.archive.ubuntu.com//ubuntu/) natty-upgrades main restricted

##N.B. software from this reposity is ENTIRELY UNSUPPORTED by the Ubuntu team, and may not be under a free license. Please satisfy yourself as to your rights to use this software. Also, please note that software in universe WILL NOT receive any updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

##N.B. software from this reposity is ENTIRELY UNSUPPORTED by the Ubuntu  team, and may not be under a free license. Please satisfy yourself as  to your rights to use this software. Also, please note that software in  universe WILL NOT receive any updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

##Uncomment the following two lines to add software from the 'backports' repository.
##N.B. software fromthis repository may not have been tested as extensively as that contained in the main release, although it includes newer versions of some applications which may provide useful feaures.
##Also, please note that software in backports WILL NOT receive any review or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

##Uncomment the following two lines to add software from Canonical's 'partner' repository. This software is not part of Ubuntu, but is offered by Canonical and the respective vendors as a service to Ubuntu users.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy partner
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

in reply to
ping ubuntu.com
is;
> ping: unknown host ubuntu.com

I had wifi just before it crashed if that helps.

Sorry it took so long to reply, it was a pain in the but to type, and I really hope it wasnt a troll or something lol.
Thanks for working with me though.

---

### Post by Kalanac on 2012-08-11
No trouble.  I didn't realise you were going to have to type that lot out by hand.  If I'd known I'd have suggested that you do the ping first.

OK, your problem is that you have no net connection.  The ping attempts to send a dummy packet of data to, in this case, ubuntu.com  It has failed to do so which means either your DNS is not working or, more likely, you have no network connection.

run

```
ifconfig -a
```

This will give you a list of your network connections.  Read the following:

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

This will give you guidance about getting your wireless connection back.  It might be easier just to plug in an ethernet cable to complete the updates.

Incidentally, is this a server install or do you have a desktop environment (gnome2/unity etc.)?

---

### Post by f1ndingwalden on 2012-08-11
OK, so I connected to an ethernet cable and am running the upgrade.
I previously had gnome.
Thanks again, and Ill keep this thread updated.

---

### Post by Kalanac on 2012-08-11
No trouble.  The problem is possibly that things are having to swap from gnome to unity.  You might have to do some command line stuff to get your desktop back, but do the upgrades first.  I'll begin scouring for guides on restoring your desktop from command line :)

---

### Post by f1ndingwalden on 2012-08-11
Okay so the update(finally) completed, but im still stuck on a terminal. While updating it  showed  
> xset unable to open display

Also when starting up it said
> Starting up ...
    * Stopping save kernel messages                    { OK }
    * Starting LightDM Display Manager                 {fail}
Ubuntu 11.10 debacle-laptop ttyl

With 'fail' in red.

Once I log in it brings me back to the EXACT same screen in the beginning
> Welcome to Ubuntu 11.04m(GNU/Linux 2.6.38-15-generic-pae i686)
*Documentation: [http://help.ubuntu.com/](http://help.ubuntu.com/)
System information as of Sat Aug 11 03:34:35 EDT 2012
System load: 0.49                   Memory usage: 1%         Processes:   89
Usage of /:   0.9% 0f 914.11GB        Swap Usage: 0%     Users logged in: 0

Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

New release 'oneiric' avaliable.
Run 'do-release-upgrade' to upgrade it. 			 		  

So Im still stuck in 11.10
Sorry that took so long, and I hope this helps.

---

### Post by f1ndingwalden on 2012-08-11
Hey kalanac, I'm going to bed and Ill check this when I wake up.

---

### Post by Kalanac on 2012-08-11
Right, so here is my working assumption:

You plugged in to ethernet
You ran: do-release-upgrade
You rebooted
The system is still Natty


That's pretty odd.  Let's try some clean up:

```
sudo apt-get update
```
Updates your package lists
```
sudo apt-get autoremove
```
Clears up any old packages your system no longer needs
```
sudo apt-get upgrade
```
Upgrades all your installed software to the latest version.

That should give you a sound starting point.  Nextly, we'll try to get the desktop back the quick and easy way:

```
sudo apt-get purge ubuntu-desktop
```
This will get rid of any desktop packages currently installed AND the config files.  This gives us a nice blank slate to re-install the desktop.

```
sudo apt-get install ubuntu-desktop
```

This will install the desktop environment again.  After that, reboot and (fingers crossed) you'll get a desktop again.

See how that goes first.  If we can't get the desktop back at this stage, we'll try again later after getting passed the version upgrade shenanigan.

I'm in the UK on GMT +1 time just now (BST) so I might be heading to bed when you get up :D

---

### Post by f1ndingwalden on 2012-08-11
WOOOHOOOO!!!
I ran the codes and re-did the upgrade and were golden!
Thankyou!!!!!
[http://www.jiveturkeyjives.com/wp-content/uploads/2010/12/Jesus_mac1.jpg](http://www.jiveturkeyjives.com/wp-content/uploads/2010/12/Jesus_mac1.jpg)

---

