---
title: "[SOLVED] Which files to download"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by inearlygaveup on 2008-10-23
23 Oct 08
Hi 
Can anyone help
When I go to download a new programme I find a big long list of presumably file names as shown - How do I know which one I need or I they just newer versions the highest number being the latest.
Martin

    *  ..
    * usbadslmodemmanager_0.4.0.deb
    * usbadslmodemmanager_0.4.1.deb
    * usbadslmodemmanager_0.4.2.deb
    * usbadslmodemmanager_0.4.3.deb
    * usbadslmodemmanager_0.4.4.deb
    * usbadslmodemmanager_0.4.5.deb
    * usbadslmodemmanager_0.4.6.deb
    * usbadslmodemmanager_0.4.7.deb
    * usbadslmodemmanager_0.4.8.deb
    * usbadslmodemmanager_0.4.9.deb
    * usbadslmodemmanager_0.5.0.deb
    * usbadslmodemmanager_0.5.1.deb
    * usbadslmodemmanager_0.5.2-0ubuntu1_i386.deb
    * usbadslmodemmanager_0.5.3_i386.deb
    * usbadslmodemmanager_0.5.4_i386.deb
    * usbadslmodemmanager_0.5.5_i386.deb
    * usbadslmodemmanager_0.5.6_i386.deb
    * usbadslmodemmanager_0.5.7_i386.deb
    * usbadslmodemmanager_0.5.8_i386.deb

---

### Post by cariboo on 2008-10-23
Pick the version specifically packaged for Ubuntu.

Jim

---

### Post by inearlygaveup on 2008-10-23
Thanks is this the one "usbadslmodemmanager_0.5.2-0ubuntu1_i386.deb" if not how do you tell

---

### Post by Kevbert on 2008-10-23
The one specifically for Ubuntu may be best. In saying that the higher the number the better, but it may not be stable (may be an experimental version that hasn't be fully tested) or has not been specifically written or customized for Ubuntu.

---

### Post by inearlygaveup on 2008-10-23
Hi they were/are supposedly all for Ubuntu 
Revision 694: /trunk/releases/ubuntu/32-bit i386
But how do you tell which to use

---

### Post by sethvath on 2008-10-23
The higher the revision number the newer is that build, ie usbadslmodemmanager_0.5.8_i386.deb is the lastest one and you should start there. 

I'm assuming you got it from [http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/) its all packaged for ubuntu so pick the newest one.

---

### Post by inearlygaveup on 2008-10-23
Great and thanks.
Is it a simple download and install

---

### Post by DrMelon on 2008-10-23
Yes, it's very simple. Once it's downloaded, just double click on the file, and it should install the package (after asking for your password).

---

### Post by inearlygaveup on 2008-10-23
Thanks a lot
Martin

---

### Post by inearlygaveup on 2008-10-23
Hi everyone

Thanks for all your help but the file doesn't work.
How do you uninstall a ".deb file"
It doesn't show up in my add/remove

---

### Post by Duck2006 on 2008-10-23
Look in System >> Administration >> Synaptic Package Manager and search the there, and if it is, mark it to be removed, click apply.

---

### Post by sethvath on 2008-10-23
What was the error in gdebi (the package installer)?

If it was installed but you cant find the menu button it means no desktop menu files were created for it. You can still find it with 
```
locate usbadslmodemmanager
```
in terminal. 

Please read the installation instructions on the website too.

---

### Post by inearlygaveup on 2008-10-23
I have got the icons, the only message I get as you hover over the panel icon is "Starting UP" and that's all it does. But both modem lights are on before you try to connect.

Although after help from the forum I think I may have installed an older package, so I thought I should uninstall the old one and try a newer package.

Is this recommended or is it better to try and find any faults.

---

### Post by inearlygaveup on 2008-10-23
Hi Duck2006

Thanks for your reply - I found the package in Synaptic Package Manager.
If I uninstall from there will it remove everything just like Windows.

Martin

---

### Post by Duck2006 on 2008-10-23
> Although after help from the forum I think I may have installed an older package, so I thought I should uninstall the old one and try a newer package.

Is this recommended or is it better to try and find any faults.

I would install the newer one. Uninstall the other one first.

---

### Post by inearlygaveup on 2008-10-23
Whats the differance between **Mark for removal and Mark for Complete removal**

---

### Post by 3rdalbum on 2008-10-23
> **inearlygaveup said:**
> Whats the differance between **Mark for removal and Mark for Complete removal**

Mark for Complete Removal also deletes configuration files that the program may have created when you first ran it. Otherwise, not a lot of difference. You can delete the config files later from within Synaptic even if you choose the first option.

---

### Post by inearlygaveup on 2008-10-23
Thanks for that the YouTube stuff is great

---

### Post by inearlygaveup on 2008-10-23
Hi I uninstalled as shown but have got this error message 

E: usbadslmodemmanager: subprocess pre-removal script returned error exit status 1

What does it mean
Do I do anything

---

### Post by inearlygaveup on 2008-10-23
Anyone on line who can help me on this one please

---

### Post by inearlygaveup on 2008-10-25
Original question Which files to download has been solved.
Thanks to everyone.
Martin

---

