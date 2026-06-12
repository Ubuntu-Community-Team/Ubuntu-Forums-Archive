---
title: "How to set permissions for manually installed eclipse on Ubuntu 14.04"
date: 2014-08-21
forum: Programming Talk
---

### Post by Yongshin on 2014-08-21
I manually installed eclipse luna (actually e(fx)clipse AinO package) on my Ubuntu 14.04 based on these instuctions that I have found on the net:
> 

[LIST=1]
[*]Extract the eclipse.XX.YY.tar.gz using

  tar -zxvf eclipse.XX.YY.tar.gz

[*]Become root and Copy the extracted folder to /opt

  sudo mv eclipse.XX.YY /opt

[*]Create a desktop file and install it:

  gedit eclipse.desktop
  and copy the following to the eclipse.desktop file.
  [Desktop Entry]
Name=Eclipse 
Type=Application
Exec=env UBUNTU_MENUPROXY=0 eclipse44
Terminal=false
Icon=eclipse
Comment=Integrated Development Environment
NoDisplay=false
Categories=Development;IDE;
Name[en]=Eclipse
  then execute the following command to automatically install it in the unity:
  desktop-file-install eclipse.desktop

[*]Create a symlink in /usr/local/bin using
  ln -s /opt/eclipse/eclipse /usr/local/bin/eclipse44

[*]For eclipse icon to be displayed in dash, eclipse icon can be added as
  cp /opt/eclipse/icon.xpm /usr/share/pixmaps/eclipse.xpm

[*]Give eclipse the required permissions to modify the osgi file.
  sudo chown -R $USER:$USER /opt/eclipse/configuration/org.eclipse.osgi
[/LIST]


But I am not sure about #6 part. I guess $USER means the root, right?
And would this be enough for the eclipse installation? 
I've been asking this around on Eclipse forum, but seems nobody there knows|cares :(

(By the way I am a one-month-old new Ubuntu user, Nice to meet you all :) )

---

### Post by slickymaster on 2014-08-21
Hi Yongshin, welcome to the forums.
> **Yongshin said:**
> I manually installed eclipse luna (actually e(fx)clipse AinO package) on my Ubuntu 14.04 based on these instuctions that I have found on the net:


But I am not sure about #6 part. I guess $USER means the root, right?
No, $USER means your username.

This has to do with running Eclipse in a multi-user environment. Read this Eclipse [help section on multi-user installations]("http://help.eclipse.org/indigo/index.jsp?topic=/org.eclipse.platform.doc.isv/reference/misc/multi_user_installs.html").

In order to execute Eclipse as your user you'll have to take ownership on the whole directory by running ```
sudo chown -R $USER:$USER /opt/eclipse/configuration/org.eclipse.osgi
```

---

### Post by Yongshin on 2014-08-21
Thank you very much. My system is not on the multi-user environments and the folder is already in my account.
So I guess I'll just leave it where it is now.

Thanks, it really helpeeeeed :)

---

### Post by slickymaster on 2014-08-21
You're welcome.

---

