---
title: "Nala another apt package manager"
date: 2022-11-15
forum: Programming Talk
---

### Post by #&amp;thj^% on 2022-11-15
There is a newer and improved apt in the works, I'm not sure if Canonical will pick it up.
I have a Developer working on a rolling release of Ubuntu, and I was asked to give "only Nala" a go. (More on the Rolling part later)
Nala is a front-end for libapt-pkg. Specifically we interface using the python-apt api.
Especially for newer users it can be hard to understand what apt is trying to do when installing or upgrading.
We aim to solve this by not showing some redundant messages, formatting the packages better, and using color to
show specifically what will happen with a package during install, removal, or an upgrade. 

I'm not going to show how this is installed due to potential breakage.(Testing Stage)
More of a first look and see only for now, but I find it very stable on my Jammy zsf install :commands are simular to apt with name change
```

me on Tue Nov 15 at 10:34 AM in ~/nala nothing to commit: main 
>> sudo nala update
&#9581;&#9472; Updating Package List &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;
&#9474;No Change: http://us.archive.ubuntu.com/ubuntu jammy InRelease                &#9474;
&#9474;No Change: http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease        &#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [100…&#9474;
&#9474;No Change: https://download.sublimetext.com apt/stable/ InRelease             &#9474;
&#9474;No Change: http://deb.volian.org/volian scar InRelease                        &#9474;
&#9474;Updated:   http://security.ubuntu.com/ubuntu jammy-security InRelease [110 KB]&#9474;
&#9474;No Change: https://repo.nordvpn.com//deb/nordvpn/debian stable InRelease      &#9474;
&#9474;No Change: http://eddie.website/repository/apt stable InRelease               &#9474;
&#9474;No Change: https://ppa.launchpadcontent.net/jonaski/strawberry/ubuntu jammy I…&#9474;
&#9474;No Change: https://ppa.launchpadcontent.net/ubuntuhandbook1/conkymanager2/ubu…&#9474;
&#9474;Fetched 210 KB in 2s (0 Bytes/s)                                              &#9474;
&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;
23 packages can be upgraded. Run 'nala list --upgradable' to see them.
So this is what will show, and list as upgrades.
```
Now upgrade:
```

 sudo nala upgrade
&#9581;&#9472; Updating Package List &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;
&#9474;No Change: http://deb.volian.org/volian scar InRelease                        &#9474;
&#9474;No Change: http://us.archive.ubuntu.com/ubuntu jammy InRelease                &#9474;
&#9474;Updated:   http://security.ubuntu.com/ubuntu jammy-security InRelease [110 KB]&#9474;
&#9474;No Change: http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease        &#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [100…&#9474;
&#9474;No Change: https://download.sublimetext.com apt/stable/ InRelease             &#9474;
&#9474;No Change: http://eddie.website/repository/apt stable InRelease               &#9474;
&#9474;No Change: https://repo.nordvpn.com//deb/nordvpn/debian stable InRelease      &#9474;
&#9474;No Change: https://ppa.launchpadcontent.net/jonaski/strawberry/ubuntu jammy I…&#9474;
&#9474;No Change: https://ppa.launchpadcontent.net/ubuntuhandbook1/conkymanager2/ubu…&#9474;
&#9474;Fetched 210 KB in 1s (0 Bytes/s)                                              &#9474;
&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;
The following packages were kept back:
libreoffice-core
&#9500;&#9472;&#9472; libreoffice-calc (< 1:7.3.7-0ubuntu0.22.04.1) will break libreoffice-calc (1:7.3.6-0ubuntu0.22.04.2)
&#9500;&#9472;&#9472; libreoffice-draw (< 1:7.3.7-0ubuntu0.22.04.1) will break libreoffice-draw (1:7.3.6-0ubuntu0.22.04.2)
&#9500;&#9472;&#9472; libreoffice-gnome (< 1:7.3.7-0ubuntu0.22.04.1) will break libreoffice-gnome (1:7.3.6-0ubuntu0.22.04.2)
&#9500;&#9472;&#9472; libreoffice-gnome (< 1:7.3.7-0ubuntu0.22.04.1) will break libreoffice-gtk-gnome 
&#9500;&#9472;&#9472; libreoffice-gtk3 (< 1:7.3.7-0ubuntu0.22.04.1) will break libreoffice-gtk3 (1:7.3.6-0ubuntu0.22.04.2)
&#9500;&#9472;&#9472; libreoffice-impress (< 1:7.3.7-0ubuntu0.22.04.1) will break libreoffice-impress (1:7.3.6-0ubuntu0.22.04.2)
&#9500;&#9472;&#9472; libreoffice-impress (< 1:7.3.7-0ubuntu0.22.04.1) will break libreoffice-ogltrans 
&#9492;&#9472;&#9472; libreoffice-writer (< 1:7.3.7-0ubuntu0.22.04.1) will break libreoffice-writer (1:7.3.6-0ubuntu0.22.04.2)

Nala was unable to determine why these were held:
  fonts-opensymbol, libreoffice-base-core, libreoffice-calc, libreoffice-common, libreoffice-draw, libreoffice-gnome, libreoffice-gtk3, libreoffice-impress, libreoffice-math, libreoffice-style-colibre, libreoffice-style-elementary, libreoffice-style-yaru, libreoffice-writer, libuno-cppu3, libuno-cppuhelpergcc3-3, libuno-purpenvhelpergcc3-3, libuno-sal3, libuno-salhelpergcc3-3, python3-uno, uno-libs-private, ure
Do you want to continue? [Y/n] 

```
I find that most will like it for the read-ability IE:
```


Auto-Removing                                                                  
================================================================================
  Package:                  Version:                                     Size:  
  linux-headers-5.15.0-25   5.15.0-25.25                               77.1 MB  
  linux-headers-5.15.0-25…  5.15.0-25.25                               24.2 MB  
  linux-image-5.15.0-25-g…  5.15.0-25.25                               11.1 MB  
  linux-modules-5.15.0-25…  5.15.0-25.25                              111.6 MB  
  linux-modules-extra-5.1…  5.15.0-25.25                              336.4 MB  
  linux-oem-6.0-headers-6…  6.0.0-1006.6                               80.5 MB  
                                                                                
================================================================================
 Upgrading                                                                      
================================================================================
  Package:                  Old Version:      New Version:               Size:  
  tzdata                    2022f-0ubuntu0.2  2022f-0ubuntu0.           333 KB  
                            2.04.0            22.04.1                           
                                                                                
================================================================================
 Summary                                                                        
================================================================================
 Auto-Remove 6 Packages                                                         
 Upgrade     1 Packages                                                         
                                                                                
 Total download size    333 KB   
 Disk space to free   640.9 MB   
                                 
Do you want to continue? [Y/n] 

Summary                                                                        
================================================================================
 Auto-Remove 6 Packages                                                         
 Upgrade     1 Packages                                                         
                                                                                
 Total download size    333 KB   
 Disk space to free   640.9 MB   
                                 
Do you want to continue? [Y/n] 
&#9581;&#9472; Downloading… &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;
&#9474; Total Packages: 1/1                                                          &#9474;
&#9474; Last Completed: tzdata_2022f-0ubuntu0.22.04.1_all.deb                        &#9474;
&#9474; Time Remaining: 0:00:00 &#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473; 100.0% • 332.7/332.7 KB • 1.0 MB/s &#9474;
&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;
&#9581;&#9472; Updating Packages &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;
&#9474;Warning: os-prober will be executed to detect other bootable partitions.      &#9474;
&#9474;Its output will be used to detect bootable binaries on them and create new bo…&#9474;
&#9474;Found EndeavourOS Linux (rolling) on /dev/sda3                                &#9474;
&#9474;Adding boot menu entry for UEFI Firmware Settings                             &#9474;
&#9474;done                                                                          &#9474;
&#9474;Removing:   linux-modules-5.15.0-25-generic (5.15.0-25.25)                    &#9474;
&#9474;Unpacking:  tzdata (2022f-0ubuntu0.22.04.1) over (2022f-0ubuntu0.22.04.0)     &#9474;
&#9474;Setting up: tzdata (2022f-0ubuntu0.22.04.1)                                   &#9474;
&#9474;Current default time zone: 'America/Denver'                                   &#9474;
&#9474;Local time is now:      Tue Nov 15 10:45:13 AM MST 2022.                      &#9474;
&#9474;Universal Time is now:  Tue Nov 15 17:45:13 UTC 2022.                         &#9474;
&#9474;Run 'dpkg-reconfigure tzdata' if you wish to change it.                       &#9474;
&#9474;&#9581;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;&#9474;
&#9474;&#9474;&#10004; Running dpkg … &#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473; 100.0% • 0:00:00 • 15/15&#9474;&#9474;
&#9474;&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;&#9474;
&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;

Notices:
  Warning: os-prober will be executed to detect other bootable partitions.
Finished Successfully

```

