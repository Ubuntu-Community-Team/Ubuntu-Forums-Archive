---
title: "Problems after new installation"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by mlkirchgessner on 2012-07-12
Hi, I'm having problems with the Ubuntu 12.04 LTS i just installed.  I initially tried to install wine and I had problems with that. after that I noticed all the updates for the system and tried to install all of those that were available.  All of them were installed except for 8 or so of them. I rebooted and now i get this message when i  access the Ubuntu Software Center - 


Items cannot be install or removed until the package catalog is repaired. Do you want to repair it now? 

I tried to that and waited for a bit and the pop up comes up saying the same thing again. I pushed cancel deciding not to do it again and the initial fix finally finished and it came up saying package operation failed. Here are the details - 





nstallArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 170772 files and directories currently installed.) 
Preparing to replace vim-common 2:7.3.429-2ubuntu2 (using .../vim-common_2%3a7.3.429-2ubuntu2.1_i386.deb) ... 
Unpacking replacement vim-common ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: warning: subprocess old post-removal script returned error exit status 5 
dpkg - trying script from the new package instead ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error processing /var/cache/apt/archives/vim-common_2%3a7.3.429-2ubuntu2.1_i386.deb (--unpack): 
 subprocess new post-removal script returned error exit status 5 
No apport report written because MaxReports is reached already
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error while cleaning up: 
 subprocess new post-removal script returned error exit status 5 
Preparing to replace libreoffice-math 1:3.5.2-2ubuntu1 (using .../libreoffice-math_1%3a3.5.3-0ubuntu1_i386.deb) ... 
Unpacking replacement libreoffice-math ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: warning: subprocess old post-removal script returned error exit status 5 
dpkg - trying script from the new package instead ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error processing /var/cache/apt/archives/libreoffice-math_1%3a3.5.3-0ubuntu1_i386.deb (--unpack): 
 subprocess new post-removal script returned error exit status 5 
No apport report written because MaxReports is reached already
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error while cleaning up: 
 subprocess new post-removal script returned error exit status 5 
Preparing to replace libreoffice-impress 1:3.5.2-2ubuntu1 (using .../libreoffice-impress_1%3a3.5.3-0ubuntu1_i386.deb) ... 
Unpacking replacement libreoffice-impress ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: warning: subprocess old post-removal script returned error exit status 5 
dpkg - trying script from the new package instead ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error processing /var/cache/apt/archives/libreoffice-impress_1%3a3.5.3-0ubuntu1_i386.deb (--unpack): 
 subprocess new post-removal script returned error exit status 5 
No apport report written because MaxReports is reached already
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error while cleaning up: 
 subprocess new post-removal script returned error exit status 5 
Preparing to replace libreoffice-draw 1:3.5.2-2ubuntu1 (using .../libreoffice-draw_1%3a3.5.3-0ubuntu1_i386.deb) ... 
Unpacking replacement libreoffice-draw ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: warning: subprocess old post-removal script returned error exit status 5 
dpkg - trying script from the new package instead ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error processing /var/cache/apt/archives/libreoffice-draw_1%3a3.5.3-0ubuntu1_i386.deb (--unpack): 
 subprocess new post-removal script returned error exit status 5 
No apport report written because MaxReports is reached already
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error while cleaning up: 
 subprocess new post-removal script returned error exit status 5 
Preparing to replace libreoffice-calc 1:3.5.2-2ubuntu1 (using .../libreoffice-calc_1%3a3.5.3-0ubuntu1_i386.deb) ... 
Unpacking replacement libreoffice-calc ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: warning: subprocess old post-removal script returned error exit status 5 
dpkg - trying script from the new package instead ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error processing /var/cache/apt/archives/libreoffice-calc_1%3a3.5.3-0ubuntu1_i386.deb (--unpack): 
 subprocess new post-removal script returned error exit status 5 
No apport report written because MaxReports is reached already
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error while cleaning up: 
 subprocess new post-removal script returned error exit status 5 
Preparing to replace libreoffice-writer 1:3.5.2-2ubuntu1 (using .../libreoffice-writer_1%3a3.5.3-0ubuntu1_i386.deb) ... 
Unpacking replacement libreoffice-writer ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: warning: subprocess old post-removal script returned error exit status 5 
dpkg - trying script from the new package instead ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error processing /var/cache/apt/archives/libreoffice-writer_1%3a3.5.3-0ubuntu1_i386.deb (--unpack): 
 subprocess new post-removal script returned error exit status 5 
No apport report written because MaxReports is reached already
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error while cleaning up: 
 subprocess new post-removal script returned error exit status 5 
dpkg: regarding .../libreoffice-core_1%3a3.5.3-0ubuntu1_i386.deb containing libreoffice-core: 
 libreoffice-core conflicts with libreoffice-calc (<< 1:3.5.3-0ubuntu1) 
  libreoffice-calc (version 1:3.5.2-2ubuntu1) is present and broken due to failed removal or installation. 
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.3-0ubuntu1_i386.deb (--unpack): 
 conflicting packages - not installing libreoffice-core 
