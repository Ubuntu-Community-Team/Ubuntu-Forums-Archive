---
title: "Add program to launcher/dash"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by peterson43 on 2011-09-23
There is a really great program that I use called "ipe" for creating simple graphics/diagrams. The program doesn't appear in the Ubuntu Software Center, but I was able to add it using Synaptic (I could have also added it using apt-get). 

I can now start ipe by typing ipe in a terminal window. However, I still can't open it from the dash. When I type ipe in the dash, it doesn't find the program. 

Also, I cannot get ipe to appear on the launcher. When I'm running ipe no icon appears in the launcher telling me that it's running. I was able to create a launcher icon to the desktop that opens ipe, but when I drag that to the launcher it just creates an empty space on the launcher where there is no icon. Strange. 

Does anyone know how to fix these problems. By the way, I'm running 11.04.

---

### Post by seawolf167 on 2011-09-23
You can drag & drop the item to the launcher or run the application, then when it appears in the launcher, right click it and select to "keep in launcher". You can also add it via the gconf-editor.

---

### Post by grahammechanical on 2011-09-23
In earlier versions of Ubuntu did this program place an icon on the desktop? In other words does it have an icon?

I had this problem with a program that I used under Wine. I installed the program using Ubuntu Classic. The icon was put on the desktop. Then I booted into Unity (Ubuntu). The icon was still there and I could drag it into the dash. It might work for you this way.

Regards.

---

### Post by peterson43 on 2011-09-30
Okay, I solved my problem. As I said before, I could add the program to the launcher, but I couldn't get the icon on the launcher (only on the desktop). Also, I couldn't run the program from the dash. 

The hint by grahammechanical turned out to be the right idea. I logged in to Ubuntu Classic, and then went to System > Preferences > Main Menu. 
I clicked on '+ New Item' to create a launcher that was incorporated in the Main Menu. I had to input the command to run the program and find the icon where it was hidden in the /usr/share.... directory but I had already figured out how to do this when I created the launcher on the desktop previously. 

After successfully adding this program to the Main Menu in the Gnome desktop, I logged back in to the Unity desktop. Now I am able to run the program from the dash, and the correct icon shows up in the launcher panel. I can right click on the icon to keep the program in the launcher panel. 

Now that I think about things more, I realize I probably didn't need to log in to Ubuntu Classic. Even in Unity you can change the Main Menu by going to System Settings > Main Menu. I always thought that this was a strange thing to include in Unity since the 'Main Menu' only appears in Gnome, but I guess it does control what programs can be found in the dash as well.

---