Here is a bigger task for Nala XFCE4 over Gnome.
```
$ sudo nala install xfce4 xfce4-goodies
[sudo] password for me: 
================================================================================
 Installing                                                                     
================================================================================
  Package:                  Version:                                     Size:  
  dbus-x11                  1.14.0-2ubuntu2                              24 KB  
  desktop-base              11.0.3ubuntu1                               3.4 MB  
  elementary-xfce-icon-th\u2026  0.17-1                                      6.1 MB  
  exo-utils                 4.17.3-1                                     34 KB  
  fonts-quicksand           0.2016-2.1                                  128 KB  
  gir1.2-libxfce4util-1.0   4.17.3-1                                      5 KB  
  gir1.2-xfconf-0           4.16.0-2                                      4 KB  
  greybird-gtk-theme        3.23.2-1                                    583 KB  
  i965-va-driver            2.4.1+dfsg1-1                               302 KB  
  intel-media-va-driver     22.4.3+dfsg1-1                              2.3 MB  
  libaom3                   3.4.0-1                                     1.8 MB  
  libasound2-plugins        1.2.7.1-1ubuntu1                             75 KB  
  libavcodec59              7:5.1.1-1ubuntu1                            5.7 MB  
  libavutil57               7:5.1.1-1ubuntu1                            355 KB  
  libcodec2-1.0             1.0.5-1ubuntu2                              8.3 MB  
  libdav1d6                 1.0.0-2                                     545 KB  
  libexo-2-0                4.17.3-1                                    268 KB  
  libexo-common             4.17.3-1                                      4 KB  
  libgarcon-1-0             4.17.2-1                                     46 KB  
  libgarcon-common          4.17.2-1                                     60 KB  
  libgarcon-gtk3-1-0        4.17.2-1                                     15 KB  
  libgsm1                   1.0.19-3                                     27 KB  
  libgtksourceview-4-0      4.8.3-1ubuntu1                              235 KB  
  libgtksourceview-4-comm\u2026  4.8.3-1ubuntu1                              592 KB  
  libigdgmm12               22.3.0+ds1-1                                143 KB  
  libkeybinder-3.0-0        0.3.2-1.1                                     9 KB  
  libmfx1                   22.3.0-1                                    3.1 MB  
  libmousepad0              0.5.10-1                                    122 KB  
  libpulsedsp               1:16.1+dfsg1-1ubuntu3                        23 KB  
  libqrencode4              4.1.1-1                                      24 KB  
  libshine3                 3.1.1-2                                      23 KB  
  libsnappy1v5              1.1.9-2                                      28 KB  
  libsoxr0                  0.1.3-4build2                                80 KB  
  libspeexdsp1              1.2.0-1                                      42 KB  
  libsvtav1enc1             1.2.1+dfsg-1                                2.4 MB  
  libswresample4            7:5.1.1-1ubuntu1                             64 KB  
  libtagc0                  1.11.1+dfsg.1-3ubuntu4                       17 KB  
  libthunarx-3-0            4.17.11-1                                    79 KB  
  libtumbler-1-0            4.17.2-1                                     25 KB  
  libutempter0              1.2.1-2build2                                 9 KB  
  libva-drm2                2.15.0-1                                      7 KB  
  libva-x11-2               2.15.0-1                                     13 KB  
  libva2                    2.15.0-1                                     62 KB  
  libvdpau1                 1.5-1                                        28 KB  
  libx264-164               2:0.164.3095+gitbaee400-                    590 KB  
                            2build1                                             
  libx265-199               3.5-2                                       1.2 MB  
  libxfce4panel-2.0-4       4.17.4-1                                     41 KB  
  libxfce4ui-2-0            4.17.8-1                                     60 KB  
  libxfce4ui-common         4.17.8-1                                    233 KB  
  libxfce4ui-utils          4.17.8-1                                     70 KB  
  libxfce4util-bin          4.17.3-1                                      6 KB  
  libxfce4util-common       4.17.3-1                                     61 KB  
  libxfce4util7             4.17.3-1                                     29 KB  
  libxfconf-0-3             4.16.0-2                                     34 KB  
  libxnvctrl0               510.47.03-0ubuntu1                           11 KB  
  libxpresent1              1.0.0-2build1                                 7 KB  
  libxvidcore4              2:1.3.7-1                                   201 KB  
  libzvbi-common            0.2.35-19                                    35 KB  
  libzvbi0                  0.2.35-19                                   262 KB  
  lm-sensors                1:3.6.0-7ubuntu1                             91 KB  
  mesa-va-drivers           22.2.1-1ubuntu1                             3.5 MB  
  mesa-vdpau-drivers        22.2.1-1ubuntu1                             3.4 MB  
  mousepad                  0.5.10-1                                    352 KB  
  ocl-icd-libopencl1        2.2.14-3                                     39 KB  
  pavucontrol               5.0-2                                       184 KB  
  pulseaudio                1:16.1+dfsg1-1ubuntu3                       908 KB  
  pulseaudio-utils          1:16.1+dfsg1-1ubuntu3                        78 KB  
  ristretto                 0.12.3-1                                    266 KB  
  tango-icon-theme          0.8.90-11                                   1.2 MB  
  thunar                    4.17.11-1                                   373 KB  
  thunar-archive-plugin     0.5.0-1                                      44 KB  
  thunar-data               4.17.11-1                                   917 KB  
  thunar-media-tags-plugin  0.3.0-2                                      53 KB  
  thunar-volman             4.17.0-1                                    134 KB  
  tumbler                   4.17.2-1                                     78 KB  
  tumbler-common            4.17.2-1                                     59 KB  
  va-driver-all             2.15.0-1                                      4 KB  
  vdpau-driver-all          1.5-1                                         5 KB  
  xfburn                    0.6.2-1build1                               482 KB  
  xfce4                     4.16                                          5 KB  
  xfce4-appfinder           4.17.1-1                                    166 KB  
  xfce4-battery-plugin      1.1.4-1                                      99 KB  
  xfce4-clipman             2:1.6.2-1                                   158 KB  
  xfce4-clipman-plugin      2:1.6.2-1                                    27 KB  
  xfce4-cpufreq-plugin      1.2.7-1                                     105 KB  
  xfce4-cpugraph-plugin     1.2.6-1                                     111 KB  
  xfce4-datetime-plugin     0.8.2-1                                      35 KB  
  xfce4-dict                0.8.4-1build1                               184 KB  
  xfce4-diskperf-plugin     2.7.0-1                                      56 KB  
  xfce4-fsguard-plugin      1.1.2-1                                      59 KB  
  xfce4-genmon-plugin       4.1.1-1                                      51 KB  
  xfce4-goodies             4.14.0                                        4 KB  
  xfce4-helpers             4.16.2-1ubuntu2                              23 KB  
  xfce4-mailwatch-plugin    1.3.0-0ubuntu2                              176 KB  
  xfce4-netload-plugin      1.4.0-1                                      57 KB  
  xfce4-notifyd             0.6.4-1ubuntu1                              145 KB  
  xfce4-panel               4.17.4-1                                    768 KB  
  xfce4-places-plugin       1.8.2-1                                      74 KB  
  xfce4-power-manager       4.17.0-1                                    117 KB  
  xfce4-power-manager-data  4.17.0-1                                    430 KB  
  xfce4-power-manager-plu\u2026  4.17.0-1                                     32 KB  
  xfce4-pulseaudio-plugin   0.4.5-1                                      97 KB  
  xfce4-screensaver         4.16.0-1                                    240 KB  
  xfce4-screenshooter       1.9.11-1                                    181 KB  
  xfce4-sensors-plugin      1.4.3-1                                     208 KB  
  xfce4-session             4.16.0-1ubuntu2                             308 KB  
  xfce4-settings            4.16.2-1ubuntu2                             881 KB  
  xfce4-smartbookmark-plu\u2026  0.5.2-1                                      23 KB  
  xfce4-systemload-plugin   1:1.3.1-1ubuntu1                             56 KB  
  xfce4-taskmanager         1.5.4-1                                     118 KB  
  xfce4-terminal            1.0.4-1                                     477 KB  
  xfce4-timer-plugin        1.7.1-1                                      53 KB  
  xfce4-verve-plugin        2.0.1-1                                      43 KB  
  xfce4-wavelan-plugin      0.6.3-1                                      40 KB  
  xfce4-weather-plugin      0.11.0-1                                    2.4 MB  
  xfce4-whiskermenu-plugin  2.7.1-1                                     206 KB  
  xfce4-xkb-plugin          1:0.8.3-1                                   461 KB  
  xfconf                    4.16.0-2                                    114 KB  
  xfdesktop4                4.17.1-1                                    186 KB  
  xfdesktop4-data           4.17.1-1                                    898 KB  
  xfwm4                     4.16.1-1                                    443 KB  
  xiccd                     0.3.0-1                                      17 KB  
                                                                                
================================================================================
 Configuring                                                                    
================================================================================
  Package:                  Version:                                     Size:  
  python3-distupgrade       1:23.04.1                                   564 KB  
  update-manager            1:22.10.4                                   1.1 MB  
  ubuntu-release-upgrader\u2026  1:23.04.1                                   135 KB  
  ubuntu-advantage-deskto\u2026  1.10                                         91 KB  
  ubuntu-desktop            1.497                                        55 KB  
  update-notifier           3.192.59                                    305 KB  
  update-manager-core       1:22.10.4                                   197 KB  
  software-properties-gtk   0.99.27.1                                   485 KB  
  ubuntu-desktop-minimal    1.497                                        55 KB  
  python3-update-manager    1:22.10.4                                   264 KB  
  ubuntu-release-upgrader\u2026  1:23.04.1                                   266 KB  
  ubuntu-advantage-tools    27.11.3~22.10.1                             749 KB  
  ubuntu-minimal            1.497                                        55 KB  
  update-notifier-common    3.192.59                                    1.2 MB  
                                                                                
================================================================================
 Suggested, Will Not Be Installed                                               
================================================================================
  Package:                  Version:                                     Size:  
  i965-va-driver-shaders    2.4.1-1                                     924 KB  
  libnvidia-compute-520     520.56.06-0ubuntu1                         55.2 MB  
  libnvcuvid1               Virtual Package                            0 Bytes  
  libnvidia-encode1         Virtual Package                            0 Bytes  
  devhelp                   43.0-1                                       68 KB  
  libxfce4ui-1-0            Virtual Package                            0 Bytes  
  fancontrol                1:3.6.0-7ubuntu1                             22 KB  
  read-edid                 3.0.2-1.1                                    19 KB  
  i2c-tools                 4.3-2build2                                  81 KB  
  pocl-opencl-icd           3.0-6                                         5 KB  
  pavumeter                 0.9.3-4build3                                23 KB  
  paprefs                   1.2-1fakesync1                               60 KB  
  ubuntu-sounds             0.14                                        261 KB  
  gnome-icon-theme          3.12.0-5                                    9.6 MB  
  kdelibs-data              Virtual Package                            0 Bytes  
  tumbler-plugins-extra     4.17.2-1                                     22 KB  
  libvdpau-va-gl1           0.4.2-1build2                                69 KB  
  libvdpau-va-gl1           0.4.2-1build2                                69 KB  
  gigolo                    0.5.2-1                                     195 KB  
  parole                    4.16.0-1                                    376 KB  
  xfce4-indicator-plugin    2.4.1-1                                      80 KB  
  xfce4-mpc-plugin          0.5.2-2                                      39 KB  
  xfce4-notes-plugin        1.9.0-1                                      45 KB  
  xfce4-radio-plugin        Virtual Package                            0 Bytes  
  xsensors                  0.70-5build1                                 17 KB  
  fortunes-mod              Virtual Package                            0 Bytes  
  mugshot                   0.4.3-1                                      78 KB  
  Either                                                                        
  \u251c\u2500\u2500 gnome                 1:42+8                                        3 KB  
  \u251c\u2500\u2500 kde-standard          5:127ubuntu3                                  2 KB  
  \u2514\u2500\u2500 wmaker                0.95.9-3                                    464 KB  
                                                                                
================================================================================
 Summary                                                                        
================================================================================
 Install   122 Packages                                                         
 Configure  14 Packages                                                         
                                                                                
 Total download size   62.3 MB   
 Disk space required  258.3 MB   
                                 
Do you want to continue? [Y/n] 


```
Here is a quick look at the help page:
```
~$ nala -h
Usage: nala [OPTIONS] COMMAND [ARGS]...

  Each command has its own help page.

  For Example: `nala history --help`

Options:
  --version                       Show program's version number and exit.
  --license                       Reads the GPLv3 which Nala is licensed
                                  under.
  --install-completion [bash|zsh|fish|powershell|pwsh]
                                  Install completion for the specified shell.
  --show-completion [bash|zsh|fish|powershell|pwsh]
                                  Show completion for the specified shell, to
                                  copy it or customize the installation.
  -h, --help                      Show this message and exit.

Commands:
  autopurge   Autopurge packages that are no longer needed.
  autoremove  Autoremove packages that are no longer needed.
  clean       Clear out the local archive of downloaded package files.
  fetch       Fetch fast mirrors to speed up downloads.
  history     Show transaction history.
  install     Install packages.
  list        List packages based on package names.
  purge       Purge packages.
  remove      Remove packages.
  search      Search package names and descriptions.
  show        Show package details.
  update      Update package list.
  upgrade     Update package list and upgrade the system.

```
EDIT: one feature i like is the show flag:
```
 nala show strawberry
Package: strawberry
Version: 1.0.10-jammy
Architecture: amd64
Installed: yes
Priority: optional
Essential: no
Section: sound
Source: strawberry
Origin: LP-PPA-jonaski-strawberry
Maintainer: Jonas Kvinge <jonas@jkvinge.net>
Installed-Size: 14.4 MB
Depends: 
  libasound2 (>= 1.0.16)
  libc6 (>= 2.34)
  libcdio19 (>= 2.1.0)
  libchromaprint1 (>= 1.3.2)
  libfftw3-double3 (>= 3.3.5)
  libgcc-s1 (>= 3.3.1)
  libgdk-pixbuf-2.0-0 (>= 2.22.0)
  libglib2.0-0 (>= 2.51.0)
  libgnutls30 (>= 3.7.3)
  libgpod4 (>= 0.7.0)
  libgstreamer-plugins-base1.0-0 (>= 1.0.0)
  libgstreamer1.0-0 (>= 1.6.0)
  libicu70 (>= 70.1-1~)
  libmtp9 (>= 1.1.0)
  libprotobuf23 (>= 3.12.4)
  libpulse0 (>= 0.99.1)
  libqt6concurrent6 (>= 6.1.2)
  libqt6core6 (>= 6.2.0)
  libqt6dbus6 (>= 6.1.2)
  libqt6gui6 (>= 6.2.0)
  libqt6network6 (>= 6.1.2)
  libqt6sql6 (>= 6.1.2)
  libqt6widgets6 (>= 6.2.0)
  libsqlite3-0 (>= 3.6.11)
  libstdc++6 (>= 11)
  libtag1v5 (>= 1.11)
  libx11-6
  libqt6sql6-sqlite
  qt6-qpa-plugins
  gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good
  gstreamer1.0-alsa
  gstreamer1.0-pulseaudio
Download-Size: 5.8 MB
APT-Sources: https://ppa.launchpadcontent.net/jonaski/ jammy/main amd64 Packages
Description: music player and music collection organizer
 Strawberry is a music player aimed at music collectors and audiophiles.
 .
 Features:
 - Play and organize music
 - Supports WAV, FLAC, WavPack, Ogg Vorbis, Speex, MPC, TrueAudio, AIFF, MP4, MP3 and ASF
 - Audio CD playback
 - Native desktop notifications
 - Playlist management and playlists in multiple formats
 - Smart and dynamic playlists
 - Advanced audio output and device configuration for bit-perfect playback on Linux
 - Edit tags on audio files
 - Automatically retrieve tags from MusicBrainz
 - Album cover art from Last.fm, Musicbrainz, Discogs, Musixmatch, Deezer, Tidal, Qobuz and Spotify
 - Song lyrics from AudD, Genius, Musixmatch, ChartLyrics, lyrics.ovh and lololyrics.com
 - Audio analyzer
 - Audio equalizer
 - Transfer music to mass-storage USB players, MTP compatible devices and iPod Nano/Classic
 - Scrobbler with support for Last.fm, Libre.fm and ListenBrainz
 - Streaming support for Subsonic-compatible servers
 - Unofficial streaming support for Tidal and Qobuz
 .
 It is a fork of Clementine. The name is inspired by the band Strawbs.


me on Tue Nov 15 at 12:05 PM in ~ branch: (HEAD) 
>> 

```

