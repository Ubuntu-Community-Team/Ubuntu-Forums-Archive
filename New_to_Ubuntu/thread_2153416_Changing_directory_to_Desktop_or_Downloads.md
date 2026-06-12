---
title: "Changing directory to Desktop or Downloads"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by KingRazor on 2013-06-11
Trying to change directory in the terminal from home to desktop, or downloads. Keeps saying "no such directory". Just trying to install a .deb file but no matter where I put it the terminal can't find it.

What do I do?

---

### Post by claracc on 2013-06-11
The question is how do you have downloaded the .deb package?, through browser?, where is the folder to keep the downloaded packages in your browser (you can see the settings in your browser)?, could be /home/name_of_user?. We need more information about how you get downloaded the package and what package is.

To see what files are inside folders you can use command ```
ls -la
```

Then for installing the .deb package you want to install, go to the folder where you have downloaded the file and execute ```
sudo dpkg -i file.deb
```, then introduce your pass when asked and it is all

---

### Post by cub on 2013-06-11
this might be old news but just in case, it matters if you write Desktop or desktop. They are case sensitive.

---

### Post by 3rdalbum on 2013-06-11
The above poster is correct: You can't do "cd downloads" when the folder is called Downloads. You need to do "cd Downloads".

If you have a GUI open, why not use it in conjunction with the terminal? If you drag a file or folder to the terminal, its file path and name get filled in. You can literally just type "cd " and drag the Downloads folder into the terminal, and press Enter

---

### Post by KingRazor on 2013-06-11
Well, it turned out I could just use the software center to install it. So that solved that.

I had downloaded the file through my browser (firefox), which saves everything to my "Downloads" folder. I tried changing directory to "Downloads" but it kept saying "no such directory", same if I tried "Desktop".

I tried moving the file to the "home" folder, since I could navigate there, but it couldn't find the file.

The case was the first thing I tried but I got the same error whether the d was capital or lowercase.

Did not know about the clicking and dragging the folder into the terminal, I'll keep that in mind for future reference.

Thanks.

---

