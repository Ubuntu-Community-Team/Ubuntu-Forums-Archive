---
title: "Need help with installing files."
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Lingadharini on 2012-08-08
Hi friends,
Since I am new to the ubuntu with Lucid lynx(10.04), I have too much difficulty with installing files downloaded from the internet.
I have no trouble with installing the .deb package, since it opens with the default Gdebi package manager by default.
The other packages such as .tar, .tar.gz, .rpm etc are confusing.
Most websites dont tell which package I am supposed to download.
How to install from .tar, .tar.gz package? Can I download .rpm package? If so, how to install from that?
Also tell me what package files I can expect and which ones I have to choose to install on my lucid lynx.
I recently downloaded the most recent version of firefox that was in .tar.gz format.
I didnt know how to install from it.

---

### Post by Bigtime_Scrub on 2012-08-08
I highly recommend to only install software from Ubuntu repositories with Ubuntu Software Center. If you insist on outside software than .debs should work for the most part. RPM's will not work and the tar balls are most likely source code that you will have to compile.

---

### Post by Lingadharini on 2012-08-08
Thanks,  I will try that..

---

### Post by audiomick on 2012-08-08
Yes, stick to the repositories if you can. As mentioned, if you really want something that is not in there, use a .deb file. If you have to try from a .tar or .tar.gz , right click on it and chose "extract" out of the menu. When it is unpacked, have a look and see if there is a read-me file in there. Packages that are distributed as .tar file very often have some instructions in a read-me as part of the package.

Files in the .rpm format are intended for Red Hat / Fedora distributions. They don't work on Debian based distributions like Ubuntu. If you really want to try it out, there is this

[https://help.ubuntu.com/community/RPM/AlienHowto]("https://help.ubuntu.com/community/RPM/AlienHowto")

I have no idea if it works. You could try it for a one off thing. If you regularly find yourself wanting to try programs that are available primarily as .rpm files, you should perhaps think of installing a Fedora / Red Hat based distribution for that purpose.

---

### Post by Lingadharini on 2012-08-08
How to add some software to a repository if the website doesnt provide such facility?

---

