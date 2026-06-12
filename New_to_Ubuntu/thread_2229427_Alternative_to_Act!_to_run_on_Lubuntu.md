---
title: "Alternative to Act! to run on Lubuntu"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by therrera1550 on 2014-06-13
Hi all,

Like many computer users we want to find an XP alternative that doesn't require us to have to get the "latest and greatest" hardware and Windows.  We couldn't afford it anyway.

I recently moved to lubuntu 14.04 on an older laptop.  It is running well and has just the apps I need for basic office and Internet use.  One of my main apps is Act! version 11.0 which we use to maintain a database of our small customer base as well as a slew of data that would otherwise consume paper and file space.  The main thing we depend on is the fact that we can run Act! either as a centralized server based  database or have it distributed on workstations that simply synchronize the master database thus spreading any changes to our three workstations.

This is especially useful if we take a laptop on the road (which we don't use daily) as we can simply synchronize it before leaving home and it has the latest data and then re-synchronize it upon returning so the data gets spread to the other workstations at home.  While I haven't yet tried it, this feature would allow us to synch on the road via a vpn to the home workstation that has the master database.

Has anyone used Act! and migrated to an open source database that can be used in this fashion?  I prefer to use the synch method as opposed to a centralize database as should the server go down, so goes the database on the workstations until it can be brought back up.  We are not in a real time database situation so synching works well for us.

I am checking out a person who has done a migration of this type using a virtual machine approach.  I've never used vm software but am open to try it.  We do have some Windows based scanners and a vm approach might be the way to access the hardware to continue being able to use them.

Any suggestions?

Thanks in advance.

Tony

---

### Post by /ADM on 2014-06-13
I have never tried to migrate an existing database from proprietary to opensource, but I will give a comment on alternatives (however these alternatives probably won't be migratable).  So you would need to re-do your client databases and relationships.

A great alternative to Act! is a software called SugarCRM.  It is available in a Community Edition (no longer updating only bug fixes) on Sourceforge and there is also a Commercial version on the SugarCRM website.  To me at least it seems designed to act as an alternative to Act!

It runs on LAMP (Linux, Apache, MySQL and PHP).

If you do not like that, there are always online options.  For example; HighRise by 37Signals is a great CRM all online, it is not free but it also is not prohibitively expensive either (starts at 24$ p/m).  I won't post links as I am not sure if it is 'allowed' but a quick search will bring them up.

Hope this info helps.

---

