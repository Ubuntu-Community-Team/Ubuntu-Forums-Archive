---
title: "Sort Software Packages by Disk Usage"
date: 2008-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by haldean on 2008-06-17
A quick tip, but I use it all the time:
If you're running out of disk space and you want to quickly see what packages are using the most space on your hard drive, use the following command:

```
dpkg-query --show --showformat='${Package;-50}\t${Installed-Size}\n' | sort -k 2 -n | grep -v deinstall | awk '{printf "%.3f MB \t %s\n", $2/(1024), $1}'
```

That will sort the packages by size, putting the largest ones on the bottom. If you only want to see the top few, you can type

```
tail -n 10
```

at the end, because in all likeliness you have a *lot* of packages installed ;D

Thanks to Cygnus for the grep -v deinstall tip ;D

---

### Post by wieman01 on 2008-06-20
Good one! Thank you.

---

### Post by sirlancelot on 2008-06-21
Also, a much easier way is to go in to Synaptic, and enabling the "Installed Size" column by going to "Settings" -> "Preferences" -> "Columns and Fonts" Click "OK" to close preferences.

You can then go to the "Status" filters and select the "Installed" filter then click on the column you want to sort by. It's interestingly called just "Size" instead of "Installed Size".

---

