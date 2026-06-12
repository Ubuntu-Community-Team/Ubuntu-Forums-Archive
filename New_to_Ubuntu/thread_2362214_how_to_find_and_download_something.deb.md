---
title: "how to find and download something.deb"
date: 2017-05-25
forum: New to Ubuntu
---

### Post by dpaddy on 2017-05-25
I need 64-bit libXp.so.6.  I have found [https://packages.ubuntu.com/search?suite=lucid&arch=i386&mode=filename&searchon=contents&keywords=libXp.so.6](https://packages.ubuntu.com/search?suite=lucid&arch=i386&mode=filename&searchon=contents&keywords=libXp.so.6) but I don't know how to use that webpage to discover the something.deb which contains libXp.so.6, neither do I know how to download whatever something.deb I need.  My options for downloading are via firefox or else wget.  When I click on a [libxp6]("https://packages.ubuntu.com/lucid/libxp6") link (from the page above) I get an error message "two or more packages specified (libxp6 lucid)".  Moreover, it seems the link is for i386, but I need 64 bit.

Would someone please walk me through how to use the tools to find and download (via firefox or wget) the .deb file I need?

Thanks

---

### Post by deadflowr on 2017-05-25
What release are you on?
This is the package for trusty.
[https://packages.ubuntu.com/trusty/amd64/libxp6/download]("https://packages.ubuntu.com/trusty/amd64/libxp6/download")
I do not see anything beyond that, though.

---

### Post by dpaddy on 2017-05-25
That download seems to contain libz.so, not libXp.so.6 ...  Anyhow, I could use some pointers about how to search for libXp.so.6  Also could use advice about how I can get past the error "two or more packages specified (libxp6 lucid)" when clicking on  [libxp6]("https://packages.ubuntu.com/lucid/libxp6") link in  [https://packages.ubuntu.com/search?s...rds=libXp.so.6]("https://packages.ubuntu.com/search?suite=lucid&arch=i386&mode=filename&searchon=contents&keywords=libXp.so.6")

---

### Post by deadflowr on 2017-05-25
It's directly from your own link.
Open your link, click on Search other suites > trusty > click on libxp6 in the listed packages > open new page and scroll down to the download > select amd64 > opens the page I linked.

Not sure where you see libz.so?

---

### Post by dpaddy on 2017-05-25
I mistyped "tar --list -f data.tar.gz" when it should have been suffix .xz instead.

 All is right with the world (for now). THANKS!

---

