---
title: "Can not install Chrome"
date: 2016-06-14
forum: New to Ubuntu
---

### Post by Tom_Carr on 2016-06-14
I have a new install of Ubuntu  16.04 64-bit.
Chromium installed just fine from the software center.
Then I went here [https://www.google.com/intl/en-US/chrome/browser/desktop/index.html](https://www.google.com/intl/en-US/chrome/browser/desktop/index.html)
Down loaded the .Deb and clicked it
It opened the software center and a button to install chrome
I pressed the install button
It said "installing" for about 3 seconds, then stopped.

---

### Post by ashwin.kj on 2016-06-14
This method is working fine for me. But I guess you can try the method mentioned in UbunutUpdates.org

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update 
sudo apt-get install google-chrome-stable
```

Hope that helps

---

### Post by jake-swensen on 2016-06-14
More information is available in this thread:

[https://askubuntu.com/questions/510056/how-to-install-google-chrome](https://askubuntu.com/questions/510056/how-to-install-google-chrome)

---

### Post by Tom_Carr on 2016-06-15
I tried installing it from the terminal.  You can see what I did below.  When I look it in the launcher it still doesn't show up.  Maybe it won't run on this computer.  The processor is 64 bit, but it will take a max of 4GB memory, so I am not clear if this is a true 64 bit box.  I do have ubuntu 16.04 64 bit installed.

```
tom@tom-Veriton-X275:~$ wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add - 
[sudo] password for tom: 
OK
tom@tom-Veriton-X275:~$ sudo sh -c 'echo "deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google.list'
tom@tom-Veriton-X275:~$ sudo apt-get update
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Get:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1,189 B]           
Get:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [916 B]         
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                 
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease       
Hit:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease     
Get:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1,345 B]
Fetched 3,450 B in 0s (3,861 B/s)     
Reading package lists... Done
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
tom@tom-Veriton-X275:~$ sudo apt-get install google-chrome-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  google-chrome-stable
0 upgraded, 1 newly installed, 0 to remove and 177 not upgraded.
Need to get 49.5 MB of archives.
After this operation, 189 MB of additional disk space will be used.
Get:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 google-chrome-stable amd64 51.0.2704.84-1 [49.5 MB]
Fetched 49.5 MB in 6s (7,446 kB/s)                                             
Selecting previously unselected package google-chrome-stable.
(Reading database ... 206470 files and directories currently installed.)
Preparing to unpack .../google-chrome-stable_51.0.2704.84-1_amd64.deb ...
Unpacking google-chrome-stable (51.0.2704.84-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up google-chrome-stable (51.0.2704.84-1) ...
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/google-chrome (google-chrome) in auto mode
tom@tom-Veriton-X275:~$ ^C
tom@tom-Veriton-X275:~$ 
```

---

### Post by howefield on 2016-06-15
Occasionally it needs a logout and log back in to see the launcher in the Dash.

---

### Post by Tom_Carr on 2016-06-15
> [COLOR=#000000]Occasionally it needs a logout and log back in to see the launcher in the Dash[/COLOR]

That worked.  Thanks.

---

### Post by howefield on 2016-06-15
Cool. Glad to hear it, you can mark he thread solved now.

---

