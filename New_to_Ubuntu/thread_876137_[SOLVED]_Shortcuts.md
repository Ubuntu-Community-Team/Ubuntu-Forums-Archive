---
title: "[SOLVED] Shortcuts"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by NaF on 2008-07-31
Transferred my WoW game folder to my Linux partition. How can I place an icon on the desktop with the WoW logo, that'll launch ```
'/home/naf/.wine/drive_c/Program Files/Games/World of Warcraft/Wow.exe' -opengl
``` 	:shock:

---

### Post by LowSky on 2008-07-31
you cant just transfer the game folder. You need to install WoW.
got instructions from here [http://ubuntu-tutorials.com/2006/12/19/how-to-install-play-world-of-warcraft-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/19/how-to-install-play-world-of-warcraft-ubuntu-510-6061-610/)

I'm asuming you alwready installed WINE
When this is finished run: 


ALT-F2 : ```
wine path/to/warcraft/installation/Install.exe 
```


(you can also optionally copy the World of Warcraft folder from a Windows installation.)

You&#8217;ve now got World of Warcraft installed and just about ready to play. You&#8217;ll want to tweak one more thing before you get going though.

World of Warcraft seems to work best using OSS audio. To set this you can do the following:


ALT-F2 : ```
winecfg
```


In the resulting menu select &#8220;Audio&#8221; and then select &#8220;OSS driver&#8221;

.. and then one last thing before you get playing. You&#8217;ll need to add a few lines to a configuration file and then you should be in business.


ALT-F2 : ```
gksudo gedit path/to/warcraft/installation/WTF/config.WTF 
```

add the lines:

```

SET SoundOutputSystem &#8220;1&#8243;
SET SoundBufferSize &#8220;100&#8243;
SET gxApi &#8220;OpenGL&#8221; 
```

Happy gaming. Ooh, I nearly forgot. To launch Warcraft you can use the following command or create a launcher with this path:

```
wine path/to/warcraft/installation/WoW.exe
```

---

### Post by eightmillion on 2008-07-31
Create a text file with the following contents.
```

[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=World of Warcraft
Exec=wine ~/.wine/drive_c/Program Files/Games/World of Warcraft/Wow.exe -opengl
Icon=/path/to/wowicon.png
Terminal=false
Type=Application
StartupNotify=false

```
You'll have to specify the proper path to your wow icon. Save this file as "wow.desktop" and drop it on your desktop and you should be good to go.

---

### Post by Separ on 2008-07-31
You CAN actually just transfer the folder as it installs next to useless information in the registry.

Just add "SET gxApi opengl" in the config.wtf file.

To add a shortcut to the desktop:

Right click Desktop, Create Launcher, Call it w/e you want, in command put "wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe" (without quotes)

and you are done :)

---

### Post by NaF on 2008-07-31
This is just beyond me, holy moly - what's wrong with a simple "right click" - "shortcut" and the thing will open with some random default application. hmpf. I really can't get anything you guys says to work. Don't wanna install it again, since that takes forever. running the launch command you suggested doesn't load properly, aka doesn't do ****. when there's "wine" in the command, do i have to specify that it's in the /.wine folder, or wat? Anyhow, think I'll just stick with my current way of opening the terminal and ```
sudo [path_to_wow] -opengl
```

---

### Post by eightmillion on 2008-07-31
I think the problem with my "solution" may be that you have to specify the full path.

You might try changing this line:
> Exec=wine ~/.wine/drive_c/Program Files/Games/World of Warcraft/Wow.exe -opengl
To this:
> Exec=wine /home/naf/.wine/drive_c/Program Files/Games/World of Warcraft/Wow.exe -opengl

---

### Post by Paqman on 2008-07-31
You can install World of Warcraft in a couple of mouse clicks using Wine Doors.

You can get [Wine Doors from Getdeb](http://www.getdeb.net/app/Wine-Doors).

---

### Post by NaF on 2008-08-01
> **eightmillion said:**
> I think the problem with my "solution" may be that you have to specify the full path.

You might try changing this line:

To this:

Weee! Got it working by adding '' in the filepath, dno if it's right - but it makes it work ;) ```
wine '/home/naf/.wine/drive_c/Program Files/Games/World of Warcraft/Wow.exe' -opengl 
```

---

### Post by NaF on 2008-08-01
> **Paqman said:**
> You can install World of Warcraft in a couple of mouse clicks using Wine Doors.

You can get [Wine Doors from Getdeb](http://www.getdeb.net/app/Wine-Doors).

Installed wine-door, but can't seem to figure out how to install WoW from it :)

---

