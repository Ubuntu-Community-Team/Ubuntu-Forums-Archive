---
title: "Looking for a WinRAR like program."
date: 2008-08-01
forum: New to Ubuntu
---

### Post by at2smithjason on 2008-08-01
I am looking for a WinRAR like unpacker.  I am going to be downloading a lot of movies and music and a lot of the music that I download is in a RAR file format.  Is there something that will read that file extention and let me move it to my music folder?  Also the other night I went back to using Windows so that i could play some of the games that I have for it. Today i reinstalled Ubuntu because using Windows after using Linux feels like cheating on my wife.:lolflag:

I am a faithful Linux user!!!

---

### Post by sdowney717 on 2008-08-01
[http://tips.webdesign10.com/how-to-open-a-rar-file-in-linux](http://tips.webdesign10.com/how-to-open-a-rar-file-in-linux)

[http://www.ubuntu-unleashed.com/2008/04/howto-crack-rar-7z-and-zip-files-with.html](http://www.ubuntu-unleashed.com/2008/04/howto-crack-rar-7z-and-zip-files-with.html)

try this out

also I think you can run winrar in wine

---

### Post by GreenN00b on 2008-08-01
You can install unrar or unrar-free using synaptic. They are command line tools but they unpack the rar archives.

---

### Post by scragar on 2008-08-01
unrar and unrar-free both work with the ubuntu **right click->extract here** option, so it's pretty helpfull.

---

### Post by GreenN00b on 2008-08-01
> **scragar said:**
> unrar and unrar-free both work with the ubuntu **right click->extract here** option, so it's pretty helpfull.

I did not knew that, thanks ...

---

### Post by gjoellee on 2008-08-01
but it have not become graphical have it? (I don't like the terminal)

---

### Post by Daveski on 2008-08-01
Try 7Zip. I use this is Windows and Linux.

---

### Post by scragar on 2008-08-01
unrar=nonfree and unrar-free

work both in the full archive manager(double click an archive), as well as when using the extract here option as I said above. they are also available on the command line if required, although most people wouldn't use them for that.

---

### Post by zvacet on 2008-08-01
```
sudo apt-get install p7zip p7zip-full
```

---

### Post by at2smithjason on 2008-08-01
> **Daveski said:**
> Try 7Zip. I use this is Windows and Linux.

Whats the interweb address for that?

---

### Post by sdowney717 on 2008-08-01
[http://www.7-zip.org/download.html](http://www.7-zip.org/download.html)

I just installed 7zip beta in wine and it runs. And has a gui

I also just installed winrar in wine and it works
winrar version 3.o beta 7

[http://en.wikipedia.org/wiki/WinRAR](http://en.wikipedia.org/wiki/WinRAR)
site mentions it does work in wine

---

### Post by scragar on 2008-08-01
7zip... can I ask why? P7zip is a port to linux available via synaptic. Easy enough to install(far easier than via wine anyway):```
sudo apt-get install p7zip
```

---

### Post by sdowney717 on 2008-08-02
simply gives wine something useful to do

---

### Post by ubuntu27 on 2008-08-02
To be able to extract or open rar files all you have to do is


```
sudo apt-get install unrar-free
```

in the terminal.


As for the GUI. Don't worry. just double click it and then a application called File .. ok, I forgot the name of it. Anyway, you don't have to use the terminal to extract a rar file.


Just right click on the rar file, and then select "Extract here"

---

### Post by rossjman1 on 2008-08-02
sudo apt-get install unrar
will allow you to access Rar files through the default archive manager installed on the system (file-roller by default).

---

### Post by Methuselah on 2008-08-02
Note that I was unable to use the free unrar on password protected archives.

---

### Post by Masoris on 2008-08-02
Why don't you install wine, and just use windows softwares?

---

### Post by Rolcol on 2008-08-02
I like peazip on Windows and they have a Linux version.

[http://www.peazip.org/](http://www.peazip.org/)  It can open up RAR in windows but I'm not sure about Linux.

---

### Post by ubuntu27 on 2008-08-05
> **Methuselah said:**
> Note that I was unable to use the free unrar on password protected archives.

Newer versions (and password protected)of rar can be opened only with the unfree-rar :(

---

