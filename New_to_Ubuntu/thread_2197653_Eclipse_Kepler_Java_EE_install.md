---
title: "Eclipse Kepler Java EE install"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by guy.dillen on 2014-01-04
I have one last question for the moment. Just to be sure, is the following procedure correct for installing Eclipse Kepler Java EE. Thanks.

[COLOR=#333333][FONT=UbuntuRegular]Download Eclipse from their [www.eclipse.org](www.eclipse.org)[/FONT][/COLOR]

[LIST=1]
[*]Extract the eclipse.XX.YY.tar.gz using
tar -zxvf eclipse.XX.YY.tar.gz

[*]Become root.
sudo -i

[*]Copy the extracted folder to /opt
cp -r eclipse.XX.YY /opt

[*]Create a desktop file and install it:
gedit eclipse.desktop
and copy the following to the eclipse.desktop file.
[Desktop Entry]
Name=Eclipse 
Type=Application
Exec=eclipse
Terminal=false
Icon=eclipse
Comment=Integrated Development Environment
NoDisplay=false
Categories=Development;IDE;
Name[en]=Eclipse
then execute the following command to automatically install it in the unity:
desktop-file-install eclipse.desktop

[*]Create a symlink in /usr/local/bin using
cd /usr/local/bin
ln -s /opt/eclipse/eclipse

[*]For eclipse icon to be displayed in dash, eclipse icon can be added as
cp /opt/eclipse/icon.xpm /usr/share/pixmaps/eclipse.xpm 
[/LIST]

---

### Post by sandyd on 2014-01-04
> **guy.dillen said:**
> I have one last question for the moment. Just to be sure, is the following procedure correct for installing Eclipse Kepler Java EE. Thanks.

[COLOR=#333333][FONT=UbuntuRegular]Download Eclipse from their [www.eclipse.org](www.eclipse.org)[/FONT][/COLOR]

[LIST=1]
[*]Extract the eclipse.XX.YY.tar.gz using
tar -zxvf eclipse.XX.YY.tar.gz

[*]Become root.
sudo -i

[*]Copy the extracted folder to /opt
cp -r eclipse.XX.YY /opt

[*]Create a desktop file and install it:
gedit eclipse.desktop
and copy the following to the eclipse.desktop file.
[Desktop Entry]
Name=Eclipse 
Type=Application
Exec=eclipse
Terminal=false
Icon=eclipse
Comment=Integrated Development Environment
NoDisplay=false
Categories=Development;IDE;
Name[en]=Eclipse
then execute the following command to automatically install it in the unity:
desktop-file-install eclipse.desktop

[*]Create a symlink in /usr/local/bin using
cd /usr/local/bin
ln -s /opt/eclipse/eclipse

[*]For eclipse icon to be displayed in dash, eclipse icon can be added as
cp /opt/eclipse/icon.xpm /usr/share/pixmaps/eclipse.xpm 
[/LIST]

Eclipse is already avaliable in the software center - when eclipse is installed, you can configure additional repositories in eclipse to get additional functionality

---

