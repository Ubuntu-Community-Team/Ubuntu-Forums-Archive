---
title: "partitioning with gdisk"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by boregard on 2012-07-12
Hi all, Iam wanting to reinstall ubuntu 12.04, but before i do this I want to repartition hd using gdisk. This will not be dual boot, just ubuntu. I have been studying documentation on gdisk for a couple of days now, and Iam fairly sure I understand all the options like n, to make new partition,and w,to write to disk& exit,ect. What i'm having trouble understanding is how to size the partition and use the optimal option. If anyone could provide me with an example cmd. for this, to get me started in right direction It would greatly appreciated. Thanks

---

### Post by oldfred on 2012-07-13
I assume you have been out to the rodbooks site?

[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

If using gpt with BIOS create a 1MB bios_grub partition with no format. 

I have always used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning. But if a server with just command line then you need gdisk.

---

### Post by boregard on 2012-07-13
Thanks oldfred, I used gparted as you suggested. Iwent to device >create part. table > advance > chose gpt. in case someone has same problem. I will study the links you provided so Ican learn to use gdisk. I need to learn how to enter the correct info for sizing the partition. btw this solved the problem I was having in another thread. I'll mark that thread solved as well. Regards

---

