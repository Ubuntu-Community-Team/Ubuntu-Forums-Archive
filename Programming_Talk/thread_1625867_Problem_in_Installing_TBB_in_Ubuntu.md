---
title: "Problem in Installing TBB in Ubuntu"
date: 2010-11-19
forum: Programming Talk
---

### Post by asianb on 2010-11-19
I hope I am not asking a stupid question.
I dowloaded TBB from this URL:
[http://www.threadingbuildingblocks.org/download.php](http://www.threadingbuildingblocks.org/download.php)
Stable Release --> tbb30_20100915oss_lin.tgz

In the pdf file "Getting_Started.pdf" in documentation. I should read "INSTALL.txt" in order to be able to install this library, but there is not a file with that name at all.
and no "install.sh".

Where I did make mistake?

---

### Post by harshavardhan1989 on 2011-02-27
I am facing the same problem. Someone please help.

---

### Post by Cesarf on 2012-04-25
I also had this problem, and since Googling didn really solve it for me... I figured I'd post what I did. I'm on 11.10 fwiw.

Download the latest version of TBB from the website. In my case it was tbb40_20120201oss_lin.tgz.
Extract it, it should be a folder named like tbb40_297oss.


Browse to that location from the terminal. Then go into /src/ then give it the make command. (make)


Before doing that I installed the latest version of the TBB Packages with apt-get. You can find the list [here.]("http://packages.ubuntu.com/source/hardy/tbb") Hope this is of help to anyone that stumbles upon this.

---

