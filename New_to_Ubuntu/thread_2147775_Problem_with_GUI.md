---
title: "Problem with GUI"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by Banshee159 on 2013-05-23
Hello brainiacsSo i installed vlc media player and synaptic package manager form the software centre. After that i saw that a popup on the top right side which said that restricted drivers were available for my GPU. I saw that an experimental unstable version is activated. So i started downloading the recommended version. But my dad had some urgent work in windows 8 so i pressed the cancel button about 10 times but still the Downloading and installing window did not close. After the download was done, i saw that a blue coloured reboot sign was next to the name of the driver but before restarting my pc i installed NVidia control panel by using these codes:sudo apt-add-repository ppa:ubuntu-x-swat/x-updatessudo apt-get updatesudo apt-get upgrade I opened the program and it worked properly and did not make any changes to the GPU settings. So i rebooted it but then the Ubuntu logo was replaced by a text saying "Ubuntu 12.04". After that a CLI(Like a full screen cmd window) welcomed me asking me for my login and password. No GUI :( . After entering the username and password inside the cmd window it said welcome to Ubuntu 12.04 followed by a message saying that "This software is free....." followed by "banshee@ubuntu:~$ "How to disable the drivers??How to get my GUI back??

---

### Post by galgalesh on 2013-05-23
You can try the startx command to start the GUI manually. However, you will have to do this every time, and if it really is a driver problem, startx will not work properly.

You can remove the drivers with ppa-purge. I think you first have to install ppa-purge

#install ppa-purge:
sudo apt-get install ppa-purge

#remove drivers:
sudo ppa-purge ppa:ubuntu-x-swat/x-updates

Let us know how it goes.

---

### Post by Banshee159 on 2013-05-23
@galgalesh: I tried startx but it gave me a big message: No screens found, Something that my driver version and GPU kernel version not same. I trien to install ppa-purge but it gave me an error. :(Help me

---

### Post by galgalesh on 2013-05-24
I can't help you unless you tell me what the error is you're getting.

---

