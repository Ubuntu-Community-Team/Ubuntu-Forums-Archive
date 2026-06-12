---
title: "Separate /home partition or /data?"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Lucifiel on 2012-07-12
Hi, I'm coming back to Linux after a few years of absence. And I've forgotten so many things but I still recognise a few familiar faces. :p Bodhi.zazen, aiyshu and so on. 

So yes, a newbie question here: is it advised to do a separate /home partition? Some people on other sites(general computer forums, distro forums, etc.) have advised /data instead. 

Currently, this Toshiba Satellite L510 netbook has a Windows 7 partition which comes first, with about 188gb of free space. So yes, plenty of space to go around.

---

### Post by oldfred on 2012-07-12
For new users I often suggest the separate /home, just to make it easier to reinstall if necessary and not have to worry about data in /home. Of course everything in /home should still be backed up.

But for those dual booting with Windows I also suggest a separate NTFS shared data partition. I generally like to separate system whether Windows or Linux from data. But I multi-boot versions of Ubuntu so I also have ext3 data partition and now use my NTFS data partition very little for new data, but it still has my Firefox & Thunderbird profiles.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) and is easily backed up.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

So if all data is in other partitions a separate /home is not required.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Lucifiel on 2012-07-12
Thanks a lot, oldfred, I've been slowly digesting them and taking down the relevant commands. :) Your help is highly appreciated. ^^

---

