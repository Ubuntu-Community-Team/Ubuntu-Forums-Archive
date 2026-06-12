---
title: "[SOLVED] Does Firefox automatically update?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by egruber on 2008-07-15
I have Hardy which came with Firefox 3 Beta 5.  Is Firefox 3 for Ubuntu still in Beta?  ....if not, does it update automatically like the add-ons, or must I do something?  I'm used to Windows saying 'Check for updates".

Thanks!!

---

### Post by phidia on 2008-07-15
The package manager & notifications take care of updates on your system. In other words when updates are available you will get an update notification.

---

### Post by Agent ME on 2008-07-15
If your account is an admin then daily your system should automatically check for updates for all software installed via the package manager and alert you when there are updates. To force it to check for updates, go to System > Administration > Upgrade Manager.

On Ubuntu and many other linux distros, nearly all software is installed and managed by a package manager automatically, allowing you to install/uninstall software from a single place, find new software, and automatically update it, as opposed to on Windows, where many programs have to fend for themselves on upgrading.

---

### Post by egruber on 2008-07-15
I guess I don't have to do anything. Can you confirm that Beta 5 is the latest Firefox for Ubuntu Hardy?  I ask because when I look on the mozilla website it says that Firefox 3 is released, but nothing about it being in Beta.  And the Windows version does not appear to be Beta.

Thanks again for your help.

---

### Post by sports fan Matt on 2008-07-15
Firefox 3 has been released.  I am not sure how far its gotten because im stuck on a windows machine for a few days till i get my new 19 inch widescreen monitor.

---

### Post by philinux on 2008-07-15
Yes.

---

### Post by oldsoundguy on 2008-07-15
yes, for all systems including the Mozilla (Ubuntuzilla) install for Gutsy (which removes FF2 and puts in FF3)

---

### Post by seagullplayer77 on 2008-07-15
I'm not sure if Firefox updates itself--Opera man myself--but I do use Songbird, which *is* Mozilla software, and it always notifies me of updates. I suppose you could always go into Synaptic and try updating the Firefox package, just to see what happens, but sometimes the versions listed in Synaptic aren't the most recent ones. Just my two cents' worth.

---

### Post by aysiu on 2008-07-15
The latest version of Firefox 3 is Firefox 3 (not beta) in the Hardy repositories. Just use the Update Manager to install updates, and you should have Firefox 3 unless...

1. You have the Mozilla Firefox instead of the Ubuntu Firefox.

2. You have messed up repositories in your /etc/apt/sources.list file.

---

### Post by webofunni on 2008-07-15
Hi,

  Look at the titile of your FF. What it says. "Mozilla Firefox Beta" or only "Mozilla Firefox". 

If only "Mozilla Firefox" then you are in stable version. 

Also "FF >> Help >> About" What it says. If no "Beta" there then you are in stable ;-)

---

### Post by nowshining on 2008-07-15
remember tho - u won't get updates of newer versions of a program - this was only a special case, however after this unless u enable the backports, ur firefox will stay the same version and only security updates get applied and this goes for all sofware.

If you want to always get a newer version - download and install the FF from the mozilla site for linux, it's easy, just untar and run the firefox script and put it in ur home folder or somewhere - make a custom menu item poiting to it...

---

### Post by monolux on 2008-07-16
I've never needed to update my FF on terminal...it automaticly did so!!

---

### Post by mempman on 2008-07-16
You can always update your firefox via Synaptic package manager as suggested in previoius posts; however, Synaptic is usually a few days behind the latest mozilla releases.  If you want to update mozilla firefox as soon as a new version comes out... you have to to "gksudo firefox" and then go Help-->Check for Updates.

---

### Post by gandaran on 2008-07-16
egruber
       for your firefox beta5 to be updated to ff3 final in ubuntu 8.04 you have to enable the updates channels, go to system » administration » software sources » update tab, tick the security's updates and the recommended updates option. then open synaptic package manager, click the refresh/reload button, then just find the firefox update and install it.

---

### Post by egruber on 2008-07-16
Thanks Gandaran!  I knew I had to do something.  Following your suggestion revealed 261 updates (including the new Firefox).

---

