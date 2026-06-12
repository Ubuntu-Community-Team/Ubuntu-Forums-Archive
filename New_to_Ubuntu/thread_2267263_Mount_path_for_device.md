---
title: "Mount path for device"
date: 2015-02-28
forum: New to Ubuntu
---

### Post by penny3 on 2015-02-28
I have downloaded ADE from WINE so that I can transfer ebooks to my reader but ADE wasn't detecting my device. After some research I found this link with information on how to create a 'persistant path' [https://appdb.winehq.org/objectManager.php?sClass=version&iId=30928](https://appdb.winehq.org/objectManager.php?sClass=version&iId=30928)   The instructions say to mount your device and note the path name. How do I find out what the mount path name is? Thanks!

---

### Post by dino99 on 2015-02-28
if you are using gnome/unity then nautilus will show you the path by right clicking on the mounted partition (simply double click to mount it, from the left pane): it will be like /media/mymountedpartition
right click again on the mounted partition to select unmount before closing the session.

---

### Post by penny3 on 2015-02-28
I am a total noob with this whole process. So I need to figure out exactly what you are saying. :)  Mounted partition? I know that when I install a flash drive, an icon appears in the unity taskbar but when I plug in the Kobo, nothing shows up at all. Is this where you meant that I should "simply double click to mount it from the left panel"? Or does it mean that, when I plug the Kobo reader in, that I should double-click on a blank area of the unity bar and it will force it to pop up? Switching to Ubuntu is a humbling experience ...

---

### Post by deadflowr on 2015-02-28
Open up the program called "Files"
and then look over at the leftside area for a section called Devices.
Is there anything listed for what may be the kobo device?

Chances are it might show an arcane name like 2GB file system something, or other.

(If that helps...)

---

### Post by penny3 on 2015-02-28
Thank you, Deadflowr! Worked like a charm! Under Devices, it actually showed Kobo eReader by name. At least I know how to safely eject the darn thing now, too. If I understand things correctly, Ubuntu recognizes the device so all I need to do now is create a dedicated drive for ADE (as per the below instructions)?  (UPDATE: I tried the below and ADE still doesn't recognize the ereader so obviously there is something more to it.)

   *Note:* Do **NOT** open ADE until clearly outlined in this how-to!  
 1) Mount your device and make note of it's mount point (This needs to be remembered exactly). For me this was /media/KOBOeReader/ 

2) The next step is to unmount your eReader (This is because winecfg cannot seem to keep the changes applied if the device is mounted). 

3) Next open winecfg and switch to the [Drives] tab. 

4) On the [Drives] tab click the "Show Advanced" button.  
 *Note:* As outlined in the comment by Kevin, WINE does not seem to have persistent drive mapping while the device is mounted. Therefore you have 2 options. Either the messy way, which is to keep the winecfg window open while ADE runs, or unmount and create a persistent entry.  
 5) Click the "Add" button. 

6) Choose a letter to map your device to (I used "O:" because that was the only letter available to me.) 

7) In the "Path" box, type the mount point from step 1. 

8) In the "Type" drop-down menu, choose "Floppy disk" as the option. 

9) Click "OK". 

10) Open ADE. If everything went correctly ADE should ask you to authorize your eReader with your Adobe account (if you authorized your computer anonymously you will be asked to authorize your computer too). To read eBooks on your device simply drag-and-drop books from your ADE library to the entry in the left pane of ADE that corresponds with your eReader. 

11) Finally remember to safely dismount your device from your computer.

---

