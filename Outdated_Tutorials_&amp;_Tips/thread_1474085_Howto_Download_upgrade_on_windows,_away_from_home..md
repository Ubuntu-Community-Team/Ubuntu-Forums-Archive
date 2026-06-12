---
title: "Howto: Download upgrade on windows, away from home. Install to linux box, at home."
date: 2010-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Ebere on 2010-05-05
First, let me point out that you can do this with a laptop that has linux on it, or with a windows laptop that has been booted to linux with a livecd, or usb, etc.

It is better if the livecd, or in the case of a laptop with linux on it, the OS on the laptop... Has the same "flavor" as the OS that you are attempting to update, or to add new packages to.

1.) Open Synaptic.

2.) Choose your packages. Do NOT hit the 'apply' button.

3.) Once you have all the packages chosen, open >File, and choose Generate Package Download Script.

4.) Name your script, and choose where you want to save it. 

A hint here: Create a new folder, and save the script inside the empty folder.

The reason for this is because when you run the script, all the package files will be downloaded into the same folder that the script resides in.

5.) Once you are set up at the library, find the script and run it. (Single or double click, according to your preferences) 

When it asks what you want to do, choose to run it in a terminal window. (I'm not talking about opening a terminal window and running a command in there. I am talking about choosing it as an option once you click on the script name, to run it.)

If you do not run it in a teminal window, but just plain run it, it will work, but there is no indication of what is being done, or when it is finished.

If you run it in a terminal window, you can watch the progress, and the window closes when it is finished.

Another hint: If you have a lot of files to download, let the terminal window finish and close. and then run the script again. Several times.

It will not download the same thing all over again. But for some reason, if there are a lot of files, it may miss some of the files. And it will pick up the ones it missed before, on subsequent runs.

6.) Back at home. Copy the folder and it's files to the machine you want to update.

I created a folder called "Cabinet" in my home directory, and then copied all the files to that folder.

7.) Open Synaptic.

Go to: >File. And choose "Add Downloaded Packages."

In the window that opens, browse to your new folder, and click open.

Note: Do not go inside the folder. Choose the folder itself. Then click "Open".

8.) Click apply, and follow all the regular steps for upgrading or adding new packages.


That should git-er-done.

---

