---
title: "FireFox 64 Freezes with Ubuntu 14"
date: 2018-12-31
forum: New to Ubuntu
---

### Post by harraust on 2018-12-31
Hi,

When I do the initial install of Ubuntu 14 Firefox opens with no issue. But each time I run the command sudo app dist-upgrade (which is ran after sudo apt update) Firefox (64) freezes the entire Thin-Client and the only way to bring it back to life is with a restart. I've reinstalled multiple times and the same thing happens after that command. 

Can someone help?

---

### Post by Autodave on 2018-12-31
It is WAY better to do a clean install rather than to upgrade to another version.  Unless there is a specific reason why you need 14.04, why not download 18.04 and start fresh?

  	 	 	 	   Every 2 years, a long term service release is made.  18.04 was the last one: released during the 4th month of 2018, hence the name 18.04.  The next LTS release will be in 2020 during the 4th month.  In the meantime, a new, short term release will be issued every 6 months.  These short term releases are only supported until the next short term release. However, the LTS releases are supported for 5 years.  It is always best to stick with the LTS releases. When it comes time to upgrade one of those, I have always found it easier and quicker to just backup what I need to keep, wipe out what is there, and do a clean install.

---

### Post by oldrocker99 on 2018-12-31
Autodave, you do have a separate /home partition or folder, don't you? It makes a reinstallation very easy, as long as you use "Something Else" and mount /home to the partition or HDD; your /home can never be too big.

---

### Post by Impavidus on 2019-01-01
Ubuntu 14.04 is old. When, after a fresh install, you run apt-get dist-upgrade, it upgrades a lot of packages (all updates that have been released in several years). Although it's Firefox that triggers the freeze, it may be an upgrade to a different package that is to blame. It's difficult to say.

Freezes are a bit hard to diagnose. Can you find anything in the logs at the time of the freeze?

And, as has been noted by others, 14.04 is nearing end of life. It has 3 months of support left. Unless you have some very specific reason you need 14.04, I suggest you do a fresh install of 18.04, skipping 16.04. But first test it in a live session.

---

### Post by harraust on 2019-01-01
14.04 is required for my use-case as I'm installing a management software over Ubuntu which is only compatible with 14.04 for the time being. I am going to attempt proceeding without running the dist-command as my end goal is to open Firefox in a terminal after the management software is installed which I can't because Firefox freezes.

---

