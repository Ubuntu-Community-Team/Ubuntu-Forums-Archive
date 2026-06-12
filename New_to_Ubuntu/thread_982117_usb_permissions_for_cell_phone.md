---
title: "usb permissions for cell phone"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by alliance1975 on 2008-11-14
I would like to install an application named “XS++ v4.1” for linux. It enables modding of Sony Ericsson phones. When unzipped the software consists of 2 folders (cust and data) and 1 file (XS++ v4.1). It requires libfltk1.1 to be loaded.

Recommended install code consists of:

aptitude install libfltk1.1
aptitude install gksu
chmod +x /your/path/to_xs/XS++ v4.1
gksudo /your/path/to_xs/XS++ v4.1 

A final stipulation reads:

You will need to set up correct usb permissions or run the program as root! (The SE phones connect via usb data cable)

Would I be better setting up a menu item that would run the program as root or would I be better off adjusting the usb permissions. The final stipulation seems to suggest that the program can be run as a user or as root, but I am not certain of this. I think it would be best to install the folders and file in a dedicated directory in my home folder, of this too I am uncertain. How would I revise the permissions of the phone’s usb connection?

Any help/suggestions?

---

### Post by Bölvaður on 2008-11-14
Try having the program in your home directory and run it (as your user) and see what happens.
I think there isn't super user rights needed for connecting to the usb, but if so, you can always start up your program with gksudo as in "gksudo nautilus" (gives you graphical version of sudo).
And start up the program from the terminal to get all the error codes if there are any.

---

### Post by Hallvor on 2008-11-14
Try this command:

sudo chmod -R 777 /your/path/to_xs/XS++ v4.1

It will allow you to run it as a regular user.

---

### Post by LowSky on 2008-11-14
well you dont need to install gksu, that is installed by default, you can check synaptic for the other file

All you need to do is put the folder anywhere you like (you /home folder should work fine)
then use the code

```
sudo chmod -R 777 /your/path/to_xs/XS++ v4.1
```
then to run it
```
/your/path/to_xs/XS++ v4.1
```

EDIT Hallvor beat me to it

---

