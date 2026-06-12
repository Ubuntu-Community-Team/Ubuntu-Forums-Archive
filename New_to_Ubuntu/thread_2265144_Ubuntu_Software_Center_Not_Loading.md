---
title: "Ubuntu Software Center Not Loading"
date: 2015-02-12
forum: New to Ubuntu
---

### Post by Cassin_Stacy on 2015-02-12
Hello, new to Ubuntu (hence the selection), running ubuntu 14.04 LTS, and my software center refuses to load. 
When trying to uninstall, or reinstall, through terminal, I am getting this message
> 
cassin@cassin-Q500A:~$ sudo apt-get remove software center
[sudo] password for cassin: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
cassin@cassin-Q500A:~$ sudo apt-get install software center
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
cassin@cassin-Q500A:~$ ^C
cassin@cassin-Q500A:~$ 
From this, I am guessing that there is some sort of conflict with Steam here, and am confused as to what it is and what to do. Any advice?

---

### Post by mörgæs on 2015-02-13
Hi, welcome to the fora.

From another thread but applies here as well:
[http://ubuntuforums.org/showthread.php?t=2265029&p=13226780&viewfull=1#post13226780](http://ubuntuforums.org/showthread.php?t=2265029&p=13226780&viewfull=1#post13226780)

---

