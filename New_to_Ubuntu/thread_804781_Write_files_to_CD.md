---
title: "Write files to CD"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Ludwig9 on 2008-05-23
I have no success in trying to write data files to a CD. The following are the instructions on how to do this:
> In a folder window menubar, choose Places*&#9656; CD/DVD Creator. The file manager opens the CD/DVD Creator folder.
In a File Browser window, this item is in the Go menu.
Drag the files and folders that you want to write to CD or DVD to the CD/DVD Creator folder.
Insert a writable CD or DVD into the CD/DVD writer device on your system.
Press the Write to Disc button, or choose File*&#9656; Write to CD/DVD. A Write to Disc dialog is displayed.
Use the Write to Disc dialog to specify how you want to write the CD, as follows:
But I see no way to "Drag the files and folders that you want to write to CD or DVD to the CD/DVD Creator folder," for there is nothing to drag, no way to specify files that I want to write to the CD. Clicking on anything in the Go Menu causes me to leave CD/DVD Writer altogether. Above the CD/DVD Creator Folder I see either "Go to:" with an empty window next to it which I have not way of filling with the name of the file I wish to write, or I see there "Location Burn\\:" And so far as I can see, I have no way of putting the name of a file in the window under "Name." 
Help, please!

---

### Post by shifty_powers on 2008-05-23
have you tried to use something linke brasero, or k3b to burn the disc?

find them both in synaptic ;)

---

### Post by stchman on 2008-05-23
> **Ludwig9 said:**
> I have no success in trying to write data files to a CD. The following are the instructions on how to do this:

But I see no way to "Drag the files and folders that you want to write to CD or DVD to the CD/DVD Creator folder," for there is nothing to drag, no way to specify files that I want to write to the CD. Clicking on anything in the Go Menu causes me to leave CD/DVD Writer altogether. Above the CD/DVD Creator Folder I see either "Go to:" with an empty window next to it which I have not way of filling with the name of the file I wish to write, or I see there "Location Burn\\:" And so far as I can see, I have no way of putting the name of a file in the window under "Name." 
Help, please!

I recommend using K3b for all your CD burning duties.

To install K3b do the following in a terminal:

Gutsy or earlier
```
sudo apt-get install k3b libk3b2-mp3
```

Hardy
```
sudo apt-get install k3b libk3b2-extracodecs
```

Launch K3b and you will be able to drag and drop the files to the CD before burning.  If you have ever used Nero, K3b will be just as easy.

---

### Post by 505 on 2008-05-23
Just open two windows of file manager. In the first, use the go menu to go to CD/DVD creator. Then in the second, locate the files and folder that you want to burn to a CD. Then either drag the files from the second screen to the first, or use copy and paste to get the files in CD/DVD Creator. After all files are in the special folder you can click "Write to disc" and the disc will be burnt.

---

### Post by Ludwig9 on 2008-05-23
> **505 said:**
> Just open two windows of file manager. In the first, use the go menu to go to CD/DVD creator. Then in the second, locate the files and folder that you want to burn to a CD. Then either drag the files from the second screen to the first, or use copy and paste to get the files in CD/DVD Creator. After all files are in the special folder you can click "Write to disc" and the disc will be burnt.
OK, it worked both ways. I had tried the copy and paste way before but must have put the cursor in the wrong place when I tried to paste. The first way seemed to me completely bizarre since I didn't know how one could possibly drag a file from one window to another. So, I dragged the file to the icon for the CD/DVD Creator at the bottom of the screen, kept the mouse button down, and low and behold the file appeared in the right place of the then opening CD/DVD Creator window. Great, thanks 505. 
I will now try the other recommended methods. One thing at a time!:)

---

### Post by Ludwig9 on 2008-05-23
> **stchman said:**
> I recommend using K3b for all your CD burning duties.

To install K3b do the following in a terminal:

Gutsy or earlier
```
sudo apt-get install k3b libk3b2-mp3
```

Hardy
```
sudo apt-get install k3b libk3b2-extracodecs
```

Launch K3b and you will be able to drag and drop the files to the CD before burning.  If you have ever used Nero, K3b will be just as easy.

I am a very new user of Linux and Hardy; I used the sudo command in Terminal, and it worked fine. I now have K3b, which may be no better the other, but is certainly easier for a neophyte to figure out how to use. Thanks, stchman.

---

### Post by Ludwig9 on 2008-05-23
> **shifty_powers said:**
> have you tried to use something linke brasero, or k3b to burn the disc?

find them both in synaptic ;)
Thanks, shifty_powers. I used Terminal to install K3b, but checked for it first in synaptic; it was there.

---

