---
title: "Backup Systems and ZFS questions - URBackup etc"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by Tecdragon on 2013-04-12
Currently I am using Emc Avamar it is great and I will continue to use  it for my company.  The problem is that I have to offshoot three smaller  companies from my larger one.  I would like to have some sort of back  up plan that is free or open source.  I have found Amanda, Bacula, Fog,  and URBackup, but I don't know a thing about any of them and would like  some advice. 
  	
Basically I want to do

  	Incremental image level backups of 3 servers some versioning would be nice

  	Workstations are secondary but would be nice
  	I would like it to dedupe - or at the very least compress data
  	 
  	Any guidance on a freebie solution would be appreciated, thanks
     

Ok so URBackup says to use ubuntu with ZFS as zfs will auto compress and de-dupe.  Ubuntu on one of their pages says you can add zfs after installation by adding a ppa directory.  does this convert the native file system to zfs?  has any one used urbackup, is there a better option available?

---

