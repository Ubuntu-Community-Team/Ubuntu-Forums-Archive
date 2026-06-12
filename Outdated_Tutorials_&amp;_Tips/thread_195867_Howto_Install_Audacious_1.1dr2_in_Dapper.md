---
title: "Howto: Install Audacious 1.1dr2 in Dapper"
date: 2006-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2006-06-13
Audacious a media player, under active development, similar to Winamp 2.x and XMMS that uses an GTK2 interface. 

Audacious is compatible with Winamp 2.x or "Classic" skins, as well as XMMS skins, and can handle a most music formats.

1. Get packages:
```
wget -c http://mikesplanet.net/dapper/audacious_1.0.0+1.1dr2-1vd2~dapper1_i386.deb
wget -c http://mikesplanet.net/dapper/audacious-docklet_0.1.1-1_i386.deb
```

2. Install dependences:
```
sudo apt-get install libartsc0 libbinio1c2 libjack0.100.0-0 libmodplug0c2 libmpcdec3 libresid-builder0c2a libsamplerate0 libsidplay1 libsidplay2 libtagc0
```

3. Install package:
```
sudo dpkg -i audacious_1.0.0+1.1dr2-1vd2~dapper1_i386.deb
```

4. Install docklet plugin:
```
sudo dpkg -i audacious-docklet_0.1.1-1_i386.deb
```
*Note: The docklet plugin deb is made via checkinstall, YMMV.*

Please let me know if you have any issues with this package, it was a difficult package to get working.

Thanks to dai <d+deb@vdr.jp> for the base debian files I used to compile the package.

---

### Post by caserio on 2006-06-13
Hi,

Don't have any issue thus far. Just a big thank you !

---

### Post by Technoviking on 2006-06-13
There are some xmms skins that will cause Audacious to crash. I have reported this to the Audacious devs, and fix will be in the next version.

---

### Post by chanders on 2006-06-14
Why would you want this player? What are the advantages over XMMS?

---

### Post by el_Salmon on 2006-06-16
[QUOTE=chanders]Why would you want this player? What are the advantages over XMMS?[/QUOTE]
GTK 2 style.

Hey Mike! Where is last.fm (Audioscrobbler) plugin ?

---

### Post by krul on 2006-06-19
Very nice!

It seems the it is already a perfect replacement of XMMS which is sooo ugly.

Installation was very easy, works like a charm, thanks!

---

### Post by krul on 2006-06-19
[QUOTE=el_Salmon]
Where is last.fm (Audioscrobbler) plugin ?[/QUOTE]

Yes I'd like to know this too...

---

### Post by PureW on 2006-06-25
[QUOTE=krul]Very nice!

It seems the it is already a perfect replacement of XMMS which is sooo ugly.

Installation was very easy, works like a charm, thanks![/QUOTE]


How do you install it on a 64bits Ubuntu?

EDIT: I managed to install it somehow... But when I open a music file (mp3) with it, nothing happens, and when I click the icon in the folder, nothing happens. How do I start it?

EDIT 2: When I open it from the terminal, I get this message: 
audacious: error while loading shared libraries: libaudacious.so: cannot open shared object file: No such file or directory
This error is listed in the official FAQ here [http://audacious-media-player.org/FAQ#5.1](http://audacious-media-player.org/FAQ#5.1) but the solution isn't working.

EDIT 3: This worked:
sudo su
echo '/usr/local/lib' >> /etc/ld.so.conf
ldconfig
exit

---

### Post by Technoviking on 2006-06-25
[QUOTE=el_Salmon]GTK 2 style.

Hey Mike! Where is last.fm (Audioscrobbler) plugin ?[/QUOTE]
I could not get that to compile yet.

---

### Post by mexikin on 2006-06-25
seemed to install fine but I get an error that says no playable cd found... everything seems to play fine on soud juicer... I'm sure its a problem on my side

---

### Post by lazyd2 on 2006-06-25
Works great, thanks!

---

### Post by krul on 2006-06-26
I found a working way to get a last.fm plug-in working:

[http://www.ubuntuforums.org/showthread.php?t=126238&page=5](http://www.ubuntuforums.org/showthread.php?t=126238&page=5)

---

