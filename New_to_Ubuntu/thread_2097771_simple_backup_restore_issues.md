---
title: "simple backup restore issues"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by beelzebufo on 2012-12-24
hello, I had a full system crash last night resulting in having to reinstall, which is no big deal because I had a back up, but now if I open simple backup and try to restore from files it backed up, when I click on the date that the backup was made, the program just freezes, goes grey, and doesn't come back up.. is there a fix for this? seems like there would be an easy way to do this, it's late, sorry for the grammar.

thanks

I also just tried with a deja dup backup I had made a while before, and it won't detect it's backup.. they are both on the root  of an external hd.

running ubuntu 12.04 on an hp with amd processors and an amd graphics card.

---

### Post by beelzebufo on 2012-12-24
no ideas? drat.

thanks anyway :)

---

### Post by Zill on 2012-12-25
beelzebufo:  Firstly, please be patient.  Responses can be a bit delayed during holidays as we are all volunteers here and *may* have other commitments! ;-)

Re Simple Backup I would suggest you ensure you have installed *exactly* the same version as you used to make the backup.  Versions have changed from time to time which *could* cause the problems you have experienced.

Having said that, Simple Backup just produces an archive of your files compressed in tgz format.  If you open the directory containing your backup you should see a file called "files.tgz".  This can be viewed with your archive manager, (such as File Roller), and extracted to the location of your choice.

Just remember that if the backup was run as root, then the backup needs to be extracted as root.  If this is the case then open Nautilus from the terminal with the prefix gksudo eg.
```
gksudo nautilus
```
Then when you have found your "files.tgz" file simply double-click or right click and open with Archive Manager.  This should ensure the archive manager opens as root.

---

