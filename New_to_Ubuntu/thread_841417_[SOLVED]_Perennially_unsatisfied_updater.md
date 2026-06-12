---
title: "[SOLVED] Perennially unsatisfied updater"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Lao_Tzu on 2008-06-26
Hello!

My updater keeps showing an orange triangle and a "!". When I click on it, the Update Manager launches and says my package information was last updated 8 days ago. I click "Check" and it goes through the list of 70 packages, but then says:

-----
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

Some index files failed to download, they have been ignored, or old ones used instead.
-----

This keeps happening and I can't seem to fix it. Any ideas? (would be hugely appreciated, as always)

Thanks...

---

### Post by panhandle on 2008-06-26
Open a terminal and type the following command:

cat /etc/apt/sources.list


List results here for our information.

---

### Post by avtolle on 2008-06-26
What version of Ubuntu are you using? The support for Edgy ended in April this year, as I recall. 

You should remove those two repositories from your /etc/apt/sources.list file if you are using a later version, or comment them out at the very least. To edit```
cp /etc/apt/sources.list /etc/apt/sources.list.bak #making a backup, just in case
sudo nano /etc/apt/sources.list #open file for editing
```
Go in, and either delete the offending sources, or comment them out by putting a # before each. Then, ^o <Enter> to save, ^x to exit nano.
Then update (from terminal)```
sudo aptitude update
``` and run```
sudo aptitude safe-upgrade
```to download and install the pending updates.

---

### Post by Lao_Tzu on 2008-06-26
Thanks, panhandle. The contents of my /etc/apt/sources.list is attached.

avtolle, I'm using Hardy 8.04 on AMD64.

---

### Post by Lao_Tzu on 2008-06-26
Thanks for that advice, avtolle. I've removed one of the offending entries from the list. This one:

```

## Added to install IE
deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main
```

And then ran the commands you suggested, which worked fine (and freed up 15.1 MB). So far, no orange exclamation triangles, so good.

I'll squeak again if it comes back... but in the meantime, thanks a lot.

---

