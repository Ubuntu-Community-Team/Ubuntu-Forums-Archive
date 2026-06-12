---
title: "VBoxLinuxGuestAddions"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by squirrel1 on 2008-05-26
I have just installed Virtual Box under Win XP with the latest download of Ubuntu.
Once Ubuntu was installed and running I found the display would not fill the whole screen, just like a missing driver.
Reading on I discovered that I would need to intsall the VBox Guest Additions. After following the instructions and looking on the net for help. I was able to mount the iso image and get that on the desktop. But no way would anything install.
I have tried typing the following into a terminal: sudo sh ./VBoxLinuxGuestAdditions.run and this didn't work.
I tried copying the files from the iso image into the Home Folder but some files would not copy (VBoxLinuxGuestAdditions.run) so when i typed in the above command nothing would Install.

Can someone tell me in straight forward terms how to install the VBoxAdditions or am I wasting my time with VBox??

---

### Post by forestpixie on 2008-05-26
It's not on the desktop - it's mounted on a cd - which is appearing on the desktop :D

open the terminal and change directory to cdrom

cd /media/cdrom

do a dir to make sure it's there if not try cdrom0

then change into the vbox directory and try to run the command again

---

### Post by mrtomservo on 2008-05-26
Just thought i'd mention that when I was in this same situation, it would only work on the directory of cdrom0, not cdrom.  Don't know why, or why it thinks i've got more than one cdrom drive. :)  Wait, probably because cdrom is my actual cdrom/dvd drive and the cdrom0 is the virtual one.  So anyway, if the cd /media/cdrom doesn't work, try this instead:
```

cd /media/cdrom0
sudo sh./VBoxLinuxGuestAdditions.run
```

---

### Post by squirrel1 on 2008-05-26
Thank you for your help, but I have done exactly as you said, Ican see the files when I do a dir, but when I type in sudo sh ./VBoxLinuxGuestAdditions.run and press return. A password is asked for,  which I entered, but the install didn't work, Command not found.

What next?

---

### Post by fwre01 on 2008-05-26
squirrel1, the command should be "sudo ./VBoxLinuxGuestAdditions.run" with no sh after sudo

---

### Post by squirrel1 on 2008-05-26
I kept trying to install the VBox Additions and then...it worked

Now I need to know how to make the desktop full screen.

---

### Post by fwre01 on 2008-05-26
I havent used the windows version (im assuming its the same as the linux version) but to make the guest full screen you can click Machine > Fullscreen Mode, or hold Right Ctrl and press f (thats also how you exit from Fullscreen Mode)

---

### Post by squirrel1 on 2008-05-26
Thank you everyone so far. We are slowly getting the hang of it.
But, if I press Ctrl-F the screen goes black with the Linux desktop still the same size.

There is no option of greater than 800x600 screen res in the preferences menu.

Surely it must be possible to have a full size desktop screen. Do I need to download and install a driver or something? And if so where do I obtain siad driver?

---

### Post by fwre01 on 2008-05-26
it sounds astho you havent got the VBOXadditions installed correctly....

im not sure how to verify the install? perhaps just run the install again. cd to /media/cdrom and run "sudo ./VBoxLinuxAdditions.run" you should see this output

> Verifying archive integrity... All good.
Uncompressing VirtualBox 1.6.0 Guest Additions for Linux installation.............................................................................................................................................................................
VirtualBox 1.6.0 Guest Additions installation
Building the VirtualBox Guest Additions kernel module...
Building the shared folder support kernel module...
Installing the VirtualBox Guest Additions...

Successfully installed the VirtualBox Guest Additions.
You must restart your guest system in order to complete the installation.


---

### Post by squirrel1 on 2008-05-26
I did see what you show.

But I will try the install again. I the mean time do you have any more suggestions if this doesn't work. Just in case.

---

### Post by fwre01 on 2008-05-26
you need to make sure you have "Auto-resize Guest Display" clicked in the Machine menu.

I think Right CTRL + G does this

---

### Post by squirrel1 on 2008-09-28
All sorted out......Installed Ubuntu in a seprate partion and all is Very Well......

Happy bunny now!!!!!!!!!

I was amazed at how everything worked without having to download and install lots of drivers.....fantastic!):P

---

### Post by squirrel1 on 2008-09-28
Abandoned V-Box and tried Ubuntu running from the CD..Full size screen and most things seemed to work, so I decided to undertake a full install of Ubuntu in a seprate partion on the HDD and I am glad I did!
I now have a wonderful 'free' operating system running on my old HP NC8000 laptop, and the WiFi card and everthing is working without downloading and installing any drivers.....fantastic!

Windoes 1-Ubuntu 2 or 3 or......

---

