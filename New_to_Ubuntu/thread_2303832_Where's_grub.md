---
title: "Where's grub"
date: 2015-11-21
forum: New to Ubuntu
---

### Post by nathan89 on 2015-11-21
I've installed Ubuntu 14.04 64 bit twice now, different ISO downloads. I just tried a fresh install, the one that wipes everything. I also set up an encryption. When I start my laptop, it goes into a purple screen for a couple of seconds, and then the screen goes black. (There's no text from grub or anything on the purple screen.)  When I mean the screen goes black I don't mean illuminated black, I mean off. I figured if I type in my encryption password it might do something, and it actually did; it booted the os. 
My two questions are, where's the grub selections and is the screen supposed to turn off when typing in the encryption password?
I've installed Ubuntu on this laptop before without issues.

---

### Post by blade4 on 2015-11-21
Try adding "nomodeset" to the grub settings. If this works, the issue is with the video drivers and you may want to update them. Here's how :   ```
sudo gedit /etc/default/grub
```  Find the line that says GRUB_CMDLINE_LINUX, and insert the parameter there ( for example add it after the "quiet " parameter that most likely is there ).  Now update the grub configuration:  ```
sudo update-grub
```  Then reboot the system  As to your other question, no the screen is not supposed to turn off when entering passwords.

---

### Post by nathan89 on 2015-11-22
Well the screen no longer goes black when I have to enter the encryption password but grub is still completely purple with no options. Changing graphics drivers to nvidia didn't fix it.

---

### Post by blade4 on 2015-11-22
> [COLOR=#000000]Well the screen no longer goes black when I have to enter the encryption password but grub is still completely purple with no options. Changing graphics drivers to nvidia didn't fix it.[/COLOR]

In your grub file, is the line "[COLOR=#000000][FONT=monospace]GRUB_HIDDEN_TIMEOUT" listed without a hastag ? The default configuration should be something like this : 

[/FONT][/COLOR]```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

```

---

### Post by oldfred on 2015-11-22
With only one install, grub menu does not appear normally. Only after a abnormal shutdown.
With BIOS you can hold shift key from BIOS until menu appears. With UEFI you press escape key, perhaps several times.

What video card/chip?
You can add nomodeset during boot, as you normally do not want it after you install correct version proprietary driver for your video card. You may want grub menu and remove nomodeset if you added as permanent boot parameter.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by nathan89 on 2015-11-22
> **blade4 said:**
> In your grub file, is the line "[COLOR=#000000][FONT=monospace]GRUB_HIDDEN_TIMEOUT" listed without a hastag ? The default configuration should be something like this : 

[/FONT][/COLOR]```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

```




It didn't have the hashtag before. I add the hashtag, updated grub, and rebooted. It works now, thanks! There is one other thing. Whenever I type in 1 letter or hit save while editing grub in gedit. It gives me this in the terminal. 

[IMG]http://i.imgur.com/NjFUBVB.jpg[/IMG]

---

### Post by nathan89 on 2015-11-22
> **oldfred said:**
> With only one install, grub menu does not appear normally. Only after a abnormal shutdown.
With BIOS you can hold shift key from BIOS until menu appears. With UEFI you press escape key, perhaps several times.

What video card/chip?
You can add nomodeset during boot, as you normally do not want it after you install correct version proprietary driver for your video card. You may want grub menu and remove nomodeset if you added as permanent boot parameter.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Edit: I just realized I might have been replying without quoting. 

The grub menu didn't appear with windows installed either. I hadn't touched the windows partition at the time. 

My laptop has a NVIDIA Quadro NVS 160M. (It's an old laptop I got off of Craigslist.) I would normally install the nvidia drivers but the nouveau drivers have MUCH better 2d performance. Sure, the NVIDIA drivers have the best 3d performance, but if I'm not playing any games, I'd much rather be able to move a window around or scroll smoothly. 

I just added nomodeset after quiet splash. It works now so I'm probably going to keep it like that.

---

### Post by grahammechanical on 2015-11-22
What you are seeing with Gedit is not happening because you are editing /etc/default/grub but because you are loading Gedit from the terminal. And it is better when loading Gedit or the file manager with administrator privileges  to use sudo -H and not just sudo.

The Grub manual says 
> 
‘GRUB_TIMEOUT’
Boot the default entry this many seconds after the menu is displayed, unless a key is pressed. The default is ‘5’. Set to ‘0’ to boot immediately without displaying the menu, or to ‘-1’ to wait indefinitely.

‘GRUB_HIDDEN_TIMEOUT’
Wait this many seconds for a key to be pressed before displaying the menu. If no key is pressed during that time, display the menu for the number of seconds specified in GRUB TIMEOUT before booting the default entry. We expect that most people who use GRUB HIDDEN TIMEOUT will want to have GRUB TIMEOUT set to ‘0’ so that the menu is not displayed at all unless a key is pressed. Unset by default. 

In Ubuntu the default for GRUB_TIMEOUT is 10 seconds and for GRUB_HIDDEN_TIMEOUT to be commented out with a #. In other words GRUB_HIDDEN_TIMEOUT is not used by Grub. You tell us that GRUB_HIDDEN_TIMEOUT was not commented out. So, what time delay do you have for GRUB_TIMEOUT? Zero?

Regards.

---

### Post by nathan89 on 2015-11-22
> **grahammechanical said:**
> What you are seeing with Gedit is not happening because you are editing /etc/default/grub but because you are loading Gedit from the terminal. And it is better when loading Gedit or the file manager with administrator privileges  to use sudo -H and not just sudo.

The Grub manual says 


In Ubuntu the default for GRUB_TIMEOUT is 10 seconds and for GRUB_HIDDEN_TIMEOUT to be commented out with a #. In other words GRUB_HIDDEN_TIMEOUT is not used by Grub. You tell us that GRUB_HIDDEN_TIMEOUT was not commented out. So, what time delay do you have for GRUB_TIMEOUT? Zero?

Regards.

I added -H after sudo but nothing changed. I still get that error in the picture. Anyway, it still opens. GRUB_HIDDEN_TIMEOUT was set to 0

---

### Post by oldfred on 2015-11-22
It used to be that you had to use gksudo for all graphical apps.
But now they do not include gksudo on live installer. Something about using pkexec, but I do not know.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

I now use this for editing system files.
sudo nano /etc/default/grub

---

### Post by blade4 on 2015-11-22
Good to know your boot problem is solved.

 > [COLOR=#000000]Whenever I type in 1 letter or hit save while editing grub in gedit. It gives me this in the terminal.[/COLOR]

Like oldfred says , the warning is related to gksudo not being used ( sudo was - and mostly still is - reserved for terminal based operations while gksudo was for operations involving GUI ). This will happen every time you invoke a GUI based application that uses GTK with sudo ( happens to me too when I invoke nautilus this way ) . No worries though , everything will still perform as intended with just sudo and you can ignore the warnings for normal usage. But ,if you don't want any warning messages, nano is also a good alternative.  

Also, I think keeping *nomodeset* should be fine so long as you're using noveau drivers. Nvidia drivers will probably not need this option though.

---

