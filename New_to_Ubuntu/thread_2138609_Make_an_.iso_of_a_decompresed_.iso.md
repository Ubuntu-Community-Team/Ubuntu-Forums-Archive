---
title: "Make an .iso of a decompresed .iso"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by Linkeichi on 2013-04-24
Hi people, i have a problem. I have a concert in ISO, i decompressed, and now i have 2 directories, Audio and Video.

Now i want to make the "ISO" again.

I use Ubuntu 12.04 64B

What i need to do?

Any suggestions?

---

### Post by Frogs Hair on 2013-04-24
You can compress folders with Right Click > Compress . There is a menu in the dialog box that allows a choice  of package type and ISO is listed among them at least on my installation . I am guessing the two folders or directories were in a master package or folder.

---

### Post by Linkeichi on 2013-04-24
I do what you suggest, but it only show me .zip .rar .tar-gz .tar .jar .cbr but .iso isnt there

I need to install something?

---

### Post by Frogs Hair on 2013-04-24
Try the following ```
sudo apt-get install p7zip-full
```

---

### Post by Linkeichi on 2013-04-25
Hi Frogs Hair, 

It didnt work, still not showing the .iso option, but add 2 o 3 options new like 7z

I restart my ubuntu and continues the same

linkeichi@linklap:~$ sudo apt-get install p7zip-full
[sudo] password for linkeichi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
p7zip-full is already the newest version.
The following packages were automatically installed and are no longer required:
  wine-gecko1.4:i386 linux-headers-3.5.0-23-generic linux-headers-3.5.0-23
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
linkeichi@linklap:~$

---

### Post by Linkeichi on 2013-05-02
Well, thanks for all, im searching again in google -_-

---

### Post by chipbuster on 2013-05-02
Have you tried using Brasero? I don't have it right now, but I seem to remember you could burn to an iso if you so chose

---

### Post by Frogs Hair on 2013-05-02
I don't why it is not working . I just installed [COLOR=#000000][FONT=Ubuntu Mono]p7zip-full on my new 13.04 installation and created a compressed iso. Once created it can be burned to disk.[/FONT][/COLOR]

---

### Post by Cheesemill on 2013-05-02
You can use Brasero, it's already installed.

Create a new video project, add the Audio and Video directories to it, then burn it to a disc image.

---

### Post by Linkeichi on 2013-05-17
chipbuster, Frogs Hair, Cheesemill Thanks, i used the brasero as you suggest and i already made my iso :)

---

