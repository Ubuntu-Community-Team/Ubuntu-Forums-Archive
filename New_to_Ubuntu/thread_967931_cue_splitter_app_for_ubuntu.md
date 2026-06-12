---
title: "cue splitter app for ubuntu?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by cairnzi on 2008-11-02
hi there, is there an cue splitter app for ubuntu? tried a couple through wine but no luck, many thanks.

---

### Post by dracayr on 2008-11-02
[http://onubuntu.blogspot.com/2007/06/splitting-cueflac-files.html](http://onubuntu.blogspot.com/2007/06/splitting-cueflac-files.html)

EDIT: for mp3's you can use mp3splt

dracayr

---

### Post by cairnzi on 2008-11-03
cheers, working fine now.

---

### Post by mlahey on 2009-07-13
I've had excellent results using Medieval CUE Splitter under wine.  

[http://www.medieval.it/content/view/28/71/]("http://www.medieval.it/content/view/28/71/")

installer doesn't work, but you can extract the program using Archive Manager

1) download [http://www.medieval.it/sw/cuesplitter_setup.exe]("http://www.medieval.it/sw/cuesplitter_setup.exe") 

2) right click on cuesplitter_setup.exe and "Open using Archive Manager"

3) extract all files to ~/.cuesplitter/ (enable "Re-create Folders" when extracting) 

4) as root create the file /usr/local/bin/cuesplitter 

```
gksudo gedit /usr/local/bin/cuesplitter
```

/usr/local/bin/cuesplitter 
```
#!/bin/sh
cd ~/.cuesplitter/
if [ "$1" != "" ]; then
filename=`echo z:$1 | sed 's/\\//\\\\/g'`
wine CUE_Splitter.exe "$filename" &
else
wine CUE_Splitter.exe &
fi
```

5) Make /usr/local/bin/cuesplitter executable
```
gksudo chmod +x /usr/local/bin/cuesplitter
```

6) download [http://www.medieval.it/images/stories/products/CUE-Splitter/icon.png]("http://www.medieval.it/images/stories/products/CUE-Splitter/icon.png") 

7) as root copy icon.png to /usr/local/share/icons/cuesplitter.png

for example
```
gksudo cp ~/Desktop/icon.png /usr/local/share/icons/cuesplitter.png
```


8 ) as root create the file /usr/local/share/applications/cusplitter.desktop
```
gksudo gedit /usr/local/share/applications/cusplitter.desktop
```

/usr/local/share/applications/cusplitter.desktop
```
[Desktop Entry]
Type=Application
Name=Cue Splitter
GenericName=Split Sound Files Using a .cue file
Version=1.0
Encoding=UTF-8
Terminal=false
Exec=/usr/local/bin/cuesplitter
Comment=Split Sound Files Using a .cue file
Icon=cuesplitter.png
Categories=GNOME;GTK;AudioVideo;Audio;
MimeType=application/x-cue
```

you can find the Cue Splitter tutorial at [http://www.enfis.it/cue-splitter-tutorial/]("http://www.enfis.it/cue-splitter-tutorial/")

---

### Post by quisnox on 2010-10-14
No. Medieval is crap.

[http://www.hydrogenaudio.org/forums/index.php?showtopic=57563&st=0&p=683198&#entry683198](http://www.hydrogenaudio.org/forums/index.php?showtopic=57563&st=0&p=683198&#entry683198)

---

