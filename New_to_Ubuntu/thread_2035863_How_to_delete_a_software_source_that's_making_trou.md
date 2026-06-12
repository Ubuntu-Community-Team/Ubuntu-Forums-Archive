---
title: "How to delete a software source that's making trouble?"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by BlueAZ on 2012-07-31
:confused:  New problem to me, but I'm sure the community can guide me thru it!

In trying to install an updated graphics driver, I was directed to add a software source:  'ubuntu-x-swat-x-update...'    This source then began blocking Update Manager from doing its job.   I removed this source from Software Sources, but Update Man'r keeps telling me it can't go forward because of '/etc/apt/sources.list.d/ubuntu-x-swat-x-update.....'    

I bravely went into /etc/apt/sources.list.d  and found 'ubuntu-x-swat-x...'  and tried to delete it.  But it won't delete.  I tried opening it in gedit and deleting the contents, but it won't let me Save.  

Is this something I shouldn't be messing with?  If so, how do I get rid of this problematic x-swat thing?           Thanks!

---

### Post by mlentink on 2012-07-31
use 
```
gksudo gedit /etc/apt/sources.list
```
and then you should be be to save

---

### Post by critin on 2012-07-31
There are commands that you can use, but I don't know them.   Go into Synaptic Package manager and search for the name of the driver or source.  Dependencies should show up, when they do choose uninstall completely.  Hopefully it will show up.  
*Commands are quicker.*

---

### Post by Elfy on 2012-07-31
> **mlentink said:**
> use 
```
gksudo gedit /etc/apt/sources.list
```
and then you should be be to save

Won't help with this  - ppa's have their own list in /etc/apt/sources.list.d/ :)

> **critin said:**
> There are commands that you can use, but I don't know them.   Go into Synaptic Package manager and search for the name of the driver or source.  Dependencies should show up, when they do choose uninstall completely.  Hopefully it will show up.  
*Commands are quicker.*Maybe you are thinking of ppa purge 

```
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```

might work

---

### Post by BlueAZ on 2012-07-31
Thanks,  but the ppa-purge command in the Terminal just returned an 'unknown command' reply.   I'd be afraid to delete the whole /sources.list -- wouldn't that remove ALL sources?

I'll try Synaptic.

---

### Post by BlueAZ on 2012-07-31
Nope!  This source problem is blocking Synaptic from opening too.  

Any other ideas?

---

### Post by ubudog on 2012-07-31
> **BlueAZ said:**
> Thanks,  but the ppa-purge command in the Terminal just returned an 'unknown command' reply.   I'd be afraid to delete the whole /sources.list -- wouldn't that remove ALL sources?

I'll try Synaptic.

Try: 
```
sudo apt-get install ppa-purge
```

And then retry Elfy's post.  :)

---

### Post by BlueAZ on 2012-07-31
> **critin said:**
> There are commands that you can use, but I don't know them.   Go into Synaptic Package manager and search for the name of the driver or source.  Dependencies should show up, when they do choose uninstall completely.  Hopefully it will show up.  
*Commands are quicker.*
Thanks, but this source problem is blocking Synaptic from even opening.

What next??

---

### Post by BlueAZ on 2012-07-31
> **ubudog said:**
> Try: 
```
sudo apt-get install ppa-purge
```

And then retry Elfy's post.  :)
Wow!  I entered this & Terminal went wild, doing a whole bunch of package updates, but ending with the same message:
Processing triggers for menu ...
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.

What next?

---

### Post by BlueAZ on 2012-07-31
> **mlentink said:**
> use 
```
gksudo gedit /etc/apt/sources.list
```
and then you should be be to save
That command opens a document with a lot of info about Restricted Extras.  I don't want to change that ppa, do I?  Nothing in it about x-swap.

---

### Post by mlentink on 2012-07-31
> **Elfy said:**
> Won't help with this  - ppa's have their own list in /etc/apt/sources.list.d/ :)

Thx. Had not looked at that. Seems I've got sme relearning to do!

---

### Post by ubudog on 2012-07-31
> **BlueAZ said:**
> Wow!  I entered this & Terminal went wild, doing a whole bunch of package updates, but ending with the same message:
Processing triggers for menu ...
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.

What next?

Seems like it might have installed correctly though -- try running:
```
ppa-purge -h
```

Do you get ppa-purge's help page?

---

### Post by wojox on 2012-07-31
```
gksudo gedit /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
```

Copy and paste the contents up here.

---

### Post by Cheesemill on 2012-07-31
```
sudo rm /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
sudo apt-get update
```

