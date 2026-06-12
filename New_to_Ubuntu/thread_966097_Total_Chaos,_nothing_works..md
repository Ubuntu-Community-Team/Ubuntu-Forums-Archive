---
title: "Total Chaos, nothing works."
date: 2008-11-01
forum: New to Ubuntu
---

### Post by JoHenning on 2008-11-01
Ok so i upgraded from 8.04 to 8.10.

During the installation progress it crashed and my Computer wouldn't start up anymore. Now i don't know how i managed it but somehow the computer started up again.
Now i'm back to the old problems, my graphics card  is not supported, my sound has a horrible quality.
And i can't install any upgrades it just won't let me do it, it tells me there are updates available so i got into the update manger and it says:


Not all Updates can be installed.

Run a partial Upgrade to install as many as possible.
This can be caused by...
A previous update which didnt complete
Problems with some of the installed software
Unofficial Software packages not provided by ubuntu
normal changes of a pre release version of ubuntu

Then i can Close or do Partial Upgrade

I choose Partial Upgrade and then I'm told.

An upgrade from inteprid to hardy is not possible with this tool

And even if i use Synaptic Package Manger nothing will work, the downloads just won't function or take 3 days for 2mb... how can i change the mirrors?


any help please  i don't have any idea what to do...

---

### Post by JoHenning on 2008-11-01
:confused:

---

### Post by mkvnmtr on 2008-11-01
Someone may be able to help you get your system squared away but it sounds like quite a job. You will have to post the exact errors you got and many more things for someone to understand enough to help. I f it was me I would get out your 8.04 live disk and boot it up. Then save all your files on another drive and finally reinstall 8.04. Then I would search the forums untile I found someone with the same machine that has had success with their installation and find out how the did it. Sometimes it is not so hard if you have the information before you start. Good luck

---

### Post by AlanR8 on 2008-11-01
So you DID backup all your files didn't you?

I would suggest a clean install, subject to the above. That's what I've just done on two machines.

---

### Post by CJ Master on 2008-11-01
This is a shot in the dark, but did you try to install 64bit intrepid onto a 32bit machine? That would account for some of the errors.

---

### Post by CatKiller on 2008-11-01
You can configure any packages that have started to install with ```
sudo dpkg --configure -a
``` Then you can edit your repository list with ```
sudo nano /etc/apt/sources.list
``` Lines that start with a # are comments and are ignored. Remove the # from any lines that have repositories you want to use. Change any instance of *hardy* to *intrepid*. Then, to get an updated list of packages to install from, use ```
sudo apt-get update
``` Then, to complete the upgrade, use ```
sudo apt-get dist-upgrade
```

Personally, I found that some of the packages couldn't be upgraded because of dependency problems. In my case, these were *amarok* and *amarok-common*. So before I could successfully do the dist-upgrade, I first had to remove Amarok with ```
sudo apt-get remove amarok
``` Then the dist-upgrade worked, and I could re-install Amarok with ```
sudo apt-get install amarok
``` You may find that it's a different package that's causing you problems.

---

### Post by JoHenning on 2008-11-02
ok thanks i guess im just gonna back up my files and put 8.04 back on...

:)

---