No apport report written because MaxReports is reached already
Preparing to replace rhythmbox 2.96-0ubuntu4 (using .../rhythmbox_2.96-0ubuntu4.1_i386.deb) ... 
Unpacking replacement rhythmbox ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: warning: subprocess old post-removal script returned error exit status 5 
dpkg - trying script from the new package instead ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error processing /var/cache/apt/archives/rhythmbox_2.96-0ubuntu4.1_i386.deb (--unpack): 
 subprocess new post-removal script returned error exit status 5 
No apport report written because MaxReports is reached already
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error while cleaning up: 
 subprocess new post-removal script returned error exit status 5 
Processing triggers for man-db ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for libglib2.0-0 ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/vim-common_2%3a7.3.429-2ubuntu2.1_i386.deb 
 /var/cache/apt/archives/libreoffice-math_1%3a3.5.3-0ubuntu1_i386.deb 
 /var/cache/apt/archives/libreoffice-impress_1%3a3.5.3-0ubuntu1_i386.deb 
 /var/cache/apt/archives/libreoffice-draw_1%3a3.5.3-0ubuntu1_i386.deb 
 /var/cache/apt/archives/libreoffice-calc_1%3a3.5.3-0ubuntu1_i386.deb 
 /var/cache/apt/archives/libreoffice-writer_1%3a3.5.3-0ubuntu1_i386.deb 
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.3-0ubuntu1_i386.deb 
 /var/cache/apt/archives/rhythmbox_2.96-0ubuntu4.1_i386.deb 
Error in function:  
Setting up wine1.4 (1.4-0ubuntu4) ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error processing wine1.4 (--configure): 
 subprocess installed post-installation script returned error exit status 5 
Setting up grub-common (1.99-21ubuntu3.1) ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-rc.d line 236. 
BEGIN failed--compilation aborted at /usr/sbin/update-rc.d line 236. 
dpkg: error processing grub-common (--configure): 
 subprocess installed post-installation script returned error exit status 5 
dpkg: dependency problems prevent configuration of rhythmbox-plugins: 
 rhythmbox-plugins depends on rhythmbox (= 2.96-0ubuntu4.1); however: 
  Package rhythmbox is not installed. 
