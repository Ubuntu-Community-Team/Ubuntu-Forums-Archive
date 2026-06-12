---
title: "googlechrome"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by jayant222003 on 2011-10-17
i am tired to install google chrome on fresh ubuntu11.04,anyone can help me

---

### Post by feedmebits on 2011-10-17
you can download the deb package from google and then install it throug the terminal.
 
sudo dpkg -i /path/to/deb/file.deb
 
or you can use this in the terminal:
 
sudo apt-get install chromium-browser

---

### Post by bootedguy on 2011-10-17
Chrome and Chromium are similar, but not the same.  Chrome is the one that Google updates frequently.  I could not get Chrome to install on 11.10, and it does not appear in the Software center on 11.10.  Chromium is an older version, and is not auto updated.

In my case, I could not get Bluetooth working in 11.10, and ended up going back to 10.10, which solved all the problems I had with 11.10.

---

### Post by oldos2er on 2011-10-17
Enable Google's linux repository to install Chrome: [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)

---

