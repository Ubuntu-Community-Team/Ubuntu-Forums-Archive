---
title: "Doing offline diff-based updates to remote Ubuntu 12.04.01 installations"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by samueldscott on 2014-04-13
We have a couple of hundred PCs and Laptops deployed world-wide in remote locations (mostly poor developing countries) with slow or no internet, which run our VM with Ubuntu 12.04.01 (LTS) as the OS.  None of these VMs are internet-facing, but many of them are connected to LANs and act as mini web-servers on the LAN; although our VM is encrypted, we have no control over other computers that are connected to these LANs.

We want to find a way to deploy only the most basic, essential security updates to 12.04.01.  Because of our unique situation, it's very difficult for us to distribute files much larger than 10 Mb.

My (very crude!) understanding is that the best way to keep Ubuntu installations updated is to use apt-get over the internet, or to create your own offline apt-get repository and use that for updates.  However, this requires files that are far too large for us to move around.

One advantage we have is that these hundreds of VMs are utterly identical - they are sealed from outside interference, and we know exactly what version of everything the VM is running.  So I was wondering if there's a way of generating an offline diff file, much smaller than an apt-get repository, that we could apply to deploy Ubuntu updates?  If so, how big would this file be likely to be (eg under 10Mb)?  Would there be a way of ensuring it only runs if it finds exactly the version of Ubuntu it's expecting?

Forgive me if these questions, or my assumptions about how Ubuntu updates work, are wrong - I'm very new to Ubuntu, and am hoping that this "absolute beginner's" forum will be quite forgiving if this is the case.  ;-)

Sam.

---

### Post by Double.J on 2014-04-14
Hi sam!


Welcome to the forums! 


I must confess this is not my area of expertise, however I also didn't want your first post to go unanswered!


I won't pretend to understand how the diff file might work. The only way I know to reliably meet dependancies is to create an offline repo with only the packages you want using [dpkg-dev]("https://help.ubuntu.com/community/Repositories/Personal"). You can have the repo only contain the packages on your system if you like, not an entire ubuntu repository.


I don't know if this may help, but during a usual update all new versions of packages are downloaded. By using the package [unattended-upgrades]("https://help.ubuntu.com/community/AutomaticSecurityUpdates") you can get just the security updates for your system? Could reduce downloads?


Just a thought but you could use split to send the updated repo in very small parts to the vms and have them reassemble it there if the internet connection is unreliable also? The custom repo can also be put on inexpensive media like cd's for distribution to non-connected machines?


Jj

---