---

### Post by mlentink on 2012-07-31
> **BlueAZ said:**
> That command opens a document with a lot of info about Restricted Extras.  I don't want to change that ppa, do I?  Nothing in it about x-swap.

Sorry, I was wrong as per Elfy's earleir post...

---

### Post by BlueAZ on 2012-07-31
> **ubudog said:**
> Try: 
```
sudo apt-get install ppa-purge
```

And then retry Elfy's post.  :)
Oh I see -- install ppa purge and THEN run Elfy's command.  OK, tried this, & got this:

:~$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates
: 
Updating packages lists
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.
Warning:  apt-get update failed for some reason
PPA to be removed: ubuntu-x-swat x-updates
comm: file 2 is not in sorted order
Package revert list generated:
 libva1/oneiric libva-x11-1/oneiric xserver-xorg-video-savage/oneiric

Disabling ubuntu-x-swat PPA from 
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
Updating packages lists
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.
Warning:  apt-get update failed for some reason
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '1.0.12-2' (Ubuntu:11.10/oneiric [amd64]) for 'libva1'
Selected version '1.0.12-2' (Ubuntu:11.10/oneiric [amd64]) for 'libva-x11-1'
Selected version '1:2.3.2-3ubuntu2' (Ubuntu:11.10/oneiric [amd64]) for 'xserver-xorg-video-savage'
The following packages were automatically installed and are no longer required:
  screen-resolution-extra dkms
Use 'apt-get autoremove' to remove them.
The following packages will be DOWNGRADED:
  libva-x11-1 libva1 xserver-xorg-video-savage
0 upgraded, 0 newly installed, 3 downgraded, 0 to remove and 96 not upgraded.
Need to get 129 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libva-x11-1 amd64 1.0.12-2 [16.0 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libva1 amd64 1.0.12-2 [38.6 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main xserver-xorg-video-savage amd64 1:2.3.2-3ubuntu2 [74.7 kB]
Fetched 129 kB in 2s (61.8 kB/s)                     
dpkg: warning: downgrading libva-x11-1 from 1.0.15-1~xup1 to 1.0.12-2.
(Reading database ... 235929 files and directories currently installed.)
Preparing to replace libva-x11-1 1.0.15-1~xup1 (using .../libva-x11-1_1.0.12-2_amd64.deb) ...
Unpacking replacement libva-x11-1 ...
dpkg: warning: downgrading libva1 from 1.0.15-1~xup1 to 1.0.12-2.
Preparing to replace libva1 1.0.15-1~xup1 (using .../libva1_1.0.12-2_amd64.deb) ...
Unpacking replacement libva1 ...
dpkg: warning: downgrading xserver-xorg-video-savage from 1:2.3.3-1~oneiric~xup1 to 1:2.3.2-3ubuntu2.
Preparing to replace xserver-xorg-video-savage 1:2.3.3-1~oneiric~xup1 (using .../xserver-xorg-video-savage_1%3a2.3.2-3ubuntu2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-savage ...
Processing triggers for man-db ...
Setting up libva-x11-1 (1.0.12-2) ...
Setting up libva1 (1.0.12-2) ...
Setting up xserver-xorg-video-savage (1:2.3.2-3ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.
E: Type 'p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
E: The list of sources could not be read.
Warning:  Something went wrong, packages may not have been reverted
 
Seems this source is still blocking its own removal...!?

---

### Post by Elfy on 2012-07-31
You have an issue with the list - I'd follow #13 for the moment

You could follow #14 but then I think that the ppa purge will fail as well - and we have no idea what you've done yet ;)

---

### Post by BlueAZ on 2012-07-31
> **wojox said:**
> ```
gksudo gedit /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
```

Copy and paste the contents up here.
Got this:
p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu oneiric main

---

### Post by BlueAZ on 2012-07-31
> **Cheesemill said:**
> ```
sudo rm /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
sudo apt-get update
```
Got this:
sudo rm /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list
rm: cannot remove `/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list': No such file or directory

---

### Post by Elfy on 2012-07-31
> **BlueAZ said:**
> Got this:
p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu oneiric main

Run the command again and add htt to the beginning of the line

[COLOR="Red"]htt[/COLOR]p://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu oneiric main 

The save and do

```
sudo apt-get update
```

Any errors now?

---

### Post by BlueAZ on 2012-07-31
Yay!!  :lolflag:        I'm not sure which thing worked, as they all returned notices of failure...               But now Update Manager and Synaptic open up and work!   So something fixed the problem!

Thanks to all ):P

---

