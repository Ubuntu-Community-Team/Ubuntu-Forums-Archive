---
title: "Setting up Dabo - &quot;No module named dabo&quot;"
date: 2011-10-27
forum: Programming Talk
---

### Post by Athefre on 2011-10-27
I've spent a couple of hours trying to get Dabo working.  The normal way of installing didn't work (as seems to happen with a lot of people), so I tried the other recommended way of creating a path file in python's "site-packages" folder.  In terminal I used gksudo..... to create and edit a dabo.pth file there and typed the following line into the file and saved:

home/james/Programming/dabo

I then tried a test "import dabo" to see if it works, but I get the error message "No module named dabo".  I've done a lot of google searching but still don't see what I'm doing wrong.

---

### Post by Athefre on 2011-10-27
After a lot more searching and testing, completing all of the steps on this page solved my problem:

[http://wiki.dabodev.com/InstallationOnLinux](http://wiki.dabodev.com/InstallationOnLinux)

The important information there may have been that I was supposed to be working in dist-packages instead of site-packages (I guess most Dabo installation guides were written for Windows users).

---

