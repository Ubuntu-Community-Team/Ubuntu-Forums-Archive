---
title: "All Video Down loader not installed properly.. Getting errors"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by Siva_Krishna_K on 2013-11-29
Hi,

I have downloaded All Video Down loader "allvideodownloader.i386.deb" from vendor site "http://www.kastorsoft.com/index_en.php".
Download was successful and i could able to see file saved at my "Desktop" (I have configured my desktop as download location)

When i am trying to install above file from terminal by using command "sudo dpkg -i allvideodownloader.i386.deb" i am getting below errors:

Selecting previously unselected package allvideodownloader.
(Reading database ... 194667 files and directories currently installed.)
Unpacking allvideodownloader (from allvideodownloader.i386.deb) ...
dpkg: dependency problems prevent configuration of allvideodownloader:
 allvideodownloader depends on libcurl3.
 allvideodownloader depends on libqt4-gui.


dpkg: error processing allvideodownloader (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Errors were encountered while processing:
 allvideodownloader

I tried to reconfigure by using command "sudo dpkg-reconfigure allvideodownloader" but nothing works for me.

also i have removed and re installed the same but no luck.

Please help on this issue..


Thanks and Regards
Siva

---

### Post by fantab on 2013-11-29
> allvideodownloader depends on **libcurl3**.
 allvideodownloader depends on **libqt4-gui**.

Have you considered installing the above two dependencies first? Try again after installing the above dependencies.

---

### Post by vasa1 on 2013-11-30
Can't a .deb also be installed using the Software Center? Won't that take care of dependencies? Just asking because I don't usually install .debs from "elsewhere".

IIRC, right-clicking on a .deb should offer an option of installing via the Software Center.

---

### Post by fantab on 2013-11-30
> **vasa1 said:**
> Can't a .deb also be installed using the Software Center? Won't that take care of dependencies? Just asking because I don't usually install .debs from "elsewhere".

IIRC, **right-clicking on a .deb should offer an option of installing via the Software Center**.

It should and it does I think... I install one particular software directly  from a .deb but it does not need any additional dependencies in Ubuntu.

Double cliks on .deb file will open the package with 'Software Center' and you can install it from 'Install' button.

---

### Post by vasa1 on 2013-11-30
Couple of other points ...

I'd be very careful about installing software from anywhere else other than the software center.

I don't see why you need to install this particular software at all.

By discussing this software we *may* be on thin ice because [this forum is quite strict about copyright]("http://ubuntuforums.org/showthread.php?t=1850955").

---

### Post by Siva_Krishna_K on 2013-11-30
Vasa1 and Fantab: Thank you guys for your help.. Software Update center does the job for me.. i have installed software with dependencies installed by Software Center by itself.

-Siva

---

### Post by sauravgoswami on 2014-01-10
follow these steps -
1. dpkg -i <your package > 
2. apt-get -f install 

it's easy one.

---

