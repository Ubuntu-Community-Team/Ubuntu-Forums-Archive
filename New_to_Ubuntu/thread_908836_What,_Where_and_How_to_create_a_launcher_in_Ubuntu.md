---
title: "What, Where and How to create a launcher in Ubuntu"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by tpyeoh on 2008-09-02
I need help as I am an idiot in Ubuntu, I need help on how, what, and where to create a launcher for the application to be display within the Application Tab.

---

### Post by drs305 on 2008-09-02
First, look through the folders and see if the app you are looking for may already be in one of the existing folders. If not:

In a terminal, type "alacarte" or right click on the Applications/Ubuntu symbol and select 'Edit Menus'.

If you want the app listed along with the folders, just click 'New Item' on the right. The new item will be seen in the main column when you click on Applications.

If you want it listed inside a folder, first click on the folder in the left window. Then click in the right window and select 'New Item'.

Select 'Application' or if it is run in a terminal, 'Application in Terminal'.

Enter a name for the item.

Enter the command to start the application. 

If it is a known program, an icon for it will automatically appear in the upper left icon area. If the app is not known, you can click on the icon symbol and navigate to the icon you want to use.

Click OK.

Added: Normally the name of the run command is the same as the name of the app. Sometimes it is not. Let's use OpenOffice Calc as an example. If you don't know the name of the command of the app, look in /usr/bin and see if anything looks like it might be the command. You can also open Synaptic, click on the app (OpenOffice.org-calc), and then select 'Properties'. Next select the 'Installed files' tab. Again, see if there is a listing in /usr/bin that may indicate the command name of the app (oo-calc).

---

### Post by tpyeoh on 2008-09-02
Thanks. But do I create a launcher for a new program like a program in startup within Windows ?

---

### Post by drs305 on 2008-09-03
From the PMs we swapped, my understanding is you want to create a launcher for an app to begin at start up. To do this, select System, Preferences, Sessions. Click the 'StartUp Programs' tab, then "+Add".

Enter a name for the application and in the Command window type the startup command for the app. Once you have entered the information click on the OK tab. Make sure the box to the left of the app name is selected/'ticked' and it will start when you log in to ubuntu.

If you don't know the command to start it, read my earlier post or tell us here what the application is and we can probably tell you what to type in the command window.

---

### Post by tpyeoh on 2008-09-04
Thanks. It is working now...

---

