---
title: "VBoxGuestAdditions.iso"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by Ymurti on 2011-10-29
Please I need help.

I installed Oracle VM VirtualBox in Ubuntu 11.10 and I installed Windows 7 using Virtual Box. I need install the VBoxGuestAdditios.iso but I do not know how. I have it on /usr/share/virtualbox/VBoxGuestAdditions.iso

Someone please can help me?

---

### Post by 3rdalbum on 2011-10-29
.iso is a disc image. You need to set up your Virtualbox virtual machine to mount the VBoxGuestAdditions.iso as a CD-ROM inside the virtual machine. Then it will appear in My Computer on Windows as a CD, and you can double-click on the installer in there to install the guest additions.

---

### Post by The Cog on 2011-10-29
The virtualbox program has to know about this cd image so it can offer it to the guest OS. If you are using the open-source version of virtualbox as installed from the Ubuntu repositories, then this is what you need to do:

1: 
Install package virtualbox-guest-additions-iso. This gives virtualbox access to the CD image to show to its guests. Use synaptic or this command: ```
sudo apt-get install virtualbox-guest-additions-iso
```

2: 
Boot the guest OS inside virtualbox.

3:
In the virtualbox menu, use Devices -> Install Guest Additions... This will cause the guest OS to see the installer CD inserted into the virtual CDROM drive. From there, it is up to win7 to do whatever it does with driver CDs.



The other way would be to use the virtualbox virtual media manager utility, register the ISO image with virtualbox, and then use the devices menu on the running VM to insert that CD image into the virtual drive. It's longer winded this way, but you might have to learn this method to install other software to the win7 guest anyway.

---

### Post by Ymurti on 2011-10-29
[QUOTE=The Cog;11405459]The virtualbox program has to know about this cd image so it can offer it to the guest OS. If you are using the open-source version of virtualbox as installed from the Ubuntu repositories, then this is what you need to do:

1: 
Install package virtualbox-guest-additions-iso. This gives virtualbox access to the CD image to show to its guests. Use synaptic or this command: ```
sudo apt-get install virtualbox-guest-additions-iso
```

2: 
Boot the guest OS inside virtualbox.

3:
In the virtualbox menu, use Devices -> Install Guest Additions...


I did till here then I could not find de Devices -> Install Guest Additions.... Please help

Obs.: I am attaching a screenshot of my desktop.

---

### Post by The Cog on 2011-10-29
Unity hides the application menu for some reason. It removes it from the application window itself, and puts it at the top of the screen, then puts the window title in fron of it to hide the actual menu items. In order to see the menu, you have to jam your cursor up to the top of the screen (regardless of where your window is placed). Then the menu appears across the top. You should find the Devices menu item up there.

---

### Post by Ymurti on 2011-10-30
> **The Cog said:**
> Unity hides the application menu for some reason. It removes it from the application window itself, and puts it at the top of the screen, then puts the window title in fron of it to hide the actual menu items. In order to see the menu, you have to jam your cursor up to the top of the screen (regardless of where your window is placed). Then the menu appears across the top. You should find the Devices menu item up there.



Dear, The cog I did as you told and here it is 2 Screenshots of what I have. I can not see any Devices menu. Please help.

---

### Post by The Cog on 2011-10-30
I think Unity is causing confusion here. You are looking at the menu for the virtualbox control window, not the guest VM window. Unity hides the menu of the current foreground window behind its title at the top of the screen. If you click the win7 guest window to bring that to the fore, then the menu at the top will (should) show specific options for the guest VM as it is running. So I think you need to:

1: click the running guest window to make it the active window
2: shove the cursor to the top of the screen to reveal the menu
3: Choose Devices / Install Guest Additions

I attach a screenshot from a window manager where you can see the different menus for the different windows.

---

### Post by Ymurti on 2011-10-30
Dear The Cog,  I did as you told me:

1: click the running guest window to make it the active window
2: shove the cursor to the top of the screen to reveal the menu

But the menu is not revealed it is very frustrating. What should I do next? Please help!

---

### Post by The Cog on 2011-10-30
I don't know. I don't use unity, I use Xubuntu with XFCE. Maybe it's just not possible to use VirtualBox with Unity properly. 

Can someone who uses Unity and VirtualBox provide a clue as to how to get the the guest VM menu?

---

### Post by The Cog on 2011-10-30
This thread is getting buried. It may be worth starting a new thread with a title like "Cannot access VirtualBox menu in Unity" if you're sure it's unity that's hiding the menu from you.

---

### Post by Paqman on 2011-10-30
> **The Cog said:**
> 
Can someone who uses Unity and VirtualBox provide a clue as to how to get the the guest VM menu?

Depends how you're running Vbox (windowed/seamless/etc). You can either use the global menu at the top or the little pop-up menu at the bottom of the Vbox window.

---

### Post by Ymurti on 2011-10-30
> **The Cog said:**
> I think Unity is causing confusion here. You are looking at the menu for the virtualbox control window, not the guest VM window. Unity hides the menu of the current foreground window behind its title at the top of the screen. If you click the win7 guest window to bring that to the fore, then the menu at the top will (should) show specific options for the guest VM as it is running. So I think you need to:

1: click the running guest window to make it the active window
2: shove the cursor to the top of the screen to reveal the menu
3: Choose Devices / Install Guest Additions

I attach a screenshot from a window manager where you can see the different menus for the different windows.


Dear The Cog and all of you that tried to help. The problem is solved. I was able to install the VBoxWindoesAdditions.exe How? I so in the screenshot that The Cog has posted that you can press Host+D to install, I tried and did not work THEN I tried Alt+Ctrl+D and here it this the screenshot of what came::p

---

### Post by Ymurti on 2011-10-30
Thank You a lot.

---

### Post by The Cog on 2011-10-31
Oh that **is** good news. Thanks for letting us know.

---

### Post by TedinOz on 2011-11-06
Sorry to hijack this thread but I have a new problem here. I am running Unity on 11.04 and have installed XP on Virtual Box Version 4.0.4 installed from repositories. 
I understand most of the earlier explanations but not sure how to download the iso for VBoxGuestAdditions. When I run [HTML]sudo apt-get install virtualbox-guest-additions-iso[/HTML] in the Terminal I get this result...

```
 sudo apt-get install virtualbox-guest-additions-iso
[sudo] password for ted: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package virtualbox-guest-additions-iso
```


If someone can help me resolve this and I am able to get the iso file I think I will be ok with the rest of the procedure.

Hoping someone can help.

Thanks

---

### Post by Paqman on 2011-11-06
On 11.04 the package is just called [virtualbox-guest-additions]("apt:virtualbox-guest-additions") (click to install).

---

### Post by TedinOz on 2011-11-06
> **Paqman said:**
> On 11.04 the package is just called [virtualbox-guest-additions]("apt:virtualbox-guest-additions") (click to install).

Thank you so much! All installed and working now :)

---

