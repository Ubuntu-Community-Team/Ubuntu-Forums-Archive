---
title: "Installing realtek HD audio manager?"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by p3thead on 2012-07-17
Hi I would like to install the realtek HD audio manager, because when I'm listening to music it sounds too "empty". I don't know how to do it so can someone please help me?

I've downloaded this driver -> [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)

And now I am for asking help because I don't know what to do with the file. I've been looking for answers on the forum and on other sites but without luck.

---

### Post by jmfal on 2012-07-17
Welcome to Ubuntu

If it's a windows app you can't use it .

Open the alsamixer in a terminal and increase all spesker volumes.
click on alssamixer link below.

---

### Post by Cheesemill on 2012-07-17
Instructions for the 3.0 kernel Linux package:

Assuming you have downloaded the file to your Downloads directory, first open up a terminal and extract the file:
```
cd Downloads
tar xvjf LinuxPkg_5.17rc5.tar.bz2
```Then navigate to the extracted folder and run the installer:
```
cd realtek-linux-audiopack-5.17
sudo ./install
```

---

### Post by p3thead on 2012-07-17
Hello and thanks for replying, the driver I linked in my previous post are for Linux I would just like to know how to install the package. 

As far as I can tell Alsamixer is just for increasing the volume? Which is not the case. I have perfect sound I would just like to mix with it a little bit so my music sounds better.

If you ever used Realteks HD audio manager you maybe know that they have presets for different types of music. I don't know how to explain it in a good way but it emphasizes certain instruments so it sounds a lot better.

Thanks Cheesemill :)

---

### Post by p3thead on 2012-07-17
> **Cheesemill said:**
> Instructions for the 3.0 kernel Linux package:

Assuming you have downloaded the file to your Downloads directory, first open up a terminal and extract the file:
```
cd Downloads
tar xvjf LinuxPkg_5.17rc5.tar.bz2
```Then navigate to the extracted folder and run the installer:
```
cd realtek-linux-audiopack-5.17
sudo ./install
```

Okey I did this and now my sound stopped working completely? :confused:

---

### Post by Cheesemill on 2012-07-17
Did you read the included Readme.txt file?
> 3. All mixer channels are muted by default. You must use a native
    or OSS mixer program to unmute appropriate channels.
So open a terminal and fire up alsamixer to unmute the channels:
```
alsamixer
```

---

### Post by p3thead on 2012-07-17
Yea just had to reboot... :P

Thanks for the help!

---

