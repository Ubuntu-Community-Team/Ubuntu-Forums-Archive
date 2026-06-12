---
title: "Ubuntu Startup Customizations (Tutorial)"
date: 2011-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by LinuxPhreak on 2011-03-15
This is my first Tutorial. Everything I discuss should work in Ubuntu  10.04, 10.10 and 11.04 beta. I've tested these tweaks on Ubuntu 10.10  and Ubuntu 11.04. 

**[COLOR=Blue]Customise Ubuntu Login Screen[/COLOR]**

Starting  with Ubuntu 10.04 the uPower boot screen was add in replace of the  older uSplash boot screen. This made customizing the way Ubuntu starts  up even easier. If your not happy with the default login theme of Ubuntu  you can modify it by doing the following. 

[LIST]
[*]Changing the background image
[*]Changing the Window Theme
[/LIST]
To  modify the the background image of the Login Screen find an image that  you would like to use. I've tested it with JPEG images and it works  fine. I don't see why their would be problem with other image formats. 

Find an image that you want to use. Note the directory of where the image is stored. 

Next open up your terminal and type or copy and paste the following commands. 

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```

The  above command will copy the Appearance window to the location that  programs are stored that will startup automatically when you get to your  login screen. 

Now you will log out of your current Ubuntu  Session and when you do this the Appearance Window should show up  automatically. You can now change the Window theme to your liking just  as you would if you where customizing your Ubuntu User Account. 

Once  you have customized the login screen to your liking you can remove the  appearance program so it will not start up again the next you need to  Log In to your computer. To do this type the following commands. 

```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

Ubuntu  uses the metacity window manager at the login screen. You can replace  metacity with more graphical window manager such as compiz. Below I will  show you how to do this in more detail. 

First you will copy the compiz program to the proper location by typing the following commands. 

```
sudo cp /usr/share/applications/compiz.desktop /usr/share/gdm/autostart/LoginWindow
```

You can also remove the metacity program by using the following command. 

```
sudo rm /usr/share/gdm/autostart/LoginWindow/metacity.desktop
```

Now you will have nicer graphics at your login prompt. 

You  can even customize your compiz settings at your login prompt. The  easiest way I've found to do this is to install the GUI Compiz Setting  Manager. You install it by typing the following commands. 

```
sudo apt-get install compizconfig-settings-manager
```

Once  the settings manager has been installed you will want to make it  startup at the login screen automatically. To do this you will type the  following commands. 

```
sudo cp /usr/share/applications/ccsm.desktop /usr/share/gdm/autostart/LoginWindow
```

Then  you will logout of your Ubuntu User Account once again and when you do  this the Compiz Setting manager will startup. You will now be able to  customize the Compiz settings for your Login Screen. 

Once the  you have customized the compiz settings to your liking you can login to  your Ubuntu User account once again and remove the Compiz Setting  Manager by typing the following commands. 

```
sudo rm /usr/share/gdm/autostart/LoginWindow/ccsm.desktop
```

**[COLOR=Blue]Customize Plymouth Screen[/COLOR]**

Now  we may want to customise the plymouth splash screen. The easiest way to  do this is to modify Ubuntu's existing plymouth splash screen images.  These images can be found in the /lib/plymouth directory of Ubuntu and  the /lib/plymouth/themes/ubuntu-logo directory. Simply find the images  you want to use to replace those existing images and copy them into the  proper directories. For example.

```
sudo cp $HOME/Pictures/image.png /lib/plymouth
```

[COLOR=Red]NOTE:  You will need to rename all your images that you replacing to the exact  same name as the ones that your replacing. For example

If your  replacing ubuntu-logo.png with image.png then you will need to remove  ubuntu-logo.png and rename image.png to ubuntu-logo.png

[COLOR=Black]After you have replaced the images you will want to update your initramfs file. To do this type the following commands.

[/COLOR][/COLOR]```
sudo update-initramfs -u
```[COLOR=Red][COLOR=Black]

When you restart your computer the images should be replaced. 
[/COLOR][/COLOR][B][COLOR=Blue]
Customise GRUB2 Screen[/COLOR][/B]

Next  we will change the GRUB2 Splash screen. To do this we will need an  image that is in a PNG format. Then we will type the following commands  into our terminal. 

```
gksudo gedit /etc/default/grub
```

Then we will scroll all the way down the page and add the following lines. 

```
GRUB_BACKGROUND=/location/of/your/image
```

Then save your changes and exit out of the gedit window. Next type the following commands into the terminal.

```
sudo update-grub
```

Now you should have your new grub screen and a fully personalised Ubuntu Desktop.

---

### Post by LinuxPhreak on 2011-03-17
I've made video on how to do what I talked about in this tutorial. You can find it on YouTube at [http://www.youtube.com/watch?v=N9VhPZHzqvY](http://www.youtube.com/watch?v=N9VhPZHzqvY)

Please keep in mind that YouTube requires your web browser to have Flash installed. Flash is considered to be a restricted software and you can install it onto your browser by typing the following into your terminal. 

```
sudo apt-get install flashplugin-installer
```

An alternative solution if you don't want to use propriotory software is to install Firefox 4 beta and sign up to You Tube's HTML5 beta test site.

---

### Post by X10A on 2011-03-18
When I switch my login background, my visual settings reset to the lowest possible setting. And when I switch it back "extra effects", my custom login background is erased.  Also I cannot change the plymouth screen. Does my new image have to be the same size as the default image?

---

### Post by LinuxPhreak on 2011-03-26
> **X10A said:**
> When I switch my login background, my visual settings reset to the lowest possible setting. And when I switch it back "extra effects", my custom login background is erased.  Also I cannot change the plymouth screen. Does my new image have to be the same size as the default image?

The visual settings could be a driver problem. If your using restricted drivers in some cases they wont start up until after you have logged in. 

About the plymouth. I usually take all of the existing images from the plymouth theme and use GIMP to modify them. I then copy them to the original location. I also take not of the pemisions of the image. 

Images should have the following permissions. 

Owner = root Read and Write
Grouo = root Read Only
Other = Read Only 

Do not allow executing.

---

### Post by X10A on 2011-03-26
WIth my new image, I changed the name of the file in /Pictures and then using the terminal, moved it to the plymouth folder, replacing the default image. But when I boot up, the plymouth image is still unchanged.  My plymouth image permissions are the same as the ones you specified.

---

### Post by LinuxPhreak on 2011-04-01
> **X10A said:**
> WIth my new image, I changed the name of the file in /Pictures and then using the terminal, moved it to the plymouth folder, replacing the default image. But when I boot up, the plymouth image is still unchanged.  My plymouth image permissions are the same as the ones you specified.

After you have replaced the plymouth images you will need to issue the following commands. 

```
sudo update-initramfs -u
```

---

### Post by X10A on 2011-04-03
I did that during my first try. And it didn't work. Does the image have to be the same size as the default ubuntu image?

---

