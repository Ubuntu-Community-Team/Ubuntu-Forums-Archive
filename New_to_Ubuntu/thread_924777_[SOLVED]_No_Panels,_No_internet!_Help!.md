---
title: "[SOLVED] No Panels, No internet! Help!"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by uberdonkey5 on 2008-09-19
I was messing around installing new themes and wall papers and also removed evolution. When I rebooted my panels were gone. Luckily I have nautilus script to open terminal, so that really easy.

HOWEVER all the posts here suggest sudo apt-get update
or upgrade. The only internet connection I have is vodafone connect pen. Does anyone know how to connect to internet with this from the terminal? (it is configured).

I read this thread:
[http://ubuntuforums.org/showthread.php?t=781683&highlight=lost+panels](http://ubuntuforums.org/showthread.php?t=781683&highlight=lost+panels)
but the file doesn't exist. So I am presuming I must connect to internet if I want my panels back!

Many thanks

---

### Post by adult swim on 2008-09-19
hit alt-f2 and type in ```
metacity --replace
```

---

### Post by uberdonkey5 on 2008-09-19
thanks for rapid reply adultswim, but doesn't seem to do anything...just freezes the terminal. I fear that I have actually removed the software for the panels somehow (though they were working fine before I shut down). Any other suggestions?

---

### Post by kansasnoob on 2008-09-19
Try:

```
 sudo apt-get install --reinstall ubuntu-desktop
```

```
 sudo apt-get -f install
```

```
 sudo apt-get update
```

```
 sudo apt-get upgrade
```

---

### Post by Therion on 2008-09-19
Drop to a terminal by hitting CTRL + ALT + F1.
Login to your account, and run this command:```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
Get back to your GUI desktop by hitting CTRL + ALT + F7.

Before any one freaks out over the **rm -rf** command I found the solution above [HERE](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/):

Or if you prefer:

h**p://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/

---

### Post by kansasnoob on 2008-09-19
Oh, and I don't know what vodafone is:

> HOWEVER all the posts here suggest sudo apt-get update
or upgrade. The only internet connection I have is vodafone connect pen. Does anyone know how to connect to internet with this from the terminal? (it is configured).

But to reinstall ubuntu-desktop you can put your live cd in and change settings in Software Sources.

[ATTACH]85844[/ATTACH]

See where it says Cd Rom?

---

### Post by lswb on 2008-09-19
Try this command from the terminal or Alt-F2

gnome-panel

---

### Post by uberdonkey5 on 2008-09-20
> **kansasnoob said:**
> Oh, and I don't know what vodafone is:



But to reinstall ubuntu-desktop you can put your live cd in and change settings in Software Sources.

[ATTACH]85844[/ATTACH]

See where it says Cd Rom?

WOW, I think this may be it. I always forget about CD ROM. I only have the terminal, but think I can run synaptic using terminal and thus make sure CD is selected as the repository. I'll try now

P.S. vodafone is a phone company that. Basically I have a usb pen which acts like a modem. Thus, without internet I just get repositories not found.

PPS. I was afraid of removing those files (not that I am worried about the remove command mentioned above, but because I had spent so much time customising ubuntu I ideally wanted a better solution). Also, I don't think the default will come back because it is not there?

---

### Post by uberdonkey5 on 2008-09-20
ok, after running sudo synaptic from terminal and selecting CD ROM I found that gnome-panel was listed as not installed. I tried to add it, but said couldn't because of problem as no available version but exists in the database. Therefore I uninstalled it, hoping to reinstall it. But when the repository list was reloaded it wasn't there. (fails to fetch archives).

Thus, maybe a problem with disk. I have another copy somewhere and can connect on Monday at work to LAN. However, still, if anyone knows how to run vodafone connect pen software from terminal, would be pleased to hear.

thanks

---

### Post by uberdonkey5 on 2008-09-20
I've done it thanks to all of the help above! Here is what I did:

1. right click on desktop and create folder. Having a folder on your desktop allows you easy access (window driven) to the file system and search capability.

2. Within the trash I found an old copy of my vodafone mobile connect pen driver. I copied this to the desktop. An alternative is to search for the driver on your computer (I was spelling it wrong, so missed this). My vodafone connect pen driver was found in this directory: usr/bin/

3. I plugged in my pen and double clicked on the driver to run it

4. In the terminal I typed*:

sudo apt-get install --reinstall ubuntu-desktop

this reinstalled evolution and gnome orca etc. Then I typed:

gnome-panel

which displayed the main panel

(NB. it is likely the CD would have worked as the repository instead, if it had been working properly! 

===============================

THANKS so much everyone. Hope this helps someone in the future as well.


*( I tried metacity --replace and sudo apt-get update but these had no effect)

---

### Post by uberdonkey5 on 2008-09-20
.

---

