---
title: "Installing Software from a PPA"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by chris48083 on 2012-01-01
Hello all--

Hopefully this isn't too painfully easy, but having just removed windows yesterday, I'm still trying to find my way around ubuntu this morning.

My question is about PPAs.  I ran into a piece of software that I would like to install and it ran me through steps for adding the PPA to my list of Software Sources.  Ok.  Cool.  Now what?  How do I run the software?  I can see it added to the list...

Thanks for the help!

-C

---

### Post by yugnip on 2012-01-01
After adding the ppa, you then need to install the software, ie

```
sudo apt-get update
sudo apt-get install your_desired_software
```

where your_desired_software is the software you wish to install. Then you should see it in the applications menu, ready to go.

---

### Post by Paqman on 2012-01-01
> **chris48083 said:**
> Ok.  Cool.  Now what?

Open Ubuntu Software Centre and install your software, just like anything available from the Ubuntu repos.

A PPA is just a mini repository. It allows your normal package management tools (eg: Software Centre, Update Manager, apt-get, etc) to access the extra packages.

---

### Post by chris48083 on 2012-01-01
Got it!  Thanks, fellas!

Clearly I have some reading/learning to do, but thanks for helping me get on my feet.

BTW - Ubuntu apparently has way better disk management than Windows and is alerting me that one of my disk is about to fail.  Fortunately there's two 80gb hard drives in this machine, unfortunately it's the one with the OS on it that's failing. 

My plan is to migrate the OS to the healthy drive and install a new drive in place of the failing one.  I have 2TB on a network drive, so I keep the drives pretty clean.  The healthy drive is formatted and has nothing on it, what's the best way to clone this drive over so I keep the install and all the software I just loaded up??

Also, is there a specific way I should partition the new drive for the faster/most efficient OS install?

Thanks again for the help!

-C

---

### Post by wildmanne39 on 2012-01-01
Hi, clonezilla is a good program for cloning but be aware if it is about to fail clonezilla may finish it off.
[http://www.clonezilla.org/](http://www.clonezilla.org/)
Thanks

---

### Post by chris48083 on 2012-01-01
Yeah, I'm not sure how much longer I have.  I guess taking the safe route would be wise.  

When I installed Ubuntu it asked me if I wanted to transfer a user over?  Can I use that to take all the software and everything else I just setup??

-C

---

### Post by wildmanne39 on 2012-01-01
Hi, I used clonezilla about 2 months ago the partition failed with the system files but I chose to continue and it cloned all my personal files on my home partiton so I did not have to start from scratch.
Thanks

---

### Post by yugnip on 2012-01-01
Clonezilla would be the best route. But if you are using 11.10, you might try Deja Dup which is already installed (System Settings/Backup). It would allow you to backup your /home folder and all it's settings. Of course you would have to reinstall the OS and grab all the apps you have previously downloaded, but at least all the settings would still be there. And it's much less intensive than Clonezilla. After a reinstall, you just go back to Backup and choose 'restore'.

Whichever you choose, it's best to get the backup thing down. Maybe after this first go you can try Deja Dup as a permanent solution.

---

