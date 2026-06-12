---
title: "grub2-common will it have to be an installed package"
date: 2011-06-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2011-06-17
#Now in Grub 1.99-7 that grub2-common is a new addition when purging grub2 will have to?
sudo apt-get purge grub-common grub-pc grub2-common
#And also of course have to install with grub2-common as an addition over current
11.04 version of grub2.
##This is first time I have noticed change so I am putting this more in the form of a question?

```
rick@rick-HP:~$ aptitude show grub-pc
Package: grub-pc                         
State: installed
Automatically installed: no
Version: 1.99-7ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 406 k
Depends: debconf (>= 0.5) | debconf-2.0, grub-common, grub2-common (=
         1.99-7ubuntu1), grub-pc-bin (= 1.99-7ubuntu1), ucf,
         grub-gfxpayload-lists
Conflicts: grub (< 0.97-54), grub-coreboot, grub-efi-amd64, grub-efi-ia32,
           grub-ieee1275, grub-legacy
Replaces: grub, grub-common (<= 1.97~beta2-1), grub-coreboot, grub-efi-amd64,
          grub-efi-ia32, grub-ieee1275, grub-legacy, grub2 (< 1.99-7ubuntu1)
Description: GRand Unified Bootloader, version 2 (PC/BIOS version)
 GRUB is a portable, powerful bootloader.  This version of GRUB is based on a
 cleaner design than its predecessors, and provides the following new features: 
 
 * Scripting in grub.cfg using BASH-like syntax. 
 * Support for modern partition maps such as GPT. 
 * Modular generation of grub.cfg via update-grub.  Packages providing GRUB
   add-ons can plug in their own script rules and trigger updates by invoking
   update-grub2. 
 * VESA-based graphical mode with background image support and complete 24-bit
   color set. 
 * Support for extended charsets.  Users can write UTF-8 text to their menu
   entries. 
   
 This package contains a version of GRUB that has been built for use with
 traditional PC/BIOS architecture.
Homepage: http://www.gnu.org/software/grub/

rick@rick-HP:~$ aptitude show grub2-common
Package: grub2-common                    
New: yes
State: installed
Automatically installed: yes
Version: 1.99-7ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 176 k
Depends: grub-common (= 1.99-7ubuntu1), dpkg (>= 1.15.4) | install-info
Conflicts: grub (< 0.97-54), grub-doc (< 0.97-29ubuntu60), grub-legacy,
           grub-legacy-doc (< 0.97-29ubuntu60)
Replaces: grub, grub-common (< 1.99-1), grub-coreboot (< 1.99-1), grub-efi (<
          1.99-1), grub-efi-amd64 (< 1.99-1), grub-efi-ia32 (< 1.99-1),
          grub-ieee1275 (< 1.99-1), grub-legacy, grub-linuxbios (< 1.99-1),
          grub-pc (< 1.99-1), grub-yeeloong (< 1.99-1)
Description: GRand Unified Bootloader (common files for version 2)
 This package contains common files shared by the distinct flavours of GRUB. The
 files in this package are specific to GRUB 2, and would break GRUB Legacy if
 installed on the same system.
Homepage: http://www.gnu.org/software/grub/

rick@rick-HP:~$ aptitude show grub-common
Package: grub-common                     
State: installed
Automatically installed: no
Version: 1.99-7ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 4,899 k
Depends: libc6 (>= 2.8), libdevmapper1.02.1 (>= 2:1.02.36), libfreetype6 (>=
         2.2.1), libfuse2 (>= 2.8.1), gettext-base, lsb-base (>= 3.0-6)
Recommends: os-prober (>= 1.33)
Suggests: multiboot-doc, grub-emu, xorriso (>= 0.5.6.pl00), desktop-base (>=
          4.0.6)
Conflicts: mdadm (< 2.6.7-2)
Breaks: lupin-support (< 0.30)
Replaces: grub-coreboot (< 1.99-1), grub-efi (< 1.99-1), grub-efi-amd64 (<
          1.99-1), grub-efi-ia32 (< 1.99-1), grub-ieee1275 (< 1.99-1),
          grub-linuxbios (< 1.96+20080831-1), grub-pc (< 1.99-1), grub-yeeloong
          (< 1.99-1)
Description: GRand Unified Bootloader (common files)
 This package contains common files shared by the distinct flavours of GRUB. It
 is shared between GRUB Legacy and GRUB 2, although a number of files specific
 to GRUB 2 are here as long as they do not break GRUB Legacy.
Homepage: http://www.gnu.org/software/grub/

rick@rick-HP:~$ 

```

---

### Post by Harry33 on 2011-06-17
**In Natty**
The latest version is 1.99~rc1-13ubuntu3
Package grub-pc depends on grub-common and grub-gfxpayload-lists. These three will have to installed.

