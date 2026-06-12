---
title: "I've deleted my GUI or I need to restore files from a live cd"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by samemistake2 on 2008-08-15
I've deleted my GUI (don't ask me how, happened ages ago while I was messing around with things that I don't understand). 

I can't run apt-get update or apt-get install ubuntu-desktop because I can't connect to the internet.

Ideally I would like to reinstall my GUI. If that's not possible then I would at least like to get my files using a live cd. I've been tinkering with that for a while and getting nowhere.

I'm becoming rather despondent. Please help.

Thanks.

P.S. The kind of person who would delete their GUI obviously is going to need some very basic help. Please keep that in mind.

---

### Post by Crafty Kisses on 2008-08-15
Have you tried reconfiguring X?
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tvtech on 2008-08-15
ok so you've fragged your os and now your feeling a little like your screwed becuase you've done it on a production computer and you need to get it back?  if that sounds right I've done the same.  okay so you need to access your drives from a live cd. that's fairly easy.  you'll need to pop in your live cd and get it up and running.  if you can get online with another computer and download knoppix it's a little better live cd in my opinion!  you'll need to go to places on your task bar in the live cd if it's ubuntu and then go to computer.  I might have to think about this for a minute or pop a live cd in so gimme a moment you might need to manually mount your drives but if you can find them you should be able to double click on them and they should auto mount and show up on your live cd desktop

yup yup ok so get the live cd running if it's a viewable drive it will show it under the places tab and then you can just click on it to mount it. and then you can access it and back up your files.

---

### Post by samemistake2 on 2008-08-15
I'll try that. Thanks for your quick reply.

---

### Post by jerome1232 on 2008-08-15
You can also edit /etc/apt/sources.list and uncomment (delete the '#' signs) any line that has "cdrom" in it (usually two at the top)
After making the changes in nano use ctrl+x to exit then hit enter then 'y' to save

```
sudo nano /etc/apt/sources.list
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by samemistake2 on 2008-08-15
> **Codename said:**
> Have you tried reconfiguring X?
```
sudo dpkg-reconfigure xserver-xorg
```

I got as selecting the color depth and this popped up

```
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf .20080815203713
```

---

### Post by samemistake2 on 2008-08-15
> **tvtech said:**
> ok so you've fragged your os and now your feeling a little like your screwed becuase you've done it on a production computer and you need to get it back?  if that sounds right I've done the same.  okay so you need to access your drives from a live cd. that's fairly easy.  you'll need to pop in your live cd and get it up and running.  if you can get online with another computer and download knoppix it's a little better live cd in my opinion!  you'll need to go to places on your task bar in the live cd if it's ubuntu and then go to computer.  I might have to think about this for a minute or pop a live cd in so gimme a moment you might need to manually mount your drives but if you can find them you should be able to double click on them and they should auto mount and show up on your live cd desktop

yup yup ok so get the live cd running if it's a viewable drive it will show it under the places tab and then you can just click on it to mount it. and then you can access it and back up your files.

Okay I've got the live cd running. I go to places->computer->53.6 GB volume and...

Unable to mount the selected volume

error:device /dev/hda1 is not removable
error: could not execute pmount

---

### Post by jerome1232 on 2008-08-19
You might want to try installing testdisk/photorec on your livecd they can recover files from corrupt volumes and restore partition tables.

---

