---
title: "Upgrade from 10.10 to 12.04 using LiveCD"
date: 2012-05-01
forum: Ohio Team - US
---

### Post by frogotronic on 2012-05-01
Hi,

  Anyone try this yet?  Is their system still usable?

Thanks,
CH

---

### Post by TBABill on 2012-05-01
I always do a fresh install, but many have upgraded. Looks like a mixed bag if you go through forum posts for the last few days. Lots of failed upgrades posted, but that could be for many various reasons so it's impossible to predict if it will work well ahead of time. I've only upgraded once and I made a backup of everything first. Took a long time so I now just save my files, do a fresh install and then copy my files back. Saves hours of time.

---

### Post by skellat on 2012-05-04
> **cement_head said:**
> Hi,

  Anyone try this yet?  Is their system still usable?

Thanks,
CH
 
That's not a normal upgrade path.  To go from 10.10 to 12.04 would mean doing each intermediate upgrade along the way.  The jump from 10.04 to 12.04 does not currently work ***yet*** using the alternate install disc as upgrader.

---

### Post by frogotronic on 2012-05-05
> **skellat said:**
> That's not a normal upgrade path.  To go from 10.10 to 12.04 would mean doing each intermediate upgrade along the way.  The jump from 10.04 to 12.04 does not currently work ***yet*** using the alternate install disc as upgrader.

@skellat

I don't think so, I think that the way it used to be.  But by inserting the LiveCD, it gives one the option of upgrading from 10.04, 10.10, 11.04. and 11.10 *directly* to 12.04.

*Or...*Is the the LiveCD going to go through the incremental path (10.10=>11.04=>11.10=>12.04)?

Several people have already tried the 11.04 to 12,04 path and its somewhat worked.

- CH

---

### Post by vegarend on 2012-05-05
> **TBABill said:**
> I always do a fresh install, but many have upgraded. Looks like a mixed bag if you go through forum posts for the last few days. Lots of failed upgrades posted, but that could be for many various reasons so it's impossible to predict if it will work well ahead of time. I've only upgraded once and I made a backup of everything first. Took a long time so I now just save my files, do a fresh install and then copy my files back. Saves hours of time.

In my opinion a fresh install is the way to go. I've tried upgrading (in smaller steps) before, and it has always turned out to be more work. 

I suppose the only value in the upgrade feature is that you don't have to back up and restore. You can get around this with the right partitioning/allocation using fresh install as well. Backups are always good though :)

---

### Post by skellat on 2012-05-08
> **cement_head said:**
> Several people have already tried the 11.04 to 12,04 path and its somewhat worked.

Could you please elaborate on that further?

---

### Post by wilee-nilee on 2012-05-08
10.10 is end of released, you have to use a specific method just to get to 11.04, I would not do it myself.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If you decide to, clone 10.10 first, or back up what you can't loose, to be covered if it fails. Personally I never upgrade I like my OS clean and fresh. :)

clonezilla.org

---

### Post by frogotronic on 2012-05-22
> **skellat said:**
> Could you please elaborate on that further?

[http://askubuntu.com/questions/135917/failure-to-boot-after-upgrade-from-10-10-to-12-04](http://askubuntu.com/questions/135917/failure-to-boot-after-upgrade-from-10-10-to-12-04)

[http://askubuntu.com/questions/128135/upgraded-from-10-10-to-12-04-how-can-i-remove-any-remnants-of-settings-of-gnome](http://askubuntu.com/questions/128135/upgraded-from-10-10-to-12-04-how-can-i-remove-any-remnants-of-settings-of-gnome)

[https://answers.launchpad.net/ubuntu/+source/gtk+3.0/+question/195487](https://answers.launchpad.net/ubuntu/+source/gtk+3.0/+question/195487)

---

### Post by frogotronic on 2012-05-22
> **wilee-nilee said:**
> 10.10 is end of released, you have to use a specific method just to get to 11.04, I would not do it myself.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If you decide to, clone 10.10 first, or back up what you can't loose, to be covered if it fails. Personally I never upgrade I like my OS clean and fresh. :)

clonezilla.org

@wilee-nilee

That information appears to be out-of-date.  When one puts a 12.04 LTS LiveCD into a machine with 10.10 installed and reboots (boots off of the LiveCD); one gets the following prompt (see attached image).  My questions are VERY simple.  Has anyone tried this, and did it do straight upgrade from 10.10 => 12.04 and did it result in a working system?

Thanks,
CH

---

### Post by fmjrey on 2012-05-25
I just upgraded a computer from 10.04 to 12.04 using the upgrade option the live CD provided when noticing ubuntu 10.04 was already installed.
A few software had to be reinstalled manually, but so far it's running fine. Compared to another machine that I upgraded from 11.10 (using ubuntu, not the live cd) I haven't had much problems. On that latter machine I ended up with many system errors popping up, most likely because it had much more tweaks/ppa added compared to the one I just upgraded with the live CD.
So globally I'd say if you haven't tweaked too much your system and only installed software from the official repos, then the live cd upgrade should be fine.
As always, make a backup of your system, just in case!!!

---

