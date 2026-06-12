---
title: "[SOLVED] How can I import address book and firefox settings after instal?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by SANDKON on 2008-10-24
New to ubuntu. Have manged to set up ubuntu on external HDD but did not imprt firefox or thunderbird settings when installing. These are on XP drive. Is it possible, and how, to import these settings into thunderbird and firefox via ubuntu, as my system does not boot into XP?

---

### Post by Bucky Ball on 2008-10-24
Boot into XP, open firefox and thunderbird respectively, Export Bookmarks and Export Addresses onto a drive/partition that Ubuntu can read. Restart, boot Ubuntu, open firefox and thunderbird respectively, Import Bookmarks and Import Addresses.

Ubuntu should be able to read your XP NTFS partition without a problem, the main part is getting them into a neat, transportable file bundle, which is what you do when you import and save them. :)

---

### Post by SANDKON on 2008-10-24
> **Bucky Ball said:**
> Boot into XP, open firefox and thunderbird respectively, Export Bookmarks and Export Addresses onto a drive/partition that Ubuntu can read. Restart, boot Ubuntu, open firefox and thunderbird respectively, Import Bookmarks and Import Addresses.

Ubuntu should be able to read your XP NTFS partition without a problem, the main part is getting them into a neat, transportable file bundle, which is what you do when you import and save them. :)
Problem is that I've just managed to get Ubuntu to boot after 2 days and on boot up screen I have as a choice XP Professional which I know is not installed on my internal HDD so I don't want to boot that. I'm waiting for replies to a previos thread about this. I guess I'll just wait until then. Thanks anyway.

---

### Post by _sAm_ on 2008-10-24
> **SANDKON said:**
> New to ubuntu. Have manged to set up ubuntu on external HDD but did not imprt firefox or thunderbird settings when installing. These are on XP drive. Is it possible, and how, to import these settings into thunderbird and firefox via ubuntu, as my system does not boot into XP?

1.Install the ntfs config and mount the parition Windows use.
sudo apt-get install ntfs-config

2. Copy the profile folder Thunderbird use and the profile Firefox use on Windows and save them in your home folder. 

3. Start Thunderbird and make one account(just so it will make the needed profiles.ini file in your home folder).

4.Change where the profiles.ini is pointing to so it points to your profile(where the settings, mail and so on are stored). 

Here is an old guide [http://www.linuxjournal.com/article/8761](http://www.linuxjournal.com/article/8761) You can still use it.

---

### Post by hyper_ch on 2008-10-24
simplest way would just to copy the whole profile folder and copying back.

---

