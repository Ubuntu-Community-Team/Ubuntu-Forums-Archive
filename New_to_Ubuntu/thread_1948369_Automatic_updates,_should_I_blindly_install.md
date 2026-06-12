---
title: "Automatic updates, should I blindly install?"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by Splatted on 2012-03-28
I've been using Lubuntu for a few months now, and the size and frequency of the automatic updates has  been worrying me a bit. Every few days I get asked to install some more updates, and though they're usually quite small, they can sometimes be over 50mb in size.  

I rarely have any idea what the updates actually do, so I just click install and hope that it's uninstalling previous versions of files so I'm not really adding 50mb of stuff. The most recent update asked for my password, which kind of freaked me out a bit since none of the others have. It says it's necessary to add or remove programs, so does that mean that previous updates were just adding on to what was already there, rather than uninstalling old versions. I'm a bit worried that if I continue installing updates have filed up my hard drive pretty soon, and it won't be know what I can delete to make more space, so it would basically mean death by update.

I would just stop installing them, but several times I've found that something that didn't work a little while ago has been fixed by some automatic update.

---

### Post by mastablasta on 2012-03-28
you could use computer janitor or similar porgrammes to remove unwanted leftovers.
 
the big update is usually kernel update which includes improvements as well as important security patches. it is possible to revert to older kernel if needed. also older kernels not in use can be deleted.
 
updates need your password if they are doing changes to system files (for example security patches, certain software updates...).
 
as for being safe - generaly yes, but i did see things get broken on updates (flash not working on some hardware, skype not launching). fixes were then posted with new updates within short time.
 
edit: LTS releases receive security patches only after certain period and as result things do not get broken by updates.

---

### Post by Paqman on 2012-03-28
> **mastablasta said:**
> you could use computer janitor or similar porgrammes to remove unwanted leftovers.
 

I wouldn't touch Computer Janitor with a bargepole. Try Bleachbit.

As for updates: they're almost all simply security updates for packages you've already got, so won't take up any noticeable extra room. What will fill up is the APT cache. You can dump all obsolete packages from that with the command:
```
sudo apt-get autoclean
```
Or by using Bleachbit.

The one exception to the above is kernel updates. These are new packages that get installed, and the old ones don't get replaced. They sit on your system taking up an unholy amount of space (>100MB each) and contributing nothing. I periodically open up Synaptic and remove all the old ones, if you want a less geeky tool for this I believe Ubuntu Tweak can sort this out for you.

---

### Post by Rodney9 on 2012-03-28
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by centaurusa on 2012-03-28
> **Splatted said:**
> I rarely have any idea what the updates actually do, so I just click install and hope that it's uninstalling previous versions of files so I'm not really adding 50mb of stuff.

My practice, over several years, has been to accept all automatic updates.  I have never had an issue with disk space, even though I keep my Ubuntu root partition relatively small (I use a separate data partition in order that all of my data files are  accessible to both Ubuntu and Windows).  On only two occasions has the updating process caused me any grief; however, both took the form of the machine refusing to boot after an official update.  

In one case, the problem was related to the kernel, but my practice has been to retain the previous kernel as a boot (GRUB) option in addition to the newly-installed version.  This allowed me to boot using the previous kernel and sit things out until there was a fix.  

The most recent incident, which is current, is an update to the xserver files for Ubuntu 10.04 LTS which, on my specific hardware, causes a failure to boot.  I have logged a bug report and, for now, have to uncheck the two miscreant files in the list of any available updates in order to avoid having them installed.  I suspect that this issue will be "fixed" by installing Ubuntu 12.04 LTS in a few weeks from now.

So, the bottom line is (a) it is usually safe to accept automatic updates, and (b) make sure that you have a full system backup (disk image) available from which you can restore a previously-working system should things go south (or just re-install Linux).

---

### Post by Splatted on 2012-03-28
Thanks guys, I feel much better about it now. :D

And thanks to the link to the Lubuntu guide. My searches always took me to Ubuntu pages. XD

---

### Post by MickeyPilgrim on 2012-03-28
I wouldn't. I followed directions and updated 11.04 to 11.10 and have not been able to use Ubuntu since. The upgrade included a new kernel, and that seems to have been the fatal problem.
  What I have decided is this; wait for the new LTS, put in the updates for that release. But Never Update To A New Release. If you have problems, and ask for help, you get a lot of not-useful advice, like, "You should have wipe/deleted your old release and and done a clean install.
  I'm still a bit angry about what happened to me. I had been reading Ubuntu books for months, OMGUbuntu was my home page - I was doing my best to learn to be part of this community. But, enough about me... Just don't believe it when you are told that you can go back to the prior installation. It's a maybe/maybe not kind of thing.
  The real problem is that there is no such thing as "Absolute Beginner Talk". This "A.B.T." board is used by everybody for every problem. People try to be helpful but most of the suggestions either assume you have a deep grasp of both hardware and Ubuntu, or they are wild guesses. I now need to wipe several failed installs out of my Ubuntu partition so I can try a clean install of 12.04, but I dread what's going to happen when I ask for help. So, again, I'd suggest you keep it simple; get  a LTS release and stick with it, just allowing the updates to that version, and never, but never update to a new version without backing up your data and wiping the old version away.

---

### Post by Vaphell on 2012-03-28
agreed distro upgrade can be a pain and sticking with what works is a good policy.
I don't think automatic updates upgrade your system version though, you have to press that fat button explicitly mentioning upgrade.
Either way having sepatate /home makes it much easier to reinstall and having it configured i never bother with upgrading the system via updates.

---

