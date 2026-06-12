---
title: "Ubuntu 21.10. Want column listing my my user apps."
date: 2022-05-09
forum: New to Ubuntu
---

### Post by Advait on 2022-05-09
[COLOR=#000000][FONT=Arial]Newbie here. I&#8217;ve been using Ubuntu 21.10 for about 10 months. I don&#8217;t know bash, coding or admin. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I&#8217;d like to get a column listing of all my User Facing Apps (UFAs). [/FONT][/COLOR][COLOR=#000000][FONT=Arial]*This list would exclude all the many background Linux apps.*[/FONT][/COLOR][COLOR=#000000][FONT=Arial] The UFAs are just the apps that appear when I scroll thru my Gnome app icon screens. I want the three tab aligned columns to be [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Column 1. Name of app. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]2. deb, appimage, flatpak or snap? [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]3. Location.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Are there terminal commands that can create this list?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Just so there&#8217;s no confusion, I have about 116 User Facing Apps. I added up the number icons on my five Gnome app menu screens.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I want this list so in case my system crashes and I need to recreate it, I&#8217;ll have a list of all my UFAs.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Edit. I just read this: [/FONT][/COLOR][[COLOR=#1155cc][FONT=Arial][/FONT][/COLOR]]("https://ubuntuforums.org/announcement.php?f=326")[COLOR=#1155cc]_[https://ubuntuforums.org/announcement.php?f=326](https://ubuntuforums.org/announcement.php?f=326)_[/COLOR][COLOR=#000000][FONT=Arial] Ouch. Scary. If one of you mods thinks my request is too risky, then let me know and delete this post. Thanks. I'll make some full clones, just in case.[/FONT][/COLOR]

---

### Post by ActionParsnip on 2022-05-09
[https://docs.flatpak.org/en/latest/using-flatpak.html](https://docs.flatpak.org/en/latest/using-flatpak.html)
[https://www.howtogeek.com/660193/how-to-work-with-snap-packages-on-linux](https://www.howtogeek.com/660193/how-to-work-with-snap-packages-on-linux)
[https://itsfoss.com/use-appimage-linux/](https://itsfoss.com/use-appimage-linux/)

---

### Post by ActionParsnip on 2022-05-09
[https://communities.vmware.com/t5/VMware-Workstation-Pro/drag-and-drop-cache-in-Debian-linux-guest/td-p/466729](https://communities.vmware.com/t5/VMware-Workstation-Pro/drag-and-drop-cache-in-Debian-linux-guest/td-p/466729)

---

### Post by Advait on 2022-05-09
Thanks. I was aware of the commands for the different app types, that's helpful, but I'd like a listing of all my user apps in one list. 

I have a tiny understanding of how powerful bash (shell?) is so I'm hoping a bash (shell?) wiz knows how to make the column list I want, with all 4 app types. 

Of course, I could spend a few months (years?) learning bash (shell?). But, like most people, I'm overloaded with other commitments.

---

### Post by vanadium on 2022-05-09
This could be done with a script that greps the .desktop launchers. "Name=" will provide the first column, "Exec=" will provide the executable. With a "which <executable" command, you can retrieve the full path name if that is what you mean by "location". To know the source, anything under "/usr/share/applications" should be installed by APT, anything in "/var/lib/snapd/desktop/applications" should be installed by Snap, anything under "/var/lib/flatpak/exports/share/applications" has been placed there by flatpak, anything in "/usr/local/share/applications" and "~/.local/share/applications" has been put there by yourself or by a script, and can be anything, including your AppImages provided the AppImage or yourself has created a launcher for it, and you kept the extension "AppImage" on the file. Otherwise, there is no way to know whether you have appimages installed or not, leave alone where.

That script would not be too complicated, but still, a script is required unless someone knows of an existing script. I do not thus far. To make it more reflecting what you see in the application menu, it also would also need to filter out files where "NoDisplay" or "Hidden" is set True.

---

### Post by Advait on 2022-05-10
@vanadium This is helpful. I can hire someone from Upwork, show them what you wrote and it'll help them write the script for me. Thanks.

---

### Post by GhX6GZMB on 2022-05-10
A quick and dirty way would be to simply do an "ls" of /usr/share/applications and $HOME/.local/share/applications
It would look like this:
```
macro@macro-pc:/usr/share/applications$ ls -la
total 796
drwxr-xr-x   3 root root 12288 May 10 00:27 .
drwxr-xr-x 266 root root 12288 Apr 14 23:34 ..
-rw-r--r--   1 root root   324 Mar 22  2020 2048-qt.desktop
-rw-r--r--   1 root root   205 Jun  3  2018 avidemux2.7-jobs-qt5.desktop
-rw-r--r--   1 root root   306 Jun  3  2018 avidemux2.7-qt5.desktop
-rw-r--r--   1 root root   441 Oct 30  2019 backintime-qt.desktop
-rw-r--r--   1 root root   462 Oct 30  2019 backintime-qt-root.desktop
-rw-r--r--   1 root root  8563 May  3 02:15 brave-browser.desktop
-rw-r--r--   1 root root  2145 Mar  9  2019 compton-conf.desktop
-rw-r--r--   1 root root   243 Apr 30  2016 compton.desktop
-rw-r--r--   1 root root 15696 May  4 00:13 defaults.list
-rw-r--r--   1 root root   202 Jan  5  2020 fcitx-config-gtk3.desktop
-rw-r--r--   1 root root  1116 Jan  8  2020 fcitx-configtool.desktop
-rw-r--r--   1 root root  1006 Jan  8  2020 fcitx.desktop
-rw-r--r--   1 root root  1085 Jan  8  2020 fcitx-skin-installer.desktop
-rw-r--r--   1 root root  1140 Jan 11  2020 featherpad.desktop
-rw-r--r--   1 root root   303 Mar 19  2020 gcr-prompter.desktop
-rw-r--r--   1 root root   611 Mar 19  2020 gcr-viewer.desktop
-rw-r--r--   1 root root   227 Feb 28  2020 geoclue-demo-agent.desktop
-rw-r--r--   1 root root   669 Dec 24  2018 hardinfo.desktop
-rw-r--r--   1 root root   423 Jan 30  2020 hplj1020.desktop
-rw-r--r--   1 root root  2461 Dec  4  2019 htop.desktop
-rw-r--r--   1 root root  1034 Oct 28  2020 im-config.desktop
-rw-r--r--   1 root root   217 Oct 11  2019 info.desktop
-rw-r--r--   1 root root   493 Apr  3  2018 isomaster.desktop
-rw-r--r--   1 root root  1521 Mar  7  2020 ktelnetservice5.desktop
-rw-r--r--   1 root root  2384 Mar 23  2020 librecad.desktop
-rw-r--r--   1 root root 24993 Apr 27 15:11 libreoffice-base.desktop
-rw-r--r--   1 root root 22732 Apr 27 15:11 libreoffice-calc.desktop
-rw-r--r--   1 root root 19673 Apr 27 15:11 libreoffice-draw.desktop
-rw-r--r--   1 root root 22750 Apr 27 15:11 libreoffice-impress.desktop
-rw-r--r--   1 root root 18494 Apr 27 15:11 libreoffice-math.desktop
-rw-r--r--   1 root root 21598 Apr 27 15:11 libreoffice-startcenter.desktop
-rw-r--r--   1 root root 21564 Apr 27 15:11 libreoffice-writer.desktop
-rw-r--r--   1 root root  4732 Apr 27 15:11 libreoffice-xsltfilter.desktop
-rw-r--r--   1 root root  1742 Mar 22  2020 lximage-qt.desktop
-rw-r--r--   1 root root  1762 Mar 22  2020 lximage-qt-screenshot.desktop
-rw-r--r--   1 root root  1820 Mar 22  2020 lxqt-about.desktop
-rw-r--r--   1 root root  2546 Jan 27  2020 lxqt-admin-time.desktop
-rw-r--r--   1 root root  2780 Jan 27  2020 lxqt-admin-user.desktop
-rw-r--r--   1 root root  4828 Mar 30  2020 lxqt-config-appearance.desktop
-rw-r--r--   1 root root  1592 Mar 30  2020 lxqt-config-brightness.desktop
-rw-r--r--   1 root root  4502 Mar 30  2020 lxqt-config.desktop
-rw-r--r--   1 root root  3014 Mar 30  2020 lxqt-config-file-associations.desktop
-rw-r--r--   1 root root  3882 Mar 22  2020 lxqt-config-globalkeyshortcuts.desktop
-rw-r--r--   1 root root  2726 Mar 30  2020 lxqt-config-input.desktop
-rw-r--r--   1 root root  1590 Mar 30  2020 lxqt-config-locale.desktop
-rw-r--r--   1 root root  2149 Mar 30  2020 lxqt-config-monitor.desktop
-rw-r--r--   1 root root  5023 Mar 22  2020 lxqt-config-notificationd.desktop
-rw-r--r--   1 root root  3102 Feb 15  2020 lxqt-config-powermanagement.desktop
-rw-r--r--   1 root root  4909 Feb 15  2020 lxqt-config-session.desktop
-rw-r--r--   1 root root  1542 Feb 15  2020 lxqt-hibernate.desktop
-rw-r--r--   1 root root  1307 Feb 15  2020 lxqt-leave.desktop
-rw-r--r--   1 root root  1700 Feb 15  2020 lxqt-lockscreen.desktop
-rw-r--r--   1 root root  1608 Feb 15  2020 lxqt-logout.desktop
-rw-r--r--   1 root root  1565 Feb 15  2020 lxqt-reboot.desktop
-rw-r--r--   1 root root  1406 Feb 15  2020 lxqt-shutdown.desktop
-rw-r--r--   1 root root  1489 Feb 15  2020 lxqt-suspend.desktop
-rw-r--r--   1 root root 19692 May 10 00:27 mimeinfo.cache
-rw-r--r--   1 root root   350 Jul 29  2020 nm-applet.desktop
-rw-r--r--   1 root root   464 Jul 29  2020 nm-connection-editor.desktop
-rw-r--r--   1 root root   186 Mar 23  2020 nm-tray.desktop
-rw-r--r--   1 root root   175 Jun 18  2019 noblenote.desktop
-rw-r--r--   1 root root  2215 Mar  9  2019 obconf-qt.desktop
-rw-r--r--   1 root root   386 Mar 11  2021 openbox.desktop
-rw-r--r--   1 root root   394 Apr 23 15:02 openjdk-11-java.desktop
-rw-r--r--   1 root root  1492 Feb 11  2020 org.debian.galternatives.desktop
-rw-r--r--   1 root root  2234 Apr  3  2020 org.gnome.FontManager.desktop
-rw-r--r--   1 root root  2133 Apr  3  2020 org.gnome.FontViewer.desktop
-rw-r--r--   1 root root  6935 Aug 28  2020 org.kde.ark.desktop
-rw-r--r--   1 root root  5866 Apr  2  2020 org.kde.bluedevilsendfile.desktop
-rw-r--r--   1 root root  5303 Apr  2  2020 org.kde.bluedevilwizard.desktop
-rw-r--r--   1 root root 10024 Jan 31 08:39 org.kde.discover.apt.urlhandler.desktop
-rw-r--r--   1 root root 10124 Jan 31 08:39 org.kde.discover.desktop
-rw-r--r--   1 root root  1130 Jan 31 08:39 org.kde.discover.notifier.desktop
-rw-r--r--   1 root root 10031 Jan 31 08:39 org.kde.discover.urlhandler.desktop
-rw-r--r--   1 root root  6456 Aug 27  2020 org.kde.k3b.desktop
-rw-r--r--   1 root root  8726 Mar  1  2020 org.kde.kcalc.desktop
-rw-r--r--   1 root root  6699 Feb 29  2020 org.kde.keditbookmarks.desktop
-rw-r--r--   1 root root  2128 Mar 31  2020 org.kde.keditfiletype.desktop
-rw-r--r--   1 root root  7651 Jul 14  2021 org.kde.kolourpaint.desktop
-rw-r--r--   1 root root  8785 Mar 19  2018 org.kde.muon.desktop
-rw-r--r--   1 root root 10226 Feb  8  2020 org.kde.partitionmanager.desktop
-rw-r--r--   1 root root  4236 Apr  2  2020 org.kde.polkit-kde-authentication-agent-1.desktop
-rw-r--r--   1 root root  6420 Apr  1  2018 org.kde.skanlite.desktop
-rw-r--r--   1 root root  5922 May  4 09:55 org.kicad.bitmap2component.desktop
-rw-r--r--   1 root root  5102 May  4 09:55 org.kicad.eeschema.desktop
-rw-r--r--   1 root root  4050 May  4 09:55 org.kicad.gerbview.desktop
-rw-r--r--   1 root root  3193 May  4 09:55 org.kicad.kicad.desktop
-rw-r--r--   1 root root  3822 May  4 09:55 org.kicad.pcbcalculator.desktop
-rw-r--r--   1 root root  4719 May  4 09:55 org.kicad.pcbnew.desktop
-rw-r--r--   1 root root  1028 Feb  4  2020 org.octave.Octave.desktop
-rw-r--r--   1 root root  1241 Mar 22  2020 pavucontrol-qt.desktop
-rw-r--r--   1 root root  2805 Mar 22  2020 pcmanfm-qt.desktop
-rw-r--r--   1 root root  2760 Mar 22  2020 pcmanfm-qt-desktop-pref.desktop
-rw-r--r--   1 root root   220 Mar 15 13:22 python3.8.desktop
-rw-r--r--   1 root root  6799 Apr  1  2020 qapt-deb-installer.desktop
-rw-r--r--   1 root root  1346 Feb 26  2019 qlipper.desktop
-rw-r--r--   1 root root   653 Mar 23  2020 qpdfview.desktop
-rw-r--r--   1 root root  1214 Mar 23  2020 qps.desktop
-rw-r--r--   1 root root  2144 Feb 25  2019 qterminal.desktop
-rw-r--r--   1 root root  2670 Feb 25  2019 qterminal_drop.desktop
-rw-r--r--   1 root root   906 Mar 23  2020 qtpass.desktop
-rw-r--r--   1 root root  2689 Feb 15  2019 quassel.desktop
-rw-r--r--   1 root root  1267 Feb  8  2020 screengrab.desktop
drwxr-xr-x   2 root root 12288 Apr 23  2020 screensavers
-rw-r--r--   1 root root   353 Oct 26  2021 software-properties-drivers-lxqt.desktop
-rw-r--r--   1 root root   397 Oct 26  2021 software-properties-lxqt.desktop
-rw-r--r--   1 root root   385 Oct 26  2021 software-properties-qt.desktop
-rw-r--r--   1 root root   518 Nov  3  2020 system-config-printer.desktop
-rw-r--r--   1 root root  1089 Mar 15  2020 timeshift-gtk.desktop
-rw-r--r--   1 root root   448 May  1  2018 transmission-qt.desktop
-rw-r--r--   1 root root  3836 Mar 30  2020 trojita.desktop
-rw-r--r--   1 root root   304 Aug 23  2019 upg-apply.desktop
-rw-r--r--   1 root root   265 Jul  2  2019 usb-creator-kde.desktop
-rw-r--r--   1 root root  4790 Feb  1 10:16 vim.desktop
-rw-r--r--   1 root root 11183 Apr  9  2020 vlc.desktop
-rw-r--r--   1 root root   234 Jan 27  2019 xscreensaver-properties.desktop
```
```
macro@macro-pc:/home/abguest/.local/share/applications$ ls -latotal 656
drwxr-x---  3 abguest abguest  4096 Jun 25  2021 .
drwxrwx--- 11 abguest abguest  4096 Mar  5 23:11 ..
-rw-r-----  1 abguest abguest   324 Mar 22  2020 2048-qt.desktop
-rw-r--r--  1 abguest abguest   441 Oct 30  2019 backintime-qt.desktop
-rw-r--r--  1 abguest abguest   477 Jun 25  2021 backintime-qt-root.desktop
-rw-r-----  1 abguest abguest  2145 Mar  9  2019 compton-conf.desktop
-rw-r-----  1 abguest abguest   243 Apr 30  2016 compton.desktop
lrwxrwxrwx  1 abguest abguest    24 May  9  2020 defaults.list -> /etc/gnome/defaults.list
-rw-r-----  1 abguest abguest   202 Jan  5  2020 fcitx-config-gtk3.desktop
-rw-r-----  1 abguest abguest  1131 May 14  2020 fcitx-configtool.desktop
-rw-r-----  1 abguest abguest  1021 May 14  2020 fcitx.desktop
-rw-r-----  1 abguest abguest  1085 Jan  8  2020 fcitx-skin-installer.desktop
-rw-r-----  1 abguest abguest  1140 Jan 11  2020 featherpad.desktop
-rw-r-----  1 abguest abguest   303 Mar 19  2020 gcr-prompter.desktop
-rw-r-----  1 abguest abguest   611 Mar 19  2020 gcr-viewer.desktop
-rw-r-----  1 abguest abguest   227 Feb 28  2020 geoclue-demo-agent.desktop
-rw-r-----  1 abguest abguest   423 Jan 30  2020 hplj1020.desktop
-rw-r-----  1 abguest abguest  2476 May 13  2020 htop.desktop
-rw-r-----  1 abguest abguest  1055 May 14  2020 im-config.desktop
-rw-r-----  1 abguest abguest   217 Oct 11  2019 info.desktop
-rw-r-----  1 abguest abguest  1521 Mar  7  2020 ktelnetservice5.desktop
-rw-r-----  1 abguest abguest 22657 Apr 22  2020 libreoffice-calc.desktop
-rw-r-----  1 abguest abguest 19684 Apr 22  2020 libreoffice-draw.desktop
-rw-r-----  1 abguest abguest 22768 Apr 22  2020 libreoffice-impress.desktop
-rw-r-----  1 abguest abguest 18554 Apr 22  2020 libreoffice-math.desktop
-rw-r-----  1 abguest abguest 21358 May 13  2020 libreoffice-startcenter.desktop
-rw-r-----  1 abguest abguest 21353 Apr 22  2020 libreoffice-writer.desktop
-rw-r-----  1 abguest abguest  4709 Apr 22  2020 libreoffice-xsltfilter.desktop
-rw-r-----  1 abguest abguest  1742 Mar 22  2020 lximage-qt.desktop
-rw-r-----  1 abguest abguest  1762 Mar 22  2020 lximage-qt-screenshot.desktop
-rw-r-----  1 abguest abguest  1835 May 13  2020 lxqt-about.desktop
-rw-r-----  1 abguest abguest  2561 May 15  2020 lxqt-admin-time.desktop
-rw-r-----  1 abguest abguest  2795 May 14  2020 lxqt-admin-user.desktop
-rw-r-----  1 abguest abguest  4828 Mar 30  2020 lxqt-config-appearance.desktop
-rw-r-----  1 abguest abguest  1592 Mar 30  2020 lxqt-config-brightness.desktop
-rw-r-----  1 abguest abguest  4502 Mar 30  2020 lxqt-config.desktop
-rw-r-----  1 abguest abguest  3029 May 14  2020 lxqt-config-file-associations.desktop
-rw-r-----  1 abguest abguest  3897 Oct 31  2020 lxqt-config-globalkeyshortcuts.desktop
-rw-r-----  1 abguest abguest  2726 Mar 30  2020 lxqt-config-input.desktop
-rw-r-----  1 abguest abguest  1590 Mar 30  2020 lxqt-config-locale.desktop
-rw-r-----  1 abguest abguest  2149 Mar 30  2020 lxqt-config-monitor.desktop
-rw-r-----  1 abguest abguest  5023 Mar 22  2020 lxqt-config-notificationd.desktop
-rw-r-----  1 abguest abguest  3117 May 24  2020 lxqt-config-powermanagement.desktop
-rw-r-----  1 abguest abguest  4924 Oct 23  2020 lxqt-config-session.desktop
-rw-r-----  1 abguest abguest  1542 Feb 15  2020 lxqt-hibernate.desktop
-rw-r-----  1 abguest abguest  1322 May 13  2020 lxqt-leave.desktop
-rw-r-----  1 abguest abguest  1715 May 13  2020 lxqt-lockscreen.desktop
-rw-r-----  1 abguest abguest  1608 Feb 15  2020 lxqt-logout.desktop
-rw-r-----  1 abguest abguest  1565 Feb 15  2020 lxqt-reboot.desktop
-rw-r-----  1 abguest abguest  1406 Feb 15  2020 lxqt-shutdown.desktop
-rw-r-----  1 abguest abguest  1489 Feb 15  2020 lxqt-suspend.desktop
-rw-r-----  1 abguest abguest 17474 May  6  2020 mimeinfo.cache
-rw-r-----  1 abguest abguest   350 Feb  8  2020 nm-applet.desktop
-rw-r-----  1 abguest abguest   479 May 14  2020 nm-connection-editor.desktop
-rw-r-----  1 abguest abguest   186 Mar 23  2020 nm-tray.desktop
-rw-r-----  1 abguest abguest   175 Jun 18  2019 noblenote.desktop
-rw-r-----  1 abguest abguest  2215 Mar  9  2019 obconf-qt.desktop
-rw-r-----  1 abguest abguest   386 Mar 17  2020 openbox.desktop
-rw-r-----  1 abguest abguest   584 Apr 28  2020 opera.desktop
-rw-r-----  1 abguest abguest  1507 May 14  2020 org.debian.galternatives.desktop
-rw-r-----  1 abguest abguest  6935 Mar  5  2020 org.kde.ark.desktop
-rw-r-----  1 abguest abguest  5866 Apr  2  2020 org.kde.bluedevilsendfile.desktop
-rw-r-----  1 abguest abguest  5303 Apr  2  2020 org.kde.bluedevilwizard.desktop
-rw-r-----  1 abguest abguest  9763 Apr  2  2020 org.kde.discover.apt.urlhandler.desktop
-rw-r-----  1 abguest abguest  9863 Apr  2  2020 org.kde.discover.desktop
-rw-r-----  1 abguest abguest  1113 Apr  2  2020 org.kde.discover.notifier.desktop
-rw-r-----  1 abguest abguest  9770 Apr  2  2020 org.kde.discover.urlhandler.desktop
-rw-r-----  1 abguest abguest  6460 Mar  5  2020 org.kde.k3b.desktop
-rw-r-----  1 abguest abguest  8726 Mar  1  2020 org.kde.kcalc.desktop
-rw-r-----  1 abguest abguest  6699 Feb 29  2020 org.kde.keditbookmarks.desktop
-rw-r-----  1 abguest abguest  2128 Mar 31  2020 org.kde.keditfiletype.desktop
-rw-r-----  1 abguest abguest  7651 Mar  1  2020 org.kde.kolourpaint.desktop
-rw-r-----  1 abguest abguest  8800 May 13  2020 org.kde.muon.desktop
-rw-r-----  1 abguest abguest 10241 May 13  2020 org.kde.partitionmanager.desktop
-rw-r-----  1 abguest abguest  4236 Apr  2  2020 org.kde.polkit-kde-authentication-agent-1.desktop
-rw-r-----  1 abguest abguest  6420 Apr  1  2018 org.kde.skanlite.desktop
-rw-r-----  1 abguest abguest  1241 Mar 22  2020 pavucontrol-qt.desktop
-rw-r-----  1 abguest abguest  2805 Mar 22  2020 pcmanfm-qt.desktop
-rw-r-----  1 abguest abguest  2760 Mar 22  2020 pcmanfm-qt-desktop-pref.desktop
-rw-r-----  1 abguest abguest   220 Apr 27  2020 python3.8.desktop
-rw-r-----  1 abguest abguest  6799 Apr  1  2020 qapt-deb-installer.desktop
-rw-r-----  1 abguest abguest  1346 Feb 26  2019 qlipper.desktop
-rw-r-----  1 abguest abguest   653 Mar 23  2020 qpdfview.desktop
-rw-r-----  1 abguest abguest  1214 Mar 23  2020 qps.desktop
-rw-r-----  1 abguest abguest  2144 Feb 25  2019 qterminal.desktop
-rw-r-----  1 abguest abguest  2670 Feb 25  2019 qterminal_drop.desktop
-rw-r-----  1 abguest abguest   906 Mar 23  2020 qtpass.desktop
-rw-r-----  1 abguest abguest  2689 Feb 15  2019 quassel.desktop
-rw-r-----  1 abguest abguest  1267 Feb  8  2020 screengrab.desktop
drwxr-x---  2 abguest abguest 12288 May  9  2020 screensavers
-rw-r-----  1 abguest abguest   368 May 14  2020 software-properties-drivers-lxqt.desktop
-rw-r-----  1 abguest abguest   412 May 14  2020 software-properties-lxqt.desktop
-rw-r-----  1 abguest abguest   385 Apr 16  2020 software-properties-qt.desktop
-rw-r-----  1 abguest abguest   518 Feb 24  2020 system-config-printer.desktop
-rw-r-----  1 abguest abguest  1104 May 13  2020 timeshift-gtk.desktop
-rw-r-----  1 abguest abguest   448 May  1  2018 transmission-qt.desktop
-rw-r-----  1 abguest abguest  3836 Mar 30  2020 trojita.desktop
-rw-r-----  1 abguest abguest   319 May 14  2020 upg-apply.desktop
-rw-r-----  1 abguest abguest   265 Jul  2  2019 usb-creator-kde.desktop
-rw-r-----  1 abguest abguest  4790 Apr 15  2020 vim.desktop
-rw-r-----  1 abguest abguest 11183 Apr  9  2020 vlc.desktop
-rw-r-----  1 abguest abguest   234 May 15  2020 xscreensaver-properties.desktop

```

The .desktop files control the icons in your Application Menu and show the programs installed with a GUI. /usr/share/applications is for the main (sudo) user, the $HOME/... are for normal users.
There's no guarantee that this list is complete (but it's probable), and there's no guarantee that they're all active. That requires further filtering.

---

### Post by Advait on 2022-05-11
> **ml9104 said:**
> A quick and dirty way would be to simply do an "ls" of /usr/share/applications and $HOME/.local/share/applications. The .desktop files control the icons in your Application Menu and show the programs installed with a GUI. /usr/share/applications is for the main (sudo) user, the $HOME/... are for normal users. There's no guarantee that this list is complete (but it's probable), and there's no guarantee that they're all active. That requires further filtering.

Thanks. Very helpful. I'll hop on to Upwork and find someone who can create the script that meets my needs.

---

### Post by Advait on 2022-05-11
Is there a script that list all the apps that appear on the Gnome app icon display pages? I'm guessing that list is stored somewhere in the Gnome files. Any ideas? Does that list contain any other info besides just the name of the icon? Does it list the type of app? (deb, appimage, flatpak, snap).

About 116 items, in my case.

---

### Post by GhX6GZMB on 2022-05-11
There is no list.
Menu and desktop is built new by the OS at every login by scanning the .desktop files.

---

### Post by Advait on 2022-05-11
> **ml9104 said:**
> There is no list. Menu and desktop is built new by the OS at every login by scanning the .desktop files.

Ahhh... Very interesting. So the code that does the .desktop scanning is presumably open source. So presumably that code could be trivially copied out and modified so (at every login) it creates a file with the list. And, with a little more modification, adds a 2nd column to the list showing the app type (deb, appimage, flatpak, snap).

My Upwork hire should now have enough info to easily make the script.

By chance you know the particular code module that has the .desktop scanning code?

---

### Post by GhX6GZMB on 2022-05-11
No idea, but far too complicated IMO.
Just scan the .desktop file names as I showed you.

---

