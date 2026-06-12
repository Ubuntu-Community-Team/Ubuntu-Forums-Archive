---
title: "HOWTO: Install 64bit flash on Ubuntu"
date: 2010-03-06
forum: Outdated Tutorials &amp; Tips
---

### Post by MichealH on 2010-03-06
[CENTER][SIZE=5]_**64 bit flash on Ubuntu.**_[/SIZE] [SIZE="3"]**[COLOR="red"]Current Revision - 30/11/2010[/COLOR]** [/SIZE]
[/CENTER]

I have tested this on the following:

Ubuntu 9.04 Jaunty Jackalope(GNOME)
Ubuntu 9.10 Karmic Koala(GNOME, KDE)
**Ubuntu 10.04 Lucid Lynx LTS (GNOME, KDE)**[COLOR="Red"]Current LTS.[/COLOR]
**Ubuntu 10.10 Maverick Meerkat (GNOME, KDE)**[COLOR="Red"]Latest Version![/COLOR]

Please tell me If it has worked out on another version/DE.

**1. Open terminal and Kill firefox**

You can do this by going to Applications>Accessories>Terminal
Or on KDE goto The Lancher and Type in search "Terminal" You'll see a terminal ;)

If you have a root password set up the you can go into Super User mode by typing:

```
sudo su
```

OR

```
sudo bash
```

If you are running as SuperUser you do NOT need to use sudo.

Also to continue kill firefox:

```
killall firefox
```**2. Goto preferred folder **

***It opens on your home folder by default***

If you would like to goto your Downloads folder type:

```
cd Downloads
```You get the drill If you would like to go up a folder incase you make a mistake just type **cd ..**

**3. Get the code **

Now type:

```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
```This may take a while...

**4. Extract the .tar.gz file**

To extract it, Ready for moving type:

```
tar xvzf libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
```With that done.. Time to get some moving done!

**5. Move the libs to the correct place**

***This will ask for your password so do not be offended***

Now after that you can now type:

```
sudo mv libflashplayer.so /usr/lib/firefox-addons/plugins
```Now restart Firefox it should be done :D

Please if there is any problems please report it here.

**Changelog**
v1.12: (30/11/2010)
- Added 10.10
v1.11: (04/07/2010)
- Added an option for "sudo bash"
v1.10: (13/05/2010)
- Added Ubuntu 10.04 to the list (Sorry for Delay )
v1.05
- Added KDE 9.10 on what wieman01 had said.
- Added KDE options
v1.00:
- This is the first Edition.

---

### Post by wieman01 on 2010-03-06
Nice. This tutorial will help me in a couple of days when I get my new computer.

---

### Post by Jesus_Valdez on 2010-03-06
My libflashplayer.so is on /home/USER/.mozilla/plugins And Flash works perfecto on every browser that I have tried.

---

### Post by wieman01 on 2010-03-13
Dude, that was a breeze! Thank you! Up and running on 64-bit Kubuntu.

---

### Post by MichealH on 2010-03-13
Edited It now says Ubuntu 9.10 KDE

---

### Post by jthirt on 2010-05-11
Excellent Howto for Flash 64bit. Thanks. :)

I did it on my fresh 10.4 Lucid install and it works great. 

Now, I was also looking for specifics regarding Chrome and found this to replace Step 5:

```

sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins
sudo mkdir /opt/google/chrome/plugins
sudo cp libflashplayer.so /opt/google/chrome/plugins

```

This will put the plugin in the right place for both Firefox and Chrome.

Finally, its probably worth providing the link to the official adobe source [here]("http://labs.adobe.com/downloads/flashplayer10_64bit.html") that contains a link to download the latest version, that may change. 

Cheers,
JT

---

### Post by Linuxforall on 2010-05-12
Actually putting libflashplayer.so in /usr/lib/mozilla/plugins works fine for FF, Chrome and Opera as well.

---

### Post by jthirt on 2010-05-13
Humm, for Chrome, it must depend on the version as it didn't use the FF one in my case and I had to copy to the Google directory to make it work. I have 5.0.375.29 beta.

At least, that's how I recall the chain of events! :P

---

### Post by Taras.M.K on 2010-05-15
Works for me! Thanks!

Also I had to reboot after all changes, to use it in opera.

---

