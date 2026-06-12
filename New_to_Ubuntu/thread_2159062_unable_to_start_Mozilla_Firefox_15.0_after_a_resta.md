---
title: "unable to start Mozilla Firefox 15.0 after a restart"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by Hankbonk on 2013-07-01
I'm running an old ubuntu 9.0 jaunty .  With this a Mozilla Firefox 3.0 was inbedded .  I installed a newer Firefox 15.0, which I didn't have problems with untill I restarted the system, getting a dialogue box (which one I sadly don't remember) on which I forced to continue the restart .  Since then the link to my Firefox 15.0 doesn't work anymore, and I'm forced to use the old 3.0 version again .  Anybody got some idea what's wrong ?

---

### Post by Impavidus on 2013-07-02
Apart from running an outdated system? It depends on what kind of link you're talking about. Symlink, launcher. How did you install firefox 15? Can't you simply recreate that link?

Anyway, you're running an outdated firefox on an outdated ubuntu. I know firefox 15 is the last one that runs on jaunty. I recommend you install a supported version, but you probably heared that before.

Edit: I checked some of your earlier threads. If you're still running a live disk changes won't survive a reboot. You have to reinstall firefox after every reboot (inconvenient), use a live usb with persistence (if your hardware supports booting from usb. Still inconvenient, but slightly less so) or install ubuntu. 10GB of disk space should suffice if you're careful.

---

### Post by houseworkshy on 2013-07-02
I don't know your hardware details but if you were using the same stuff in 2009, guessing by the Ubuntu version, then you may fare better with a modern Xubuntu.  It's lighter on system resources and most importantly will have all the various security and bug fixed patches.  Lighter again is Lubuntu which is a bit old fashioned windows like.  Either way the first thing to do after installing anything is updateing and that simply can't be done with jaunty.   As you have got as far as a broken Jaunty, and have prepared a partition ( I've read some of your other posts too) , you've got the preinstall bits correctly sorted already, so don't persist with an insecure unsupported headache.  You may well find that a live session ( always try one of those first anyway ) solves all the problems by not creating them in the first place. If you have special reasons for using jaunty you could always virtualise it later, if it's a matter of being able to read old data the new system will still be able to handle it, eg libre office can open and play with anything created with open office.  So just back up your home/username to something external or even another partition ( be sure to remember any encription passwords etc ).

---

### Post by Hankbonk on 2013-07-02
Thanks for you your reply, Impavidus .

I installed Firefox 15.0 by downloading the archive file and then extracting it in \home\henk\firefox15, where was created a folder called firefox .  I then created a link (nowhere there was specified 'Symlink' or 'Launcher'), which I placed on my Desktop .
I allready recreated that link under another name,like you adviced, but when I executed it I had the same response : none .

I'm running ubuntu 9.04 from a 4GB HDD for quite a while now .  Not enough to install a better ubuntu system .  

I have been using this firefox version for quite some months now, and I never had similar problems with it, even if I restarted the system with firefox active .  It is only with that last restart when I got that dialogue box and went on with the restart that afterwards it didn't wanted to run anymore .  Maybe if I reinstall the whole firefox folder, I could lose the problem, what do you think ?

Hoping to hear from you, I remain,

Henk Vanneste
Gent/Belgium .

---

### Post by Hankbonk on 2013-07-02
Thanks for your reply Houseworkshy .

I must admit that I don't understand anything of your reply, guess I'm a real beginner in ubuntu .
But thanks for replying anyhow !

Henk Vanneste
Gent/Belgium .

---

### Post by Hankbonk on 2013-07-02
Impavidus and houseworkshy : I'm now running Firefox 15.0 Dutch again !

I have simply reinstalled it fully !

Thanks for pointing me out in the right direction !

Now I'll mark this thread as [Solved] .

Henk Vanneste,
Gent/Belgium.

---

