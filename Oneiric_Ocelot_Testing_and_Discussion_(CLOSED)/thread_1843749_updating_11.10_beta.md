---
title: "updating 11.10 beta"
date: 2011-09-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by robgraves on 2011-09-14
If I download and install ubuntu 11.10 beta1 and keep it updated, does it become the final by continually updating or do i actually have to keep downloading, say beat2, and release candidate etc?  Or if beta1 is not capable of doing this is, can you with beta2 or release candidate?
      Sorry, I've never done much  with a beta release before.

---

### Post by akand074 on 2011-09-14
You don't have to reinstall the new versions. When you update, you will get the new file versions and essentially become "beta2" etc. Though, you may want to do a clean install of the final release, especially if you've made any configuration changes during testing.

---

### Post by DustinCasler on 2011-09-14
The betas will turn into the finished 11.10. Also you can always move to the next version without a fresh install by doing using sudo apt-get dist-upgrade. I guess it's really whichever is more comfortable for you.

---

### Post by tobe.9 on 2011-09-14
Hi,

I decided to install ubuntu distribution on my laptop. I want to have newest version so i downloaded beta version of oneric ocelot. I expect some bug here but i have question what will happen when final version will be released? Will be my installaition still beta version for next release and i will have unstable software or after updating i will have stable version of ubuntu 11.10?

---

### Post by 3rdalbum on 2011-09-14
> **DustinCasler said:**
> Also you can always move to the next version without a fresh install by doing using sudo apt-get dist-upgrade.

Just to clarify, Dustin means you can use 'sudo apt-get dist-upgrade' to make sure your system is up-to-date. That command does not go to a whole new major version.

For example, it will never take you from 11.10 to 12.04. However it WILL take you from 11.10 beta to whatever the current state of 11.10 is.

So yes, in short, you don't need to reinstall or anything. Just keep your 11.10 up-to-date and it will become the final release.

---

### Post by howefield on 2011-09-14
Thread moved to the development "*Ubuntu +1 (Oneiric Ocelot)*" forum.

If you apply the updates, you will end up with the finished release. 

There are drawbacks to running development software as you seem to be aware, so be sure to read the stickies in this forum.

---

### Post by Lars Noodén on 2011-09-14
If you keep doing the software updates you will have the latest version and leave the beta behind.  If you do not do any software updates, your system will stay beta.

---

### Post by cariboo on 2011-09-14
Merged two threads on the same subject.

---

### Post by ngsupb on 2011-09-14
each development version must have this question **BOLDED** and sticked.

Every time the same question.

---

### Post by jerrylamos on 2011-09-14
> **ngsupb said:**
> each development version must have this question **BOLDED** and sticked.

Every time the same question.

And every time the Wrong Answer.

I install Beta 1.  updated every day.  Busted big time.  Says do a "sudo dpkg --reconfigure -a".  That powers down.  No evidence left for a launchpad bug,

Real hardware running Narwhal, Meerkat, Lynx LTS, etc. just fine.

O.K., re-install.  Updates O.K. for several days.  Then Wham!  Says do a "sudo dpkg --reconfigure -a".  That powers down.  No evidence left for a launchpad bug. 

O.K., re-install again.  Update in progress.,,,,

Ever since Dapper Drake Beta, there have always been some crash or other on Alpha's and 
Beta's which is why they are called "unstable" code, so I have to do a re-install.

If you don't want to do re-installs then wait for the real release code.  This is a development forum....

Another thing.  New install takes maybe 2,600,000 bytes +/-.  Keep doing installing, oops, up over 3,000,000 and going.  Higher and higher with every update.  Now one thing I do is look at /boot.  I use Synaptic to completely remove any old kernels.  That helps, but not as much as a new install.

Oh, yes, I do an exec:
```

#! /bin/bash
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

My working hypothesis when running pre-Alpha, Alpha 1,2,3, Beta 1, 2, Release Candidate is be prepared to do a new install at any time.  That's why this is a 5 boot pc....

Jerry

---

### Post by fjgaude on 2011-09-14
Thanks, Jerry, for the speak the truth as I have experienced it over the past few years.

The moderator can make a simple statement to the effect "**expect to re-install, reboot many times from Alpha through Beta and release.**"

---

### Post by seeker5528 on 2011-09-15
> **fjgaude said:**
> The moderator can make a simple statement to the effect "**expect to re-install, reboot many times from Alpha through Beta and release.**"

You should only "expect" to re-install if.....

[list]A: You have hardware that has proven to be problematic.[/list]

[list]B: You just let things get uninstalled without thinking about what is being removed and in some cases investigating/asking if there is some question.[/list]

[list]C: You just prefer to re-install when there is additional stuff that won't be installed when doing 'apt-get upgrade', 'aptitude safe-upgrade', or the equivalent in Synaptic of having the upgrade method set to 'Default Upgrade' and using the 'Mark All Upgrades' button.[/list]

Outside of that, you expect to have problems, you expect that some problems will be difficult, and in some cases those will require a re-install, but largely it depends on you, your experience level, patience, determination, masochism, etc....

Following Debian unstable, with some updates from experimental, and following Ubuntu by switching my Ubuntu sources.list to point to the new development repositories when they come online, it's pretty rare for me to re-install and when I do it's pretty rare that it is for some reason other than HDD failure, bad RAM, or other issue that cause file/filesystem corruption.

Once in a while you may have to purge the system back to the basics and build it up again, but that's where the patience/masochism comes in. :p

If you use a PPA some of them have a higher risk factor than others.

Later, Seeker

---

