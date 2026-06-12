---
title: "[SOLVED] Disk space configuration and layout."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by __lonewolf on 2008-08-05
Hello all.
  Have a question for those smarter then me with linux.  I currently have a computer for the kids to share which has a 20gb and a 30gb drive in them.  The 30gb currently has 32-bit hardy installed on it.  The 20gb is empty.  I would like to reconfigure things so that I can maximize space for the home directory, since two of the kids want to play nwn and the install can easily run up to 8gb(each) with stuff added on. 

Any suggestions or how to's on how to configure this?  Is there anyway I can install nwn so that they can share one install, thus saving disk space?  

Thanks in advance.

---

### Post by hyper_ch on 2008-08-05
neverwinter nights 1 or 2? Just curious.

---

### Post by __lonewolf on 2008-08-05
nwn 1.  Still working on getting nwn2 to work on another box we have.  Worked in wine until I applied all the updates to the game.

---

### Post by northern lights on 2008-08-05
I see two possible set ups:

--A--
20GB HDD
           10GB  /           32-bit Hardy
           1-2GB /SWAP
           8-9GB             Shared data
30GB HDD
           15GB  /HOME A     Home Kid A
           15GB  /HOME B     Home Kid B

--B--
30GB HDD
           10GB  /           32-bit Hardy
           1-2GB /SWAP
           18-19GB           Shared data
20GB HDD
           10GB  /HOME A     Home Kid A
           10GB  /HOME B     Home Kid B

I'd say A is the best setup, but if most of the kids' data is shared other than one game, maybe B would work better.

As far as a clue on the size of the swapspace is concerned:
How much physical memory does the comp have?
Are you planning on hibernating?

Still, on the whole nwn thing:
Two installed instances of the same application are a terrible solution. Never played the game, so I ain't certain, but most games have the option for multiple savegames or player profiles. Run it and check.

---

### Post by hyper_ch on 2008-08-05
I'd say using 2 GB (on the 30 gb drive) as swap, the rest as root (/) and use the 20 GB drive as /home

You can then install NVN into /opt

The account configs should the depend on which user is logged in and be stored in their according home folder.

---

### Post by __lonewolf on 2008-08-05
thanks for the layout ideas.  I would love to install it in a common location and have them use the same install, since they are on the one box so only one can play at a time anyway.  I am just not sure how to set it up.  Maybe time to try and play around with it. 

thanks!

---

### Post by __lonewolf on 2008-08-07
:)
Thank you to all the suggestions.  Got the machine reconfigured and using another script I found, I was able to setup the software with one installation and user files separate.

Thanks!!!!

---

### Post by billgoldberg on 2008-08-07
> **__lonewolf said:**
> :)
Thank you to all the suggestions.  Got the machine reconfigured and using another script I found, I was able to setup the software with one installation and user files separate.

Thanks!!!!

Could you mark the thread as solved please.

It's on the top of the page in the thread tools drop down menu.

---

