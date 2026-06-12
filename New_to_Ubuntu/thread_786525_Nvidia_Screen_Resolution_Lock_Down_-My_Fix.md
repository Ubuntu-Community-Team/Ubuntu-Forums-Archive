---
title: "Nvidia Screen Resolution Lock Down -My Fix"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by akhirah on 2008-05-08
This is my first forum post, please excuse the noobness LOL!

I installed Ubuntu Hardy Heron 8.0.2 on my PC.  Ubuntu recognised and installed all my hardware, impressive. Once I logged in I noticed the refresh rate was locked down @ 50MHZ, causing me severe eye strain. After a few googles and perusing the Multi-media & Video forum I attempted to take action.

But to no avail, the guides in the Video forum were comprehensive but beyond my intellectual capacity. He hee! So, I concocted my very own simple solution (admittedly with reference to the guide in the video forum). 

STEP 1 (Skip Step 1 if u have NVIDIA SERVER SETTINGS INSTALLED)......

Firstly,click the gnome menu (the feet icon on the taskbar), click on Add/Remove.

Under SHOW, select ALL OPEN SOURCE APPLICATIONS
In the SEARCH box type, NVIDIA SERVER

Select and install NVIDIA SERVER SETTINGS. 

STEP 2..............................................................

Once installed, open the application under System>ADMINISTRATION>NVIDIA SERVER SETTINGS

Click on X Server Display Configuration, set your desired settings and then click on APPLY(I set mines at 1280 X 1024 @ 85MHZ) Does this remedy your refresh rate problem? If it does, then click SAVE TO X CONFIGURATION FILE. Restart the computer to double check the settings are effective upon startup.  Goto STEP 3 if u got errors saving to file.

STEP 3...............................................................


In my experience I had errors saving to the X CONFIGURATION FILE, the changes I made to it never applied on start-up nor made permanent changes to the xorg.conf file..permission issues most likely!

The solution I came up with to solve this issue, I did the following -Within NVIDIA SERVER SETTINGS I previewed the file, copied the whole text and saved it to a text file on the desktop. From there, I accessed terminal under the ACCESSORIES menu. Punched the following commands:

sudo -s -H (To gain root access)
Enter your normal password

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup (To backup your existing display configuration file)

gksudo gedit /etc/X11/xorg.conf (To open the file for editing)
I removed all the contents of the file.

I copied the contents of the file from the desktop and pasted into the xorg.conf file and then saved it. Walaa, works everytime!

I do suggest you consult your monitors manufacturers manual to determine resolutions supported, Horizontal and vertical snyc rates, if available, Pixel Clock too. These settings can be directly entered into your xorg.conf file.

Plz dont blast my noobness, we all gotta start somewhere!

---

