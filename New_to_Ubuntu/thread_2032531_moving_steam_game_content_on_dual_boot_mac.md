---
title: "moving steam game content on dual boot mac"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by plussr on 2012-07-24
I'm not sure how to go about moving game content from my mac osx partition to my ubuntu 12.4 partition to work under steam in wine, so I don't have to download it twice. I've found this for windows:

```

cd $HOME/.wine/drive_c/Program\ Files/Steam/ 
mv steamapps steamapps.bak
ln -s <ABSOLUTE-WINDOWS-DRIVE-MOUNT-POINT>/Program\ Files/Steam/steamapps steamapps
```

But I don't understand it (much, I know what cd and mv do) and it's windows specific. Any help is greatly appreciated

---

### Post by xeramon on 2012-08-04
Also looking for help: [https://developer.valvesoftware.com/wiki/Steam_under_Linux#Save_space_on_dual-boot_machines](https://developer.valvesoftware.com/wiki/Steam_under_Linux#Save_space_on_dual-boot_machines)

The site says I just have to execute this in the terminal: 

```
cd $HOME/.wine/drive_c/Program\ Files/Steam/ 
mv steamapps steamapps.bak
ln -s <ABSOLUTE-WINDOWS-DRIVE-MOUNT-POINT>/Program\ Files/Steam/steamapps steamapps
```

This is the first time I'm using Ubuntu.
My steam games content is localated here "D:/Program Files(x86)/Steam/steamapps"
so do i have to execute this?:
```
cd $HOME/.wine/drive_c/Program\ Files/Steam/ 
mv steamapps steamapps.bak
ln -s D:/Program\ Files(x86)/Steam/steamapps steamapps
```

Thanks in advance!

Edit: I just executed "cd $HOME/.wine/drive_c/Program\ Files/Steam/" but it says it was not found.
(Steam on linus is at: "home/Persönlicher Ordner/PlayOnLinux's virtual drives/steam/drive_c/Program Files/Steam" (german Ubuntu: Persönlicher Ordner -> Private Folder or sth. like that))

Edit2: Now I did folowing, i didnt got any errors, but the content is still not linked...
```
cd $HOME/Persönlicher Ordner/PlayOnLinux's virtual drives/steam/drive_c/Program Files/Steam
mv steamapps steamapps.bak
ln -s D:/Program\ Files(x86)/Steam/steamapps steamapps
```

Edit3: Just did this and still didnt helped:
```

cd $HOME/Persönlicher Ordner/PlayOnLinux's virtual drives/steam/drive_c/Program Files/Steam
mv steamapps steamapps.bak
ln -s media/GAMES/Program\ Files\ (x86)/Steam/steamapps steamapps
```

---

### Post by Cheesemill on 2012-08-04
> **plussr said:**
> I'm not sure how to go about moving game content from my mac osx partition to my ubuntu 12.4 partition to work under steam in wine, so I don't have to download it twice. I've found this for windows:

```

cd $HOME/.wine/drive_c/Program\ Files/Steam/ 
mv steamapps steamapps.bak
ln -s <ABSOLUTE-WINDOWS-DRIVE-MOUNT-POINT>/Program\ Files/Steam/steamapps steamapps
```But I don't understand it (much, I know what cd and mv do) and it's windows specific. Any help is greatly appreciated

You can't use the same game content on a Windows (or Wine) machine that you have on your Mac. They are written differently.

---

### Post by xeramon on 2012-08-04
> **Cheesemill said:**
> You can't use the same game content on a Windows (or Wine) machine that you have on your Mac. They are written differently.

They are games on steam that can also be used on linux, like SuperMeatBoy.
(i could also play games per wine)
[B][COLOR="Red"]
EDIT: [/COLOR][/B]I got the solution, just move to your windows-steamfolder make a shortcut of your current SteamApps, and then move this shortcut in the Ubuntu-steamfolder, delete the ubuntu-steamapps folder and rename your shortcut to SteamApps!

---

