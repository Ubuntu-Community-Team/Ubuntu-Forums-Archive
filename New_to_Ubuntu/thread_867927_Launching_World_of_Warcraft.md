---
title: "Launching World of Warcraft"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Sithely on 2008-07-23
Hi,
I'm new to Linux but so far I'm loving Ubuntu.  I followed the guide from here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) and I got warcraft to install and run, but I have to open the actual folders and find wow.exe to get it to work.

I tried the method shown there:
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Exec=wine /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
Icon=WoW.svg
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=false

and it does make an icon in my applications/games for wow but when I click it, it won't launch.

I've tried changing the exec line with my path but still no luck. I copied my installation from windows to Ubuntu and it's in /home/sithely/World of Warcraft  (sithely being my username)

I'd greatly appreciate some help with this.

Thanks

---

### Post by Flyingjester on 2008-07-23
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329) following the instructions on the bottom of the page might help you out.

---

### Post by kk0sse54 on 2008-07-23
It won't work because it can't find the exe since you are not pointing it to the right place. Edit the line Exec= and it should work or if you are looking for another way to start it go into the wine menu and press browse C drive. Then under program files navigate to WOW and just double click on the exe within to start the game and it should start if you installed it properly.

---

### Post by Sithely on 2008-07-23
> **C!oud said:**
> It won't work because it can't find the exe since you are not pointing it to the right place. Edit the line Exec= and it should work or if you are looking for another way to start it go into the wine menu and press browse C drive. Then under program files navigate to WOW and just double click on the exe within to start the game and it should start if you installed it properly.

My actual command is
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Exec=/home/sithely/World of Warcraft/wow.exe
Icon=WoW.svg
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=false

I"m a little confused about the C drive.  Does linux refer to drives same as windows?  I actually copied all the files from my C drive in the windows partition and copied it to /home/sithely folder in my Linux partition so the location should be /home/sithely/world of warcraft right?

Whenever I click on the icon in my applications tab it says Failed to execute child process "/home/sithely/World" (No such file or directory)

Thanks

---

### Post by match002001 on 2008-07-23
I may be just jumping in at the wrong time but if you are using Wine in order to run it, then what happens is when you install a windows app in a Linux enviornment it uses Wine to install it. Wine creates a fold within, I believe, the home/sithely directory it is a hidden folder named ".wine", within that you will see a folder labeled "c_drive". 

That is what I think they are talking about. If you are used to Windows then you should be good from there and find the Wow.exe file.

Hope that helps :)

---

### Post by Sithely on 2008-07-23
> **match002001 said:**
> I may be just jumping in at the wrong time but if you are using Wine in order to run it, then what happens is when you install a windows app in a Linux enviornment it uses Wine to install it. Wine creates a fold within, I believe, the home/sithely directory it is a hidden folder named ".wine", within that you will see a folder labeled "c_drive". 

That is what I think they are talking about. If you are used to Windows then you should be good from there and find the Wow.exe file.

Hope that helps :)

YES that was it. I just moved my install file to the .wine/c_drive and it works 

thanks so much everyone

---

### Post by kk0sse54 on 2008-07-23
Good job mate :) and no linux does not refer to drives as Windows does. Instead when I was talking about the c drive I was talking about wine's folders but you figured it out anyways :grin:

---

### Post by Sithely on 2008-07-23
Yeah I'm getting the hang of it.  thanks :)

---

