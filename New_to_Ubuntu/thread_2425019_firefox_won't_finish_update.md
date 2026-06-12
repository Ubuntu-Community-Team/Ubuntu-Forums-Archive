---
title: "firefox won't finish update"
date: 2019-08-19
forum: New to Ubuntu
---

### Post by jaxom98 on 2019-08-19
Hello, I am trying to get firefox 31 updated.  The down loads are arriving and the files seem to be extracting correctly.  BUT things seem to be stopping at this point. How do I make firefox complete the update?

OS : edubuntu14.04 
ram 4 Gb
hdd 320 Gb,  make unknown
My main computer is down and getting repaired, so I pulled this old one out to use in the mean time.

---

### Post by Autodave on 2019-08-19
14.04?  You may not be able to install FF 31 on there because that system is too old and can't support it.  I believe that it is time to upgrade by doing a clean install of 18.04.

---

### Post by Impavidus on 2019-08-19
How are you trying to update Firefox?

Edubuntu 14.04 has reached end of life. It was the last release of Edubuntu, so no release of Edubuntu is supported now. There is, however, still an edubuntu-desktop package available from the repositories for Ubuntu 18.04. Firefox 31 is so old that it appears your computer was not fully up to date when support for 14.04 ended.

You could try to get your computer somewhat upgraded by pointing it to the old releases server. See this guide and follow it up to and including the **sudo apt-get dist-upgrade** command: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades). It won't give you a properly secured and up-to-date system, but in an emergency, it may do. A fresh install of 18.04 is better. Depending on the speed of your internet connection, that could take anywhere between 40 minutes and a few hours.

---

### Post by jaxom98 on 2019-08-20
Hello Impavidus, your terminal command did the trick. Firefox is now current on ver66. 

Re the OS upgrade, I wait until 6 months has passed for any bugs to surface in the LTS, then upgrade.  As stated this is an old computer put aside when I got the main computer.


Thank you

---

### Post by Impavidus on 2019-08-20
The current version of Firefox is 68, not 66. But at least version 66 is better than version 31.

Waiting for 6 months after release before you upgrade to the next version of Ubuntu is indeed a good idea, but Ubuntu 16.04 is over three years old. Most bugs are gone by now. There are probably less known bugs in 16.04 than in 14.04. 18.04 too is more than a year old and pretty well polished.

---

### Post by cruzer001 on 2019-08-20
FF68 is also a ESR (long term support) release.

[https://wiki.mozilla.org/Release_Management/Calendar](https://wiki.mozilla.org/Release_Management/Calendar)

---

