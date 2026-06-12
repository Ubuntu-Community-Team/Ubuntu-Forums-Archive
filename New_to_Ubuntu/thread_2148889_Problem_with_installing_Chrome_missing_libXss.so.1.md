---
title: "Problem with installing Chrome: missing libXss.so.1"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by parriaga on 2013-05-27
I've just installed Ubuntu 12.04 and I'm trying to install Google Chrome and Spotify. They seemed to have installed properly, but when I try and run them from terminal (clicking them from the Unity Dash thing doesn't work), I get the following error:

error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

So I tried installing a few libraries as suggested various places online and I've installed libXss1, libqtcore4, and libqt4-dbus, but still get the error. What am I missing?
Thanks!


Herpderp, fixed it by reinstalling ubuntu.

---

### Post by sudo san on 2013-05-27
Did you install through the command line and did you get any errors?
If you got the unmet dependencies error, you may need to open Terminal (Ctrl + Alt + Del) and enter:
```
sudo apt-get update
sudo apt-get install -f
```

Hope it helps.

---

### Post by zeljkojagust on 2013-05-27
If you're running 64bit version of Ubuntu, you need to install ia32-libs-multiarch package to satisfy some 32bit dependencies Chrome and Spotify requires.

---

### Post by parriaga on 2013-05-27
> **zeljkojagust said:**
> If you're running 64bit version of Ubuntu, you need to install ia32-libs-multiarch package to satisfy some 32bit dependencies Chrome and Spotify requires.

Hmm, I've tried installing that, but still get the error.

---

### Post by monkeybrain2012 on 2013-05-27
You need to install libxsss1
```
sudo apt-get install libxss1
```

ia32-libs-multiarch is for running 32 bit applications is 64 bit machines. Chrome has 64 bit version for Linux so that is not needed. Don't know about Spotify.

---

### Post by parriaga on 2013-05-27
> **sudo san said:**
> Did you install through the command line and did you get any errors?
If you got the unmet dependencies error, you may need to open Terminal (Ctrl + Alt + Del) and enter:
```
sudo apt-get update
sudo apt-get install -f
```

Hope it helps.

I didn't have any problems when it installed, which is why I'm kinda confused as to why I'm getting this. I did both of those multiple times, although I have been getting errors with sudo apt-get update, because it's having trouble connecting to security.ubuntu.com, but I thought that was an unrelated issue.

---

### Post by parriaga on 2013-05-27
If this helps, when I try:
locate libXss.so.1

I get:
/usr/lib/debug/usr/lib/x86_64-linux-gnu/libXss.so.1.0.0
/usr/lib/i386-linux-gnu/libXss.so.1
/usr/lib/i386-linux-gnu/libXss.so.1.0.0

---

### Post by parriaga on 2013-05-27
> **monkeybrain2012 said:**
> You need to install libxsss1
```
sudo apt-get install libxss1
```

ia32-libs-multiarch is for running 32 bit applications is 64 bit machines. Chrome has 64 bit version for Linux so that is not needed. Don't know about Spotify.

Both are 64 bit versions. I've got libxss1 installed already and it still doesn't work. Though for some reason when I ls in /usr/lib/x86_64-linux-gnu, libXss.so is a different color than the rest of them. Does that mean it's not working correctly?

---

### Post by monkeybrain2012 on 2013-05-27
Can you do 
```
ldd /opt/google/chrome/chrome
```

and post the out put? The first letter is a small "L".

---

### Post by parriaga on 2013-05-27
Output from ldd /opt/google/chrome/chrome

```
    linux-vdso.so.1 =>  (0x00007fff193ff000)
    libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fbfac3ae000)
    libXrandr.so.2 => /usr/lib/x86_64-linux-gnu/libXrandr.so.2 (0x00007fbfac1a6000)
    libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007fbfabf9b000)
    libXss.so.1 => not found
    libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007fbfabd8a000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fbfabb81000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fbfab97d000)
    libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007fbfab72e000)
    libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007fbfab52b000)
    libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007fbfab236000)
    libgtk-x11-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0 (0x00007fbfaabfc000)
    libgdk-x11-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0 (0x00007fbfaa949000)
    libatk-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0 (0x00007fbfaa727000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0 (0x00007fbfaa507000)
    libpangocairo-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0 (0x00007fbfaa2fa000)
    libcairo.so.2 => /usr/lib/x86_64-linux-gnu/libcairo.so.2 (0x00007fbfaa03c000)
    libpango-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0 (0x00007fbfa9df3000)
    libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007fbfa9b56000)
    libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007fbfa9920000)
    libnss3.so => /usr/lib/x86_64-linux-gnu/libnss3.so (0x00007fbfa9619000)
    libnssutil3.so => /usr/lib/x86_64-linux-gnu/libnssutil3.so (0x00007fbfa93f1000)
    libsmime3.so => /usr/lib/x86_64-linux-gnu/libsmime3.so (0x00007fbfa91ca000)
    libplc4.so => /usr/lib/x86_64-linux-gnu/libplc4.so (0x00007fbfa8fc5000)
    libnspr4.so => /usr/lib/x86_64-linux-gnu/libnspr4.so (0x00007fbfa8d85000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fbfa8b68000)
    libgconf-2.so.4 => /usr/lib/x86_64-linux-gnu/libgconf-2.so.4 (0x00007fbfa893a000)
    libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007fbfa86f5000)
    libXcomposite.so.1 => /usr/lib/x86_64-linux-gnu/libXcomposite.so.1 (0x00007fbfa84f2000)
    libasound.so.2 => /usr/lib/x86_64-linux-gnu/libasound.so.2 (0x00007fbfa8205000)
    libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007fbfa8001000)
    libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007fbfa7dfb000)
    libcups.so.2 => /usr/lib/x86_64-linux-gnu/libcups.so.2 (0x00007fbfa7ba7000)
    libgcrypt.so.11 => /lib/x86_64-linux-gnu/libgcrypt.so.11 (0x00007fbfa7928000)
    libbz2.so.1.0 => /lib/x86_64-linux-gnu/libbz2.so.1.0 (0x00007fbfa7718000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fbfa74ee000)
    libudev.so.0 => /lib/x86_64-linux-gnu/libudev.so.0 (0x00007fbfa72e0000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fbfa6fe0000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fbfa6ce4000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fbfa6acd000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fbfa670e000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fbfb1e73000)
    libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fbfa64f0000)
    libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007fbfa62e7000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007fbfa60aa000)
    libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007fbfa5d5b000)
    libpangoft2-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0 (0x00007fbfa5b30000)
    libXinerama.so.1 => /usr/lib/x86_64-linux-gnu/libXinerama.so.1 (0x00007fbfa592d000)
    libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007fbfa571e000)
    libXcursor.so.1 => /usr/lib/x86_64-linux-gnu/libXcursor.so.1 (0x00007fbfa5513000)
    libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007fbfa530f000)
    libpixman-1.so.0 => /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x00007fbfa5087000)
    libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007fbfa4e5f000)
    libxcb-shm.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0 (0x00007fbfa4c5c000)
    libxcb-render.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-render.so.0 (0x00007fbfa4a51000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fbfa483a000)
    libplds4.so => /usr/lib/x86_64-linux-gnu/libplds4.so (0x00007fbfa4635000)
    libdbus-glib-1.so.2 => /usr/lib/x86_64-linux-gnu/libdbus-glib-1.so.2 (0x00007fbfa440f000)
    libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007fbfa41d0000)
    libgnutls.so.26 => /usr/lib/x86_64-linux-gnu/libgnutls.so.26 (0x00007fbfa3f14000)
    libavahi-common.so.3 => /usr/lib/x86_64-linux-gnu/libavahi-common.so.3 (0x00007fbfa3d08000)
    libavahi-client.so.3 => /usr/lib/x86_64-linux-gnu/libavahi-client.so.3 (0x00007fbfa3af6000)
    libgpg-error.so.0 => /lib/x86_64-linux-gnu/libgpg-error.so.0 (0x00007fbfa38f2000)
    libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fbfa36ee000)
    libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fbfa34e8000)
    libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007fbfa32c9000)
    libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007fbfa30ac000)
    libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007fbfa2dde000)
    libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007fbfa2bb5000)
    libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007fbfa29b1000)
    libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007fbfa27a9000)
    libtasn1.so.3 => /usr/lib/x86_64-linux-gnu/libtasn1.so.3 (0x00007fbfa2597000)
    libp11-kit.so.0 => /usr/lib/x86_64-linux-gnu/libp11-kit.so.0 (0x00007fbfa2385000)
    libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007fbfa2180000)


```


and for good measure, the one from /opt/spotify/spotify-client/spotify

```

    linux-vdso.so.1 =>  (0x00007fff1f7ac000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f9a8a5f7000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f9a8a3ef000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f9a8a0ee000)
    libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f9a89df9000)
    libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007f9a89bf7000)
    libQtGui.so.4 => /usr/lib/x86_64-linux-gnu/libQtGui.so.4 (0x00007f9a88f28000)
    libQtCore.so.4 => /usr/lib/x86_64-linux-gnu/libQtCore.so.4 (0x00007f9a88a56000)
    libQtDBus.so.4 => /usr/lib/x86_64-linux-gnu/libQtDBus.so.4 (0x00007f9a887d9000)
    libQtNetwork.so.4 => /usr/lib/x86_64-linux-gnu/libQtNetwork.so.4 (0x00007f9a8848c000)
    libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f9a881f0000)
    libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007f9a87fa1000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0 (0x00007f9a87d80000)
    libgdk-x11-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0 (0x00007f9a87ace000)
    libgtk-x11-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0 (0x00007f9a87494000)
    libcairo.so.2 => /usr/lib/x86_64-linux-gnu/libcairo.so.2 (0x00007f9a871d5000)
    libpango-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0 (0x00007f9a86f8c000)
    libatk-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0 (0x00007f9a86d6a000)
    libcef.so => /opt/spotify/spotify-client/libcef.so (0x00007f9a838d1000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f9a835d5000)
    libXss.so.1 => not found
    libasound.so.2 => /usr/lib/x86_64-linux-gnu/libasound.so.2 (0x00007f9a832e7000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f9a830e3000)
    libssl.so.0.9.8 => /lib/x86_64-linux-gnu/libssl.so.0.9.8 (0x00007f9a82e90000)
    libcrypto.so.0.9.8 => /lib/x86_64-linux-gnu/libcrypto.so.0.9.8 (0x00007f9a82b02000)
    libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f9a828e6000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f9a826d0000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f9a82310000)
    libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f9a81fdc000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f9a8a82d000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f9a81d9f000)
    libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007f9a81b68000)
    libaudio.so.2 => /usr/lib/x86_64-linux-gnu/libaudio.so.2 (0x00007f9a81950000)
    libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007f9a81728000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f9a81510000)
    libSM.so.6 => /usr/lib/x86_64-linux-gnu/libSM.so.6 (0x00007f9a81308000)
    libICE.so.6 => /usr/lib/x86_64-linux-gnu/libICE.so.6 (0x00007f9a810ee000)
    libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007f9a80ede000)
    libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007f9a80cd4000)
    libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f9a80ac3000)
    libQtXml.so.4 => /usr/lib/x86_64-linux-gnu/libQtXml.so.4 (0x00007f9a8087f000)
    libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f9a8063b000)
    libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007f9a80432000)
    libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007f9a8022e000)
    libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007f9a7fedf000)
    libpangocairo-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0 (0x00007f9a7fcd2000)
    libXinerama.so.1 => /usr/lib/x86_64-linux-gnu/libXinerama.so.1 (0x00007f9a7facf000)
    libXrandr.so.2 => /usr/lib/x86_64-linux-gnu/libXrandr.so.2 (0x00007f9a7f8c7000)
    libXcursor.so.1 => /usr/lib/x86_64-linux-gnu/libXcursor.so.1 (0x00007f9a7f6bc000)
    libXcomposite.so.1 => /usr/lib/x86_64-linux-gnu/libXcomposite.so.1 (0x00007f9a7f4b9000)
    libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007f9a7f2b6000)
    libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007f9a7f0af000)
    libpangoft2-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0 (0x00007f9a7ee85000)
    libpixman-1.so.0 => /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x00007f9a7ebfd000)
    libxcb-shm.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0 (0x00007f9a7e9fa000)
    libxcb-render.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-render.so.0 (0x00007f9a7e7f0000)
    libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f9a7e5d1000)
    libnss3.so.1d => /usr/lib/x86_64-linux-gnu/libnss3.so.1d (0x00007f9a7e2ca000)
    libnssutil3.so.1d => /usr/lib/x86_64-linux-gnu/libnssutil3.so.1d (0x00007f9a7e0a2000)
    libsmime3.so.1d => /usr/lib/x86_64-linux-gnu/libsmime3.so.1d (0x00007f9a7de7b000)
    libplc4.so.0d => /usr/lib/x86_64-linux-gnu/libplc4.so.0d (0x00007f9a7dc76000)
    libnspr4.so.0d => /usr/lib/x86_64-linux-gnu/libnspr4.so.0d (0x00007f9a7da36000)
    libgconf-2.so.4 => /usr/lib/x86_64-linux-gnu/libgconf-2.so.4 (0x00007f9a7d808000)
    libcups.so.2 => /usr/lib/x86_64-linux-gnu/libcups.so.2 (0x00007f9a7d5b4000)
    libgcrypt.so.11 => /lib/x86_64-linux-gnu/libgcrypt.so.11 (0x00007f9a7d335000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f9a7d10b000)
    libXt.so.6 => /usr/lib/x86_64-linux-gnu/libXt.so.6 (0x00007f9a7cea4000)
    libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f9a7cca1000)
    libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007f9a7ca9c000)
    libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007f9a7c87c000)
    libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f9a7c676000)
    libplds4.so => /usr/lib/x86_64-linux-gnu/libplds4.so (0x00007f9a7c471000)
    libdbus-glib-1.so.2 => /usr/lib/x86_64-linux-gnu/libdbus-glib-1.so.2 (0x00007f9a7c24b000)
    libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007f9a7c00c000)
    libgnutls.so.26 => /usr/lib/x86_64-linux-gnu/libgnutls.so.26 (0x00007f9a7bd50000)
    libavahi-common.so.3 => /usr/lib/x86_64-linux-gnu/libavahi-common.so.3 (0x00007f9a7bb44000)
    libavahi-client.so.3 => /usr/lib/x86_64-linux-gnu/libavahi-client.so.3 (0x00007f9a7b932000)
    libgpg-error.so.0 => /lib/x86_64-linux-gnu/libgpg-error.so.0 (0x00007f9a7b72e000)
    libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007f9a7b45f000)
    libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007f9a7b237000)
    libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007f9a7b033000)
    libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007f9a7ae2a000)
    libtasn1.so.3 => /usr/lib/x86_64-linux-gnu/libtasn1.so.3 (0x00007f9a7ac19000)
    libp11-kit.so.0 => /usr/lib/x86_64-linux-gnu/libp11-kit.so.0 (0x00007f9a7aa07000)
    libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007f9a7a802000)


```

---

### Post by monkeybrain2012 on 2013-05-27
From the 5th line libXss.so.1 is not found but it should be in /usr/lib/x86_64-linux-gnu/ , but your libXss.so.1 is in /usr/lib/i386-linux-gnu/

Can you update your database and then locate libXss.so.1 again?
```
sudo updatedb
locate libXss.so.1
```

---

### Post by parriaga on 2013-05-27
So locate libXss.so.1 gives:
```

/usr/lib/debug/usr/lib/x86_64-linux-gnu/libXss.so.1.0.0
/usr/lib/i386-linux-gnu/libXss.so.1
/usr/lib/i386-linux-gnu/libXss.so.1.0.0

```

Even after running updatedb

---

### Post by parriaga on 2013-05-27
Not sure what was wrong, but reinstalling ubuntu seems to have fixed it. Thanks all!

---

### Post by Brutalix on 2013-07-06
> **parriaga said:**
> So locate libXss.so.1 gives:
```

/usr/lib/debug/usr/lib/x86_64-linux-gnu/libXss.so.1.0.0
/usr/lib/i386-linux-gnu/libXss.so.1
/usr/lib/i386-linux-gnu/libXss.so.1.0.0

```

Even after running updatedb

Well someone here pointed out that Chrome is 64 bit... 
It should look like this: 
/usr/lib/i386-linux-gnu/libXss.so.1
/usr/lib/i386-linux-gnu/libXss.so.1.0.0
/usr/lib/x86_64-linux-gnu/libXss.so.1
/usr/lib/x86_64-linux-gnu/libXss.so.1.0.0

The LibXss you had installed was just the i386 version. I found the same problem when installing freesurfer, but looking in synaptic for libxss, i found another version to install and then everything worked. 
Hope this helps if any other people stumble into this problem.
 
Kind regards
Brutalix

---

### Post by deadflowr on 2013-07-06
> [COLOR=#000000]Well someone here pointed out that Chrome is 64 bit...[/COLOR]

Chrome offer both a 32bit and 64bit version.
So that information is wrong.

I've reinstalled chrome several times recently on development branches.(Saucy)
My solution, and the method I've found to work best is
First
```
sudo dpkg -i path-to-chrome-debfile
```
Then it starts and ends with the missing dependency libxss1.
Then I run
```
sudo apt-get install libxss1
```
which installs the libxss1 package, and then finishes installing chrome.

One time, though, the packages were broken, and so I then ran
```
sudo apt-get install -f
```
and when the broken packages were fixed, the previous installations finished installing without a hitch.

---