---

### Post by Bashing-om on 2022-11-15
In addition:

Please see the coverage in our WeeklyNewsletter:
[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue761#Apt.2B-.2B-.3F_Nala_is_Like_Apt_in_Ubuntu_but_Better](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue761#Apt.2B-.2B-.3F_Nala_is_Like_Apt_in_Ubuntu_but_Better)

[INDENT]wysiwyg[/INDENT]

---

### Post by #&amp;thj^% on 2022-11-16
Thanks B-om, the screenshots make it a lot more desirable, and the fact of some very nice options.
Ability to download from 16 different mirrors.
BTW: I wasn't in the repos at least on mine "22.04.1"as reported in the Foss link.

---

### Post by Bashing-om on 2022-11-16
hey like:

Yeah neat stuff in nala - and it is available in 22.04:
> 
sysop@x2204mini:~$ apt list nala
Listing... Done
nala/jammy-backports,jammy-backports 0.11.1~bpo22.04.1 all
sysop@x2204mini:~$ 


Just for some reason not released to the universe repo.

 [INDENT]sometimes I wonder[/INDENT]

---

### Post by ian-weisser on 2022-11-16
Wonder no more!

```

$ rmadison nala
 nala | 0.11.1~bpo22.04.1 | jammy-backports/universe | source, all
 nala | 0.11.1            | kinetic/universe         | source, all
 nala | 0.11.1            | lunar/universe           | source, all

```

(Egad, I'd be lost without rmadison. It's so useful when troubleshooting package versions!)

and also [https://tracker.debian.org/pkg/nala](https://tracker.debian.org/pkg/nala) (also super-helpful):

```

               
[LIST]
[*]         [2022-08-12]         [             nala 0.11.1 MIGRATED to testing         ]("https://tracker.debian.org/news/1353663/nala-0111-migrated-to-testing/")         (Debian testing watch)
[*]         [2022-08-07]         [             Accepted nala 0.11.1 (source) into unstable         ]("https://tracker.debian.org/news/1352389/accepted-nala-0111-source-into-unstable/")         (Stephan Lachnit)
[*]         [2022-07-24]         [             nala 0.10.0 MIGRATED to testing         ]("https://tracker.debian.org/news/1348489/nala-0100-migrated-to-testing/")         (Debian testing watch)
[*]         [2022-07-19]         [             Accepted nala 0.10.0 (source) into unstable         ]("https://tracker.debian.org/news/1347132/accepted-nala-0100-source-into-unstable/")         (Stephan Lachnit)
[*]         [2022-06-19]         [             nala 0.9.1 MIGRATED to testing         ]("https://tracker.debian.org/news/1337708/nala-091-migrated-to-testing/")         (Debian testing watch)
[*]         [2022-06-13]         [             Accepted nala 0.9.1 (source) into unstable         ]("https://tracker.debian.org/news/1334289/accepted-nala-091-source-into-unstable/")         (Stephan Lachnit)
[*]         [2022-06-01]         [             nala 0.9.0 MIGRATED to testing         ]("https://tracker.debian.org/news/1330026/nala-090-migrated-to-testing/")         (Debian testing watch)
[*]         [2022-05-27]         [             Accepted nala 0.9.0 (source) into unstable         ]("https://tracker.debian.org/news/1328263/accepted-nala-090-source-into-unstable/")         (Stephan Lachnit)
[*]         [2022-05-12]         [             Accepted nala 0.8.2 (source all) into unstable, unstable         ]("https://tracker.debian.org/news/1324317/accepted-nala-082-source-all-into-unstable-unstable/")         (Debian FTP Masters)                           (signed by: Stephan Lachnit)
[/LIST]
          

```

So, reconstructing the pieces, the initial upload to Debian was in May (too late for 22.04).

It merged into 22.10. 

Then, [https://bugs.launchpad.net/ubuntu/+source/nala/+bug/1984053](https://bugs.launchpad.net/ubuntu/+source/nala/+bug/1984053) : A backport request for 22.10 to 22.04 in August. Completed in 10 days.

---

### Post by mIk3_08 on 2022-11-17
Wow. This is new. Is it okay if I'll ask why is it called nala? Regards and cheers.

---

### Post by Dennis N on 2022-11-18
As it says in the description, it has a transaction history with details of past transactions like Fedora's dnf history function. That can be really useful. But then it seems you would probably have to use this exclusively to also record transactions done with Ubuntu's other methods like Ubuntu Software, apt, synaptic, Software Updater and unattended upgrades. 

```
dmn@Zotac:~$ apt show nala
Package: nala
Version: 0.11.1
Priority: optional
Section: universe/admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Volian Developers <volian-devel@volian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 430 kB
Depends: python3-anyio, python3-httpx, python3-pexpect, python3-rich, python3-tomli, python3-typer, python3-typing-extensions, python3:any, apt, python3-apt
Recommends: python3-socksio
Homepage: https://gitlab.com/volian/nala
Download-Size: 103 kB
APT-Sources: http://mirror.arizona.edu/ubuntu kinetic/universe amd64 Packages
Description: Commandline frontend for the APT package manager
 Nala is a frontend for the APT package manager. It has a lot
 of the same functionality, but formats the output to be more
 human readable. Also implements a history function to see past
 transactions and undo/redo them. Much like Fedora's dnf history.

```

---

### Post by #&amp;thj^% on 2022-11-18
> **ian-weisser said:**
> Wonder no more!

```

$ rmadison nala
 nala | 0.11.1~bpo22.04.1 | jammy-backports/universe | source, all
 nala | 0.11.1            | kinetic/universe         | source, all
 nala | 0.11.1            | lunar/universe           | source, all

```

(Egad, I'd be lost without rmadison. It's so useful when troubleshooting package versions!)

and also [https://tracker.debian.org/pkg/nala](https://tracker.debian.org/pkg/nala) (also super-helpful):

```

               
[LIST]
[*]         [2022-08-12]         [             nala 0.11.1 MIGRATED to testing         ]("https://tracker.debian.org/news/1353663/nala-0111-migrated-to-testing/")         (Debian testing watch)
[*]         [2022-08-07]         [             Accepted nala 0.11.1 (source) into unstable         ]("https://tracker.debian.org/news/1352389/accepted-nala-0111-source-into-unstable/")         (Stephan Lachnit)
[*]         [2022-07-24]         [             nala 0.10.0 MIGRATED to testing         ]("https://tracker.debian.org/news/1348489/nala-0100-migrated-to-testing/")         (Debian testing watch)
[*]         [2022-07-19]         [             Accepted nala 0.10.0 (source) into unstable         ]("https://tracker.debian.org/news/1347132/accepted-nala-0100-source-into-unstable/")         (Stephan Lachnit)
[*]         [2022-06-19]         [             nala 0.9.1 MIGRATED to testing         ]("https://tracker.debian.org/news/1337708/nala-091-migrated-to-testing/")         (Debian testing watch)
[*]         [2022-06-13]         [             Accepted nala 0.9.1 (source) into unstable         ]("https://tracker.debian.org/news/1334289/accepted-nala-091-source-into-unstable/")         (Stephan Lachnit)
[*]         [2022-06-01]         [             nala 0.9.0 MIGRATED to testing         ]("https://tracker.debian.org/news/1330026/nala-090-migrated-to-testing/")         (Debian testing watch)
[*]         [2022-05-27]         [             Accepted nala 0.9.0 (source) into unstable         ]("https://tracker.debian.org/news/1328263/accepted-nala-090-source-into-unstable/")         (Stephan Lachnit)
[*]         [2022-05-12]         [             Accepted nala 0.8.2 (source all) into unstable, unstable         ]("https://tracker.debian.org/news/1324317/accepted-nala-082-source-all-into-unstable-unstable/")         (Debian FTP Masters)                           (signed by: Stephan Lachnit)
[/LIST]
          

```

So, reconstructing the pieces, the initial upload to Debian was in May (too late for 22.04).

[B][U]It merged into 22.10. 
[/U][/B]
Then, [https://bugs.launchpad.net/ubuntu/+source/nala/+bug/1984053](https://bugs.launchpad.net/ubuntu/+source/nala/+bug/1984053) : A backport request for 22.10 to 22.04 in August. Completed in 10 days.
Thanks ian-weisser that was a nice reminder on "rmadison" as well I've kind of forgot about that one.

---

