---
title: "Need easy Way to Install Multiple OTF Fonts"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by clbph on 2012-09-20
This is my first experience with Ubuntu and I desperately need help.

[SIZE=3]I plan to use Scribus to try and duplicate some of the documentation I previously produced with Adobe InDesign. For consistency, and corporate reasons, I need to install 170+ OTF fonts. I managed to transfer the OTF files to a holding folder, but am running into a real time consuming method of installation. I have opened the fonts in the Font Viewer and am clicking the fonts one at a time. Installation is S L O W with some fonts taking as long as three minutes EACH to install.

Is there a faster way?

Previously, I was able to select the entire group, Right Click and say "Install Fonts". Is there a Linux equivalent of this method?

Thanks and I apologize for my ignorance.[/SIZE]

---

### Post by Matuka on 2012-09-20
I'm a beginner and I've just recently installed Xubuntu and I decided to replace the global font from droid-sans to Helvetica. I managed to do this by creating a folder in my user folder (Not sure what you would call it, perhaps you will. For me its 'home/Nathan/'). I named the folder ".fonts" and I placed my folders with the *.OTF files in there and it detected them perfectly fine.

I created the folder and moved the folders in there by using the Terminal. If you want to do it via the GUI then you would want to make sure that you are able to see hidden files (Not sure whether this is global for all desktop environments, but ctrl+h in my file-manager is the hotkey to enable the ability to see/unsee hidden folders & files).

I hope this helps. :>

---

### Post by GreatDanton on 2012-09-20
This will help you: [http://ubuntuforums.org/showpost.php?p=12145191&postcount=2](http://ubuntuforums.org/showpost.php?p=12145191&postcount=2)

Regards.

---

### Post by clbph on 2012-09-20
Thanks, Matuka, for the quick response, but I think I'm talking about a different scenario. These fonts are not for global use, if I'm correctly interpreting the use of Global, but will be called as needed for use in documents and, yes, on-screen. It is just disappointing that I started this font install around 10:00 AM this morning and it is still underway and 2:15 this afternoon. Previously, this entire installation package would take about two minutes to complete.

I installed Ubuntu 12.4 as the sole operating system on the same PC I used to use. I am bound and determined to learn Linux!

---

### Post by clbph on 2012-09-20
Thanks, GreatDanton, you were pointing me where I needed to go, but the directions fall apart when I opened the home folder. I am unable to locate a .fonts folder. You are correct that ctrl-h reveals hidden folders, but  that did not help. I tried some searches, but no folder matching that name showed.

I'm going to have to resume this tomorrow . . . out of time for today.

---

### Post by JKyleOKC on 2012-09-20
> **clbph said:**
> Thanks, GreatDanton, you were pointing me where I needed to go, but the directions fall apart when I opened the home folder. I am unable to locate a .fonts folder. You are correct that ctrl-h reveals hidden folders, but  that did not help. I tried some searches, but no folder matching that name showed.

I'm going to have to resume this tomorrow . . . out of time for today.
You can create the folder either from the desktop or from a terminal screen. From the desktop, right-click on a blank area of the desktop and a menu should pop up, with "create folder" or words to that effect as one of the choices. From a terminal screen, enter "mkdir .fonts" at the prompt and hit Enter. Either way this will create the directory in your home folder and you can proceed.

Hope this helps! If I could find a way to make Scribus create files totally compatible with Microsoft Publisher I would switch to it myself. My print shop requires Publisher files, unfortunately...

---

### Post by GreatDanton on 2012-09-20
Exactly. You can create folder with terminal, or with Nautilus. Open file manager (Nautilus), and navigate to the home folder. After that right click on the white background and select create a new folder. Name it:```
.fonts
```Put your files in .fonts folder (you can see it by pressing ctrl+h). After that follow the instructions.

Regards.

---

