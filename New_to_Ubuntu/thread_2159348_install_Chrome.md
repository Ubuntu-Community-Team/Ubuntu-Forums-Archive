---
title: "install Chrome"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by ub9876 on 2013-07-02
13.04 with XFCE
cant get Chrome browser to install. I downloaded it ok from the Google site. What terminal code will install it???
The Ubuntu software center SUCKS.

---

### Post by Dennis N on 2013-07-02
It comes as a .deb file, so you could install it with **gdebi** package installer which available in the Ubuntu repos (package name: **gdebi**)

---

### Post by craig10x on 2013-07-02
I would assume it works the same in Xubuntu, on ubuntu you can also just right click the deb file you have of Chrome and there should be an option to install it using the ubuntu software center...click that and then about a minute later, the software center should open with a button to install it....

If you don't get that, then download gdebi and then you will be able to right click the file and install with gdebi as the previous poster mentioned...
Chrome is not available in software center because it has a license agreement i guess...that is why only chromium is in the software center...but like you, i prefer Chrome myself....that is how i install it...right clicking the file and then having ubuntu software center do it...

---

### Post by Bashing-om on 2013-07-02
ub9876; Hi !

I have successfully installed Google-chrome on 13.04 with xfce. on a AMD64 system; This is how I did it.
1. At the time of my install Chrome required the old library "libudev0_175-0ubuntu13_amd64.deb" -note for AMD64 -
```

wget -c www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu//pool/main/u/udev/libudev0_175-0ubuntu13_amd64.deb

sudo dpkg -i libudev0*.deb

```
2. Next is to get the file verification keys from Google's server:
download the key and then use apt to install it.
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```
3.Update your sources:
```
sudo apt-get update
```
4. And install the package:
```
sudo apt-get install google-chrome-stable
```

In the event there is a problem check:
  That a new file under /etc/apt/sources.list.d with the following contents:
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main was created.
Else manually create the file with that content. And run the update/upgrade commands once more.

Find Google-chrome installed :applications menu ->internet !!

[INDENT][INDENT]hope this helps[/INDENT][/INDENT]

---

### Post by KARNVORbeefRAGE on 2013-07-02
If all else fails, Chromium (open-sourced version of Chrome without the tracking) should install ok.
```

sudo apt-get install chromium-browser
```

---

### Post by newb85 on 2013-07-02
Bashing-om hit the nail on the head, but it's a little cleaner/easier to follow the steps and download links at [http://www.omgchrome.com/install-google-chrome-in-ubuntu-13-10/](http://www.omgchrome.com/install-google-chrome-in-ubuntu-13-10/).

---

