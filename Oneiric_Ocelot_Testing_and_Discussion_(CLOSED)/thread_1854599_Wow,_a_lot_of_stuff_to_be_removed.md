---
title: "Wow, a lot of stuff to be removed"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by whoop on 2011-10-04
Maybe I missed something but what's this all about:
```

The following packages will be REMOVED:
  flashplugin-downloader:i386 flashplugin-installer ia32-libs-multiarch:i386
  libacl1:i386 libasound2:i386 libasyncns0:i386 libatk1.0-0:i386 libattr1:i386
  libaudio2:i386 libavahi-client3:i386 libavahi-common3:i386 libc6:i386 libcairo2:i386
  libcomerr2:i386 libcups2:i386 libcupsimage2:i386 libcurl3:i386 libdatrie1:i386
  libdb5.1:i386 libdbus-1-3:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386 libdrm2:i386
  libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386
  libgcc1:i386 libgcrypt11:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libgnutls26:i386
  libgpg-error0:i386 libgssapi-krb5-2:i386 libgtk2.0-0:i386 libice6:i386 libidn11:i386
  libjasper1:i386 libjpeg62:i386 libjson0:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libllvm2.9:i386
  libmng1:i386 libnspr4:i386 libnspr4-0d:i386 libnss3:i386 libnss3-1d:i386 libogg0:i386
  libpango1.0-0:i386 libpcre3:i386 libpixman-1-0:i386 libpng12-0:i386 libpulse0:i386
  libqt4-dbus:i386 libqt4-declarative:i386 libqt4-designer:i386 libqt4-network:i386
  libqt4-opengl:i386 libqt4-qt3support:i386 libqt4-script:i386 libqt4-scripttools:i386
  libqt4-sql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386
  libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386 librtmp0:i386
  libsamplerate0:i386 libsasl2-2:i386 libsasl2-modules:i386 libselinux1:i386 libsm6:i386
  libsndfile1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386
  libtasn1-3:i386 libthai0:i386 libtiff4:i386 libuuid1:i386 libvorbis0a:i386
  libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libxau6:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcb1:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxft2:i386 libxi6:i386
  libxinerama1:i386 libxrandr2:i386 libxrender1:i386 libxss1:i386 libxt6:i386
  libxxf86vm1:i386 nspluginviewer:i386 nspluginwrapper zlib1g:i386
The following packages will be upgraded:
  apparmor apparmor-utils bash-completion gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  libapparmor-perl libapparmor1 libc-bin libc-dev-bin libc6 libc6-dev libc6-i386
  libgwibber-gtk2 libgwibber2 logrotate multiarch-support python-piston-mini-client
20 upgraded, 0 newly installed, 117 to remove and 0 not upgraded.
Need to get 12.9 MB of archives.
After this operation, 132 MB disk space will be freed.
Do you want to continue [Y/n]? n


```

I have a 64bit machine.

---

### Post by arpanaut on 2011-10-04
Don't Do It...
You'll be sorry!

Check this out:
[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)

Wait a while and the repos usually fix themselves.

But then again since this is all i386 stuff it may be part of the transition to multi-arch support.
I haven't tested 11.10 on my 64 bit lappy yet... other than live-cd, Might want to wait for more knowledgeable support.

---

### Post by alphacrucis2 on 2011-10-04
I think the term "partial upgrade" is a bit of a misnomer. When these dependency issues arise in the repos maybe instead of update manager offering a partial upgrade it should say instead "Do you want to destroy your system? Type Y to proceed!"

---

### Post by foxy123 on 2011-10-04
Clicked on OK and now a lot of stuff is broken including Skype which I was trying to fix :mad:

---

### Post by Hakkatuka on 2011-10-04
It seems to be fixed now.

---

### Post by ubupirate on 2011-10-04
> **foxy123 said:**
> Clicked on OK and now a lot of stuff is broken including Skype which I was trying to fix :mad:

Why would you do such a thing? xD

---

### Post by cariboo on 2011-10-04
> **ubupirate said:**
> Why would you do such a thing? xD

They obviously didn't read the [partial upgrade]("http://ubuntuforums.org/showthread.php?t=1751299") sticky at the top of the page. :)

---

### Post by foxy123 on 2011-10-05
> **cariboo907 said:**
> They obviously didn't read the [partial upgrade]("http://ubuntuforums.org/showthread.php?t=1751299") sticky at the top of the page. :)

well, I was doing something in synptic and saw updates. Probably synaptic does not show Partial Update thingy or at least I don't remember if it appeared at all. After hitting the Apply Updates button it was too late. Anyway, ran teh Update Manager this morning and it is fine now.

---

### Post by Harry33 on 2011-10-05
> **foxy123 said:**
> well, I was doing something in synptic and saw updates. Probably synaptic does not show Partial Update thingy or at least I don't remember if it appeared at all. After hitting the Apply Updates button it was too late. Anyway, ran teh Update Manager this morning and it is fine now.

Synaptic always tries to do what you ask for, but it will never break dependencies (no force installation).
However, Synaptic will, if you ask for it, uninstall anything. This means it will uninstall all the packages, which would otherwise be left with broken dependencies.

---

### Post by 3rdalbum on 2011-10-05
If you mark a change that causes other changes to occur, Synaptic always tells you straight away. It also gives you a chance to review changes and "chicken out" when you click the Apply button.

Oh well, you've learned something now, you're lucky it was only the i386 packages :-)

---

