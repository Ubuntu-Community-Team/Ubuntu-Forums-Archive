---
title: "PlayOnLinux giving me fits on Xenial"
date: 2018-07-17
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2018-07-17
Getting this when trying to install any version of wine. Doesn't matter x86 or x64. Keeps saying not a valid file, and everything else after fails because it can't do anything with the first .pol file. /home is mounted via sshfs. Is only thing different from my other laptop which has home local and it works flawlessly. Don't know what to do, or how to fix.

All permissions are correct. It is downloading and writing the .pol file to the tmp folder, just errors out when extracting.

```
dvdripper@dvdripper:~$ playonlinux
Looking for python... 2.7.12 - wxversion(s): 3.0-gtk2
selected
[main] Message: PlayOnLinux (4.2.10) is starting
[clean_tmp] Message: Cleaning temp directory
[Check_OpenGL] Warning: check_dd_x86 missing, test skipped
[Check_OpenGL] Warning: check_dd_amd64 missing, test skipped
[POL_System_CheckFS] Message: Checking filesystem for /home/dvdripper/.PlayOnLinux/
[main] Message: Filesystem is compatible
[install_plugins] Message: Checking plugin: ScreenCap...
[install_plugins] Message: Checking plugin: PlayOnLinux Vault...
[update_check] Message: List is up to date
[POL_SetupWindow_Init] Message: Creating new window for pid 2678
[POL_System_SetArch] Message: POL_ARCH set to x86
[POL_Wine_InstallVersion] Message: Installing wine version path: 3.12, x86
Server sha1 : 323274195a0729f1cbc3de438650901300669022
Client sha1 : 323274195a0729f1cbc3de438650901300669022
PlayOnLinux package manager: 4.2.10


Opening /home/dvdripper/.PlayOnLinux/tmp/PlayOnLinux-wine-3.12-linux-x86.pol
Extracting: /home/dvdripper/.PlayOnLinux/tmp/PlayOnLinux-wine-3.12-linux-x86.pol...
tar: wineversion/3.12/lib/libwine.so: Cannot utime: No such file or directory
tar: wineversion/3.12/lib/libwine.so.1: Cannot utime: No such file or directory
tar: wineversion/3.12/bin/wineg++: Cannot utime: No such file or directory
tar: Exiting with failure status due to previous errors
This file: /home/dvdripper/.PlayOnLinux/tmp/PlayOnLinux-wine-3.12-linux-x86.pol isn't a valid PlayOnLinux package!
[POL_Wine_Install_resources] Message: Installing gecko for wine 3.12 x86
[POL_Wine_Install_resources] Message: Linking gecko
ln: failed to create symbolic link '/home/dvdripper/.PlayOnLinux//wine/linux-x86/3.12/share/wine/gecko': No such file or directory
[POL_Wine_Install_resources] Message: wine_gecko-2.40-x86.msi already installed. Skipping
[POL_Wine_Install_resources] Message: Installing mono for wine 3.12 x86
[POL_Wine_Install_resources] Message: Linking mono
ln: failed to create symbolic link '/home/dvdripper/.PlayOnLinux//wine/linux-x86/3.12/share/wine/mono': No such file or directory
[POL_Wine_Install_resources] Message: Installing wine-mono-4.5.6.msi
[POL_Download] Message: Downloading http://wine.playonlinux.com/mono/wine-mono-4.5.6.msi
[POL_Download] Message: Download MD5 matches
[POL_SetupWindow_Close] Message: Closing window for pid 2678
Registered PID: 2412 (Missing)
Registered PID: 2450 (Missing)
Registered PID: 2678 (Present)
Registered PID: 2887 (Missing)
```

---

