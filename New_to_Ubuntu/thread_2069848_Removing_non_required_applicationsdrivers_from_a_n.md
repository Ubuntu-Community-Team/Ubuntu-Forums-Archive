---
title: "Removing non required applications/drivers from a new Ubuntu desktop installation"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by himoundary on 2012-10-11
Hi,

I'm need to set up an Ubuntu box to function primarily as a testing server. However I'd like it to have a very** very basic Desktop/Windowing system**. 

Now, I am very new to Linux.

So, I am thinking of doing this: I install the the latest Ubuntu desktop version and then remove all packages/applications/etc from it that I don't need. This would include
- Drivers like sound driver, printer driver, etc etc
- Applications like media players, office suites etc etc

Basically the only things I need are a **browser, a text editor, and a terminal application.** I want to remove everything else, as the Ubuntu box will run inside a VMWare virtual machine inside my main Windows machine (which I can't change at the moment because I run applications which depend on Windows). So I want this to consume as little processor/RAM/disk space as possible.

Is there an _easy way_ to do this, without breaking any dependencies etc?

Also, would the opposite approach of installing a **Ubuntu server**, and then adding a desktop environment be better? I tried doing that but the results weren't so good. 

Finally, if someone knows about this (**not very important**):
I intend to use this with* VMWare Unity* mode (which has _nothing _to do with Ubuntu's Unity shell), and I believe it needs either KDE or Gnome to work (and works on Ubuntu's unity too). Does someone know if I can use any lighter desktop environments instead of GNOME/KDE/Ubuntu Unity that still support the *VMWare Unity* feature?

Don't bother about answering the whole question if you can't; just answer the parts you can.

Thanks!

---

### Post by wildmanne39 on 2012-10-11
Hi, you should do a server or minimal install it is much easier and safer then removing packages that are already installed.
Thanks

---

### Post by himoundary on 2012-10-11
> **Wild Man said:**
> Hi, you should do a server or minimal install it is much easier and safer then removing packages that are already installed.
Thanks
Is a minimal install what you get from the server iso? 

When running the ubuntu installer (via VMWare) I found no options to configure the installation (both when creating the server VM and desktop VM). Is that how it normally is, or is Ubuntu preventing me from seeing the customization options at the time of install?

---

### Post by wildmanne39 on 2012-10-11
Hi, here is a link for the minimal install.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

With this install you choose which packages to install.

The server addition does not have a desktop installed but I think it installs all required packages for the console desktop.
Thanks

---

### Post by raja.genupula on 2012-10-11
Yes , ubuntu minimal ISO is a Ubuntu core with out any other extra packages . so after installing it everything you have to  do manually . 

customization while installation is not possible in Ubuntu , because is not designed for Specific group of people .

even you feel like its a lengthy job , its exactly what you need . you can get it as you want to look it .

---

### Post by himoundary on 2012-10-12
> **Wild Man said:**
> Hi, here is a link for the minimal install.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

With this install you choose which packages to install.

The server addition does not have a desktop installed but I think it installs all required packages for the console desktop.
Thanks
Thanks for the minimal install tip, Wild Man! This is exactly what I needed. Had to spend some time doing it, but now I have a barebones desktop environment on a minimal installation (and nothing else!) 
And I actually have to start the desktop environment from the console (I like that, since I can choose not to if I don't need it!)

Thanks so much!

---

### Post by nothingspecial on 2012-10-12
Glad to hear it.

When your issue is resolved, please mark your thread as solved using the "Thread Tools" button.

I've done it for you this time :)

---

### Post by wildmanne39 on 2012-10-12
Hi, your welcome!
Enjoy

---

