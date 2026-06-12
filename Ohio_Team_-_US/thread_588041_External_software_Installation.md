---
title: "External software Installation"
date: 2007-10-23
forum: Ohio Team - US
---

### Post by qureshia49 on 2007-10-23
Hello everyone,

I am a newbie from Cincinnati, OH, and just switched from Vista to Linux Ubuntu. Can someone help me in providing information as how to install external software e.g Adobe products, Inter-Video, Macromedia, etc., etc. I double click on the downloaded file which is in bin or non-exe format. Also how can I have my other hard drives in the Ubuntu's "explorer. The only data I see is that under my "/" partition.
Would appreciate a respond with possible solutions.

Thank you.

Ash

---

### Post by js_fr on 2007-10-23
To install external software there are several ways, depending on how the software is provided.
[LIST]
[*] first check if the software is not already in the Ubuntu / universe / multiverse repositories (see [here]("https://help.ubuntu.com/community/Repositories/Ubuntu") how to enable the universe / multiverse repositories). Then you can easily install it with Synaptic.
[*]The software has it's own repository. Then add the link to the repository to the file /etc/apt/sources.list, type (in a terminal): ```
sudo apt-get update
``` Then you are able to install the software with synaptic. More details [here]("https://help.ubuntu.com/community/Repositories")
 [*]The software comes as .deb file. Then go to the directory where you downloaded the deb file and install it with```
sudo dpkg -i [name of your deb file]
```
[*]You have to compile the software from source. 
[/LIST] 
A general introduction on installing software you can find [here]("https://help.ubuntu.com/community/InstallingSoftware")
Acrobat Reader you can get as .deb package ... but Ubuntu already comes with a free PDF reader. Macromedia (Flash?) should be in the multiverse repository: [https://help.ubuntu.com/community/RestrictedFormats/Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash")

> Also how can I have my other hard drives in the Ubuntu's "explorer. The only data I see is that under my "/" partition.
In Linux there are no drive letters like in Windows, everything is under "/". To get a list of all your mounted drives and the place where they are mounted type (in a terminal):
```
sudo mount -l
``` 
You can manually mount new drives with the "mount" command and unmound them with "umount". If you want to mount them every time you boot you'll have to add a line to /etc/fstab. A good intoduction on mount is here:  [https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount")
If you connect a removable device (e.g. an USB drive) it should be mounted automatically and you get a link to it on your desktop and in your file browser.

---

### Post by qureshia49 on 2007-10-23
Thanks so very much** js_fr**. You provided links that answers most of my question. I will post again should I need assistance. Again, many many thanks.


Ash

---

### Post by qureshia49 on 2007-10-24
Hi js_fr ...:)

The link you gave me above is for Ubuntu 6.xx. I have installed 7.10 and they are different. But I still tried to follow but I still don't understand how can I install products like Macromedia Dreamweaver, Adobe Photoshop, Corel Draw X, etc., etc. If you or someone could guide me I would be very grateful.

Thanks.

Ash

---

### Post by Cybergod on 2007-10-24
You might want to research this site [http://winehq.org/]("http://winehq.org/") because you are wanting to install Microsoft Windows Software.

There are alternatives.  You might even try searching Google :)

Give GIMP and Kompozer a try.

---

### Post by kngcrntrd on 2007-10-31
You may also want to try Automatix2.  Go to [HTML] http://getautomatix.com[/HTML] to check it out.  Also, you want to look for files with the ".deb" extension.  Ubuntu is Debian, and you can just double-click a .deb file to install it.

---

### Post by Vorian on 2007-11-01
It's probably best not to use Automatix.  A technical analysis from a Debian/Ubuntu developer can be found at [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by lyceum on 2007-11-02
> **qureshia49 said:**
> Hi js_fr ...:)

The link you gave me above is for Ubuntu 6.xx. I have installed 7.10 and they are different. But I still tried to follow but I still don't understand how can I install products like Macromedia Dreamweaver, Adobe Photoshop, Corel Draw X, etc., etc. If you or someone could guide me I would be very grateful.

Thanks.

Ash

Not everything that works on Windows will work on any Linux distro, including Ubuntu. I have not been able to get Studio 8 running at all. WINE will work with somethings, but not all. You can also try CrossOver Linux

[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

It has a nice grafical interface, but still did not work for me for Studio 8. If you were thinking CS3, forget it. Sorry, Adobe does not play well with Linux, by their own choice. 

As for Automatix, anything you want to do with it you can do with sudo apt-get or Synaptic Package Manager. Check out the links in my signature. There's some great info there for new users.

---

