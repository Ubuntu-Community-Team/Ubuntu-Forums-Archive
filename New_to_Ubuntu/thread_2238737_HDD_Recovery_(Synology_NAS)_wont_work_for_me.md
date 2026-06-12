---
title: "HDD Recovery (Synology NAS) wont work for me"
date: 2014-08-09
forum: New to Ubuntu
---

### Post by ayhan2 on 2014-08-09
Dear members,
I have never used any kind of Unix Linux based OS till now and i am an absolut newbie in this case. 
I have a NAS system for home use and it is a Synology DS213j. After my holiday came home then turned all my netwerk devices on. Unfortunatelly my intern HDD on th Synology crashed and wont start prtoperly. I can login and see what happened. It says a kind of system crash. To solving this problem need to reinstall synology NAS OS. It is painfull because need a clean preparation which means it will format my HDD. Because of the file sytem n the HDD i cannot see the content on any windows based OS device. I can see via Synology login interface; all my files srill there but because of system failure cannot acces them.. I can read but not edit/copy/move... Very sad.
This is the solution that Synology provides: [http://www.synology.com/en-global/support/faq/579](http://www.synology.com/en-global/support/faq/579)
As you can see there is a solution and i can save my files with Ubuntu. So i decided to install it on my Laptop (Acer 5920g) Installation was OK. According to the recovery guide provided by Synology,  i did everything on the guide. But on the step 11:
> Run the following command to mount all of the hard  drives from your DiskStation.
  **root@ubuntu:~$ mdadm –Asf && vgchange -ay**

i am getting this on terminal;
```
root@ayhan-Aspire-5920G:~# mdadm –Asf && vgchange -ay
mdadm: cannot open –Asf: No such file or directory
root@ayhan-Aspire-5920G:~# 

```
so i cannot move on for further operations or comments. Any help would be preciated.

Thank you.
PS: I know my english is sucks.

---

