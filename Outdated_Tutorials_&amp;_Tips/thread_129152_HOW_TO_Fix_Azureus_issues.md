---
title: "HOW TO: Fix Azureus issues"
date: 2006-02-13
forum: Outdated Tutorials &amp; Tips
---

### Post by newuser111 on 2006-02-13
if you have been having issues with Azureus try this, I had azureus installed from the repositories, from one of the ones in the Ubuntu sources generator

but I've had constant problems with it, updates not installing, torrent files not downloading, etc.  When running as root even then the updates didnt apply properly

Heres what to do, uninstall Azureus completely then reinstall the latest from the azureus website it to a folder with user permissions, Azureus doesn't work well if set with root permissions, and it can auto update, so updates from repos are not needed


step 1. Uninstall azureus from repos or delete wherever you installed it if not as a deb file

step 2. Download latest azureus from website [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)
download the file Azureus_2.4.0.0_linux.tar.bz2 to a location of your chosing

step 3.  Copy Azureus.  **sudo cp Azureus_2.4.0.0_linux.tar.bz2 /opt/** or your location of chosing, this can be in your /home/user directory if you like, but this may be a problem if you have multiple users


step 3. change to /opt/ with **cd /opt/**


step 4. Unpack azureus. **sudo tar -xvjf Azureus_2.4.0.0_linux.tar.bz2** it will create a folder called azureus

step 5. Change permissions of folder to user.  **sudo chown -R user:user /opt/azureus** user must be substituted for your user name

step 6. the launch location for azureus is /opt/azureus/azureus, you can run it from the /opt/azureus directory from terminal by typing ./azureus its a good idea to update your menus to add the location for azureus, use smeg/alacarte for gnome

---

### Post by siorai on 2006-02-17
Thank you. This worked perfectly. :D

---

### Post by no1wantdthisname on 2006-02-17
Yeah I've had the torrents not downloading problem.  It has to do with torrents with spaces in the filename.  Azureus requires the full file path to the file as well.  
I wanted azureus to work for any user and leave it root owned though.  Here's how I fixed it.  

Get from [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/) and unpack into /opt/
I wouldn't use azureus deb files.  They seem to install the free java version, and those cause all kinds of problems with azureus.  It's better to just use the sun version.
Then: 

```
sudo gedit /usr/local/bin/azureus
```
and then paste the following:
```
#!/bin/sh

if [ "$1" != "" ]
 then
        /opt/azureus/azureus "$1"
 else
        /opt/azureus/azureus
fi
```

```
sudo chmod +x /usr/local/bin/azureus
```
Auto-update still doesn't work, so I just rm /opt/azureus and replace it with any new version when they come out.

---

