---
title: "How-to skype video Intrepid Ibex"
date: 2008-12-30
forum: Outdated Tutorials &amp; Tips
---

### Post by spiderbatdad on 2008-12-30
[COLOR="Blue"][SIZE="4"]This short guide assumes you have installed skype on Intrepid Ibex and that your cam is identified by skype under the options video menu, but the test fails to start your cam.[/SIZE][/COLOR]

There is a commonly used work around to preload libv4l and start skype to get video working: ```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
``` Try that command in your terminal. If that allows you to use video in skype, you may want to create a launcher rather than enter the command each time you want to start skype. The above command will not work in a launcher. You will need to create a script as described below.

[COLOR="Blue"][SIZE="4"]Create a folder and simple script in your home directory[/SIZE][/COLOR]

```
mkdir ~/bin
touch ~/bin/skype.sh
gedit ~/bin/skype.sh
# paste in the little #!/bin/bash script below. make sure #!/bin/bash is the very first line.no space or indent or skipped line.

chmod 775 ~/bin/skype.sh
```

```
#!/bin/bash
sleep 2
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

~/bin is in my path as set in .bashrc. But there might be a provision in intrepid to automatically put bin in your path, if you create the directory...a little .gconf prog, i think, anyway...

If it doesn't work...append .bashrc by adding the following at the end of the file.

```
gedit ~/.bashrc
# paste in the two lines below, and save.
export PATH=$PATH:$HOME/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/bin
```

Now create a launcher by right clicking on your panel and selecting: "Add to panel." Then select "Custom Application Launcher." Then click the Add button, bottom right corner of the add to panel application window.
A new dialog box opens. For the name use Skype. For the command, use the browse button, and browse to the file skype.sh in the bin directory of your home folder.

Happy skypeing...the above process will also work for gyachi or other programs suffering from incompatibility with libv4l-0 in Intrepid.

---

### Post by poltiser on 2009-01-03
I did first step and it does not work

U8.1 AMD64 Creative Life ...

:(

---

### Post by flint_ on 2009-01-10
This worked for me, I would very much like to thank  spiderbatdad
WWND.   I am in Barre Vermont.  You can come down and collect your free beer.  Very good fix!  It would be nice to see the libraries adjusted...

---

### Post by daball46 on 2009-01-15
error: dependency is not satisfiable: libqt-core
cant install package for skype-debian for ubuntu

---

### Post by Elvin Mammadov on 2009-01-16
It works now..Thanx man...You are the best :)))

But I have another problem My camera is not working also in Amsn or with other programs i.e when i sign in Facebook I want to capture pic with my webcam It said NO WEBCAM FOUND.But after I eneterd your codes it works on skype but not other.What Can I do?

---

### Post by spiderbatdad on 2009-01-19
> **Elvin Mammadov said:**
> It works now..Thanx man...You are the best :)))

But I have another problem My camera is not working also in Amsn or with other programs i.e when i sign in Facebook I want to capture pic with my webcam It said NO WEBCAM FOUND.But after I eneterd your codes it works on skype but not other.What Can I do?

What is other? Are you trying to capture pictures with "cheese" to post to facebook, or is this some web app that facebook runs? Sorry not familiar with facebook. I apologise but it would be much better to post this type of question in "general help" or the "beginners help" section, as you are likely to get feedback from users of that service.

---

### Post by aramman on 2009-03-21
THX man , worked for me too;)

---

### Post by brookie on 2009-05-25
Thanks. This worked for my logitech messenger camera so now my video transmission is good, however, my video reception is still bad. Video freezes when people move, and also disapears when I drag the video frame around my desktop. 
Any ideas how to improve video reception?

---

### Post by danieR on 2009-06-01
The solution that worked for me on Ubuntu 9.04 64 bit:

First start by running
```
sudo apt-get install lib32v4l-0
```

This will install the 32 bit version of libv4l (it doesn't overwrite the 64 bit version)

Then wherever the above solution says
```
/usr/lib/libv4l/v4l2convert.so
```

replace with
```
/usr/**lib32**/libv4l/v4l2convert.so
```

---

### Post by KennyMcC on 2009-09-13
> **danieR said:**
> The solution that worked for me on Ubuntu 9.04 64 bit:

First start by running
```
sudo apt-get install lib32v4l-0
```

This will install the 32 bit version of libv4l (it doesn't overwrite the 64 bit version)

Then wherever the above solution says
```
/usr/lib/libv4l/v4l2convert.so
```

replace with
```
/usr/**lib32**/libv4l/v4l2convert.so
```

Thanks. :D It works with my Ubuntu 9.04 64 and Trust Megapixel USB2 Webcam Live WB-5400 (0c45:624e Microdia PC Camera (SN9C201))

---

### Post by zosomos on 2009-09-15
Tried it and the terminal started repeatedly printing "X Error, request 140, minor 18, error code 11 BadAlloc (insufficient resources for operation)".

---

### Post by DigitalRanger on 2009-09-19
Just wanted to say thanks.
The OP worked for me too.

Strangely, I'd tested Ubuntu 9.04 with Wubi for a few months and the webcam "just worked" for me with Skype. Although once I installed on *bare metal* it didn't work anymore - until I found this work around.

Thanks again.

---

### Post by Ian Clark on 2009-09-24
Awesome fix.  Thanks! :guitar:

---

### Post by energy10 on 2009-11-15
Thanks a lot . Works  on karmic .

---

### Post by m4r1u52 on 2011-04-13
Many thanks spiderbatdad.

---

### Post by igor1102828 on 2011-06-18
Actually, it works also in Ubuntu 11.04 64bit, both in Skype and cheese, but the web-camera (in my case it is also Creative live! model VF0220, 041e:4053) starts to show the image in skype with delay about 20-30 seconds! Whereas the same trick in Ubuntu 8.10 provided normal work of web-camera. Has anyone some ideas how to treat this disease?

---

