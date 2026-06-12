---
title: "tar.gz"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by 1chad1 on 2008-08-18
How do I install a tar.gz file, I downloaded my printer driver but I am not sure how to install it 
Thanks
chad

---

### Post by jualin on 2008-08-18
Check out [this link]("http://monkeyblog.org/ubuntu/installing/#source")

---

### Post by lisati on 2008-08-18
tar.gz files are archives. Often websites will have instructions for installing them somewhere near the download area. Failing that, open up the file from your desktop (or wherever you saved the downloaded file) using the GUI, and look for a "Read me" file.
Let us know how you get on, and if you need further help.

---

### Post by 1chad1 on 2008-08-18
thanks for the info and quick reply Ill give it a go
Chad

---

### Post by kansasnoob on 2008-08-18
Just out of curiosity what is the make and model of your printer?

---

### Post by 1chad1 on 2008-08-18
The printer I am trying to install is a canon lbp 3000 mono laser and after installing this one i will be attempting to install a canon mp600.
i am still having a bit of trouble, I keep getting a Permission denied message The console commands are
chad@chad-desktop:~$ cd'/home/chad/Desktop/cndrvcups-capt-1.70' 
bash: cd/home/chad/Desktop/cndrvcups-capt-1.70: No such file or directory
chad@chad-desktop:~$ /home/chad/Desktop/cndrvcups-capt-1.70/Makefile
bash: /home/chad/Desktop/cndrvcups-capt-1.70/Makefile: Permission denied
chad@chad-desktop:~$ 
if I just use the make command I  get
chad@chad-desktop:~$ cd '/home/chad/Desktop/cndrvcups-common-1.70' 
chad@chad-desktop:~/Desktop/cndrvcups-common-1.70$ ./configure
bash: ./configure: No such file or directory
chad@chad-desktop:~/Desktop/cndrvcups-common-1.70$ make
for dir in cngplp buftool cpca; do (cd $dir; make $target)|| exit 1; done
make[1]: Entering directory `/home/chad/Desktop/cndrvcups-common-1.70/cngplp'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/chad/Desktop/cndrvcups-common-1.70/cngplp'
make: *** [all] Error 1
I mst be going wrong someware but I am following the istructions and I still can.t get it to work
Chad

---

### Post by kansasnoob on 2008-08-18
Well this doc says, > Based on the driver files provided I assume that this will work for Canon LBP 1120, 1210, 3000, 3200, 3210, 3300, 3600, 5000 printers as well as the Canon LBP 2900 and 2900i.

Complex but detailed:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

---

### Post by 1chad1 on 2008-08-18
ok thanks ill have a look

---

