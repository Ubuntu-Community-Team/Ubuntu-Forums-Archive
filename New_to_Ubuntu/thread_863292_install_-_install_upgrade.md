---
title: "install - install upgrade"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by RayAuckland on 2008-07-18
Some years ago I was in linux.

I had my "home" folder on a different partition, it was great if I wanted to install a new vision of linux I never lost any of my information, until I installed a new version one day and lost everything.

So the question is if I went to install the latest version 8.04 (as far as I know,on DVD Australia magazine APC July 2008 ) if I went to install the next upgrade whenever it comes out, would that "home" folder be say "read-only" protected so none on the information in there would be lost by the next upgrade install?

---

### Post by manishtech on 2008-07-18
Hope you remember the process!!

Say your / is sda1 , swap is sda2 and /home is sda3
Now when you proceed to install the distro, it asks you to mount at least / and swap, you specify both and you have option to select more partitions. So now you mount sda3 as /home.

Now when you proceed, it asks you to format / but formatting /home is not necessary, so /home is just mounted not formatted.

I hope you got it. I explained it in n00best way I could have. A bit stupid way too.. :)

---

### Post by manishtech on 2008-07-18
Additional information:

When you go to install any disto and you mount partitions, then there are some partitions which need to be formatted before continuing.
These include / , /boot , /usr and some more...

/home does no come in this category

Am not sure of /usr/sbin and /etc

---

### Post by mlentink on 2008-07-18
If you upgrade, your home folder is generally left alone. 
But the set-up you used earlier ( a separate 'home'-partition) actually makes a lot of sense. I'm using it myself precisely for the reasons you mentioned.

Fortunately, the Ubuntu installer will let you create such a partition during the drive/partition setup phase of the installation process.

---

### Post by benfindlay on 2008-07-18
If you upgrade to the new version of ubuntu using the built in upgrader, it does everything for you on the fly, preserving your user folders in place!

Hope this help!

Ben

---

### Post by manishtech on 2008-07-18
> **benfindlay said:**
> If you upgrade to the new version of ubuntu using the built in upgrader, it does everything for you on the fly, preserving your user folders in place!

Hope this help!

Ben
Frankly speaking. I have screwed up my system once using this. I even hear a lots of such cases where upgradation breaks things.
Ont he other hand, some people report that their upgrade works flawlessly

---

### Post by RayAuckland on 2008-07-18
Yes I think that is how I lost my "home" partition because the instructions were not clear. I was "UPSET" by the changes. 

Mind you it would be great if the newer version install said something like "you already have data in your "home" partition would you like this backuped - this can be deleted later after the install if you wish?"

---

### Post by manishtech on 2008-07-18
> **RayAuckland said:**
> Yes I think that is how I lost my "home" partition because the instructions were not clear. I was "UPSET" by the changes. 

Mind you it would be great if the newer version install said something like "you already have data in your "home" partition would you like this backuped - this can be deleted later after the install if you wish?"
If you meant newer version installs as fresh and not upgradation:
But it cant detect your home partition unless you explicitly tell its home.
When you tell that a partition is home and not check "Format", then still its safe....

---

