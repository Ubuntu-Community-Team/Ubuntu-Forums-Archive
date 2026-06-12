---
title: "Can't Install 1 package softare update"
date: 2024-02-23
forum: New to Ubuntu
---

### Post by rifqilubis on 2024-02-23
I can update all application, except System Software.

---

### Post by Impavidus on 2024-02-23
System Software is just an indication of the type of software, not the actual package name. And there could be many reasons why some upgrade doesn't install: phased updates (although they can be forced), a dependency issue resulting from a server glitch, a dependency issue resulting from packages from non-official sources on your system, broken package management.

Let's see the details. In a terminal, run```
sudo apt update
sudo apt upgrade
```Those are two commands. The output is text, so you can copy-paste it to the forum.

I use the terminal, because that's the same on every flavour of Ubuntu and has been for many releases. Unlike the GUI tools.

---

### Post by rifqilubis on 2024-02-23
> **Impavidus said:**
> System Software is just an indication of the type of software, not the actual package name. And there could be many reasons why some upgrade doesn't install: phased updates (although they can be forced), a dependency issue resulting from a server glitch, a dependency issue resulting from packages from non-official sources on your system, broken package management.

Let's see the details. In a terminal, run```
sudo apt update
sudo apt upgrade
```Those are two commands. The output is text, so you can copy-paste it to the forum.

I use the terminal, because that's the same on every flavour of Ubuntu and has been for many releases. Unlike the GUI tools.



here the list for sudo apt update:


```
Hit:1 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable InRelease                                                
Hit:3 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease                                          
Hit:4 [https://deb.librewolf.net](https://deb.librewolf.net) jammy InRelease                                                                
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease                                               
Hit:6 [https://repo.radeon.com/amdgpu/23.20/amdgpu/ubuntu](https://repo.radeon.com/amdgpu/23.20/amdgpu/ubuntu) jammy InRelease                                       
Hit:7 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) jammy InRelease                            
Get:8 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]
Ign:9 [https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu](https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu) jammy InRelease
Hit:10 [https://repo.radeon.com/amdgpu/23.20/rocm/apt/5.7](https://repo.radeon.com/amdgpu/23.20/rocm/apt/5.7) jammy InRelease        
Err:11 [https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu](https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu) jammy Release
  404  Not Found [IP: 2620:2d:4000:1::81 443]
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://brave-browser-apt-rel
ease.s3.brave.com stable InRelease' doesn't support architecture 'i386'
E: The repository 'https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu jammy Release' does not have
 a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

And here for sudo apt upgrade

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-hwe-22.04 : Depends: linux-modules-extra-6.5.0-21-generic but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

---

### Post by deadflowr on 2024-02-23
You need to fix your sources.

First,
the codeblocks PPA is dead and has no packages for 22.04.
You need to remove it.
Run
```
sudo add-apt-repository -r ppa:codeblocks-devs/daily
```

Second,
you need to add a  part to the brave repo list
should read like
```
deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg, **arch=amd64**] https://brave-browser-apt-release.s3.brave.com/ stable main
```
You need to add the arch=amd64 or else it'll want to keep looking for the i386 packages that don't exist.


But the only actual error is the codeblocks PPA error.

Once you remove that you can try re-running apt update and apt upgrade.
If it gives you the same error message again, try running the command it shows.
```
sudo apt --fix-broken install
```

---

### Post by rifqilubis on 2024-02-24
do i need remove through terminal or go to directory itself?



because i run the first code you gave me, it giving me this message:
```
Repository: 'deb [https://ppa.launchpadcontent.net/codeblocks-devs/daily/ubuntu/](https://ppa.launchpadcontent.net/codeblocks-devs/daily/ubuntu/) jammy main'
Description:
Built daily from an imported branch of the SVN trunk.

To install Code::Blocks from this PPA, open a terminal and type:

sudo add-apt-repository ppa:codeblocks-devs/daily
sudo apt-get update
sudo apt-get install codeblocks codeblocks-contrib
More info: [https://launchpad.net/~codeblocks-devs/+archive/ubuntu/daily](https://launchpad.net/~codeblocks-devs/+archive/ubuntu/daily)
Removing repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Hit:1 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease
Get:2 [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable InRelease [3.589 B]                                      
Get:3 [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable/main arm64 Packages [16,7 kB]                            
Get:4 [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable/main amd64 Packages [16,6 kB]                            
Get:5 [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable/main armhf Packages [16,7 kB]                            
Hit:6 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease                                          
Hit:7 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) jammy InRelease                                                      
Get:8 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]                                     
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]                                      
Hit:10 [https://deb.librewolf.net](https://deb.librewolf.net) jammy InRelease                                                               
Hit:11 [https://repo.radeon.com/amdgpu/23.20/amdgpu/ubuntu](https://repo.radeon.com/amdgpu/23.20/amdgpu/ubuntu) jammy InRelease                                      
Hit:12 [https://repo.radeon.com/amdgpu/23.20/rocm/apt/5.7](https://repo.radeon.com/amdgpu/23.20/rocm/apt/5.7) jammy InRelease                                       
Ign:13 [https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu](https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu) jammy InRelease
Err:14 [https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu](https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu) jammy Release
  404  Not Found [IP: 2620:2d:4000:1::81 443]
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://brave-browser-apt-rel
ease.s3.brave.com stable InRelease' doesn't support architecture 'i386'
E: The repository 'https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu jammy Release' does not have
 a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


```

---

### Post by rifqilubis on 2024-02-24
> **deadflowr said:**
> 

Second,
you need to add a  part to the brave repo list
should read like
```
deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg, **arch=amd64**] https://brave-browser-apt-release.s3.brave.com/ stable main
```
You need to add the arch=amd64 or else it'll want to keep looking for the i386 packages that don't exist.



brave repo? you mean brave directory? like a folder file?


edit 2: nevermind. i think i got it

edit 3: how to edit it?  i use kate it gave me weird word

edit 4: what do you mean by [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) stable main

---

### Post by Impavidus on 2024-02-24
OK, you think you got it, but let's make it sure.

Somewhere in the file /etc/apt/sources.list, or in a file in the directry /etc/apt/sources.list.d/ is a line telling where the brave repository can be found. That line must be changed to the one given by deadflowr. It's the line starting with deb. Note that you need root permissions to edit that file. The proper way to edit files with root permisions is to use sudoedit. By default it uses the nano text editor, but you can change that if you want, using the EDITOR environment variable.

Your initial problem appears to be caused by a messed up package manager. A simple```
sudo apt --fix-broken install
```should fix that, or at least give more information.

---

### Post by ajgreeny on 2024-02-24
```
sudoedit /etc/apt/sources.list.d/brave-browser-release.list
```
and then change the line to ```
deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg, arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main
``` simply by adding that** , arch=amd64**.
Press Ctrl+o (o for overwrite) then Enter, and finally Ctrl+X to close nano  - *#(This in case you don't know nano)*

What you see, however, is not an error but a warning that the 32bit systems are no longer available so if you do nothing about it nothing bad will happen, you will just see that warning every time you update the repos.

---

### Post by rifqilubis on 2024-02-27
> **Impavidus said:**
> OK, you think you got it, but let's make it sure.

Somewhere in the file /etc/apt/sources.list, or in a file in the directry /etc/apt/sources.list.d/ is a line telling where the brave repository can be found. That line must be changed to the one given by deadflowr. It's the line starting with deb. Note that you need root permissions to edit that file. The proper way to edit files with root permisions is to use sudoedit. By default it uses the nano text editor, but you can change that if you want, using the EDITOR environment variable.

Your initial problem appears to be caused by a messed up package manager. A simple```
sudo apt --fix-broken install
```should fix that, or at least give more information.


done that but it gave me this, sorry for late reply. forgot to open linux.

```
[FONT=monospace][COLOR=#000000]sudo apt --fix-broken install[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  codeblocks-common i965-va-driver:i386 intel-media-va-driver:i386 libapparmor1:i386 libasound2:i386
  libasound2-plugins:i386 libastyle3 libasyncns0:i386 libbrotli1:i386 libc6-i386 libcodeblocks0
  libdbus-1-3:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libglib2.0-0:i386 libgnutls30:i386
  libhogweed6:i386 libigdgmm12:i386 libjack-jackd2-0:i386 libnettle8:i386 libnm0:i386 libogg0:i386
  libopus0:i386 libp11-kit0:i386 libpng16-16:i386 libpulse0:i386 libsamplerate0:i386 libsndfile1:i386
  libtasn1-6:i386 libtinyxml2.6.2v5 libva-drm2:i386 libva-glx2 libva-glx2:i386 libva-x11-2:i386 libva2:i386
  libvorbis0a:i386 libvorbisenc2:i386 libvulkan1:i386 libwxbase3.0-0v5 libwxgtk3.0-gtk3-0v5 libwxsmithlib0
  libxinerama1:i386 libxss1:i386 linux-headers-6.2.0-39-generic linux-headers-6.5.0-14-generic
  linux-headers-6.5.0-15-generic linux-hwe-6.2-headers-6.2.0-39 linux-hwe-6.5-headers-6.5.0-14
  linux-hwe-6.5-headers-6.5.0-15 linux-image-6.2.0-39-generic linux-image-6.5.0-14-generic
  linux-image-6.5.0-15-generic linux-modules-6.2.0-39-generic linux-modules-6.5.0-14-generic
  linux-modules-6.5.0-15-generic linux-modules-extra-6.2.0-39-generic linux-modules-extra-6.5.0-14-generic
  linux-modules-extra-6.5.0-15-generic mesa-va-drivers:i386 mesa-vulkan-drivers:i386 va-driver-all:i386
  valgrind
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-modules-extra-6.5.0-21-generic
The following NEW packages will be installed:
  linux-modules-extra-6.5.0-21-generic
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
45 not fully installed or removed.
Need to get 0 B/76,6 MB of archives.
After this operation, 455 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 341306 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-6.5.0-21-generic_6.5.0-21.21~22.04.1_amd64.deb ...
Unpacking linux-modules-extra-6.5.0-21-generic (6.5.0-21.21~22.04.1) ...
dpkg-deb (subprocess): ZSTD_decompressStream error : Corrupted block detected  

[COLOR=#000000]**dpkg-deb:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#FF5454]**error:**[/COLOR][COLOR=#000000] <decompress> subprocess returned error exit status 2[/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing archive /var/cache/apt/archives/linux-modules-extra-6.5.0-21-generic_6.5.0-21.21~22.04.1[/COLOR]
_amd64.deb (--unpack):
 cannot copy extracted data for './lib/modules/6.5.0-21-generic/kernel/drivers/net/ethernet/neterion/s2io.ko' t
o '/lib/modules/6.5.0-21-generic/kernel/drivers/net/ethernet/neterion/s2io.ko.dpkg-new': unexpected end of file
 or stream
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-6.5.0-21-generic_6.5.0-21.21~22.04.1_amd64.deb
[COLOR=#FF5454]**E: **[/COLOR][COLOR=#000000]Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

[/FONT]
```

---

### Post by rifqilubis on 2024-02-27
shoud i just upgrade the package(update) right now? or there something wrong

---

### Post by rifqilubis on 2024-02-27
shoud i just upgrade the package(update) right now? or there something wrong


edit: sorry, accidentally double comment

---

### Post by Impavidus on 2024-02-29
It looks like one archive has been damaged. Try to delete it. It will be redownloaded automatically when you try again:```
sudo rm [FONT=monospace][COLOR=#000000]/var/cache/apt/archives/linux-modules-extra-6.5.0-21-generic_6.5.0-21.21~22.04.1[/COLOR][/FONT][FONT=monospace]_amd64.deb[/FONT]
```
Then try```
sudo apt update
sudo apt --fix-broken install
```

---

### Post by rifqilubis on 2024-02-29
```
Repository: 'deb https://ppa.launchpadcontent.net/codeblocks-devs/daily/ubuntu/ jammy main'Description:
Built daily from an imported branch of the SVN trunk.


To install Code::Blocks from this PPA, open a terminal and type:


sudo add-apt-repository ppa:codeblocks-devs/daily
sudo apt-get update
sudo apt-get install codeblocks codeblocks-contrib
More info: https://launchpad.net/~codeblocks-devs/+archive/ubuntu/daily
Removing repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://packages.microsoft.com/repos/code stable InRelease                                               
Hit:3 https://brave-browser-apt-release.s3.brave.com stable InRelease                                         
Hit:4 http://id.archive.ubuntu.com/ubuntu jammy InRelease                                                     
Get:5 http://id.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]                                    
Hit:6 https://deb.librewolf.net jammy InRelease                                                               
Get:7 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                                     
Hit:8 https://repo.radeon.com/amdgpu/23.20/amdgpu/ubuntu jammy InRelease                                      
Hit:9 https://repo.radeon.com/amdgpu/23.20/rocm/apt/5.7 jammy InRelease                                       
Ign:10 https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu jammy InRelease                        
Err:11 https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu jammy Release
  404  Not Found [IP: 2620:2d:4000:1::81 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/codeblocks-devs/release/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```


here is the code when i try to run command that you gave me, to remove codeblocks ppa.

---

### Post by rifqilubis on 2024-02-29
does it succesfull? or still fail?

---

### Post by rifqilubis on 2024-03-01
> **Impavidus said:**
> It looks like one archive has been damaged. Try to delete it. It will be redownloaded automatically when you try again:```
sudo rm [FONT=monospace][COLOR=#000000]/var/cache/apt/archives/linux-modules-extra-6.5.0-21-generic_6.5.0-21.21~22.04.1[/COLOR][/FONT][FONT=monospace]_amd64.deb[/FONT]
```
Then try```
sudo apt update
sudo apt --fix-broken install
```



```

[FONT=monospace][COLOR=#000000]Reading package lists... Done[/COLOR]
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  codeblocks-common i965-va-driver:i386 intel-media-va-driver:i386 libapparmor1:i386 libasound2:i386
  libasound2-plugins:i386 libastyle3 libasyncns0:i386 libbrotli1:i386 libc6-i386 libcodeblocks0
  libdbus-1-3:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libglib2.0-0:i386 libgnutls30:i386
  libhogweed6:i386 libigdgmm12:i386 libjack-jackd2-0:i386 libnettle8:i386 libnm0:i386 libogg0:i386
  libopus0:i386 libp11-kit0:i386 libpng16-16:i386 libpulse0:i386 libsamplerate0:i386 libsndfile1:i386
  libtasn1-6:i386 libtinyxml2.6.2v5 libva-drm2:i386 libva-glx2 libva-glx2:i386 libva-x11-2:i386 libva2:i386
  libvorbis0a:i386 libvorbisenc2:i386 libvulkan1:i386 libwxbase3.0-0v5 libwxgtk3.0-gtk3-0v5 libwxsmithlib0
  libxinerama1:i386 libxss1:i386 linux-headers-6.2.0-39-generic linux-headers-6.5.0-14-generic
  linux-headers-6.5.0-15-generic linux-hwe-6.2-headers-6.2.0-39 linux-hwe-6.5-headers-6.5.0-14
  linux-hwe-6.5-headers-6.5.0-15 linux-image-6.2.0-39-generic linux-image-6.5.0-14-generic
  linux-image-6.5.0-15-generic linux-modules-6.2.0-39-generic linux-modules-6.5.0-14-generic
  linux-modules-6.5.0-15-generic linux-modules-extra-6.2.0-39-generic linux-modules-extra-6.5.0-14-generic
  linux-modules-extra-6.5.0-15-generic mesa-va-drivers:i386 mesa-vulkan-drivers:i386 va-driver-all:i386
  valgrind
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-modules-extra-6.5.0-21-generic
The following NEW packages will be installed:
  linux-modules-extra-6.5.0-21-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
70 not fully installed or removed.
Need to get 76,6 MB of archives.
After this operation, 455 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://id.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-modules-extra-6.5.0-21-generic amd64 6
.5.0-21.21~22.04.1 [76,6 MB]
Fetched 76,6 MB in 14s (5.591 kB/s)                                                                            
(Reading database ... 341310 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-6.5.0-21-generic_6.5.0-21.21~22.04.1_amd64.deb ...
Unpacking linux-modules-extra-6.5.0-21-generic (6.5.0-21.21~22.04.1) ...
Setting up libip4tc2:amd64 (1.8.7-1ubuntu5.2) ...
Setting up librewolf (123.0-1) ...
Setting up mesa-vulkan-drivers:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up mesa-vulkan-drivers:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up mesa-vdpau-drivers:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up tcpdump (4.99.1-3ubuntu0.2) ...
Installing new version of config file /etc/apparmor.d/usr.bin.tcpdump ...
Setting up libgbm1:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up libgbm1:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up libip6tc2:amd64 (1.8.7-1ubuntu5.2) ...
Setting up libcpanel-json-xs-perl:amd64 (4.27-1ubuntu0.1) ...
Setting up firmware-sof-signed (2.0-1ubuntu4.5) ...
Setting up unzip (6.0-26ubuntu3.2) ...
Setting up binutils-common:amd64 (2.38-4ubuntu2.6) ...
Setting up libssl3:i386 (3.0.2-0ubuntu1.15) ...
Setting up libjavascriptcoregtk-4.0-18:amd64 (2.42.5-0ubuntu0.22.04.2) ...
Setting up less (590-1ubuntu0.22.04.2) ...
Setting up linux-libc-dev:amd64 (5.15.0-97.107) ...
Setting up libctf-nobfd0:amd64 (2.38-4ubuntu2.6) ...
Setting up dnsmasq-base (2.90-0ubuntu0.22.04.1) ...
Setting up libxatracker2:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up dns-root-data (2023112702~ubuntu0.22.04.1) ...
Setting up tzdata (2024a-0ubuntu0.22.04) ...

Current default time zone: 'Asia/Jakarta'
Local time is now:      Sab 02 Mar 2024 08:45:44  WIB.
Universal Time is now:  Sat Mar  2 01:45:44 UTC 2024.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

Setting up libuv1:amd64 (1.43.0-1ubuntu0.1) ...
Setting up linux-modules-6.5.0-21-generic (6.5.0-21.21~22.04.1) ...
Setting up linux-image-6.5.0-21-generic (6.5.0-21.21~22.04.1) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-6.5.0-17-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-6.5.0-17-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-6.5.0-21-generic
I: /boot/initrd.img is now a symlink to initrd.img-6.5.0-21-generic
Setting up linux-modules-extra-6.5.0-21-generic (6.5.0-21.21~22.04.1) ...
Setting up libxtables12:amd64 (1.8.7-1ubuntu5.2) ...
Setting up libglapi-mesa:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up libglapi-mesa:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up openjdk-17-jre-headless:amd64 (17.0.10+7-1~22.04.1) ...
Setting up python-apt-common (2.4.0ubuntu3) ...
Setting up linux-hwe-6.5-headers-6.5.0-21 (6.5.0-21.21~22.04.1) ...
Setting up brave-browser (1.63.165) ...
Setting up libtiff5:amd64 (4.3.0-6ubuntu0.8) ...
Setting up mesa-va-drivers:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up mesa-va-drivers:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up libbinutils:amd64 (2.38-4ubuntu2.6) ...
Setting up libde265-0:amd64 (1.0.8-1ubuntu0.2) ...
Setting up openssl (3.0.2-0ubuntu1.15) ...
Setting up linux-headers-6.5.0-21-generic (6.5.0-21.21~22.04.1) ...
Setting up libxml2:amd64 (2.9.13+dfsg-1ubuntu0.4) ...
Setting up libxml2:i386 (2.9.13+dfsg-1ubuntu0.4) ...
Setting up libctf0:amd64 (2.38-4ubuntu2.6) ...
Setting up code (1.87.0-1709078641) ...
Setting up linux-image-generic-hwe-22.04 (6.5.0.21.21~22.04.11) ...
Setting up google-chrome-stable (122.0.6261.94-1) ...
Setting up bind9-libs:amd64 (1:9.18.18-0ubuntu0.22.04.2) ...
Setting up iptables (1.8.7-1ubuntu5.2) ...
Setting up python3-apt (2.4.0ubuntu3) ...
Setting up openjdk-17-jre:amd64 (17.0.10+7-1~22.04.1) ...
Setting up libgl1-mesa-dri:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up libgl1-mesa-dri:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up python3-distupgrade (1:22.04.19) ...
Setting up libegl-mesa0:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up libegl-mesa0:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up openjdk-17-jdk-headless:amd64 (17.0.10+7-1~22.04.1) ...
Setting up ubuntu-release-upgrader-core (1:22.04.19) ...
Setting up libwebkit2gtk-4.0-37:amd64 (2.42.5-0ubuntu0.22.04.2) ...
Setting up libxml2-utils (2.9.13+dfsg-1ubuntu0.4) ...
Setting up bind9-host (1:9.18.18-0ubuntu0.22.04.2) ...
Setting up linux-headers-generic-hwe-22.04 (6.5.0.21.21~22.04.11) ...
Setting up binutils-x86-64-linux-gnu (2.38-4ubuntu2.6) ...
Setting up linux-generic-hwe-22.04 (6.5.0.21.21~22.04.11) ...
Setting up libglx-mesa0:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up libglx-mesa0:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Setting up binutils (2.38-4ubuntu2.6) ...
Setting up openjdk-17-jdk:amd64 (17.0.10+7-1~22.04.1) ...
Setting up ubuntu-release-upgrader-qt (1:22.04.19) ...
Setting up bind9-dnsutils (1:9.18.18-0ubuntu0.22.04.2) ...
Setting up language-pack-en (1:22.04+20240212) ...
Setting up language-pack-en-base (1:22.04+20240212) ...
Generating locales (this might take a while)...
Generation complete.
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for libc-bin (2.35-0ubuntu3.6) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.5+git20211018-1ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for shared-mime-info (2.1-2) ...
Processing triggers for plymouth-theme-kubuntu-text (1:22.04.10) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for install-info (6.8-4build1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for linux-image-6.5.0-21-generic (6.5.0-21.21~22.04.1) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-6.5.0-21-generic
W: Possible missing firmware /lib/firmware/amdgpu/ip_discovery.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_6_ta.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_6_sos.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/aldebaran_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/aldebaran_sjt_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/aldebaran_sjt_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_9_4_3_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_9_4_3_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_toc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sdma_4_4_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi10_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_3_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vcn_4_0_3.bin for module amdgpu
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-21-generic
Found initrd image: /boot/initrd.img-6.5.0-21-generic
Found linux image: /boot/vmlinuz-6.5.0-17-generic
Found initrd image: /boot/initrd.img-6.5.0-17-generic
Found linux image: /boot/vmlinuz-6.5.0-15-generic
Found initrd image: /boot/initrd.img-6.5.0-15-generic
Found linux image: /boot/vmlinuz-6.5.0-14-generic
Found initrd image: /boot/initrd.img-6.5.0-14-generic
Found linux image: /boot/vmlinuz-6.2.0-39-generic
Found initrd image: /boot/initrd.img-6.2.0-39-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.5.0-21-generic
W: Possible missing firmware /lib/firmware/amdgpu/ip_discovery.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_6_ta.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_6_sos.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/aldebaran_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/aldebaran_sjt_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/aldebaran_sjt_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_9_4_3_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_9_4_3_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_toc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sdma_4_4_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi10_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_3_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vcn_4_0_3.bin for module amdgpu

[/FONT]
```

here what i got.

---

### Post by Impavidus on 2024-03-02
No errors, although there are a few warnings. It looks like all packages have been properly installed. Your main problem appears to be solved.

Maybe there are still some things to clean up, if you wish. In post #13 you showed that there's still an obsolete reference to the codeblocks-devs repository. Hunt it down in /etc/apt/sources.list or /etc/apt/sources.list.d/ and remove it. You also have a lot of packages that can be autoremoved. Many of those are 32-bit libraries. Normally Ubuntu doesn't use any 32-bit libraries, but some third party software needs them. If you're sure no applications (including third party applications not properly registered with the package manager) use those, you can remove them. Easiest is to use autoremove, for example```
sudo apt autoremove
```

---

### Post by rifqilubis on 2024-03-02
> **Impavidus said:**
> No errors, although there are a few warnings. It looks like all packages have been properly installed. Your main problem appears to be solved.

Maybe there are still some things to clean up, if you wish. In post #13 you showed that there's still an obsolete reference to the codeblocks-devs repository. Hunt it down in /etc/apt/sources.list or /etc/apt/sources.list.d/ and remove it. You also have a lot of packages that can be autoremoved. Many of those are 32-bit libraries. Normally Ubuntu doesn't use any 32-bit libraries, but some third party software needs them. If you're sure no applications (including third party applications not properly registered with the package manager) use those, you can remove them. Easiest is to use autoremove, for example```
sudo apt autoremove
```



```

Here the output that console gave me:

[FONT=monospace][COLOR=#000000]Reading package lists... Done[/COLOR]
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  codeblocks-common i965-va-driver:i386 intel-media-va-driver:i386 libapparmor1:i386 libasound2:i386
  libasound2-plugins:i386 libastyle3 libasyncns0:i386 libbrotli1:i386 libc6-i386 libcodeblocks0
  libdbus-1-3:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libglib2.0-0:i386 libgnutls30:i386
  libhogweed6:i386 libigdgmm12:i386 libjack-jackd2-0:i386 libnettle8:i386 libnm0:i386 libogg0:i386
  libopus0:i386 libp11-kit0:i386 libpng16-16:i386 libpulse0:i386 libsamplerate0:i386 libsndfile1:i386
  libtasn1-6:i386 libtinyxml2.6.2v5 libva-drm2:i386 libva-glx2 libva-glx2:i386 libva-x11-2:i386 libva2:i386
  libvorbis0a:i386 libvorbisenc2:i386 libvulkan1:i386 libwxbase3.0-0v5 libwxgtk3.0-gtk3-0v5 libwxsmithlib0
  libxinerama1:i386 libxss1:i386 linux-headers-6.2.0-39-generic linux-headers-6.5.0-14-generic
  linux-headers-6.5.0-15-generic linux-hwe-6.2-headers-6.2.0-39 linux-hwe-6.5-headers-6.5.0-14
  linux-hwe-6.5-headers-6.5.0-15 linux-image-6.2.0-39-generic linux-image-6.5.0-14-generic
  linux-image-6.5.0-15-generic linux-modules-6.2.0-39-generic linux-modules-6.5.0-14-generic
  linux-modules-6.5.0-15-generic linux-modules-extra-6.2.0-39-generic linux-modules-extra-6.5.0-14-generic
  linux-modules-extra-6.5.0-15-generic mesa-va-drivers:i386 mesa-vulkan-drivers:i386 va-driver-all:i386
  valgrind
0 upgraded, 0 newly installed, 63 to remove and 0 not upgraded.
After this operation, 2.371 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 347629 files and directories currently installed.)
Removing codeblocks-common (20.03-3.1) ...
Removing va-driver-all:i386 (2.14.0-1) ...
Removing i965-va-driver:i386 (2.4.1+dfsg1-1) ...
Removing intel-media-va-driver:i386 (22.3.1+dfsg1-1ubuntu2) ...
Removing libasound2-plugins:i386 (1.2.6-1) ...
Removing libpulse0:i386 (1:15.99.1+dfsg1-1ubuntu2.1) ...
Removing libapparmor1:i386 (3.0.4-2ubuntu2.3) ...
Removing libasound2:i386 (1.2.6.1-1ubuntu1) ...
Removing libastyle3:amd64 (3.1-2build1) ...
Removing libasyncns0:i386 (0.8-6build2) ...
Removing libfontconfig1:i386 (2.13.1-4.2ubuntu5) ...
Removing libfreetype6:i386 (2.11.1+dfsg-1ubuntu0.2) ...
Removing libbrotli1:i386 (1.0.9-2build6) ...
Removing valgrind (1:3.18.1-1ubuntu2) ...
Removing libc6-i386 (2.35-0ubuntu3.6) ...
Removing libwxsmithlib0 (20.03-3.1) ...
Removing libcodeblocks0 (20.03-3.1) ...
Removing libdbus-1-3:i386 (1.12.20-2ubuntu4.1) ...
Removing libsndfile1:i386 (1.0.31-2ubuntu0.1) ...
Removing libflac8:i386 (1.3.3-2ubuntu0.2) ...
Removing libnm0:i386 (1.36.6-0ubuntu2) ...
Removing libglib2.0-0:i386 (2.72.4-0ubuntu2.2) ...
Removing libgnutls30:i386 (3.7.3-4ubuntu1.4) ...
Removing libhogweed6:i386 (3.7.3-1build2) ...
Removing libigdgmm12:i386 (22.1.2+ds1-1) ...
Removing libjack-jackd2-0:i386 (1.9.20~dfsg-1) ...
Removing libnettle8:i386 (3.7.3-1build2) ...
Removing libvorbisenc2:i386 (1.3.7-1build2) ...
Removing libvorbis0a:i386 (1.3.7-1build2) ...
Removing libogg0:i386 (1.3.5-0ubuntu3) ...
Removing libopus0:i386 (1.3.1-0.1build2) ...
Removing libp11-kit0:i386 (0.24.0-6build1) ...
Removing libpng16-16:i386 (1.6.37-3build5) ...
Removing libsamplerate0:i386 (0.2.2-1build1) ...
Removing libtasn1-6:i386 (4.18.0-4build1) ...
Removing libtinyxml2.6.2v5:amd64 (2.6.2-6ubuntu0.22.04.1) ...
Removing libva-drm2:i386 (2.14.0-1) ...
Removing libva-glx2:amd64 (2.14.0-1) ...
Removing libva-glx2:i386 (2.14.0-1) ...
Removing libva-x11-2:i386 (2.14.0-1) ...
Removing libva2:i386 (2.14.0-1) ...
Removing mesa-vulkan-drivers:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing libvulkan1:i386 (1.3.204.1-2) ...
Removing libwxgtk3.0-gtk3-0v5:amd64 (3.0.5.1+dfsg-4) ...
Removing libwxbase3.0-0v5:amd64 (3.0.5.1+dfsg-4) ...
Removing libxinerama1:i386 (2:1.1.4-3) ...
Removing libxss1:i386 (1:1.2.3-1build2) ...
Removing linux-headers-6.2.0-39-generic (6.2.0-39.40~22.04.1) ...
Removing linux-headers-6.5.0-14-generic (6.5.0-14.14~22.04.1) ...
Removing linux-headers-6.5.0-15-generic (6.5.0-15.15~22.04.1) ...
Removing linux-hwe-6.2-headers-6.2.0-39 (6.2.0-39.40~22.04.1) ...
Removing linux-hwe-6.5-headers-6.5.0-14 (6.5.0-14.14~22.04.1) ...
Removing linux-hwe-6.5-headers-6.5.0-15 (6.5.0-15.15~22.04.1) ...
Removing linux-image-6.2.0-39-generic (6.2.0-39.40~22.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.2.0-39-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-21-generic
Found initrd image: /boot/initrd.img-6.5.0-21-generic
Found linux image: /boot/vmlinuz-6.5.0-17-generic
Found initrd image: /boot/initrd.img-6.5.0-17-generic
Found linux image: /boot/vmlinuz-6.5.0-15-generic
Found initrd image: /boot/initrd.img-6.5.0-15-generic
Found linux image: /boot/vmlinuz-6.5.0-14-generic
Found initrd image: /boot/initrd.img-6.5.0-14-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Removing linux-image-6.5.0-14-generic (6.5.0-14.14~22.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.5.0-14-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-21-generic
Found initrd image: /boot/initrd.img-6.5.0-21-generic
Found linux image: /boot/vmlinuz-6.5.0-17-generic
Found initrd image: /boot/initrd.img-6.5.0-17-generic
Found linux image: /boot/vmlinuz-6.5.0-15-generic
Found initrd image: /boot/initrd.img-6.5.0-15-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Removing linux-image-6.5.0-15-generic (6.5.0-15.15~22.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.5.0-15-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-21-generic
Found initrd image: /boot/initrd.img-6.5.0-21-generic
Found linux image: /boot/vmlinuz-6.5.0-17-generic
Found initrd image: /boot/initrd.img-6.5.0-17-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Removing linux-modules-extra-6.2.0-39-generic (6.2.0-39.40~22.04.1) ...
Removing linux-modules-6.2.0-39-generic (6.2.0-39.40~22.04.1) ...
Removing linux-modules-extra-6.5.0-14-generic (6.5.0-14.14~22.04.1) ...
Removing linux-modules-6.5.0-14-generic (6.5.0-14.14~22.04.1) ...
Removing linux-modules-extra-6.5.0-15-generic (6.5.0-15.15~22.04.1) ...
Removing linux-modules-6.5.0-15-generic (6.5.0-15.15~22.04.1) ...
Removing mesa-va-drivers:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for libc-bin (2.35-0ubuntu3.6) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for shared-mime-info (2.1-2) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...

[/FONT]
```


I hope all things clear. i will inform you guys, if its still have the same problem.

---

