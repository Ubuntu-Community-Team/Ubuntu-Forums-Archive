---
title: "Google Chrome Install by Terminal"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-05-21
Hello All,
Is it possible to install google Chrome via a command terminal, instead of going to google.com and installing that way?
Thanks for the help
Ubuntu 13.04

---

### Post by Frogs Hair on 2013-05-21
The open source Chromium which Chrome is based on can be installed from the command line, but not Chrome without the source . See Below

---

### Post by deadflowr on 2013-05-21
Yep.

This is dated but should still apply:

[http://www.liberiangeek.net/2011/12/install-google-chrome-using-apt-get-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/12/install-google-chrome-using-apt-get-in-ubuntu-11-10-oneiric-ocelot/)

Basically you need to add the chrome repos.
Then update
And install

---

### Post by Cheesemill on 2013-05-21
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

Replace amd64 with i386 if you want the 32-bit version.

This is exactly the same as downloading it from the website, just using the wget command instead of a browser.

---

### Post by ajgreeny on 2013-05-21
Is there some good reason for your wanting to do it that way?

There is no source code for Google Chrome as it is a proprietary application, so you can not install in that manner, but if you have the google chrome .deb file available to you it is possible to use the terminal to install it with ```
sudo dpkg -i /path/to/google-chrome.deb
```

Chromium, the open source browser on which google-chrome is built, can be installed like any other open source application, of course, ie using the .deb package in terminal as above, using the package manager, or if you wish using the source code from an archive.

---

### Post by Santana001 on 2013-05-21
Wow i was looking for this thxs

---

### Post by monkeybrain2012 on 2013-05-21
You don't need to add chrome repo,  just grab the deb from Google and right click to install it and that's it. The repo will be automatically created.  Some people apparently try to push for Chromium, that is fine but just bear in mind that Chromium is not Chrome, it is stripped down and quite crippled by comparison, it doesn't have the built in pdf browser and updated flash for examples. Chromium is also very outdated.  

If you want to install Chrome on *buntu 13.04, you need to grab libudev0 which is absent from 13.04's repository

There are download links for this package here. 

[http://www.webupd8.org/2013/04/fix-google-chrome-cant-be-installed-in.html](http://www.webupd8.org/2013/04/fix-google-chrome-cant-be-installed-in.html)

---

### Post by vasa1 on 2013-05-21
> **monkeybrain2012 said:**
> ...
If you want to install Chrome on *buntu 13.04, you need to grab libudev0 which is absent from 13.04's repository
...
Hi, that's no longer necessary since Chrome 27 (which has the fix for the missing dependency) is now Chrome stable. I installed it on 13.04 last night without any dependency issue.

---

### Post by Tjkhan on 2013-05-21
try 
```

sudo dpkg -i /path/to/google-chrome.deb
```

---