dpkg: error processing rhythmbox-plugins (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of grub-pc-bin: 
 grub-pc-bin depends on grub-common (= 1.99-21ubuntu3.1); however: 
  Package grub-common is not configured yet. 
dpkg: error processing grub-pc-bin (--configure): 
 dependency problems - leaving unconfigured 
Setting up resolvconf (1.63ubuntu14) ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-rc.d line 236. 
BEGIN failed--compilation aborted at /usr/sbin/update-rc.d line 236. 
dpkg: error processing resolvconf (--configure): 
 subprocess installed post-installation script returned error exit status 5 
Setting up winbind (2:3.6.3-2ubuntu2.3) ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-rc.d line 236. 
BEGIN failed--compilation aborted at /usr/sbin/update-rc.d line 236. 
dpkg: error processing winbind (--configure): 
 subprocess installed post-installation script returned error exit status 5 
dpkg: dependency problems prevent configuration of libreoffice-base-core: 
 libreoffice-base-core depends on libreoffice-core (= 1:3.5.3-0ubuntu1); however: 
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1. 
dpkg: error processing libreoffice-base-core (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-gnome: 
 libreoffice-gnome depends on libreoffice-core (= 1:3.5.3-0ubuntu1); however: 
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1. 
dpkg: error processing libreoffice-gnome (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of grub-pc: 
 grub-pc depends on grub-common; however: 
  Package grub-common is not configured yet. 
 grub-pc depends on grub-pc-bin (= 1.99-21ubuntu3.1); however: 
  Package grub-pc-bin is not configured yet. 
dpkg: error processing grub-pc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of rhythmbox-mozilla: 
 rhythmbox-mozilla depends on rhythmbox (= 2.96-0ubuntu4.1); however: 
  Package rhythmbox is not installed. 
dpkg: error processing rhythmbox-mozilla (--configure): 
 dependency problems - leaving unconfigured 
Setting up network-manager (0.9.4.0-0ubuntu4.1) ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-rc.d line 236. 
BEGIN failed--compilation aborted at /usr/sbin/update-rc.d line 236. 
dpkg: error processing network-manager (--configure): 
 subprocess installed post-installation script returned error exit status 5 
dpkg: dependency problems prevent configuration of rhythmbox-plugin-magnatune: 
 rhythmbox-plugin-magnatune depends on rhythmbox (= 2.96-0ubuntu4.1); however: 
  Package rhythmbox is not installed. 
dpkg: error processing rhythmbox-plugin-magnatune (--configure): 
 dependency problems - leaving unconfigured 
Setting up cron (3.0pl1-120ubuntu4) ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-rc.d line 236. 
BEGIN failed--compilation aborted at /usr/sbin/update-rc.d line 236. 
dpkg: error processing cron (--configure): 
 subprocess installed post-installation script returned error exit status 5 
Setting up imagemagick (8:6.6.9.7-5ubuntu3.1) ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-mime line 64. 
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 64. 
dpkg: error processing imagemagick (--configure): 
 subprocess installed post-installation script returned error exit status 5 
dpkg: dependency problems prevent configuration of libreoffice-gtk: 
 libreoffice-gtk depends on libreoffice-core (= 1:3.5.3-0ubuntu1); however: 
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1. 
dpkg: error processing libreoffice-gtk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of rhythmbox-plugin-zeitgeist: 
 rhythmbox-plugin-zeitgeist depends on rhythmbox (>= 2.96-0ubuntu4.1); however: 
  Package rhythmbox is not installed. 
 rhythmbox-plugin-zeitgeist depends on rhythmbox (<< 2.97); however: 
  Package rhythmbox is not installed. 
dpkg: error processing rhythmbox-plugin-zeitgeist (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of grub2-common: 
 grub2-common depends on grub-common (= 1.99-21ubuntu3.1); however: 
  Package grub-common is not configured yet. 
dpkg: error processing grub2-common (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of rhythmbox-plugin-cdrecorder: 
 rhythmbox-plugin-cdrecorder depends on rhythmbox (= 2.96-0ubuntu4.1); however: 
  Package rhythmbox is not installed. 
dpkg: error processing rhythmbox-plugin-cdrecorder (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-uno: 
 python-uno depends on libreoffice-core (= 1:3.5.3-0ubuntu1); however: 
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1. 
dpkg: error processing python-uno (--configure): 
 dependency problems - leaving unconfigured 
Setting up apparmor (2.7.102-0ubuntu3.1) ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-rc.d line 236. 
BEGIN failed--compilation aborted at /usr/sbin/update-rc.d line 236. 
dpkg: error processing apparmor (--configure): 
 subprocess installed post-installation script returned error exit status 5 
dpkg: dependency problems prevent configuration of libreoffice-help-en-us: 
 libreoffice-help-en-us depends on libreoffice-writer | language-support-translations-en; however: 
  Package libreoffice-writer is not installed. 
  Package language-support-translations-en is not installed. 
dpkg: error processing libreoffice-help-en-us (--configure): 
 dependency problems - leaving unconfigured 
Setting up pulseaudio (1:1.1-0ubuntu15.1) ... 
feature.pm did not return a true value at /usr/lib/perl/5.14/File/Glob.pm line 7. 
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/File/Glob.pm line 7. 
Compilation failed in require at /usr/sbin/update-rc.d line 236. 
BEGIN failed--compilation aborted at /usr/sbin/update-rc.d line 236. 
dpkg: error processing pulseaudio (--configure): 
 subprocess installed post-installation script returned error exit status 5 
dpkg: dependency problems prevent configuration of vim-tiny: 
 vim-tiny depends on vim-common (= 2:7.3.429-2ubuntu2.1); however: 
  Package vim-common is not installed. 
dpkg: error processing vim-tiny (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth: 
 pulseaudio-module-bluetooth depends on pulseaudio; however: 
  Package pulseaudio is not configured yet. 
dpkg: error processing pulseaudio-module-bluetooth (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libpam-winbind: 
 libpam-winbind depends on winbind (= 2:3.6.3-2ubuntu2.3); however: 
  Package winbind is not configured yet. 
dpkg: error processing libpam-winbind (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of pulseaudio-module-x11: 
 pulseaudio-module-x11 depends on pulseaudio; however: 
  Package pulseaudio is not configured yet. 
dpkg: error processing pulseaudio-module-x11 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-exe-thumbnailer: 
 gnome-exe-thumbnailer depends on imagemagick; however: 
  Package imagemagick is not configured yet. 
dpkg: error processing gnome-exe-thumbnailer (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of pulseaudio-module-gconf: 
 pulseaudio-module-gconf depends on pulseaudio; however: 
  Package pulseaudio is not configured yet. 
dpkg: error processing pulseaudio-module-gconf (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-emailmerge: 
 libreoffice-emailmerge depends on python-uno | python3-uno; however: 
  Package python-uno is not configured yet. 
  Package python3-uno is not installed. 
dpkg: error processing libreoffice-emailmerge (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of indicator-sound: 
 indicator-sound depends on pulseaudio; however: 
  Package pulseaudio is not configured yet. 
dpkg: error processing indicator-sound (--configure): 
 dependency problems - leaving unconfigured




Any help at all would be greatly appreciated. Thanks!

---

### Post by miegiel on 2012-07-12
Try the solution **[COLOR="DarkOrange"]SlugSlug[/COLOR]** posted here: [http://ubuntuforums.org/showthread.php?p=12093363#post12093363](http://ubuntuforums.org/showthread.php?p=12093363#post12093363)

---

