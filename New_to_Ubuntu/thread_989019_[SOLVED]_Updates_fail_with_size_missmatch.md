---
title: "[SOLVED] Updates fail with size missmatch"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by MaxVK on 2008-11-21
Hi. I'm running Ubuntu 7.10.

Yesterday 3 updates were made available:
hpijs
hplip
hplip-data

Unfortunately when I tried to run the update I received the following error messages:

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch

I have tried changing the sources in Synaptic (according to another similar thread here), but this failed as well, with the same error.

Nothing seems to be wrong with my internet connection, which is direct LAN->Router->Broadband.

Can anyone help?

Regards

Max

---

### Post by jimmy the saint on 2008-11-21
try changing servers.  Go into synaptic and under settings>repositories pick "other for server.  click on choose best server (it is called something like that).  Pick that server it chooses and try again.

---

### Post by MaxVK on 2008-11-21
Thanks Jimmy, but I already tried that with no success.

---

### Post by jimmy the saint on 2008-11-21
hmm.  I ran those updates with no issues yesterday or this morning so it isn't likely to be the packages, especially if you tried from multiple servers.

---

### Post by niteshifter on 2008-11-21
Hi,

I have this problem as well.

I think the source material for the update is corrupt: I've tried different servers and a different path (network connections from me):

They all fail. All other material - video streams, file transfers, assorted other protocols - they all work. Just this update keeps dying.

---

### Post by MaxVK on 2008-11-21
That sounds like a possibility, but the problem is, what do we do about it?

---

### Post by plucky on 2008-11-21
Either log a bug report so they can fix the problem or check this [thread]( http://ubuntuforums.org/showthread.php?t=988241) for a workaround.


Hope this helps

Good Luck

---

### Post by MaxVK on 2008-11-22
Thanks Plucky - I had a quick read of that link - has anyone manually installed these updates manually like that? Is that a safe thing to do with regard to the way updates are normally done?

Cheers

Max

---

### Post by DesiArnez6 on 2008-11-22
Ive also got the same exact problem. I haven't done anything about it yet, but while searching across the net, came across these:

[https://bugs.launchpad.net/ubuntu/+bug/300162](https://bugs.launchpad.net/ubuntu/+bug/300162)
[https://answers.launchpad.net/ubuntu/+question/52049](https://answers.launchpad.net/ubuntu/+question/52049)

I'm not an advanced user so I waited before punching in a whole bunch of code I didn't understand without seeing more responses and follow ups on those threads.

---

### Post by MaxVK on 2008-11-23
Agreed - I dont like the idea of simply typing a bunch of stuff I dont understand.

Can anyone shed any light on the commands from the link above?
What exactly will these commands do?

> Open a Terminal from the menu Applications &#8594; Accessories &#8594; Terminal and type:
(when the system ask you a password give your user password, you will not see nothing when you type it, then press enter)

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove


---

### Post by cdtech on 2008-11-23
I'm thinking a source issue rather than a divert.

There is a bug report, and changing the source could help....

---

### Post by MaxVK on 2008-11-23
Thanks for your reply cdtech, but I have to ask... what does that mean? ;)

Max

---

### Post by cdtech on 2008-11-23
a package's version mismatch. If you received any package mismatch you could check with:
```
dpkg-divert --list
```
Although I'm thinking this may not be a divert. You could check with the above command.

---

### Post by dtgolder on 2008-11-23
bump--have had the same issues now for a number of days--but only on one of my ubuntu systems (I have 4 running). Strange.

Update:

Started to track this down. Have two systems running Gutsy 7.10--one is a desktop build (running MythTV primarily) and the other is a server build--which is the one having the problem.

Have changed the repository sources on the server to match those of the desktop (desktop build updated normally). Still have the same problem.

Ran the following as per the recommendation in this thread (with the exception of the distro upgrade commands):

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
*** sudo apt-get upgrade *** did not run this
*** sudo apt-get dist-upgrade *** did not run this
sudo apt-get clean
sudo apt-get autoremove

No luck here either--still giving the same 'size type mismatch' errors.

So not sure what the issue is, but it seems isolated to the server build--question I have for others with this issue is whether they're using desktop, alternate, or server installs?

-----------------

Found this: [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/300247](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/300247)

Seems it may be related to a Gutsy bug as well, and has been attributed to an 'archive accounting error'...new packages are to be released shortly?

---

### Post by Man_Beach on 2008-11-23
I'm getting it with desktop and the UK server.

---

### Post by MaxVK on 2008-11-23
Same here - 7.10 desktop

---

### Post by Jodelman on 2008-11-23
Same problem for me.

---

### Post by dtgolder on 2008-11-24
Hmmm...that's a surprise. Wonder why it's working on the one desktop install I have, but not for some of you? (Really expected this to be a server-install only issue).

Looks like it's fixed now...you may (as I did) have to reload the repository info (click the blue "Check" button in Update Manager).

---

### Post by MaxVK on 2008-11-25
Thanks to dtgolder mentioning that the problem seems to be fixed, I tried, and it has!

I'm going to mark this thread as solved, even though, technically, we didn't get to the bottom of the problem. Hopefully the same thing wont happen again.

Thanks to all who participated.

Max

---

