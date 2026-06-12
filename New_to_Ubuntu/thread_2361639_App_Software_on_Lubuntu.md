---
title: "App Software on Lubuntu"
date: 2017-05-18
forum: New to Ubuntu
---

### Post by sed_faster on 2017-05-18
Hello folks,

I updated all my system through "apt-get update". When I navigate through menus on my lubuntu I found this app "Menu->System Tools->Software". I acceded this app and saw the "updates". As the app reported I need update the system I push the button I wait.... after wait more a less 1 hour the bar didn't finished: [http://imgur.com/a/kdVFy](http://imgur.com/a/kdVFy)

My system:
> 
1-https://www.asus.com/us/Motherboards/PRIME-B250-PRO/
2-https://ark.intel.com/products/97123/Intel-Core-i5-7500-Processor-6M-Cache-up-to-3_80-GHz
3-SSD 120GB Kingston
4-Only two screen (VGA - 17") and (HDMI - 22")
5-8GB Ram


> 
user@user:~$ uname -a Linux user 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
user@user:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty


What should I do?
Thanks

---

### Post by vasa1 on 2017-05-18
> **Edgar_Oliveira said:**
> ...[http://imgur.com/a/kdVFy](http://imgur.com/a/kdVFy)
...
Please use the forum's attachment facility by clicking on the paperclip icon *above* the posting area. If you don't see this icon, click on *Go Advanced* below the posting area after which you will see this icon.
From the [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945"):> 4.   If you include screenshots, use the forum attachment system rather than an offsite host such as imgur.

For now, after running *sudo apt-get update* use *sudo apt-get dist-upgrade*. I'm on Lubuntu 16.04 and don't the route you mentioned. Or just use Synaptic.

---

