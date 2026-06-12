---
title: "Things are going...weird."
date: 2013-12-28
forum: New to Ubuntu
---

### Post by exolutionist on 2013-12-28
Hello ubuntu community,

I'm kind of...how you say...extremely new to ubuntu. I've installed it once before but never used it. Now I'm running a CF-30 with the newest version (downloaded a week ago) and it seems to be working kind of weird. And not the I'm used to windows and now I have linux weird.

First, the Ubuntu Software Center seems to only have a handful of items, and anytime I search something to get (I.E. Myunity) it shows a magazine I can buy?

Second, if I try to get something manually in the terminal I get:
:~$ sudo apt-get install myunity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package myunity

Third, the software update poped up, but froze at 6% and when I restarted it it didnt even register any updates to do.

And so, if anyone can toss me some help it would be amazing, and if anyone has a thread on here pertaining to this or has a how-to or something like that I would be very happy.

Thanks!!

---

### Post by oldfred on 2013-12-28
Just to refresh things. # is just a comment, do not copy or type comments.
 #houseclean
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

If you get any errors then stop & post those.

---

### Post by exolutionist on 2013-12-28
As soon as I typed the sudo apt-get update I recieved this

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

**EDIT:** Seems to be working once I restarted it. Letting it sit and run I'll keep you posted.

---

### Post by oldfred on 2013-12-28
That means you have it open somewhere else. Any application tying to update creates a lock. I sometimes get that when I leave synaptic open and then try something from command line.

Do you still have Software Center open, or did it not close correctly and leave a lock file?

---

### Post by exolutionist on 2013-12-28
I dont think I closed it correctly. But It's running right now. and going. I think I'm just to impatient and as soon as it stalls I'm wondering why.

---

### Post by coldraven on 2013-12-29
I don't think that MyUnity is in the software centre so you won't find it there.
Some developers create programs and distribute them with PPAs.
[http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/](http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/)

Also read this thread because MyUnity might not work with your version of Ubuntu.
[http://askubuntu.com/questions/203709/how-do-i-install-myunity-on-12-10](http://askubuntu.com/questions/203709/how-do-i-install-myunity-on-12-10)

---

