---
title: "Fresh install of 12.04 LTS, can't install anything and my HDMI out doesn't work"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by AzrinArius on 2013-10-28
Hi,

I just installed 12.04 LTS and I can't install Chrome. The software centre tells me that "The installation or removal of a software package failed.", the details gives me:

```
dpkg: dependency problems prevent configuration of google-chrome-stable:i386: 
 google-chrome-stable:i386 depends on xdg-utils (>= 1.0.2). 
dpkg: error processing google-chrome-stable:i386 (--install): 
 dependency problems - leaving unconfigured
```

It asks me if I want to repair the package catalogue and I choose to repair. Then the same thing happens. I googled and found this: [http://askubuntu.com/questions/130182/item-cannot-be-installed-or-removed-until-the-package-catalogue-is-repaired](http://askubuntu.com/questions/130182/item-cannot-be-installed-or-removed-until-the-package-catalogue-is-repaired)

I followed the advice through:

```
xuri@xuri-lp:~$ sudo apt-get clean
xuri@xuri-lp:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xuri@xuri-lp:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libgconf-2-4:i386 libatk1.0-0:i386 libk5crypto3:i386 libstdc++6:i386 libxfixes3:i386 libxcomposite1:i386 libldap-2.4-2:i386 libroken18-heimdal:i386 libidn11:i386 libnss3:i386
  libjpeg-turbo8:i386 screen-resolution-extra libjpeg8:i386 libdbus-glib-1-2:i386 libasn1-8-heimdal:i386 libcairo2:i386 libgnutls26:i386 libgssapi3-heimdal:i386 libtasn1-3:i386 libfreetype6:i386
  libexpat1:i386 libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386 libp11-kit0:i386 libwind0-heimdal:i386 libxau6:i386 libpixman-1-0:i386 libcups2:i386 libcurl3:i386
  libxinerama1:i386 libkrb5support0:i386 libxft2:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386 libkeyutils1:i386 libasound2:i386 libxrender1:i386 libhcrypto4-heimdal:i386 libnspr4:i386
  libhx509-5-heimdal:i386 libxss1:i386 libheimbase1-heimdal:i386 libtiff4:i386 libjasper1:i386 libvdpau1 libavahi-client3:i386 thunderbird-globalmenu libx11-6:i386 libsasl2-2:i386
  libfontconfig1:i386 libpango1.0-0:i386 libheimntlm0-heimdal:i386 libxdamage1:i386 libxcb-render0:i386 librtmp0:i386 libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386
  libxext6:i386 libsasl2-modules:i386 libavahi-common3:i386 libxrandr2:i386 libsqlite3-0:i386 libgtk2.0-0:i386 libkrb5-26-heimdal:i386 libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

I still can't install anything.

The other problem I'm having is with the HDMI out on my laptop( Lenovo z580 ). If I leave things default I can output to my external monitor just fine. But, if I install the prop NVIDIA drivers I can't. Obviously I'd rather be running on the NV drivers but I don't know how to fix this. I need the HDMI out to work.

Thanks for any advice. :)

Edit:

Forgot to mention that I ran an update as soon as Ubuntu was installed.

---

### Post by AzrinArius on 2013-10-28
Ok, the package thing is solved. For some reason I grabbed the 32bit version and I needed the 64bit version. My face is red. :D

The HDMI issue is still there though.

---

