---
title: "[SOLVED] sauerbraten ctf"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Zopiac on 2008-06-26
how to install over previous version?

---

### Post by ibuclaw on 2008-06-28
If you haven't already downloaded it, then do so. I prefer to download files into the /tmp directory. You may chose to differ if you wish, it isn't imperative that you do so.
```

cd /tmp
wget http://switch.dl.sourceforge.net/sourceforge/sauerbraten/sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2

```
Extract the bunzip/tarball
```

tar -vjxf sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2

```
And then move the extracted directory to a (preferably isolated) folder.
I prefer to keep all my 3rd party games and software inside the /opt directory, but you may put the folder anywhere you like.
```
sudo mv sauerbraten /opt/sauerbraten
```
Next, backup your current sauerbraten execution script.
```
sudo cp /usr/games/sauerbraten /usr/games/sauerbraten.old
```
And write over the sauerbraten launch file (point it in the new location of where sauerbraten resides).
This is simply done by changing "/usr/lib/games/" to the directory where you've kept sauerbraten. And change "sauer_client" to "sauerbraten_unix".

Here is the sed command for the current example.
```
sudo sed -i 's/\/usr\/lib\/games\//\/opt\//;s/sauer_client/sauerbraten_unix/' /usr/games/sauerbraten
```
And when you run the diff command on the sauerbraten and sauerbraten.old files, this should be your output:
```

iain@fredbuntu:/usr/games$ diff sauerbraten sauerbraten.old
3,4c3,4
< cd /opt/sauerbraten
< exec ./sauerbraten_unix -q"$HOME/.sauerbraten" -r "$@"
---
> cd /usr/lib/games/sauerbraten
> exec ./sauer_client -q"$HOME/.sauerbraten" -r "$@"

```
If so, remove the tarball.
```
rm sauerbraten_2008_06_20_ctf_edition_linux.tar
```
And run the app from your main menu.

Regards
Iain

---

### Post by bhadotia on 2008-06-28
I've downloaded the tar , now how can I install it?

---

### Post by ChameleonDave on 2008-06-28
> **bhadotia said:**
> I've downloaded the tar , now how can I install it?

There is a guide above.

> ```

bzip2 -d sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2
tar -xf sauerbraten_2008_06_20_ctf_edition_linux.tar

```

It is more efficient to do that part like this:

```

tar -vjxf sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2

```

---

### Post by bhadotia on 2008-06-28
How do I launch it ? I've moved it to /opt/sauerbraten.

---

### Post by bhadotia on 2008-06-28
> **ChameleonDave said:**
> There is a guide above.
Yeah, I know. But this only gives instruction to one who has the earlier version already  installed. Please give a detailed description of the installation process. The wikis in the tar are confusing and not through enough.

---

### Post by bhadotia on 2008-06-28
I know I can always run the game with:
```
cd /opt/sauerbraten/ && ./sauerbraten_unix 
```
But the problem is I am unable to make a menu entry . In the "command" option I browse to /opt/sauerbraten/sauerbraten_unix. But after making the launcher I am unable to launch the game with it. Please help with this.

---

### Post by Zopiac on 2008-06-29
ok the guide didnt work :D isnt there a 64bit deb installer? that would be asier. I don't know where the guide died, because i had to restart x

---

### Post by ibuclaw on 2008-06-29
To create a launch script, open a terminal and run
```
sudo gedit /usr/games/sauerbraten
```
And paste this into the file
```

#!/bin/sh

cd /opt/sauerbraten
exec ./sauerbraten_unix -q"$HOME/.sauerbraten" -r "$@"

```
Once you've saved and quit. Make it executable.
```
sudo chmod a+x /usr/games/sauerbraten
```
To create a desktop entry:
```
sudo gedit /usr/share/applications/sauerbraten.desktop
```
And paste in
```

[Desktop Entry]
Encoding=UTF-8
Icon=/opt/sauerbraten/data/cube.png
Name=Sauerbraten
Comment=Sauerbraten Online FPS
Exec=/usr/games/sauerbraten
Terminal=false
Type=Application
Categories=Game;
StartupNotify=true

```
And a desktop entry will now be under /Applications/Games

Thank-you ChameleonDave, I didn't know that.
bhadotia, I hope the above gives the answers you need.
Zopiac, bah! Download the 64bit version then ;P

[EDIT]
You will also need to install libsdl-mixer in order to play the game
```
sudo apt-get install libsdl-mixer1.2
```
Also, for those who are lazy, I found a deb file at everyone's favourite [getdeb.net]("http://getdeb.net/search.php?keywords=sauerbraten").
It's been made ready-packaged for both 32 and 64bit systems.

Regards
Iain

---

### Post by Zopiac on 2008-06-29
> **tinivole said:**
> 
Also, for those who are lazy, I found a deb file at everyone's favourite [getdeb.net]("http://getdeb.net/search.php?keywords=sauerbraten").
It's been made ready-packaged for both 32 and 64bit systems.


the download says: Ubuntu Gutsy 64 bits - 20071227
im guessing that means 12/27/07, not 6/28/08 :P


im a hassle.

edit: unless the hardy one (Ubuntu Hardy 64 bits - 0.0.20080620) would work for gutsy?

edit2: WOW nvm i have HH im a dimwit >.<

---

### Post by bhadotia on 2008-07-01
tinivole, thanks for the link . I am lazy with all this setup thing.:)

---

