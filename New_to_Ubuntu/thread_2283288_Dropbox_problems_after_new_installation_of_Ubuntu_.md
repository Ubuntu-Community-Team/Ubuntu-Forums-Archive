---
title: "Dropbox problems after new installation of Ubuntu 14.04"
date: 2015-06-20
forum: New to Ubuntu
---

### Post by germanix on 2015-06-20
After re-installing Ubuntu 14.04 plus all of the updates, I proceeded to install Dropbox. This would not work in the software center, so I installed in the terminal with the following command:
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
I then started dropbox with the command:
~/.dropbox-dist/dropboxd
Dropbox then started. The dropbox icon appeared in the top panel only (not in the unity dock) and started to update my dropbox files. After the files were all updated, I could not exit the terminal by typing "exit". I had to use the "close button". As soon as I close the terminal, the dropbox icon disappears from the top panel.
I have dropbox set to start at start-up but this does not happen. The icon does not show up on the top panel nor in the dock. When I try to start dropbox by searching for it in applications and then clicking directly on the application icon, it does not start. The icon does not appear in the dock, nor in the panel. After waiting a few minutes a window appears asking for my linux id, saying I have to verify that dropbox needs to start. Even after I enter my ID nothing happens.
So the only way that I can start Dropbox at the moment is to start direct from the terminal, but the the terminal will will close down properly afterwards, and as soon as I do close it down, dropbox stops and does not update any new files!
If anyone can help me solve this problem I would be very gratefull.
I have now re-installed dropbox again and the problem is still there but this time I get the following error in the terminal:
IOError: [Errno 13] Permission denied: '/var/lib/dropbox/.dropbox-dist/dropbox-lnx.x86_64-3.6.7/futures-2.1.3-py2.7.egg/EGG-INFO/top_level.txt'

---

### Post by Frogs Hair on 2015-06-20
If you can remove the current installation of dropbox , try the following command. Edit: prior to installing nautilus-dropbox open the home folder and use Ctrl +H to display hidden folders and delete the .dropbox folder. A new one will be created when nautilus-dropbox is installed. Open dropbox from the icon in  dash.
 ```
sudo apt-get install nautilus-dropbox 
```

---

### Post by ptn107 on 2015-06-21
Dropbox should not have anything in /var/lib.  Everything should be under your home folder e.g. ~/.dropbox, and ~/.dropbox-dist.  nautilus-dropbox puts things in /var/lib but it just leads to permissions problems.  It is a horrible wrapper package.

You can install Dropbox directly from the website:
```
wget -c -t0 http://linux.dropbox.com/ubuntu/pool/main/dropbox_2015.02.12_amd64.deb
sudo dpkg -i dropbox_2015.02.12_amd64.deb; sudo apt-get -fy install
```

It then walks you through the config with your username and password.  Everything goes into your home folder.

---

### Post by germanix on 2015-06-21
Hi ptn 107, I used the code that you provided and it worked like a charm. I am now a happy man. Thank you very much for your help, and thank you too, Frogs Hair. Drop Box now seems to work fine, this however not on Unity 14.04, for some reason it would not install properly what ever I did. So I deleted that and installed Ubuntu Mate 15.04 and now Drop Box. Thank you all once again and have a good day.

---

