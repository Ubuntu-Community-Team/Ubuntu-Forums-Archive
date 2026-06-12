---
title: "Rearranging partitions/temp directory in terminal"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by JCongo on 2011-12-01
Hi, I purchased a new VPS service running ubuntu 11.04 32 bit. My prior VPS services just had 1 partition and was straight forward. However my new one has 3 and I would like to know how to merge the 'tmp' partition with the largest one. 

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              34G  1.2G   31G   4% /
none                  242M  176K  242M   1% /dev
none                  249M     0  249M   0% /dev/shm
none                  249M   48K  248M   1% /var/run
none                  249M     0  249M   0% /var/lock
/dev/sda6             1.9G   35M  1.8G   2% /tmp
/dev/sda2              92M   27M   61M  31% /boot

```

I don't want or need that temp partition so I would prefer to remove it along with any page file and increase the size of sda3. Also what is with the other four 249 meg blocks? What would be the best way to deal with this?

---

