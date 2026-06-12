---
title: "HOWTO: Edit maps for Wolfenstein 3D"
date: 2009-01-13
forum: Outdated Tutorials &amp; Tips
---

### Post by dbbolton on 2009-01-13
This guide will show you how to edit the maps in Wolfenstein 3D, one of the greatest FPS's of all time :D . First, you need to install dosbox:

```
sudo aptitude update && sudo aptitude install dosbox
```Next, you will need to acquire the Wolf 3D files. If you already have the game, great. If not, download it for free here:
[http://www.dosgamesarchive.com/download/download.php?id=15]("http://www.dosgamesarchive.com/download/download.php?id=15%5B/url")

For the purposes of this tutorial, I'll assume you downloaded the game from this source. Extract the archive and cd to its content (watch out, it's a little tarbomb) :

```

mkdir wolf
mv wolf3d.zip wolf
cd wolf
unzip wolf3d.zip

```Now we need to "install" the game to get the necessary files for editing. I'm going to assume the folder "wolf" is in your home directory

```
 dosbox ~/wolf/DEICE.EXE
```A dialog will ask you where you want to install the game; since we mounted ~/wolf as C: in dosbox, we want to install the game there as well. Type C and hit enter. Then, it will ask you about a directory. Just hit enter again, then Y to create that directory. Now exit dosbox with the command "exit".

We need to execute the new "WOLF.EXE" file with dosbox:

```
dosbox ~/wolf/WOLF3D/WOLF.EXE
```This will extract the necessary files automatically. Go ahead and exit dosbox.

Next, we need to setup the map editor. I use NMAP. You can get it here:
[http://toastytech.com/files/nmap.zip](http://toastytech.com/files/nmap.zip)

And read the documentation here:
[http://toastytech.com/files/nmap.txt](http://toastytech.com/files/nmap.txt)

The easiest way to do this is as follows:
```

cd
wget http://toastytech.com/files/nmap.zip
mkdir nmap
mv nmap.zip nmap
cd nmap
unzip nmap.zip

```Next, we need to move a couple files from the WOLF3D folder to the nmap folder:

```

cp ~/wolf/WOLF3D/GAMEMAPS.WL1 ~/nmap/
cp ~/wolf/WOLF3D/MAPHEAD.WL1 ~/nmap/ 

```That's it. Now you can launch the editor with:
```
dosbox ~/nmap/NMAP.EXE
```After you're done editing, you will need to copy those two files back to your WOLF3D folder. It's not a bad idea to make backups:

```

cp ~/wolf/WOLF3D/GAMEMAPS.WL1 ~/wolf/WOLF3D/GAMEMAPS.WL1.original
cp ~/wolf/WOLF3D/MAPHEAD.WL1 ~/wolf/WOLF3D/MAPHEAD.WL1.original
cp -i ~/nmap/GAMEMAPS.WL1 ~/wolf/WOLF3D/GAMEMAPS.WL1
cp -i ~/nmap/MAPHEAD.WL1 ~/wolf/WOLF3D/MAPHEAD.WL1

```

NOTE: If you didn't get the game files from the above link, you may need to edit ~/nmap/NMAP.CFG -- make the first character a "0" if you have version 1.0 of Wolf 3D.

If you have any problems following this guide, please let me know and I will do my best to help.

---

