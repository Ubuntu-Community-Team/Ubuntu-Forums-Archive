---
title: "HOW TO: Creating a One Click Connection Launcher For Your Bluetooth Device"
date: 2007-01-14
forum: Outdated Tutorials &amp; Tips
---

### Post by tsav87 on 2007-01-14
I had struggled getting my Bluetooth Mouse to connect to my computer so I did some research, put it all together and came up with the idea to make it simple for anyone else to accomplish what I was trying to do.  Here it is.

First off you will need to turn on both your computer and your bluetooth device.  If your bluetooth device has a connect/reset button, press it now.

Open up the terminal and enter this into it.
```
sudo /etc/init.d/bluez-utils restart (On some computers it may be sudo /etc/init.d/bluetooth restart)
```

When that completes, enter this into the terminal.
```
sudo hidd --search
```

That will yield something that looks like this.
```
Searching ...
        XX:XX:XX:XX:XX:XX            Name of Device

```
(Note, if you get all zeros, restart the bluetooth services again and try searching again.  Also, your not going to get "XX:XX:XX:XX:XX:XX", it will be numbers and letters, this is your device's bluetooth address.)

Now, create a .txt file and name it whatever you wish to call it.  Inside the text file enter in this code.
```
sudo /etc/init.d/bluez-utils restart (or, depending on your computer, sudo /etc/init.d/bluetooth restart)
sudo hidd --connect XX:XX:XX:XX:XX:XX

```

Save the file and place it in your Home Folder, or Subfolder of your Home Folder.

Then right click on your desktop and select Create Launcher.
Change Type from Application to Application in Terminal
Make sure it looks something like this.
[IMG]http://i50.photobucket.com/albums/f305/Travis_777/Screenshot.png[/IMG]

You can change the Icon if you want by clicking "No Icon"

This can also be done on one of the panels.  Simply right click on the panel you want it on and choose "Add to Panel" then choose Custom Application Launcher and do the same as above.

I hope this helps someone out, i know it sure would have helped me when I was searching for it.

-Travis

Oh, and by the way, this is all assuming that your Bluetooth Receiver is installed and working on your computer.

---

