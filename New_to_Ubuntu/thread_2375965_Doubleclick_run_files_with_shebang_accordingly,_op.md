---
title: "Doubleclick: run files with shebang accordingly, open others with text editor"
date: 2017-10-29
forum: New to Ubuntu
---

### Post by barrywhyte on 2017-10-29
Is that possible? I find it inconvenient that I have to use context menu to either run or view a text file based on my setting.

Thanks.

---

### Post by mc4man on 2017-10-29
What version of Ubuntu are you using?
What files are affected?

Generally it has nothing to do with a shebang or not, only text files marked as executable would have options to run, view or ask
(current Ubuntu default is to view such files.

If Ubuntu (udisks2)  was operating properly then one could set the option to run. Then all text files marked as executable would run, all not set would be viewed. 

For the most part this is what I see here in Ubuntu 16.04 & 17.10.
 However in the case of files on a ntfs partition all files are currently being marked as executable which to me is a [bug..]("https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1728467")

---

