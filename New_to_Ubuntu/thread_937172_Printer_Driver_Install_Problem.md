---
title: "Printer Driver Install Problem"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by rayboston on 2008-10-03
Hi Folks,

I am trying to install a driver for a Brother MFC8500 in Ubuntu.  I've downloaded the LPR and CUPS .deb files from the Brother site, but when I try to install the LPR I get the following error:

```

rays@office-ubuntu:~/Downloads$ sudo dpkg -i mfc8500lpr-1.1.2-1.i386.deb 
(Reading database ... 95938 files and directories currently installed.)
Preparing to replace mfc8500lpr 1.1.2-1 (using mfc8500lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc8500lpr ...

Setting up mfc8500lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC8500': No such file or directory
chown: cannot access `/var/spool/lpd/MFC8500': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC8500': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC8500': No such file or directory


rays@office-ubuntu:~/Downloads$ cd /var/spool/lpd
bash: cd: /var/spool/lpd: No such file or directory

```

It appears the entire lpr server is not installed.  Am I missing something?

Thanks!

Ray

---

### Post by kylet450 on 2008-10-03
your in your directory Downloads

Do:

cd ~ ( till you get to your home )

cd /

then cd /var/spool/lpd

---

### Post by rayboston on 2008-10-03
Hi,

Thanks, but I'm confused. Those will just move me to my home directory, then the root directory.  Are you saying I should run the dpkg from the root directory?

Ray

---

### Post by kylet450 on 2008-10-03
no this ( from root dir ) cd /var/spool/lpd

after you done the .deb pkg ( where ever thats located )

---

### Post by rayboston on 2008-10-03
Ah.  But the problem is that /var/spool/lpd doesn't exist. 

I'm wondering if the printer system is installed at all.

---

### Post by kylet450 on 2008-10-03
do to your .deb file and open it by right clicking it.
Try installing it like that.

OR

If your using hardy/Intrepid it should automatically set it up for you when you plug it in.

---

### Post by rayboston on 2008-10-03
Thanks.

Sadly, no such luck.  I ran it with Gdebi.

But I get the same result with the command line.

---

### Post by kylet450 on 2008-10-03
Oh sorry but theres not much i can do :(

Sorry.

But plug it in and turn on and see what comes up.

---

### Post by rayboston on 2008-10-03
Yeah.  It's a puzzler.

Do you think I should just create a /var/spool/lpd?  

rays@office-ubuntu:/var/spool$ ls
anacron  cron  cups  cups-pdf  mail  openoffice

---

### Post by kylet450 on 2008-10-03
No, you shouldent do that.

Plug your printer in and see what it says:

if you have already done that, try printing a text file.

---

### Post by rayboston on 2008-10-03
Oh... too late ... I already did it.

Amazingly it worked.  I was able to install LPR.  Then I installed CUPS and its complained about missing directories.  So I created those.  

After that I deleted my printers from the printer tool and reinstalled it.  I found my drivers and printed a test page and that worked!

Amazing.  I still wonder if I'm missing something or if the Brother install scripts assumed that one had already installed other printers.

---

