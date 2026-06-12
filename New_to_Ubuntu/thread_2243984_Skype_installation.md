---
title: "Skype installation"
date: 2014-09-12
forum: New to Ubuntu
---

### Post by ianmol on 2014-09-12
Hi

I am getting a problem in installing skype. 
During installation I get a message related to libqtwebkit4
I am new to Ubuntu (14.04), can you please let me know what to do ....
Any help is appreciated. Thanks.

---

### Post by ian-weisser on 2014-09-12
Please show us the exact error message, and the steps you take to reach the error message.

---

### Post by redrumrogue on 2014-09-13
You may have to install dependencies after installing skype.  After installing skype type "sudo apt-get -f install" in terminal ... by the way I don't think skype 4.2 for linux works on ubuntu 14.04.  You need to install skype 4.3.

---

### Post by fantab on 2014-09-13
Have you enabled 'multiverse' repositories? 'Software Center' -> edit -> 'software sources': select both 'Partner' and 'Independent' repositories. Then 'reload' or sudo apt-get update.

---

