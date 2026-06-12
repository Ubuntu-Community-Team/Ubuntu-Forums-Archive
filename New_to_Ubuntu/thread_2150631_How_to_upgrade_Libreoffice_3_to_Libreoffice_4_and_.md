---
title: "How to upgrade Libreoffice 3 to Libreoffice 4 and to have access to my external disk"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by PedroPV on 2013-06-01
I have just instaled Ubuntu paralel to my Windows 7 laptop and do not know how to:
(a) upgrade Libreoffice 3 to Libreoffice 4
(b) import writer files from the Windos side of my computer
(c) import files from my backup externel drive
(d) open my personal email acounts

Will I have to lose everything I have in Windows 7 partition? So far, I have only been able to import files through Drobox.

---

### Post by Buntu Bunny on 2013-06-02
> **PedroPV said:**
> I have just instaled Ubuntu paralel to my Windows 7 laptop and do not know how to:
(a) upgrade Libreoffice 3 to Libreoffice 4
<snip> .... .

This may help with the upgrade part - [http://www.ubuntukiller.com/2013/04/libreoffice-402-release-how-to-install.html]("http://www.ubuntukiller.com/2013/04/libreoffice-402-release-how-to-install.html")

---

### Post by Hekabe on 2013-06-02
> **PedroPV said:**
> I have just instaled Ubuntu paralel to my Windows 7 laptop and do not know how to:
(b) import writer files from the Windos side of my computer

Do you know what filesystem type your windows partition is? It could be exfat, which means you'll need to install exfat-utils for it to be accessible to Ubuntu.

---

### Post by NikTh on 2013-06-02
> **Buntu Bunny said:**
> This may help with the upgrade part - [http://www.ubuntukiller.com/2013/04/libreoffice-402-release-how-to-install.html](http://www.ubuntukiller.com/2013/04/libreoffice-402-release-how-to-install.html)

If the libreoffice is pre-installed , 3.x version.. then a ```
sudo apt-get dist-upgrade
``` is enough to upgrade the current version to 4.x 

[http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4](http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4)


LibreOffice is pre-installed in Ubuntu (vanilla). If I remember correctly is not pre-installed in some flavors.. (Lubuntu - Xubuntu... )

------------------------------------------------------------------

As for the external disk, plug the disk into the PC and then open a terminal (CTRL+ALT+T) and post back here the results of 

```
sudo fdisk -l 
sudo parted -l
```

---

### Post by ShadowVegan on 2013-06-02
To import files from Windows, you should be able to mount the Windows partition within Ubuntu, then navigate to whatever directory they are stored in. I believe you can mount it from 'Places' but it's been a while since I dual partitioned so I'm not positive.

To import files from your external HDD you should be able to just plug it in and copy them to whatever device you want them on, is the external HDD not registering when you plug it in?

To open your email accounts, do you want to do so through a web browser or a client? Through a web browser it's the same in any operating system, just go to the website and login. If you want to use a client, I recommend Mozilla Thunderbird which should be pre-installed.

---

### Post by gifford on 2013-06-02
For the upgrade part and to make sure things work correctly with Libreoffice do this:
sudo apt-get purge libreoffice*
sudo add- apt-repository ppa: libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice
This ppa will give you libreoffice 4.0X and give you the updates as well.

---

