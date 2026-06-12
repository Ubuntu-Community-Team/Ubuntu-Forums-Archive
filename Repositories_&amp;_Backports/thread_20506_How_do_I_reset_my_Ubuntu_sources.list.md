---
title: "How do I reset my Ubuntu sources.list?"
date: 2005-03-17
forum: Repositories &amp; Backports
---

### Post by rykel on 2005-03-17
Hi all,

I am running Hoary preview in Singapore locale. (ie. many of the repositories in sources.list seem to have "sg" in their domain; eg. sg.archive.ubuntu.org)

However, I believe I have messed up my sources.list as many of the repositories cannot work (cannot stat/404 errors etc.) when I apt-get update them.

I would like to know where I can see a default Ubuntu sources.list that was installed initially onto my system?

Or, can I simply delete the current one and the OS will re-write a fresh new one for me?

Thanks for helping me with such a simple question!!


Best Regards,

Rykel
Singapore

---

### Post by dusu on 2005-03-17
Hi,

The OS will not rewrite the sources.list file for you.
Maybe you can just copy the lines


```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted
```

in your sources.list file. Do not forget to add multiverse if you need it.

I do not think that the sg matters so much (I hope I'm not mistaken !)

---

### Post by rykel on 2005-03-17
i'll go reset it straightaway. thank you very much!!    :-P

---

### Post by rykel on 2005-03-19
hi,

i faced a problem after updating apt-get using your sources.list... these are e messages...

rykel@diamond1:/media/windowsd/SuperDVD/Linux$ sudo apt-get update
Password:

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release [19.9kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources [173kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages [2170kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources [864kB]
Fetched 3244kB in 2m20s (23.2kB/s)
Reading Package Lists... Done

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: You may want to run apt-get update to correct these problems

as you can see, tis is the problem i faced... GPG errors... could it be related to my locale, which *might* require "sg" prefixes? also, wat does "IGN" stand for?

hope u can enlighten me, thank u!!!


best regards

rykel
singapore

---

