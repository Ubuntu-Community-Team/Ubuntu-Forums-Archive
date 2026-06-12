---
title: "no start up - freezes"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by padeco on 2008-07-18
hi there,
i have been using hardy heron, since it came out, and so far no major issues. except, a few minutes ago i installed Plone!

plone v. 2.5 (combined installer that also installs zope and python 2.4). had to install gc++. no other changes.

now my system does shut down normally. however, when i restart it freezes on a window just prior to user name.

this is really weird, i do not feel like reinstalling everything since it is running so nicely and it seems like a waste of time. i no that the info i gave may not make sense but any help will be appreciated.

kind regards,
padeco

---

### Post by LinuxRocks713 on 2008-07-18
Reboot in recovery mode and remove plone (if its in the UBUNTU repos)

```

$ sudo apt-get remove plone

```

---

### Post by padeco on 2008-07-18
i did  not install it from apt-get, i downloaded the version i needed from their site, which was an older one.

i tried to sudo apt-get install --reinstall ubuntu-desktop, but it did not work. also tried sudo dpkg -configure -a, and it also nothing happens.

this is so sad, i just hope i do not have to re-install.

i can run any commands, and sudo apt-get update that is no worries.

many thanks,
padeco

---

### Post by sdowney717 on 2008-07-18
hmmm
try 
$ sudo dpkg-reconfigure xserver-xorg

---

### Post by RomeReactor on 2008-07-18
Hi. So this issue is with the X server not working? If you boot into recovery mode try using XFIX.

---

### Post by u_roland on 2008-07-20
I had the exact same Problem (on 8.04), and no clue how to fix it. The system freezes right before the login screen. There is nothing but the "loading" mouse cursor, which is movable. I found error messages in syslog and auth.log.

After I (maybe too hastly) reinstalled ubuntu those error messages were gone, so I cant post them. But it was something like. "Cannot authenticate user" multiple times.

I'd be glad if someone knew how to install that old version of Plone on 8.04. I had it running on 7.10.

---

### Post by padeco on 2008-07-22
thanks guys!
i had enough of looking around, so installed xubuntu 7.04. it works great, except thunar takes ages to load files when you try to browse your folders etc. . .

many thanks,
padeco

---

