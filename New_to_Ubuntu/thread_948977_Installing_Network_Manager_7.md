---
title: "Installing Network Manager 7"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by MissusCT on 2008-10-15
Hi all,

I'm completely new to all of this, I recently bought an Asus Eee PC, and a 3 Mobile Broadband Huawei USB modem. My Eee PC came with Linux, I didn't realise the two weren't compatible until it was too late :(

Nevertheless after researching on the net I found that with some tweaks I could get it working by installing Ubuntu, which I have, and now I apparently need to install/update to Network Manager 7. I've searched on these forums but the posts look quite complicated and I was wondering if anyone had a tutorial for the absolute noob? The terminal code is going completely over my head and I have no idea how I would even begin to edit files or upgrade.

Thank you for any help you can give me :)

:confused::confused::confused:

---

### Post by jbrown96 on 2008-10-15
There are two options: install the 8.10 beta or change your repositories. I don't have an eee, but I haven't had any problems with 8.10 beta. This would probably be the easiest way to go, but it is beta software. As a newbie, there may be problems that will keep bringing you back here. 

I would recommend updating your repositories. this will all be done in a terminal (Applications-->Accessories-->Terminal). Justin copy and paste these commands
1. Back up your sources. ```
sudo cp /etc/apt/sources.lst /etc/apt/sources.lst.back
``` If there is ever a problem with your sources you can restore them to the original settings by swapping the two files (sudo cp /etc/apt/sources.lst.back /etc/apt/sources.lst)
2. Edit your sources file to include the 8.10 repositories. If you are using Kubuntu, replaces gedit with kate. ```
sudo gedit /etc/apt/sources.lst
``` This will bring up a new window that is a text editor. find the following lines; they will be near the beginning. > deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted You need to change both of these lines. Change hardy to intrepid. Be sure that there are the same number of spaces and that the case is the same. It should now read: > deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted Save and exit gedit.
3. Update your sources ```
sudo apt-get update
```
4.  Close the terminal and open Synaptic (System-->Administration-->Synaptic) Search for network-manager. It should have a green square with a star on it. Left click and select upgrade. Then apply the changes. 
You may need to logout/restart for the changes to take effect
5. change your repositories back after successful installation. DO NOT RUN ANY UPDATES! ```
 sudo cp /etc/apt/sources.lst.back /etc/apt/sources.lst 
``` Then, update your repositories. ```
 sudo apt-get update 
```

---

### Post by Patrick793 on 2008-10-15
Actually, instead of installing the Intrepid version, install the version made for Hardy using the repositories from [this thread](http://ubuntuforums.org/showthread.php?t=797059)

```
gksudo gedit /etc/apt/sources.list
```

Add this to the end of the file.

```
## Network Manager 0.7
deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main
```

Finally, update.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jbrown96 on 2008-10-15
> **Patrick793 said:**
> Actually, instead of installing the Intrepid version, install the version made for Hardy using the repositories from [this thread](http://ubuntuforums.org/showthread.php?t=797059)

```
gksudo gedit /etc/apt/sources.list
```

Add this to the end of the file.

```
## Network Manager 0.7
deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main
```

Finally, update.

```
sudo apt-get update && sudo apt-get upgrade
```
+1 to this solution. You should probably remove this section after you install for security reasons. When you run the upgrade command, it will complain about installing unsigned packages. Someone could highjack this and cause a security breach if you leave them enabled.

---

### Post by MissusCT on 2008-10-15
Thank you for such a quick reply!

When I try to back up my sources it says:

cp: cannot stat '/etc/apt/sources.lst': No such file or directory

---

### Post by Patrick793 on 2008-10-15
It's sources.**list**, not sources.**lst**.

---

### Post by jbrown96 on 2008-10-15
> **Patrick793 said:**
> It's sources.**list**, not sources.**lst**.

Sorry my mistake. Too much tab completion.

---

### Post by MissusCT on 2008-10-15
Thank you guys so so so much! 

Had to go temporarily offline in order to install the updates, fingers crossed it worked :)

---

### Post by Plumtreed on 2008-10-25
Thanks everybody, I followed the suggestion about NetworkManager 0.7 for Hardy and everything goes really well! It slips easily from mobile broadband, wireless or wired....good stuff! The problem with GnomePPP and 'work-offline' in Firefox is also sorted.:)

---

### Post by piju on 2008-11-05
thanks for sharing.

---

