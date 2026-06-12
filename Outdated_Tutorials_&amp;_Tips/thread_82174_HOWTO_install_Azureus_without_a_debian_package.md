---
title: "HOWTO install Azureus without a debian package"
date: 2005-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by celticmonkey on 2005-10-26
Installing things without apt-get lacks elegance, but here's how for Azureus:

You need Java installed for Azureus to work. Here a good HOWTO on that:
[http://www.ubuntuforums.org/showthread.php?t=76735](http://www.ubuntuforums.org/showthread.php?t=76735)

Next download azureus GTK from sourceforge and put it somewhere where users can access it:

```
wget -c http://internap.dl.sourceforge.net/sourceforge/azureus/Azureus_2.3.0.4_linux.GTK.tar.bz2
sudo tar jxvf Azureus_2.3.0.4_linux.GTK.tar.bz2 -C /opt/
sudo chown -R root:root /opt/azureus
sudo chmod -R a+wrx /opt/azureus
```

Next make a link so you can start it:

```
sudo gedit /usr/bin/azureus.sh

# Insert the following lines into the new file
cd /opt/azureus/
./azureus

# Save the edited file

sudo chmod +x /usr/bin/azureus.sh
```

Lastly, add it to you gnome-panel menu:
```

sudo gedit /usr/share/applications/azureus.desktop

# Insert the following lines into the new file

[Desktop Entry]
Name=Azureus
Comment=Azureus
Exec=azureus.sh
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;
```

To refresh the gnome-panel type:
```
killall gnome-panel
```

And there you go.

---

### Post by Pablo_Escobar on 2005-10-26
My simple question is :
Why do You put Azureus int opt directory, my gtk version is nicely placed in my home directory, no need for root work, no troubles with chmod, no messing with root-owned directories.
It work flawlessly, and I was wondering what are the bright sides of puting it into /opt/ directory ??

---

### Post by wellery on 2005-10-26
[quote=Pablo_Escobar]My simple question is :
Why do You put Azureus int opt directory, my gtk version is nicely placed in my home directory, no need for root work, no troubles with chmod, no messing with root-owned directories.
It work flawlessly, and I was wondering what are the bright sides of puting it into /opt/ directory ??[/quote]

Your solution will work fine for you if you are the only user, but then if another user wanted Azureus then they would also have to install it in their home directory. If 5 users want it then that's 5 installations. if it's in the /opt/ directory then all users can use it and their configuration is stored in .Azureus in their home directory.

---

### Post by Pablo_Escobar on 2005-10-26
[QUOTE=wellery]Your solution will work fine for you if you are the only user, but then if another user wanted Azureus then they would also have to install it in their home directory. If 5 users want it then that's 5 installations. if it's in the /opt/ directory then all users can use it and their configuration is stored in .Azureus in their home directory.[/QUOTE]

Didn't though about it, yep being the only user on the box can alter Your way of thinking :) Thanks for clearing that up :)

---

