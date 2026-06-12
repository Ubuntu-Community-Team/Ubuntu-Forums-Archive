---
title: "Not able to install Team Viewer in Ubuntu 14.04.1"
date: 2015-06-01
forum: New to Ubuntu
---

### Post by karthik24 on 2015-06-01
When I try to install Team Viewer in my Ubuntu 14.04.1 computer got this error. dependency is not satisfiable: lib32asound2.
Tried to install the same using apt-get, got Package not found message in terminal.
Please help

---

### Post by howefield on 2015-06-01
Did you use the 32-Bit / 64-Bit Multiarch .deb file from the teamviewer.com website?

---

### Post by sandyd on 2015-06-01
Teamviewer amd64 package dependencies [are broken]("https://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx#multiarch").

Run this:
```

sudo apt-get install libc6:i386 libgcc1:i386 libasound2:i386 libexpat1:i386 libfontconfig1:i386 libfreetype6:i386 libjpeg62:i386 libpng12-0:i386 libsm6:i386 libxdamage1:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxrandr2:i386 libxrender1:i386 libxtst6:i386 zlib1g:i386
wget http://download.teamviewer.com/download/teamviewer_i386.deb
sudo dpkg -i teamviewer_i386.deb

```

What this does:

1. Installs required i386 libraries
2. Downloads teamviewer i386
3. Installs teamviewer i386

---

### Post by karthik24 on 2015-06-01
I tried to install 64 bit, it got error in the 64bit OS. I tried to install Multi architecture of TV. It got installed succesfully and I'm able to use it. Thank you for all for tried to help me to fix the issue.

---

### Post by karthik24 on 2015-06-03
Yes, I used the 32-Bit / 64-Bit Multiarch of Team Viewer,then the installation done without any errors or issues.

---

### Post by Graciela_Balparda on 2016-01-18
> **sandyd said:**
> Teamviewer amd64 package dependencies [are broken]("https://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx#multiarch").

Run this:
```

sudo apt-get install libc6:i386 libgcc1:i386 libasound2:i386 libexpat1:i386 libfontconfig1:i386 libfreetype6:i386 libjpeg62:i386 libpng12-0:i386 libsm6:i386 libxdamage1:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxrandr2:i386 libxrender1:i386 libxtst6:i386 zlib1g:i386
wget http://download.teamviewer.com/download/teamviewer_i386.deb
sudo dpkg -i teamviewer_i386.deb

```

What this does:

1. Installs required i386 libraries
2. Downloads teamviewer i386
3. Installs teamviewer i386

Ubuntu 14.04 32 bit still getting error libjpeg62 is not installed in 3rd step

---

### Post by Edward_Fish on 2016-01-19
I think you can download the deb file, then:
sudo dpkg -i team-viewer-file-name
If it failed because of dependencies then
sudo apt-get update
sudo apt-get install -f
Check if TeamViewer is now installed. If not:
sudo dpkg -i team-viewer-file-name
Hopefully that works, let me know!

---

### Post by Eric Davelaar on 2016-05-30
After frustrating attempts with other suggestions which did not work, finally success! 
Thank you - thank you - thank you!

---

### Post by EnterG on 2016-06-24
> **Eric Davelaar said:**
> After frustrating attempts with other suggestions which did not work, finally success! 
Thank you - thank you - thank you!

So what did you do ? Please  tell everybody !

Finally i fixed it ! 

May sound weird but worked for me . 
Go to Teamviewer Extras>Options>Remote control>choose quality custom settings>custom settings>and tick improve application compatibility.

---

### Post by Eric Davelaar on 2017-01-26
My apologies for not checking in again, and for my comment that was meant as a replay of course to a previous post!
If memory serves, the solution provided by Edward_Fish did the trick for me (download the deb file, install with dpkg).

I upgraded to 16.04 a few months later, Teamviewer occasionally reports an error when I start up - but works/

---

