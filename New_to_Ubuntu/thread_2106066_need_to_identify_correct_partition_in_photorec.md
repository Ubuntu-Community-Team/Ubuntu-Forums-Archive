---
title: "need to identify correct partition in photorec"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by necron_99 on 2013-01-17
I am trying to recover files from a deleted 212 GB Linux partition running Photorec on the Rescue Remix 11.10 CD. Photorec finds these partitions:

No partition 0 0 1 38913 80 63 625142448 sectors
1 P windows RE(store) 0  32 33 1958 64 26 31457280
2 * HPFS - NTFS 1958 64 27 1971 0 13 204800 (SYSTEM RESERVED)
3 P HPFS - NTFS 1971 0 14 11128 12 23 14707971 (ACER)
4 E Extended 11128 42 49 38913 70 5 446367746
5 L Linux Swap 38424 129 42 38913 70 5 7852032

Should I select 4?

---

### Post by mapes12 on 2013-01-18
If that's where you think your data is located then yes. Photorec uses read only access to get to your stuff so even if it's not the correct partition then you can't do any harm. Just back out and try somewhere else.

---

### Post by bab1 on 2013-01-18
> **necron_99 said:**
> I am trying to recover files from a deleted 212 GB Linux partition running Photorec on the Rescue Remix 11.10 CD. Photorec finds these partitions:

No partition 0 0 1 38913 80 63 625142448 sectors
1 P windows RE(store) 0  32 33 1958 64 26 31457280
2 * HPFS - NTFS 1958 64 27 1971 0 13 204800 (SYSTEM RESERVED)
3 P HPFS - NTFS 1971 0 14 11128 12 23 14707971 (ACER)
4 **[COLOR="Red"]E[/COLOR]** Extended 11128 42 49 38913 70 5 446367746
5 L Linux Swap 38424 129 42 38913 70 5 7852032

Should I select 4?
Hmmmm, if you deleted the partition how can you select it now.

Note that the **[COLOR="Red"]E[/COLOR]** stands for extended.  That partition is used to hold other partitions.  The only other Linux permission is the swap partition and for sure you don't want that.

I guess what I'm saying is: it may have data, but then again it may not.

---

