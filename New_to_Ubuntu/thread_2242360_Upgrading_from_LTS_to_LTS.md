---
title: "Upgrading from LTS to LTS?"
date: 2014-09-01
forum: New to Ubuntu
---

### Post by newbietwo on 2014-09-01
Just came back to Ubuntu with 14.04...

Awesome...

When you upgrade from Ubuntu LTS to LTS I know that their is the one click upgrade...

How do you manage ppa's for the upgrade?  Do you have to disable through ppa manager?  Then, after upgrade re-enable?

Thanks for the knowledge.

---

### Post by TheFu on 2014-09-01
The non-core repos are disabled as part of the update process.
After the upgrade finishes, just edit the file (be smart about it), update, upgrade and life should be fine - that's the theory.  Some PPAs may not have 14.04 code ready, so be prepared.  Wouldn't hurt to know that going in.

I've migrated about 6 servers from 12.04 to 14.04 without any surprises. I think the main surprise was the change to apache 2.4 (or was it 2.6?) on one system. I don't use apache much anymore - mostly nginx here the last 8 yrs now - so my apache-fu is weak.

Desktop updates were mostly painless - except FreeNX. Decided to switch to x2go instead and had issues for 2-3 months, until an update in August made everything nice - better than FreeNX has been the last 5 yrs! I'm very happy ... er ... mostly. ;)

I am not the typical Ubuntu end-user, please understand that and temper my excitement with realistic expectations. No social networking used here, lots of inconvenient security on the network, and I have **backup religion** beyond what most users seem to have. I've been burned and learned my lesson.

BTW - please,please, please make a know-you-can-recover backup before beginning this process. Sometimes bad things happen - just sayin'.

---

### Post by mcduck on 2014-09-01
The upgrade should automatically disable any third-party repositories, including PPAs. They won't get automatically enabled afterwards, but if you use the PPA manager it should be able to check which of the PPA repositories have packages available for the new version and automatically enable those for you. Any third-party sources other than PPA repositories you might have to manually edit/enable again. (The updater just comments them out so it's fairly straightforward job to do)

---

### Post by grahammechanical on 2014-09-01
I would also revert the desktop as close to a default desktop as possible. If you have added themes and icon sets revert to default versions. And deactivate the proprietary video driver and use the open source video driver instead.

I would further add, to wait until Update Manager offers you an upgrade to the next LTS. Some people rush to upgrade the first day of a new release. There is a command we can use but many found that rushing the upgrade to 14.04 before Update Manager offered the upgrade did not give them success.

Look at the posts on this forum and you will see why many of us recommend a fresh install. I have tested upgrades from a default 10.04 to 12.04 and a default 10.4 to 14.04 and I did not have problems. I see that success as being down to having a default install of Ubuntu to start with.

Regards

---

### Post by ian-weisser on 2014-09-01
If you are using lots of PPAs to get the latest software, then you probably shouldn't be using an LTS.

---

### Post by TheFu on 2014-09-02
> **ian-weisser said:**
> If you are using lots of PPAs to get the latest software, then you probably shouldn't be using an LTS.

For certain values of "lots of", I suppose that is true. ;)

PPAs are often per-release too. I've zero issues with the nginx PPA or others for well-known servers and applications.  OTOH - using Joe's Kewl-ish-App PPA is always risky on any release.

---

