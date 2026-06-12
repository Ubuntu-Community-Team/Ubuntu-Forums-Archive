---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-05-30
forum: Philippine Team
---

### Post by alifakoor on 2017-05-30
hi everyone
i had a problem
when in try to "sudo apt-get -f install" , i get this massage:
```

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  blt fonts-sil-gentium fonts-sil-gentium-basic frozen-bubble-data
  gir1.2-ges-1.0 javascript-common libalien-sdl-perl libcapture-tiny-perl
  libclass-inspector-perl libcompress-bzip2-perl libfile-sharedir-perl
  libges-1.0-0 libguess1 libjs-jquery libjs-jquery-ui libmikmod3
  librubberband2v5 libsdl-gfx1.2-5 libsdl-image1.2 libsdl-mixer1.2
  libsdl-pango1 libsdl-perl libsdl-ttf2.0-0 libsdl2-2.0-0 libsndio6.1
  libtie-simple-perl libva-wayland1 libva-x11-1 linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-75
  linux-headers-4.4.0-75-generic linux-headers-4.8.0-36
  linux-headers-4.8.0-36-generic linux-headers-4.8.0-45
  linux-headers-4.8.0-45-generic linux-headers-4.8.0-46
  linux-headers-4.8.0-46-generic linux-headers-4.8.0-49
  linux-headers-4.8.0-49-generic linux-image-4.4.0-71-generic
  linux-image-4.4.0-75-generic linux-image-4.8.0-36-generic
  linux-image-4.8.0-45-generic linux-image-4.8.0-46-generic
  linux-image-4.8.0-49-generic linux-image-extra-4.4.0-71-generic
  linux-image-extra-4.4.0-75-generic linux-image-extra-4.8.0-36-generic
  linux-image-extra-4.8.0-45-generic linux-image-extra-4.8.0-46-generic
  linux-image-extra-4.8.0-49-generic linux-signed-image-4.8.0-36-generic
  linux-signed-image-4.8.0-45-generic linux-signed-image-4.8.0-46-generic
  linux-signed-image-4.8.0-49-generic mplayer-skins musescore-soundfont-gm
  python-matplotlib-data python3-cycler python3-dateutil python3-gst-1.0
  python3-matplotlib python3-numpy python3-tk python3-tz rtmpdump snap-confine
  teeworlds-data timgm6mb-soundfont tk8.6-blt2.5 youtube-dl
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.8.0-53-generic
Suggested packages:
  fdutils linux-tools
The following NEW packages will be installed:
  linux-image-4.8.0-53-generic
0 upgraded, 1 newly installed, 0 to remove and 54 not upgraded.
14 not fully installed or removed.
Need to get 0 B/23.6 MB of archives.
After this operation, 72.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 513287 files and directories currently installed.)
Preparing to unpack .../linux-image-4.8.0-53-generic_4.8.0-53.56~16.04.1_amd64.deb ...
Done.
Unpacking linux-image-4.8.0-53-generic (4.8.0-53.56~16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.8.0-53-generic_4.8.0-53.56~16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.8.0-53-generic' to '/boot/System.map-4.8.0-53-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.8.0-53-generic_4.8.0-53.56~16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"
```

any body can help me??
pleaseeeeeeee

---

### Post by Bashing-om on 2017-05-30
alifakoor; Hello;

The package manager tells you what is going on and a possible likely solution:
> 
 cannot copy extracted data for './boot/System.map-4.8.0-53-generic' to '/boot/System.map-4.8.0-53-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error


Show us what that " disk full" is all about, post back the output of terminal commands:
```

df -h
df -i

```

Try what the package manager suggests:
```

sudo apt autoremove

```

Be aware IF apt has no operating head room the command 'autoremove' will fail. We then drop down to lower levels to cope .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

