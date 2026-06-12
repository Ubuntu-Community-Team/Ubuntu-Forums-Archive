---
title: "How to play flash based games"
date: 2015-07-25
forum: New to Ubuntu
---

### Post by gimmkis on 2015-07-25
Hello to all the Ubuntu people!:p
Total new to linux.
1)I installed ubuntu on a 4GB usb stick to drive a Vaio laptop with no hard drive on.
2)Ubuntu seems to work fine without installing it, since there's no HD.
3)Ubuntu's firefox works fine, all video sites like youtube work fine, but when i go to flash based game WAR2 it says i have to install flash player.
4)I read some threads here about installing a flash plugin, so when i paste the command 
[I]
sudo apt-get update && sudo apt-get install adobe-flashplugin[/I]

[FONT=verdana]in the terminal, it starts to work and at the end it says:[/FONT]

[FONT=courier new]"Reading package lists...done
 Reading package lists...done
 Building depedency tree
 Reading state information...Done
 E: Unable to locate package adobe-flashplugin
 ubuntu@ubuntu:~$ "[/FONT]

[FONT=verdana]So, does this mean i have to download some adobe-flashplugin file first? 

[/FONT][FONT=verdana]
[/FONT]

---

### Post by howefield on 2015-07-25
Try flashplugin-installer instead..

```
sudo apt-get install flashplugin-installer
```

---

### Post by gimmkis on 2015-07-25
Nope.  that command didn't work either. I still get the " [FONT=courier new]E: Unable to locate package [/FONT]flashplugin-installer[FONT=courier new] "

i also downloaded  [I]flashplayer_11_plugin_debug.i386.tar.gz .
 [/I]**Is this the right file?**
[/FONT]

---

### Post by Bucky Ball on 2015-07-25
No. The one howefield suggested is the one you should be going for. If you are getting the error 'Unable to locate package flashplugin-installer' then something is odd as that package is in the Ubuntu repositories.

Does it show up in Software Centre when you search for it? Do you have the Ubuntu partner repositories enabled (not sure but this might be necessary)?

---

### Post by gimmkis on 2015-07-26
No i don't see it in Software Cetre. Cause i'm a newbie  i thought i should download it first.
**Please explain step by step how i  enable the Ubuntu partner repositories .**
Another odd is that neither firefox keeps the bookmarks and browsing history, nor the ubuntu>downloads itself keep the downloaded files when i reboot ubuntu.

---

### Post by ajgreeny on 2015-07-26
I think you  are using a live system which would explain your problem. If you have any way to install the OS fully to a larger USB, not just live, you may find you can install that flashplugin-installer.
The system may run too slowly from USB, however, and make these games unplayable, but it's worth a try.

---

### Post by howefield on 2015-07-26
> **gimmkis said:**
> No i don't see it in Software Cetre. Cause i'm a newbie  i thought i should download it first.
**Please explain step by step how i  enable the Ubuntu partner repositories .**
Another odd is that neither firefox keeps the bookmarks and browsing history, nor the ubuntu>downloads itself keep the downloaded files when i reboot ubuntu.

How did you make the USB installation ?

If you used the Startup Disk Creator to make a Live USB image, you would need to drag the slider in the option "Stored in reserved space" as far as it will go. This will create a disk that will maintain states between reboots.

---

### Post by gimmkis on 2015-07-26
Now really, come on you guys, as a newbie i followed the instructions here [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows).
It's not mentioned there that it's all about a Live USB image , is it?
it's not even mentioned anything about the other configurations you talk about.
So, as far as i know , and since it seemed to work fine, working with the laptop and firefox and all, i followed everything by the book.
So, looking for a hard drive now to have a full instalation.;)

---

### Post by howefield on 2015-07-26
> **gimmkis said:**
> Now really, come on you guys, as a newbie i followed the instructions here [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows).
It's not mentioned there that it's all about a Live USB image , is it?
it's not even mentioned anything about the other configurations you talk about.
So, as far as i know , and since it seemed to work fine, working with the laptop and firefox and all, i followed everything by the book.
So, looking for a hard drive now to have a full instalation.;)

Never mind with the "Now really, come on you guys" - that page does exactly what it says on the tin.. showing you "How to create a bootable USB stick on Windows".

There is an option to set a persistence file which will maintain states between reboots.

---

