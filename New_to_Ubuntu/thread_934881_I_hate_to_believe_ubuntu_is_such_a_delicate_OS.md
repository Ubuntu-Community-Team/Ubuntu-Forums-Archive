---
title: "I hate to believe ubuntu is such a delicate OS"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by bobigeorge on 2008-10-01
Hello

I have to write these because I love Ubuntu for its stability. 

But all one need to hang Ubuntu 8.04 installed on my HP520 laptop is to insert a video cd into it!!!! Totem opens by default and remains stuck forever.... The only thing left with me is to restart my lap by HITTING THE POWER BUTTON(which I hate most) 

I am open to suggestions..

Thanks in advance

---

### Post by iaculallad on 2008-10-01
If you could access your Terminal:

For Shutdown

```
sudo shutdown -h now
```

EDIT: Or for Restart

```
sudo shutdown -r now
```

---

### Post by lisati on 2008-10-01
There are other media players that might suit you better. Have a look [here]("https://help.ubuntu.com/8.04/musicvideophotos/C/index.html") for some ideas.

---

### Post by rybaxs on 2008-10-01
try to play other movie and use other player.. does your Laptop have dual OS?

---

### Post by kpkeerthi on 2008-10-01
Go to menu System -> Preferences -> Removable drives and media -> Multimedia tab, and turn off totem from autoloading. Try mplayer in place of totem.

---

### Post by bobigeorge on 2008-10-02
Thank you for your quick replay... NO I can't access my terminal... only thing I am left with is to restart by power switch..

---

### Post by bobigeorge on 2008-10-02
Thanks kpkeerthi.. But there is no multimedia tab in mh System -> Preferences -> Removable drives and media -> I am using Ubuntu 8.04

---

### Post by rbc on 2008-10-02
Yeah. The multimedia tab is now under System-->Preferences-->Preferred Applications, but there is nothing to un-check to stop Totem from starting. One thing you can try is this: Alt+F2, then type gconf-editor. When the window opens, navigate to apps/nautilus/preferences, then uncheck media_automount_open. Keep in mind though, this will prevent all removable media from opening (not mounting, but opening), including thumb drives. You may or may not want that. Still don't know if this is going to help with the shutdown problem

---

### Post by whizbaby on 2008-10-02
I dont know if this is the matter here, but which model do you have, the one with 1GB RAM or one of those with 512MB RAM? I had several video playback issues with gnome (and kde) on a small dell laptop with 512MB RAM and 1Ghz CPU. It didnt matter if the movie was from CD/DVD or streaming from the net. Switching to enlightenment solved my video problem. But as I said in the beginning, it might have nothing to do with your problem.

---

### Post by perlluver on 2008-10-02
Also you never have to use the power switch, instead you would press Ctrl>Print Screen/SysRQ>REISUB, that will shut down the hard drive, and reboot.  That is the magic key combination for Linux.

---

### Post by binbash on 2008-10-02
dude remove totem and install vlc.try to open the dvds with that

---

### Post by philinux on 2008-10-02
To gently restart system it's ALT SysRq
[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

To stop totem autostarting look in Nautilus Edit>Prefs>Media

---

### Post by JoshuaRL on 2008-10-02
For specific media, right click it and go to Preferences>Open With.  Then choose your desired application.  I, like many here, prefer VLC for all video.

---

### Post by KIAaze on 2008-10-02
This thread also mentions this bug:
[http://ubuntuforums.org/showthread.php?t=26834](http://ubuntuforums.org/showthread.php?t=26834)

The fact that totem freezes or crashes definitely shouldn't freeze the whole system.
This is a critical bug and should be reported.
Actually, it seems it has already been reported here:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/233896](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/233896)

If it's just X that freezes, you should be able to get back to the login screen by hitting CTRL+ALT+backspace.

Please run the following command from a terminal to store the command-line output in a text file (necessary since it seems to crash the system):
```
totem 1>totem.log 2>&1
```

This may help figuring out what happens.

---

