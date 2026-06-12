---
title: "No settings menu at all in Ubuntu"
date: 2015-01-08
forum: New to Ubuntu
---

### Post by anbu-s on 2015-01-08
I'm new to Ubuntu - using version 14.04.1LTS - trying to figure out how things work

I was tyring to uninstall the untested version of Evolution (3.13) to the stable (3.12) release. While I was successful in doing that with some help from forums, now I lost my settings menu all together.
When I click on the wifi settings for example, I get this error

Failed to execute child process Gnome-control-center

I tried to do install gnome-control-center


 but get this error msg when I tried sudo apt-get install gnome-control-center


 gnome-control-center : Depends: gnome-settings-daemon (>= 3.9.91) but 3.8.6.1-0ubuntu11.2 is to be installed
E: Unable to correct problems, you have held broken packages.


Please help

---

### Post by kerry_s on 2015-01-08
**sudo apt-get -f install**

will fix your broken packages

---

### Post by deadflowr on 2015-01-08
How'd you install evolution 3.13?

---

### Post by anbu-s on 2015-01-08
> **kerry_s said:**
> **sudo apt-get -f install**

will fix your broken packages

I get this when i run this 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  highlight highlight-common libcryptui0a libgeocode-glib0 liblua5.1-0
  seahorse-daemon
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by anbu-s on 2015-01-08
> **deadflowr said:**
> How'd you install evolution 3.13?

I may have enable some PPAs which got the 3.13 update. Since then I've had some help from forum members - got evolution back to 3.12. But now cannot accesss any of my system settings. Please help!!

---

### Post by deadflowr on 2015-01-08
Could you point us to where you got your previous help, so we don't post useless info which you might have already tried.

My overall thinking though is that you still have leftover crud from the ppa's which is causing problems.
But I don't know what you did to revert back to the old evolution, so all info about that will help everyone...

---

### Post by anbu-s on 2015-01-08
> **deadflowr said:**
> Could you point us to where you got your previous help, so we don't post useless info which you might have already tried.

My overall thinking though is that you still have leftover crud from the ppa's which is causing problems.
But I don't know what you did to revert back to the old evolution, so all info about that will help everyone...

This is what I did to revert back to old evoltuion

sudo apt-get update
sudo apt-get install ppa-purge
sudo ppa-purge ppa:fta/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install evolution-mapi

---

### Post by mc4man on 2015-01-08
Did you or do you have another gnome3 related ppa enabled?
what's this - 
```
apt-cache policy gnome-control-center
```

and
```
echo $DESKTOP_SESSION
```

---

### Post by anbu-s on 2015-01-08
> **mc4man said:**
> Did you or do you have another gnome3 related ppa enabled?
what's this - 
```
apt-cache policy gnome-control-center
```

Here is the response - looks like I've gnome3 related ppa. How do i disable them?

anbu@Terminatore:~$ apt-cache policy gnome-control-center
gnome-control-center:
  Installed: (none)
  Candidate: 1:3.12.1-0ubuntu1~trusty5
  Version table:
     1:3.12.1-0ubuntu1~trusty5 0
        500 [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/) trusty/main amd64 Packages
     1:3.8.6-0ubuntu1~trusty2 0
        500 [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) trusty/main amd64 Packages
     1:3.6.3-0ubuntu56.1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.6.3-0ubuntu56 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages

---

### Post by mc4man on 2015-01-08
You may have missed from prior post 
```
 echo $DESKTOP_SESSION
```

Basically when you ran the dist-upgrade when getting rid of the other ppa you upgraded to all that the gnome3 ppa has to offer. So what's your intent here?

---

### Post by anbu-s on 2015-01-08
My intent is to get ubuntu working on the standard stable platform withe evolution 3.12.xx.

How do I get rid of gnome3 ppa's and get my ubuntu settings back? I'm new to linux so dont know exactly what I'm doing!!

---

### Post by anbu-s on 2015-01-08
echo $DESKTOP_SESSION

returns

gnome

---

### Post by anbu-s on 2015-01-08
Somehow I managed to solve this

I ran this command

sudo apt-get install gnome-settings-deamon

then

sudo apt-get install gnome-control-center
 

It seem to have fixed it all

---