**In Oneiric**
The latest version is 1.99-7ubuntu1
Package grub-pc depends on grub-common, grub-pc-bin, grub2-common and grub-gfxpayload-lists.
These five will have to be installed.

---

### Post by garvinrick4 on 2011-06-17
Ran purge grub-pc the purge grub-common as per below. grub-common
also removes grub2-common and grub-pc-bin:
So to purge and reinstall grub-pc as needed for users now and again still only
have to:
sudo apt-get purge grub-common grub-pc
# and grub if want to purge legacy.
```

rick@rick-HP:~$ sudo apt-get purge grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-gfxpayload-lists* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 44 not upgraded.
After this operation, 483 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 165845 files and directories currently installed.)
Removing grub-gfxpayload-lists ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Processing triggers for man-db ...
rick@rick-HP:~$ aptitude show grub2-common
Package: grub2-common                    
New: yes
State: installed; will be removed because nothing depends on it
Automatically installed: yes
Version: 1.99-7ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 176 k
Depends: grub-common (= 1.99-7ubuntu1), dpkg (>= 1.15.4) | install-info
Conflicts: grub (< 0.97-54), grub-doc (< 0.97-29ubuntu60), grub-legacy,
           grub-legacy-doc (< 0.97-29ubuntu60)
Replaces: grub, grub-common (< 1.99-1), grub-coreboot (< 1.99-1), grub-efi (<
          1.99-1), grub-efi-amd64 (< 1.99-1), grub-efi-ia32 (< 1.99-1),
          grub-ieee1275 (< 1.99-1), grub-legacy, grub-linuxbios (< 1.99-1),
          grub-pc (< 1.99-1), grub-yeeloong (< 1.99-1)
Description: GRand Unified Bootloader (common files for version 2)
 This package contains common files shared by the distinct flavours of GRUB. The
 files in this package are specific to GRUB 2, and would break GRUB Legacy if
 installed on the same system.
Homepage: [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

rick@rick-HP:~$ aptitude show grub-common
Package: grub-common                     
State: installed
Automatically installed: no
Version: 1.99-7ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 4,899 k
Depends: libc6 (>= 2.8), libdevmapper1.02.1 (>= 2:1.02.36), libfreetype6 (>=
         2.2.1), libfuse2 (>= 2.8.1), gettext-base, lsb-base (>= 3.0-6)
Recommends: os-prober (>= 1.33)
Suggests: multiboot-doc, grub-emu, xorriso (>= 0.5.6.pl00), desktop-base (>=
          4.0.6)
Conflicts: mdadm (< 2.6.7-2)
Breaks: lupin-support (< 0.30)
Replaces: grub-coreboot (< 1.99-1), grub-efi (< 1.99-1), grub-efi-amd64 (<
          1.99-1), grub-efi-ia32 (< 1.99-1), grub-ieee1275 (< 1.99-1),
          grub-linuxbios (< 1.96+20080831-1), grub-pc (< 1.99-1), grub-yeeloong
          (< 1.99-1)
Description: GRand Unified Bootloader (common files)
 This package contains common files shared by the distinct flavours of GRUB. It
 is shared between GRUB Legacy and GRUB 2, although a number of files specific
 to GRUB 2 are here as long as they do not break GRUB Legacy.
Homepage: [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

rick@rick-HP:~$ sudo purge grub-common
sudo: purge: command not found
rick@rick-HP:~$ sudo apt-get purge grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
 [COLOR=Red] grub-common* grub-pc-bin* grub2-common*[/COLOR]
0 upgraded, 0 newly installed, 3 to remove and 44 not upgraded.
After this operation, 7,406 kB disk space will be freed.
Do you want to continue [Y/n]?

```Installing grub-pc by itself install[COLOR=Red] all packages[/COLOR] as per below:```
rick@rick-HP:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc-bin grub2-common
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  [COLOR=Red]grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common[/COLOR]
0 upgraded, 5 newly installed, 0 to remove and 44 not upgraded.
Need to get 0 B/3,039 kB of archives.
After this operation, 7,889 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 165528 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.99-7ubuntu1_amd64.deb) ...
Selecting previously deselected package grub2-common.
Unpacking grub2-common (from .../grub2-common_1.99-7ubuntu1_amd64.deb) ...
Selecting previously deselected package grub-pc-bin.
Unpacking grub-pc-bin (from .../grub-pc-bin_1.99-7ubuntu1_amd64.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.99-7ubuntu1_amd64.deb) ...
Selecting previously deselected package grub-gfxpayload-lists.
Unpacking grub-gfxpayload-lists (from .../grub-gfxpayload-lists_0.3_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up grub-common (1.99-7ubuntu1) ...
Setting up grub2-common (1.99-7ubuntu1) ...
Setting up grub-pc-bin (1.99-7ubuntu1) ...
Setting up grub-pc (1.99-7ubuntu1) ...

Creating config file /etc/default/grub with new version
Setting up grub-gfxpayload-lists (0.3) ...
rick@rick-HP:~$ 
```So basically purge grub-pc grub-common (for grub-pc 1.99-7ubuntu1
To install just grub-pc (for grub-pc 1.99-7ubuntu1)
#Has not really changed at all from earlier version just new packages added:

Log info:
```

Start-Date: 2011-06-17  02:25:28
Commandline: apt-get purge grub-pc
Purge: grub-pc:amd64 (1.99-7ubuntu1), grub-gfxpayload-lists:amd64 (0.3)
End-Date: 2011-06-17  02:25:58

Start-Date: 2011-06-17  02:41:08
Commandline: apt-get purge grub-common
Purge: grub-pc-bin:amd64 (1.99-7ubuntu1), grub-common:amd64 (1.99-7ubuntu1), grub2-common:amd64 (1.99-7ubuntu1)
End-Date: 2011-06-17  02:41:14

Start-Date: 2011-06-17  02:42:40
Commandline: apt-get install grub-pc
Install: grub-pc:amd64 (1.99-7ubuntu1), grub-gfxpayload-lists:amd64 (0.3, automatic), 
grub-pc-bin:amd64 (1.99-7ubuntu1, automatic), grub-common:amd64 (1.99-7ubuntu1, automatic), 
grub2-common:amd64 (1.99-7ubuntu1, automatic)
End-Date: 2011-06-17  02:45:04

```

---

### Post by Quackers on 2011-06-17
Thanks garvinrick4, that's good to know :-)

---

### Post by seeker5528 on 2011-06-17
> **garvinrick4 said:**
> So to purge and reinstall grub-pc as needed for users now and again still only
have to:
sudo apt-get purge grub-common grub-pc

If all you care about is purging the configuration so disk mappings and other grub configurations will be done from scratch, grub-pc should be the only thing you have to purge.

If all you want to do is change the location where grub will be installed you can do ```
sudo dpkg-reconfigure grub-pc
``` or instead of using dpkg-reconfigure you can accomplish the same thing in Synaptic by selecting grub-pc, then on the package menu select 'Configure...'. 

Later, Seeker

---

### Post by garvinrick4 on 2011-06-18
> If all you care about is purging the configuration so disk mappings and  other grub configurations will be done from scratch, grub-pc should be  the only thing you have to purge.Yes basically the same as previous versions of grub-pc, the new packages in grub did not
effect the purging and reinstalling process. If want to purge all remnants of grub-pc then
purging grub-common will be rid of new packages also in (1.99-7ubuntu1). So in effect all
tutorials on purging and reinstalling grub are still in play.

---

### Post by seeker5528 on 2011-06-18
> **garvinrick4 said:**
> If want to purge all remnants of grub-pc then
purging grub-common will be rid of new packages also in (1.99-7ubuntu1). So in effect all
tutorials on purging and reinstalling grub are still in play.

Only the packages you specify get purged, additional packages only get removed, so if those additional packages actually need to be purged to get rid of remnants you would have to specify those packages too.

Maybe there are some issues I'm not aware of, but I'm not seeing how grub-common and the new packages would factor into the issues that would typically lead people to purge and re-install grub.

If there *is* reason to purge some of the new packages I'm sure that will be figured out soon enough, I don't see a reason to assume that ahead of there actually being problems reported to indicate that to be the case.

If there was some indication of packages being corrupted, file system being corrupted, problems on a new hard drive after replacing one where sectors were starting to fail, etc... I might be more inclined to be more thorough when purging and re-installing. Otherwise why do more than is necessary?

Later, Seeker

---

### Post by garvinrick4 on 2011-06-18
> If there was some indication of packages being corrupted, file system  being corrupted, problems on a new hard drive after replacing one where  sectors were starting to fail, etc... I might be more inclined to be  more thorough when purging and re-installing. Otherwise why do more than  is necessary?
I agree with you, at times is not necessary and at times necessary and 
the new grub packages make no difference in code to do so. Thank you kindly,
enjoy your day.

---

### Post by seeker5528 on 2011-06-18
> **garvinrick4 said:**
> I agree with you, at times is not necessary and at times necessary and 
the new grub packages make no difference in code to do so.

Just because it's doesn't seem necessary to change code, doesn't mean it shouldn't be changed.

All I'm saying is, if you only want to do what's necessary the majority of the time, don't do something that will cause more to be done, if you want to be thorough, make sure you *are* being thorough.

Later, Seeker

---

