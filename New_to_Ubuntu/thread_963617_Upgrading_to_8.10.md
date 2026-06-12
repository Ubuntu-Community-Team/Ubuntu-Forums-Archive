---
title: "Upgrading to 8.10"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by TekkieFreak on 2008-10-30
Hi Everyone,  

I've been running the 8.10 beta...I'm wondering if there's any way to just upgrade to the release version without re-installing.  Thanks a bunch.

---

### Post by Mindzai on 2008-10-30
```
sudo apt-get dist-upgrade
``` should do it :)

EDIT: Sorry it's not that simple since 8.04 was a LTS release, have a look here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Fass on 2008-10-30
> **TekkieFreak said:**
> Hi Everyone,  

I've been running the 8.10 beta...I'm wondering if there's any way to just upgrade to the release version without re-installing.  Thanks a bunch.

sudo aptitude update
sudo aptitude upgrade

That's it. If you've been running the 8.10 beta, then just updating your system today will mean you will have the same system as the people who install the final today.

---

### Post by TekkieFreak on 2008-10-30
Here's my output from lsb_release...however I don't know what it said 
before.  So am I running the actual release?  I ran an update via adept yesterday evening....and tried to run one this morning.  It told me there was nothing to update this morning though.  Thanks for any help. :) 

ariel@Pikachu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid
ariel@Pikachu:~$

---

### Post by OrangeCrate on 2008-10-30
> **Mindzai said:**
> ```
sudo apt-get dist-upgrade
``` should do it :)

EDIT: Sorry it's not that simple since 8.04 was a LTS release, have a look here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

> **Fass said:**
> sudo aptitude update
sudo aptitude upgrade

That's it. If you've been running the 8.10 beta, then just updating your system today will mean you will have the same system as the people who install the final today.

Please read from post #93 on in this thread:

[http://ubuntuforums.org/showthread.php?t=936696&page=10](http://ubuntuforums.org/showthread.php?t=936696&page=10)

---

### Post by OrangeCrate on 2008-10-30
> **TekkieFreak said:**
> Hi Everyone,  

I've been running the 8.10 beta...I'm wondering if there's any way to just upgrade to the release version without re-installing.  Thanks a bunch.

If you have been doing the normal updates since installing the Beta, and it's up to date now, you have the final.

-----

BTW, reinstalling is not the preferred method of upgrading. Please see post #96 in this thread for guidance:

[http://ubuntuforums.org/showthread.php?t=936696&page=10](http://ubuntuforums.org/showthread.php?t=936696&page=10)

---

### Post by mankoff on 2008-10-30
I'm in the same situation... I've run "sudo apt-get dist-upgrade" prior to seeing the link to post #93 above... "lsb_release -a" shows the same output as above.

What is odd is that if I go to the System Menu, then About Ubuntu, and then select Version and Release Numbers from the right sidebar, I get this text:

> This version () was released in so its version number is .

This makes me think I'm not quite running Intrepid Ibex / 8.10. I've read the rest of the thread regarding apt-get v. aptitude, and I don't see how to recover from upgrading with apt-get. Any suggestions?

Thanks,

   -k.

---

### Post by OrangeCrate on 2008-10-30
> **mankoff said:**
> I'm in the same situation... I've run "sudo apt-get dist-upgrade" prior to seeing the link to post #93 above... "lsb_release -a" shows the same output as above.

**What is odd is that if I go to the System Menu, then About Ubuntu, and then select Version and Release Numbers from the right sidebar, I get this text:**



This makes me think I'm not quite running Intrepid Ibex / 8.10. I've read the rest of the thread regarding apt-get v. aptitude, and I don't see how to recover from upgrading with apt-get. Any suggestions?

Thanks,

   -k.

Mine says the same thing. I'm not sure what it means. It looks like an incomplete sentence, that may or may not be updated at some point.

Suggestion...

Do an update with Update Manager. I would assume there will be no upgrades available. (*)

Then go to the "System Monitor", and check which release is listed in the "System" tab. It should say 8.10 (intrepid).

```
lsb_release -a
```

should tell you the same thing... Intrepid 8.10

I don't think that jdong said it wouldn't work, it's just not the supported way of doing upgrades.

(I do know that forcing partial upgrades that have unmet dependencies using apt-get dist-upgrade, can bork your system. You have to be careful.)

Anyway, if everything is as I said above, you should be good to go.

Edit:

* I see that updates are beginning to trickle through now.

---

### Post by TekkieFreak on 2008-10-30
Thanks guys!!! Great info here. I just installed a couple weeks ago and was able to get my sound working...so I would hate to re-install in case it were to break something.

I'm running KDE and I absolutely love my desktop.  It is beautiful. :)

---

