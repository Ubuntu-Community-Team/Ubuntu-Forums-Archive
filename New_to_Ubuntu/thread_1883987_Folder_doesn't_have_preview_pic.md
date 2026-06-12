---
title: "Folder doesn't have preview pic?"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by dixcuxx on 2011-11-20
In file explorer of Ubuntu, there is only pic preview for pic or video, but if there is pic/video in a folder, the folder wouldn't have preview pic on the folder icon like Windows. Anyway to solve this?

---

### Post by dixcuxx on 2011-11-20
seem like no one knows about this...

---

### Post by lswb on 2011-11-20
Don't know of a way for folders to automatically show a preview, but you can assign the icon or picture of your choice to the folder easily. Just right click, select properties, then click on the icon at the upper left. A file selection dialog will open and you can select any picture or stock icon file from anywhere in your system.

---

### Post by Frogs Hair on 2011-11-20
Gloobus Preview will display the items in folders by name but there are special instructions to make it work properly in 11.10 . [http://www.ubuntubuzz.com/2011/10/install-gloobus-preview-on-ubuntu-1110.html](http://www.ubuntubuzz.com/2011/10/install-gloobus-preview-on-ubuntu-1110.html)

Elementary Nautilus has a photo / file preview named Clutterflow that worked on 10.04 -11.04 , but I don't know if it is maintained because it has morphed into the Marlin file browser project .[http://www.installubuntulinux.com/2011/05/install-nautilus-elementary-in-ubuntu.html](http://www.installubuntulinux.com/2011/05/install-nautilus-elementary-in-ubuntu.html)

---

### Post by dixcuxx on 2011-11-20
> **Frogs Hair said:**
> Gloobus Preview will display the items in folders by name but there are special instructions to make it work properly in 11.10 . [http://www.ubuntubuzz.com/2011/10/install-gloobus-preview-on-ubuntu-1110.html](http://www.ubuntubuzz.com/2011/10/install-gloobus-preview-on-ubuntu-1110.html)

Elementary Nautilus has a photo / file preview named Clutterflow that worked on 10.04 -11.04 , but I don't know if it is maintained because it has morphed into the Marlin file browser project .[http://www.installubuntulinux.com/2011/05/install-nautilus-elementary-in-ubuntu.html](http://www.installubuntulinux.com/2011/05/install-nautilus-elementary-in-ubuntu.html)

So sound like Gloobus Preview is the best shot! :D

---

### Post by Frogs Hair on 2011-11-20
After installed click on the folder and press the space bar .

---

### Post by dixcuxx on 2011-11-20
> **Frogs Hair said:**
> After installed click on the folder and press the space bar .

ho nice:popcorn: I will try this out tonight!

---

### Post by dixcuxx on 2011-11-21
> **Frogs Hair said:**
> Gloobus Preview will display the items in folders by name but there are special instructions to make it work properly in 11.10 . [http://www.ubuntubuzz.com/2011/10/install-gloobus-preview-on-ubuntu-1110.html](http://www.ubuntubuzz.com/2011/10/install-gloobus-preview-on-ubuntu-1110.html)

Elementary Nautilus has a photo / file preview named Clutterflow that worked on 10.04 -11.04 , but I don't know if it is maintained because it has morphed into the Marlin file browser project .[http://www.installubuntulinux.com/2011/05/install-nautilus-elementary-in-ubuntu.html](http://www.installubuntulinux.com/2011/05/install-nautilus-elementary-in-ubuntu.html)

I install gloobus preview, but still the preview shows nothing for a folder.

---

### Post by dixcuxx on 2011-11-21
> **Frogs Hair said:**
> After installed click on the folder and press the space bar .

Just a big icon of the folder, it is not a preview.....just like your pic...

---

### Post by dixcuxx on 2011-11-21
What I try to do..is that just like Windows, all the folders would have a priview pic on it if there is a pic or video in it, then it just randomly pic a preview out of the pic/video in the folder as the priview pic of the folder, then I don't need to open any pic or video inside to folder to know what does the folder contain.

---

### Post by Frogs Hair on 2011-11-21
If you want to view a folder inside another folder you have to open the parent  folder first . In the screen shot the backgrounds folder was inside the pictures folder which had to be opened first .

If you want to search and open a file location use the " Search For Files " function . The preview is to view a folder with a large number of items inside instead selecting and opening each item  . This is nice if can't remember which folder an item is stored in .

---

### Post by dixcuxx on 2011-11-21
> **Frogs Hair said:**
> If you want to view a folder inside another folder you have to open the parent  folder first . In the screen shot the backgrounds folder was inside the pictures folder which had to be opened first .

If you want to search and open a file location use the " Search For Files " function . The preview is to view a folder with a large number of items inside instead selecting and opening each item  . This is nice if can't remember which folder an item is stored in .

Yeah It is not about folder in another folder. Just a folder with some pics and videos in it, but if I preview the folder icon with the "space key", then just the big folder icon pic.

---

### Post by dFlyer on 2011-11-21
Linux is not windows and shouldn't be. If you want to run windows, run it. Linux has a lot of program that will allow you to simulate a windows environment, but again it's not windows, and I and a lot of others like it that way.

---

### Post by Frogs Hair on 2011-11-21
> **dixcuxx said:**
> Yeah It is not about folder in another folder. Just a folder with some pics and videos in it, but if I preview the folder icon with the "space key", then just the big folder icon pic.

If that's the case the  preview is not working properly .

---

### Post by Frogs Hair on 2011-11-21
If you are using Unity and not the Gnome shell or Classic Gnome try the version of the Gloobus in the software center and remove the PPA first .

---

### Post by dixcuxx on 2011-11-21
> **Frogs Hair said:**
> If you are using Unity and not the Gnome shell or Classic Gnome try the version of the Gloobus in the software center and remove the PPA first .

I did these steps to install:

sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
sudo apt-get update
sudo apt-get install gloobus-preview gloobus-sushi libgdk-pixbuf2.0-dev

how should I clearly uninstall these!?

---

### Post by Frogs Hair on 2011-11-21
Open the Software Center and remove the following .

1. Globus Preview replacement for Gnome Sushi

2. a quick look for Linux 
      gloobus-preveiw 

While the Software Center is open use the edit tab in the global menu on the top panel . Open software sources > other software and remove the two lines in the last screen shot . ( click on the lines and use the remove option on the bottom .) 

If not asked to update the sources list after removing the lines . close the Software Center and run the update command in the terminal .```
sudo apt-get update
``` 
After that you can open the Software Center and install the Gloobus Preview . 

The PPA can be removed from the terminal as well , but I don't have the purge command for that one .

---

### Post by dixcuxx on 2011-11-22
> **Frogs Hair said:**
> Open the Software Center and remove the following .

1. Globus Preview replacement for Gnome Sushi

2. a quick look for Linux 
      gloobus-preveiw 

While the Software Center is open use the edit tab in the global menu on the top panel . Open software sources > other software and remove the two lines in the last screen shot . ( click on the lines and use the remove option on the bottom .) 

If not asked to update the sources list after removing the lines . close the Software Center and run the update command in the terminal .```
sudo apt-get update
``` 
After that you can open the Software Center and install the Gloobus Preview . 

The PPA can be removed from the terminal as well , but I don't have the purge command for that one .

I follow all of your steps, but then now I choose a folder,video,pic press space but have no response at all.

---

### Post by dixcuxx on 2011-11-22
> **Frogs Hair said:**
> Open the Software Center and remove the following .

1. Globus Preview replacement for Gnome Sushi

2. a quick look for Linux 
      gloobus-preveiw 

While the Software Center is open use the edit tab in the global menu on the top panel . Open software sources > other software and remove the two lines in the last screen shot . ( click on the lines and use the remove option on the bottom .) 

If not asked to update the sources list after removing the lines . close the Software Center and run the update command in the terminal .```
sudo apt-get update
``` 
After that you can open the Software Center and install the Gloobus Preview . 

The PPA can be removed from the terminal as well , but I don't have the purge command for that one .

I just try again. In Software Center, I click install gloobus-preivew, the load bar come out and load for awhile, then just I can click the install button again but I can never see it is installed.

---

### Post by hakermania on 2011-11-22
Hey, If I remember correctly, Dolphin file manager has this feature.

---

### Post by dixcuxx on 2011-11-22
> **hakermania said:**
> Hey, If I remember correctly, Dolphin file manager has this feature.

What is that...

---

### Post by timsdeepsky on 2011-11-22
I believe it is a kde file manager

---

### Post by timsdeepsky on 2011-11-22
Sorry,,,,here it is....

[http://dolphin.kde.org/]("http://dolphin.kde.org/")

---

### Post by maizuddin35 on 2011-11-22
I think you can try this out [http://www.webupd8.org/2011/10/cover-thumbnailer-083-adds-nautilus-3x.html](http://www.webupd8.org/2011/10/cover-thumbnailer-083-adds-nautilus-3x.html)  its a cover thumbnailer .

---

### Post by dixcuxx on 2011-11-23
> **timsdeepsky said:**
> I believe it is a kde file manager

installing, take very long time...may be I am too far away from the server

---

### Post by dixcuxx on 2011-11-23
Dolphin file manager has folder preview for local drive, but not local network share which is what i need.

---

