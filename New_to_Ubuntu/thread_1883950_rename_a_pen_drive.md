---
title: "rename a pen drive"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by lenypl on 2011-11-20
i am using ubuntu 11.10. i buy a new pen pen drive i want to rename it.how can i do that.i cant find any option

---

### Post by Rex Bouwense on 2011-11-20
I'm not sure if there is an easier way but if you have Gparted, launch it and then select your flash drive.  Unmount the flash drive and then select label (under the partition menu).  Type your new name and that should do it.

---

### Post by fantab on 2011-11-20
Use DISK UTILITY to rename the pen-drive. You can do this by editing the label.

---

### Post by Rex Bouwense on 2011-11-20
+1  See, I knew there was an easier way.:popcorn:

---

### Post by fdrake on 2011-11-20
```

man tune2fs
sudo tune2fs -L "My_Pen" /dev/pendrive

```

---

### Post by lenypl on 2011-11-21
> **fantab said:**
> Use DISK UTILITY to rename the pen-drive. You can do this by editing the label.
i go for disk utility >edit partition and a  window comes but i cant type anything in the place of label

---

### Post by Rex Bouwense on 2011-11-21
You have to unmount the flash drive before you can do anything.  Works just fine.

---

### Post by lenypl on 2011-11-22
> **Rex Bouwense said:**
> You have to unmount the flash drive before you can do anything.  Works just fine.thank you for your help i success fully done it. now i had to copy the files from the driveand paste in another drive. in windows it can done by right click >copy.then open other drive and simply right click >paste.how can i do a copy and paste in ubuntu 11.10.when i right click there was no copying options .pls help

---

### Post by audiomick on 2011-11-22
Can you copy and paste using ctrl+c and ctrl+v ?
Can you select the file, then copy using the option in the "edit" menu?

---

### Post by fantab on 2011-11-22
> **lenypl said:**
> thank you for your help i success fully done it. now i had to copy the files from the driveand paste in another drive. in windows it can done by right click >copy.then open other drive and simply right click >paste.how can i do a copy and paste in ubuntu 11.10.when i right click there was no copying options .pls help

It is same as in Windows, right click-Copy - right click-Paste. Check again.

---

### Post by lenypl on 2011-11-23
[QUOTE=audiomick;11479488]Can you copy and paste using ctrl+c and ctrl+v ?
Can you select the file, then copy using the option in the "edit" menu?[/QUO
ctrl +c,ctrl+v doesnt work. when i plug pen drive it automatically opens with vlc player. then i go media >open file tosee the folder. i try to change the setting removable media>ask what to  do,open folder and do nothing.but it doesnt works the files open only with vlc player

---

### Post by audiomick on 2011-11-23
What sort of files are on the USB drive? Are they films or music?

---

### Post by dniMretsaM on 2011-11-23
What is the file system type on the drive? Some types don't support labeling.

---

### Post by lenypl on 2011-11-24
> **audiomick said:**
> What sort of files are on the USB drive? Are they films or music?
yes it contains films,music and photos.any of them cant copy and paste

---

### Post by audiomick on 2011-11-24
So you can't do anything with the files, but VLC can play them, right?

I gather you can see the folder on the drive in the file manager, Nautilus. If you right click on the folder, or one of the files in it, and choose "properties", what does it say on the "permissions" tab? It sounds like the drive is being mounted with no permission for you to copy anything. I don't know why this could be, I am sorry.

I would try opening an instance of the file manager with root privileges using
```
gksudo nautilus
```

and see if I could copy off files in that instance of the file manager.

If you do this, you should be aware that 
- what you copy will, I believe, belong to root. You will have to right click> properties> permissions and change the ownership to you. You can do this to a folder, and click the button to make the setting apply to everything in the folder

- using nautilus in this form is dangerous. If you tell it to delete a system file by mistake, it will just go ahead and do it. You should only use nautilus with root privileges for very specific jobs, and close it as soon as you have finished what you wanted to do.

This will get your files copied off, I think, but will not solve the question why you can't do this in the normal manner. I am afraid I can't help there, sorry.

---

### Post by lenypl on 2011-11-25
> **audiomick said:**
> So you can't do anything with the files, but VLC can play them, right?

I gather you can see the folder on the drive in the file manager, Nautilus. If you right click on the folder, or one of the files in it, and choose "properties", what does it say on the "permissions" tab? It sounds like the drive is being mounted with no permission for you to copy anything. I don't know why this could be, I am sorry.

I would try opening an instance of the file manager with root privileges using
```
gksudo nautilus
```and see if I could copy off files in that instance of the file manager.

If you do this, you should be aware that 
- what you copy will, I believe, belong to root. You will have to right click> properties> permissions and change the ownership to you. You can do this to a folder, and click the button to make the setting apply to everything in the folder

- using nautilus in this form is dangerous. If you tell it to delete a system file by mistake, it will just go ahead and do it. You should only use nautilus with root privileges for very specific jobs, and close it as soon as you have finished what you wanted to do.

This will get your files copied off, I think, but will not solve the question why you can't do this in the normal manner. I am afraid I can't help there, sorry.friend i cant open any of my drives. if i double click any of my file it opens with  vlc player.and i cant do any thing

---

### Post by dniMretsaM on 2011-11-25
I think that means you have VLC set as your default file browser. Not exactly sure how to change that in GNOME/Unity though (I normally use KDE but right now I'm on my sis's Win7 laptop :(). If you need me to though I can look around in a live environment.

---

### Post by lenypl on 2011-11-26
> **dniMretsaM said:**
> I think that means you have VLC set as your default file browser. Not exactly sure how to change that in GNOME/Unity though (I normally use KDE but right now I'm on my sis's Win7 laptop :(). If you need me to though I can look around in a live environment. thank you for your kind informtion.

---

### Post by lenypl on 2011-11-27
> **lenypl said:**
> thank you for your kind informtion.if you get any information to help me pls replay.because an os in which can perfom copy and paste is waste. now i am using windows 7 . i want to continue in ubuntu

---

### Post by dniMretsaM on 2011-11-27
Ok, I'll boot up a live GNOME environment and post back. And what type of file system is it?

---

### Post by lenypl on 2011-11-28
> **dniMretsaM said:**
> Ok, I'll boot up a live GNOME environment and post back. And what type of file system is it? thank you very much for friend. i find a solution.i just completely remove the vlc player threw synaptic package manager and re install threw software centre. now its ok.but i cant find why it happened?. if you can find it pls inform me and give a correct method for correcting.

---

