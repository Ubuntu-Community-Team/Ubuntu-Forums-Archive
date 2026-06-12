---
title: "Login Screen Resolution"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by elend_heiler on 2008-05-08
hello..all!! :)

i have problem,,with my login screen resolution..
i've already installed my nvidia driver..

but when iam reboot..this message appear..

"out of range max 1024x768"

i guess,,my login sreen resolution too big,,,coz my monitor just 
support 1024x768 lower..

is there a way to change my login screen resolution???

thanks before!! :KS

---

### Post by akhirah on 2008-05-08
Hello, this is my very first post and naturally my first reply.  I hope my post benefits as I am relatively new to Ubuntu.

Firstly, click the gnome menu (the feet icon on the taskbar), click on Add/Remove.

Under SHOW, select ALL OPEN SOURCE APPLICATIONS
In the SEARCH box type, NVIDIA SERVER 

Select and install NVIDIA SERVER SETTINGS. Once installed, open the application under System>ADMINISTRATION>NVIDIA SERVER SETTINGS

Click on X Server Display Configuration, set your desired settings and then click on APPLY.  Does this remedy your resolution problem? If it does, then click SAVE TO X CONFIGURATION FILE.

In my experience I had errors saving to the X CONFIGURATION FILE, the changes I made to it never applied on start-up. 

The solution I came up with to solve this issue, I did the following -Within NVIDIA SERVER SETTINGS  I previewed the file, copied the whole text and saved it to a text file on the desktop.  From there, I accessed terminal under the ACCESSORIES menu.  Punched the following commands:

sudo -s -H (To gain root access)
Enter your normal password

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup (To backup your existing display configuration file)

gksudo gedit /etc/X11/xorg.conf (To open the file for editing) 
I removed all the contents of the file.

I copied the contents of the file from the desktop and pasted into the xorg.conf file and then saved it. Walaa, works everytime!

I do suggest you consult your monitors manufacturers manual to determine resolutions supported, Horizontal and vertical snyc rates, if available, Pixel Clock too. These settings can be directly entered into your xorg.conf file.

Hope that helps!

---

### Post by philinux on 2008-05-08
Simple gui, install startupmanager from synaptic. You'll see the option for the login screen res when you start it up. The menu entry is placed in System>Admin.

---

### Post by sy88 on 2008-05-08
Hmm, yet another method would be to edit /etc/X11/xorg.conf by going to the SubSection "Display" under the Section "Screen" and putting the correct resolution for your mode (ie. Modes "1024x768").  Then just restart X by ctrl-alt-bksp or restart your computer.

---

### Post by philinux on 2008-05-08
> **sy88 said:**
> Hmm, yet another method would be to edit /etc/X11/xorg.conf by going to the SubSection "Display" under the Section "Screen" and putting the correct resolution for your mode (ie. Modes "1024x768").  Then just restart X by ctrl-alt-bksp or restart your computer.

Yep if your using gutsy or previous. Hardy has no screen resolution info in its xorg.conf from a clean install.

---

### Post by sy88 on 2008-05-08
> **philinux said:**
> Yep if your using gutsy or previous. Hardy has no screen resolution info in its xorg.conf from a clean install.

Does that startup manager you mentioned modify another config file?  I'm curious as to which file it changes? :)

---

### Post by philinux on 2008-05-08
> **sy88 said:**
> Does that startup manager you mentioned modify another config file?  I'm curious as to which file it changes? :)

Well I reckon it must be menu.lst and usplash.whatever

---

### Post by elend_heiler on 2008-05-08
thank to all...my problem was solved :KS

many2 thanks!!

---

