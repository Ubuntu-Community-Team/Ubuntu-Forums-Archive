---
title: "No UPnP backends found unable to setup Mythbuntu"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Peterfc on 2008-07-06
Hi All

I have downloaded mythbuntu and i am trying to get it setup. After selecting English and then going to the next screen i get a message "No UPnp backends found" I have looked in the System under Preferences and also the Administration but found nothing about UPnp. I found nothing under the [www.mythbuntu.org/support](www.mythbuntu.org/support) documentation. Can anybody help.

Thanks for reading this post

---

### Post by tone33 on 2008-08-31
I'm having the same issue...any resolution to this?

---

### Post by Thacker on 2008-09-02
Same here - very frustrating especially as MeTV setup couldn't have been 
simpler.  Help please!

---

### Post by soluckytouselinux on 2008-12-10
hi everyone. love that ubuntu. having the same problem. maybe it's not made for ubuntu. no one has replied to this, so no answers??

---

### Post by ReddogOne on 2009-01-06
Not it should just work (not that that is helpful).

When you install to leave everything as default as possible seems to be a good option. 

I'm having problems with remote frontend though. In the past I have been asked if the system is standalone and if you say it isn't all the UPnP stuff just seems to work but not getting the question anymore!!!

---

### Post by ReddogOne on 2009-01-09
If you are desperate to try anything... install Ubuntu then use the following commands to install mythtv on machine (one with the backend, which may be same as frontend).

sudo apt-get update
sudo apt-get install mythtv

For some reason this seems to set things up so that UPnP works and the database is all nice and lovely. 

To further configure things you can install the mythbuntu control panel thing!

Like to say this is all my own discovery but I found it [here]("http://parker1.co.uk/mythtv_ubuntu.php"). Its how I set up my original system (but had forgotten).

---

### Post by Peterfc on 2009-01-09
Thanks Reddogone 

I have not done anything that started this thread because i am new and it seemed a bit much to do. I will now with your link get back to it.

Many thanks.

---

### Post by heikal on 2009-01-27
try this:
sudo/etc/init.d/mythtv-backend start....gd lck

---

### Post by ReddogOne on 2009-01-29
> **Peterfc said:**
> Thanks Reddogone

You're welcome. Something I have noticed (but not fully tested) is that you want (to try) powering-up the backend before the front end.

I wondering the if check of UPnP servers is done when you log-in (rather than run the client).

Will do more testing the next time my system fails. Not so often these days :)

---

### Post by Mythgruntled on 2009-02-02
Post deleted - issue resolved, see:
[http://ubuntuforums.org/showthread.php?t=1061276](http://ubuntuforums.org/showthread.php?t=1061276)

---

