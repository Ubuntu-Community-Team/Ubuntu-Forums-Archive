---
title: "Backup to Remote Windows PC"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by atomant2 on 2011-11-29
I want to have a specific folder synced in the background to a remote windows machine anytime there are new files in the folder.  Is there an easy way to do this?

---

### Post by carverj on 2011-11-30
I know rsync is a great utility that backs up data to a remote location, perhaps it could be used to suit your purpose. 
I don't know from experience though so maybe someone else will have a better suggestion.

---

### Post by jumpyjester on 2011-11-30
As an alternative to RSYNC, I use Deja Dup. It can back up to most things via various protocols 
 
cant remeber the apt name so use 
apt-cache search deja
 
That sould give you the name then use apt-get install (deja name)
 
Its fairly straight forward to setup and will do what you need.

---

