---
title: "a red triangle with exclamation sign in it doest go away while everything is updated."
date: 2015-04-17
forum: New to Ubuntu
---

### Post by sebastiaan5 on 2015-04-17
I have ubuntu 14.04.02 LTS and in the right upper corner of my screen there is an a red triangle with exclamation sign in it, that doesnt go away.

Clicking on it the message says, "The update information is outdated.  This may be caused by network problems or by a repository that is no  longer available. Please update manually by clicking on this icon and  then selecting 'Check for updates' and check if some of the listed  repositories fail." There is no network problem since internet works  fine. When I check for updates, shows your computer is up to date

greets

---

### Post by deadflowr on 2015-04-17
You'll probably need to do the old standby
Open the dash menu, and search for terminal.
Open it and run
```
sudo apt-get update
```
post the results in this thread.
Please use code tags.
(To use code tags when replying go to either adv reply, or use the Reply to Thread option and then the code tags is the # symbol in the editor's toolbar.)

---

### Post by Impavidus on 2015-04-17
"The update information is outdated" means that the list of available software updates is outdated. "The software is up to date" means that all installed software is of the latest version when compared to the list of available software updates. So there is no contradiction. Please post the output of deadflowr's command.

Note that a network problem can also be caused by a server side problem.

---

### Post by sebastiaan5 on 2015-04-17
the last lines after executing the command:


Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Fetched 3,097 kB in 10s (308 kB/s)                                             
W: Failed to fetch [http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by grahammechanical on 2015-04-17
The Update Manager said it.

> The update information is outdated.  This may be caused by network problems or _by a repository that is no  longer available_.

And those "404 Not Found" messages prove it. Disable those PPAs. We do that in System Settings>Software & Updates>Other Software tab.

Oh, by the way, this

> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

means that you have two methods of Updating/Upgrading working at the same time. For example, if we open the Software Centre it will lock certain directories to prevent another method of updating from interfering. Then if we use another method of updating we get messages like that.

Regards.

---

### Post by sebastiaan5 on 2015-04-18
Is it bad that i have two methods of Updating/Upgrading working at the same time?

greetz

---

### Post by deadflowr on 2015-04-18
> **sebastiaan5 said:**
> Is it bad that i have two methods of Updating/Upgrading working at the same time?

greetz

Are they though?
Working at the same time, I mean.
One will work be working, while the other will say what is seen above:
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This means that one is not working...

However, you can switch between either when the other is done.

---

