---
title: "HOWTO : Install Adobe flash for Firefox and fix sound issues (Ubuntu Dapper 32-bit)"
date: 2006-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by epennings on 2006-10-12
**Important notes :** 

edit :
Most of the information in this guide can also be found here:
[https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3]("https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3")
You should try installing Flash using that guide first.

This HOWTO is meant for the 32-bit version of Ubuntu Dapper. I cannot garantuee it works for other versions of Ubuntu.

I assume you use the default Ubuntu version of Firefox. If you have another version make sure you know the installation path.

I use the manual method to install Flash. Installing the **flashplugin-nonfree** package never works for me. You should uninstall it before using this HOWTO.


**Before installing**

Make sure you have enabled universe/multiverse repositories : [[COLOR="RoyalBlue"]HOWTO[/COLOR]]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

Update you system :
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Flash requires 2 fontpackages to be installed :
```

sudo apt-get install gsfonts gsfonts-x11
```

**Dowloading and installing Adobe Flash**

Download the latest installer from Adobe :
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz 
```

Extract the files from the archive : 
```
tar -zxf install_flash_player_7_linux.tar.gz
```

**[COLOR="Red"]*** You have to close your browser for the next 2 steps ***[/COLOR]**

Run the installer :
```
sudo install_flash_player_7_linux/flashplayer-installer
```

When asked to enter an installation path enter the path where you browser is  installed (/usr/lib/firefox by default)
```
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):**/usr/lib/firefox**
```

The installer should complete without errors. To confirm that the plugin is installed correctly start Firefox and type the following in the navigation bar :
```

about:plugins
```

You should see something like this :
```
Shockwave Flash

    File name: /usr/lib/firefox/plugins/libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

If you dont see it you probably installed the flash plugin in the wrong path.


**Fixing (sound) issues**

Most issues I had with Flash are related to sound. Possible issues are :
- Firefox freezing/crashing while/after viewing a flash movie
- No sound in flash
- Very bad syncing
- Movies on Youtube or Google video stop playing afer 1/2 seconds

The most common fix is this one :
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

Flash expects /temp/.esd to exist, to fix this type :
```
ln -s /tmp/.esd-1000 /tmp/.esd
```

To prevent having to retype this everytime you start your computer you could add the above command to rc.local :
```
sudo gedit /etc/rc.local
```

If the sound still isn't working properly you could try the fix discribed [[COLOR="RoyalBlue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=255422&highlight=flash")

Another fix is discribed [[COLOR="RoyalBlue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=186594&highlight=flash")

**end of HOWTO**

I hope this helped you to get Flash working correctly. If you have any additions/corrections to this guide please let me know. I'd also like to know if it worked for other versions of Ubuntu and/or other browsers.

---

### Post by PriceChild on 2006-10-12
It is important to note that you should first attempt this wiki:
[https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3](https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3)

---

### Post by TrendyDark on 2006-10-12
The sound problem can be fixed by simply making firefox/Flash use AOSS for sound. Takes about 2 seconds :)

---

### Post by dannyboy79 on 2006-10-12
do these instructions work for Opera? Firefox is way to slow on my P MMX 266mhz 128mb ram running Xubuntu. Opera just flys. I was able to install Adobe Reader from scratch, next gonna try flash but was wondering if I should follow this? Thanks for any suggestions.

---

### Post by epennings on 2006-10-12
The installer is compatible with Opera, just install it in the right path.
 I'm not sure your computer has the minimum requirements for Flash, it will probably run a bit choppy.

---

### Post by desperado666 on 2006-10-12
If you encounter flas sound problems with opera start opera with this argument
"aoss opera"

you may need to install 

 * alsa-oss

Further instructions can be found here

[http://wiki.ubuntuusers.de/Opera/Multimedia](http://wiki.ubuntuusers.de/Opera/Multimedia)
and here
[https://help.ubuntu.com/community/OperaBrowser?highlight=%28opera%29#head-801db7120330e998f5a482a4c5b7629458c6f32f](https://help.ubuntu.com/community/OperaBrowser?highlight=%28opera%29#head-801db7120330e998f5a482a4c5b7629458c6f32f)

---

### Post by steveneddy on 2006-11-05
I manually downloaded flash version 9 beta for linux and manually installed in correct folder and it looks beautiful and acts more predictably than the version 7. 

No probs and no issues.

NOTE-you need to do this with Firefox off, not open.

-SE

---

### Post by Deeman on 2007-07-25
OK, I will probably not get a reply because I just have to vent..  I am new, totally new and after installing Adobe Flash I have no sound at all!  I am trying not to get frustrated but I will admit that I think I am losing the battle.  I have tried this fix and no dice.

---

