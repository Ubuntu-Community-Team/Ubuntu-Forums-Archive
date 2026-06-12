---
title: "Need help &quot;E: Sub-process /usr/bin/dpkg returned an error code (1)&quot;"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by laigdotcom on 2013-12-12
I've tried to make a clean install of Ubuntu 13.10 from Ubuntu 12.04 LTS. Anyway, whenever I installed a program, the code come out noticed me about "dpkg: error processing libkfbapi1 (--configure):". I assume that the problem came from this moment when I was installing some programs from Software center then suddenly my computer turned off. After that I faced this problem that mentioned above.

Please help me out.

```
sudo apt-get install subdownloaderReading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  subdownloader
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
35 not fully installed or removed.
Need to get 0 B/720 kB of archives.
After this operation, 2,323 kB of additional disk space will be used.
Selecting previously unselected package subdownloader.
(Reading database ... 222023 files and directories currently installed.)
Unpacking subdownloader (from .../subdownloader_2.0.14-1.1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Processing triggers for man-db ...
dpkg: error processing libgif4:amd64 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of openjdk-7-jre:amd64:
 openjdk-7-jre:amd64 depends on libgif4 (>= 4.1.4); however:
  Package libgif4:amd64 is not configured yet.


dpkg: error processing openjdk-7-jre:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of defa
ult-jre:
 defa
ult-jre depends on openjdk-7-jre (>= 7~u3-2.1.1); however:
  Package openjdk-7-jre:amd64 is not configured yet.


dpkg: error processing default-jre (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkhtml5:
 libkhtml5 depends on libgif4 (>= 4.1.4); however:
  Package libgif4:amd64 is not configured yet.


dpkg: error processing libkhtml5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kdelibs5-plugins:
 kdelibs5-plugins depends on libkhtml5 (= 4:4.11.2-0ubuntu2.1); however:
  Package libkhtml5 is not configured yet.


dpkg: error processing kdelibs5-plugins (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on libkhtml5 (>= 4:4.3.4); however:
  Package libkhtml5 is not configured yet.
 kde-runtime depends on kdelibs5-plugins (>= 4:4.11.2); however:
  Package kdelibs5-plugins is not configured yet.


dpkg: error processing kde-runtime (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on kde-runtime; however:
  Package kde-runtime is not configured yet.


dpkg: error processing kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkgapi2-2:amd64:
 libkgapi2-2:amd64 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.


dpkg: error processing libkgapi2-2:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on libgif4 (>= 4.1.4); however:
  Package libgif4:amd64 is not configured yet.


dpkg: error processing mplayer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of smplayer:
 smplayer depends on mplayer | mplayer-nogui | mplayer-mt | mplayer2; however:
  Package mplayer is not configured yet.
  Package mplayer-nogui is not installed.
  Package mplayer-mt is not installed.
  Package mplayer2 is not installed.


dpkg: error processing smplayer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgdiplus:
 libgdiplus depends on libgif4 (>= 4.1.4); however:
  Package libgif4:amd64 is not configured yet.


dpkg: error processing libgdiplus (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmono-system-drawing4.0-cil:
 libmono-system-drawing4.0-cil depends on libgdiplus (>= 2.6.7); however:
  Package libgdiplus is not configured yet.


dpkg: error processing libmono-system-drawing4.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgtk2.0-cil:
 libgtk2.0-cil depends on libmono-system-drawing4.0-cil (>= 1.0); however:
  Package libmono-system-drawing4.0-cil is not configured yet.


dpkg: error processing libgtk2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgtk-sharp-beans-cil:
 libgtk-sharp-beans-cil depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.


dpkg: error processing libgtk-sharp-beans-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libnotify0.4-cil:
 libnotify0.4-cil depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.


dpkg: error processing libnotify0.4-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of banshee:
 banshee depends on libgtk-sharp-beans-cil; however:
  Package libgtk-sharp-beans-cil is not configured yet.
 banshee depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.
 banshee depends on libnotify0.4-cil (>= 0.4.0~r2998); however:
  Package libnotify0.4-cil is not configured yet.


dpkg: error processing banshee (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of banshee-extensions-common:
 banshee-extensions-common depends on banshee (>= 2.6.1); however:
  Package banshee is not configured yet.


dpkg: error processing banshee-extensions-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of banshee-extension-albumartwriter:
 banshee-extension-albumartwriter depends on banshee-extensions-common (= 2.4.0-2ubuntu1); however:
  Package banshee-extensions-common is not configured yet.
 banshee-extension-albumartwriter depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.
 banshee-extension-albumartwriter depends on libmono-system-drawing4.0-cil (>= 1.0); however:
  Package libmono-system-drawing4.0-cil is not configured yet.


dpkg: error processing banshee-extension-albumartwriter (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of banshee-extension-coverwallpaper:
 banshee-extension-coverwallpaper depends on banshee-extensions-common (= 2.4.0-2ubuntu1); however:
  Package banshee-extensions-common is not configured yet.
 banshee-extension-coverwallpaper depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.


dpkg: error processing banshee-extension-coverwallpaper (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of banshee-extension-lyrics:
 banshee-extension-lyrics depends on banshee-extensions-common (= 2.4.0-2ubuntu1); however:
  Package banshee-extensions-common is not configured yet.
 banshee-extension-lyrics depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.


dpkg: error processing banshee-extension-lyrics (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of banshee-extension-soundmenu:
 banshee-extension-soundmenu depends on banshee (>= 2.6.1); however:
  Package banshee is not configured yet.
 banshee-extension-soundmenu depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.
 banshee-extension-soundmenu depends on libnotify0.4-cil (>= 0.4.0~r2998); however:
  Package libnotify0.4-cil is not configured yet.


dpkg: error processing banshee-extension-soundmenu (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of simplyhtml:
 simplyhtml depends on openjdk-6-jre | openjdk-7-jre | java2-runtime; however:
  Package openjdk-6-jre is not installed.
  Package openjdk-7-jre:amd64 is not configured yet.
  Package java2-runtime is not installed.
  Package default-jre which provides java2-runtime is not configured yet.
  Package openjdk-7-jre:amd64 which provides java2-runtime is not configured yet.


dpkg: error processing simplyhtml (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of freemind:
 freemind depends on default-jre | sun-java6-jre; however:
  Package default-jre is not configured yet.
  Package sun-java6-jre is not installed.
 freemind depends on simplyhtml (>> 0.13); however:
  Package simplyhtml is not configured yet.


dpkg: error processing freemind (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of javahelp2:
 javahelp2 depends on default-jre | java2-runtime; however:
  Package default-jre is not configured yet.
  Package java2-runtime is not installed.
  Package default-jre which provides java2-runtime is not configured yet.
  Package openjdk-7-jre:amd64 which provides java2-runtime is not configured yet.


dpkg: error processing javahelp2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-kde4:
 python-kde4 depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 python-kde4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.
 python-kde4 depends on libkhtml5 (>= 4:4.11.1); however:
  Package libkhtml5 is not configured yet.


dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde-config-touchpad:
 kde-config-touchpad depends on python-kde4 (>= 4:4.5); however:
  Package python-kde4 is not configured yet.


dpkg: error processing kde-config-touchpad (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qapt-batch:
 qapt-batch depends on kde-runtime; however:
  Package kde-runtime is not configured yet.


dpkg: error processing qapt-batch (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kubuntu-debug-installer:
 kubuntu-debug-installer depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kubuntu-debug-installer depends on qapt-batch; however:
  Package qapt-batch is not configured yet.


dpkg: error processing kubuntu-debug-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of smplayer-themes:
 smplayer-themes depends on smplayer; however:
  Package smplayer is not configured yet.


dpkg: error processing smplayer-themes (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of smplayer-skins:
 smplayer-skins depends on smplayer; however:
  Package smplayer is not configured yet.


dpkg: error processing smplayer-skins (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of smtube:
 smtube depends on smplayer (>= 0.7.0) | mplayer | vlc | dragonplayer | totem | gnome-mplayer; however:
  Package smplayer is not configured yet.
  Package mplayer is not configured yet.
  Package vlc is not installed.
  Package dragonplayer is not installed.
  Package totem is not installed.
  Package gnome-mplayer is not installed.


dpkg: error processing smtube (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up subdownloader (2.0.14-1.1) ...
dpkg: dependency problems prevent configuration of libatk-wrapper-java:
 libatk-wrapper-java depends on default-jre | java2-runtime; however:
  Package default-jre is not configured yet.
  Package java2-runtime is not installed.
  Package default-jre which provides java2-runtime is not configured yet.
  Package openjdk-7-jre:amd64 which provides java2-runtime is not configured yet.


dpkg: error processing libatk-wrapper-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatk-wrapper-java-jni:amd64:
 libatk-wrapper-java-jni:amd64 depends on default-jre | java2-runtime; however:
  Package default-jre is not configured yet.
  Package java2-runtime is not installed.
  Package default-jre which provides java2-runtime is not configured yet.
  Package openjdk-7-jre:amd64 which provides java2-runtime is not configured yet.
 libatk-wrapper-java-jni:amd64 depends on libatk-wrapper-java (>= 0.30.4-0ubuntu4); however:
  Package libatk-wrappNo apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                er-java is not configured yet.


dpkg: error processing libatk-wrapper-java-jni:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkolab0:
 libkolab0 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.


dpkg: error processing libkolab0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkfbapi1:
 libkfbapi1 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.


dpkg: error processing libkfbapi1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgif4:amd64
 openjdk-7-jre:amd64
 default-jre
 libkhtml5
 kdelibs5-plugins
 kde-runtime
 kdepim-runtime
 libkgapi2-2:amd64
 mplayer
 smplayer
 libgdiplus
 libmono-system-drawing4.0-cil
 libgtk2.0-cil
 libgtk-sharp-beans-cil
 libnotify0.4-cil
 banshee
 banshee-extensions-common
 banshee-extension-albumartwriter
 banshee-extension-coverwallpaper
 banshee-extension-lyrics
 banshee-extension-soundmenu
 simplyhtml
 freemind
 javahelp2
 python-kde4
 kde-config-touchpad
 qapt-batch
 kubuntu-debug-installer
 smplayer-themes
 smplayer-skins
 smtube
 libatk-wrapper-java
 libatk-wrapper-java-jni:amd64
 libkolab0
 libkfbapi1
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by ian-weisser on 2013-12-12
> **laigdotcom said:**
> ```

dpkg: error processing libgif4:amd64 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
```

Let's try fixing it the easy way first:
```
sudo apt-get install --reinstall libgif4:amd64
```

---

