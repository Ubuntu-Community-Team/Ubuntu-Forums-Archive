---
title: "404 error messages when trying to install Flash"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by tekkitan on 2008-11-06
I am just having issues trying to install flash via apt, as well as an apt-get upgrade. Seems to be a ton of 404 errors:

The following NEW packages will be installed:
  flashplugin-nonfree ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32nss-mdns lib32stdc++6 lib32z1
  libasound2-plugins libc6-i386 libpulse0 libsamplerate0 nspluginwrapper
0 upgraded, 13 newly installed, 0 to remove and 12 not upgraded.
Need to get 29.5MB/29.7MB of archives.
After this operation, 123MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libc6-i386 2.8~20080505-0ubuntu7
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main lib32gcc1 1:4.3.2-1ubuntu11
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main lib32z1 1:1.2.3.3.dfsg-12ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main lib32stdc++6 4.3.2-1ubuntu11
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main lib32asound2 1.0.17a-0ubuntu4
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe ia32-libs 2.2ubuntu18
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse nspluginwrapper 1.1.2-0ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse flashplugin-nonfree 10.0.12.36ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libpulse0 0.9.10-2ubuntu9
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libsamplerate0 0.1.3-1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libasound2-plugins 1.0.17-0ubuntu4
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.8~20080505-0ubuntu7_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.8~20080505-0ubuntu7_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/lib32gcc1_4.3.2-1ubuntu11_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/lib32gcc1_4.3.2-1ubuntu11_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/z/zlib/lib32z1_1.2.3.3.dfsg-12ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/z/zlib/lib32z1_1.2.3.3.dfsg-12ubuntu1_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/lib32stdc++6_4.3.2-1ubuntu11_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/lib32stdc++6_4.3.2-1ubuntu11_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/lib32asound2_1.0.17a-0ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/lib32asound2_1.0.17a-0ubuntu4_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu18_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu18_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/n/nspluginwrapper/nspluginwrapper_1.1.2-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/n/nspluginwrapper/nspluginwrapper_1.1.2-0ubuntu1_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.12.36ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.12.36ubuntu1_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.10-2ubuntu9_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.10-2ubuntu9_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsamplerate/libsamplerate0_0.1.3-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsamplerate/libsamplerate0_0.1.3-1_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-plugins/libasound2-plugins_1.0.17-0ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-plugins/libasound2-plugins_1.0.17-0ubuntu4_amd64.deb)  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



apt-get update fixes nothing.

---

### Post by Paqman on 2008-11-06
Try pinging for a server that you can connect to. System > Admin > Software Sources > Download from > Other > Select best server.

---

### Post by zvacet on 2008-11-06
Do what **Paqman** adviced you and  in your source list add this line

```
deb http://archive.canonical.com/ubuntu interpid partner
```

sava and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

In synaptic search box type **adobe-flashplugin** and whan you find it install it.

---

