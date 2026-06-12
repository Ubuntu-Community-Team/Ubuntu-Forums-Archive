---
title: "PNG Icons not displaying on Pop OS and other distros"
date: 2024-10-31
forum: Packaging and Compiling Programs
---

### Post by oliver-gerber on 2024-10-31
Hello There :)

I've looked at so many places now and can't figure this out. I'm having a rather strange problem with my new apps icons. The deb package i created via dpkg-deb seems to put the icons at the correct location as far as I know, but somehow they do not get displayed anywhere. Neither on the desktop nor the app-launcher (however it's called) and the dock. It's just completely invisible. I tried it in VMs like Mint, Ubuntu, Pop OS, Ubuntu Studio. Ubuntu Studio is actually the only distro that displays the icons correctly everywhere and also let's me put it onto the "taskbar". On my local Pop OS actually at the moment it shows in the app launcher window, but not in the dock and also not on the desktop. I get the cog wheel icon instead. On the dock I also cannot add it to favorites so it sticks to the dock. On Mint it shows in the "startmenu" but not on the taskbar, if i right click the startmenu icon and click on "add to desktop", the desktop icon shows fine.  Not sure if i can pin it there. So it's a little weird to be honest and everywhere a little different. After installing the deb file I have the following files and file contents:

/usr/local/bin/PickyColors
/usr/share/applications/digital.sector7.PickyColors.desktop
/usr/share/icons/hicolor/512x512/apps/digital.sector7.PickyColors.png
/usr/share/icons/hicolor/64x64/apps/digital.sector7.PickyColors.png
/usr/share/icons/hicolor/16x16/apps/digital.sector7.PickyColors.png
/usr/share/icons/hicolor/128x128/apps/digital.sector7.PickyColors.png
/usr/share/icons/hicolor/32x32/apps/digital.sector7.PickyColors.png
/usr/share/icons/hicolor/256x256/apps/digital.sector7.PickyColors.png
*(I saw there are actually far more resolution folders, so i added them without any consequences)*

$ cat /usr/share/applications/digital.sector7.PickyColors.desktop
[Desktop Entry]
Version=1.0
Type=Application
Name=PickyColors
Exec=/usr/local/bin/PickyColors
Icon=digital.sector7.PickyColors
Categories=Graphics;Utility;

$ ls -la /usr/local/bin/PickyColors 
-rwxr-xr-x 1 sector7 sector7 86576864 Oct 29 17:26 /usr/local/bin/PickyColors

I can open up all pngs via file manager without problem and they display correctly. As said, Ubuntu Studio displays them all correctly from the start. Can anyone see what I'm doing wrong here?

Edit: What I also just noticed. If I right click the icon in the app launcher and select "Pin to dash" then it actually puts the shortcut onto the dock with the icon being displayed. When i click it, the app pops up, but shows itself as a separate app-icon on the dock without my icon but the cogwheel-document icon. So somehow the app launches, but isn't the app that the .desktop file refers to anymore? Does that make sense? It's a python/pyside6 app of which i made a one-file executable with pyInstaller, maybe that's important...

Thanks a lot for your help...

All the best,
Oli

---

