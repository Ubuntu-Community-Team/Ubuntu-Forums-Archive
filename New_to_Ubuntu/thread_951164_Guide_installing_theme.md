---
title: "Guide installing theme"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Optimus_Jazz on 2008-10-17
Hi,

i am attempting to install a mac os theme,im quite new to ubuntu and am having some difficulites.Any help would be appreciated!

I am using this guide and the downloads that come with it

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)


Now the first problem im encountering is finding AWN manager,which in the instructions said it can be found at

System->Preferences->AWN manager.

But it is not here.

I tried to see if i needed to install it but when i try to do this i get an error

[[IMG]http://img221.imageshack.us/img221/729/screenshotgnomeappinstaed1.th.png[/IMG]](http://img221.imageshack.us/my.php?image=screenshotgnomeappinstaed1.png)[[IMG]http://img221.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

I think its because i edited the source.list with the code provided for installing the dock.Any idea on were i go next?
Thanks,
J

---

### Post by perlluver on 2008-10-17
What exactly is the error you are getting?

---

### Post by perlluver on 2008-10-17
Ok in the terminal, run sudo apt-get update, and then try to install them files again, ```
sudo apt-get install avant-window-navigator-trunk awn-manager-trunk awn-extras-applets-trunk
```   Awn is also available through synaptic, and add/remove programs.  Called Avant Window Navigator.

---

### Post by Optimus_Jazz on 2008-10-17
> **perlluver said:**
> Ok in the terminal, run sudo apt-get update, and then try to install them files again, ```
sudo apt-get install avant-window-navigator-trunk awn-manager-trunk awn-extras-applets-trunk
```   Awn is also available through synaptic, and add/remove programs.  Called Avant Window Navigator.



Thanks i managed to get through this step,it was my error as i entered the sudo code into the source.list file (i am quite tired)

I am now having trouble applying the elegent glass theme.
I have downloaded the folder,and extracted it to the correct folder.
When i usm awn managed to select the Elegant_glass.tgz file the folder is empty:confused:

---

### Post by perlluver on 2008-10-17
> **Optimus_Jazz said:**
> Thanks i managed to get through this step,it was my error as i entered the sudo code into the source.list file (i am quite tired)

I am now having trouble applying the elegent glass theme.
I have downloaded the folder,and extracted it to the correct folder.
When i usm awn managed to select the Elegant_glass.tgz file the folder is empty:confused:

I am thinking you have to extract it from the tar.gz file, to use it.

---

### Post by Optimus_Jazz on 2008-10-17
> **perlluver said:**
> I am thinking you have to extract it from the tar.gz file, to use it.

could you guide me through this.

When i open the folder there is know tar.gz file.Only a Theme.awn and Thumbs.png file.

---

### Post by Optimus_Jazz on 2008-10-17
unfortunatly this is turning out to be a disaster.
When installing the dock i deleted my top panel!So everything is gone :(
Is there anyway to restore this?

---

### Post by Optimus_Jazz on 2008-10-17
Have now tried to install fonts and using the code word for word it is not working.I am getting an error message dispalyed each time

[[IMG]http://img235.imageshack.us/img235/6326/screenshotjonathanjonatyz8.th.png[/IMG]](http://img235.imageshack.us/my.php?image=screenshotjonathanjonatyz8.png)[[IMG]http://img235.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

