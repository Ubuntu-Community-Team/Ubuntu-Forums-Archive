---
title: "Which version &amp; how to install?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Saurabhdua on 2008-11-09
Hi Guys,

Iam eager to try my hands-on a new nightly build of Mozilla browser called Minefield that is still in alpha stage.

I have come across the following link to download the "Linux Version":

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/")

However, there are 4 entries in total(couple for both Linux-i686 & Linux-x86).

Can anyone please guide me on which one to download & how to install the same??

Iam a newbie so please be a bit elaborative!

Wating...Waiting....Waiting!

---

### Post by ad_267 on 2008-11-09
I've got no idea what the .complete.mar files are, maybe that is explained somewhere on the website. You probably want the firefox-3.1b2pre.en-US.linux-i686.tar.bz2 file, unless you're using 64 bit Ubuntu, then you want firefox-3.1b2pre.en-US.linux-x86_64.tar.bz2.

Edit: I thought it would be source code but it's not, it's precompiled. To run it you have to close firefox if it is already open and then run the firefox-bin executable. You also have to make bash look in the current directory for libraries. To do this you need to open up a terminal and go to the directory where you extracted the archive, then run:
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
./firefox-bin
```

---

