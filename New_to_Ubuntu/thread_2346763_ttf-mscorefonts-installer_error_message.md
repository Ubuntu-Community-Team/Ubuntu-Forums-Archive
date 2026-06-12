---
title: "ttf-mscorefonts-installer error message"
date: 2016-12-18
forum: New to Ubuntu
---

### Post by Vaclav Vasek on 2016-12-18
I keep getting  this error message on each startup

ttf-mscorefonts-installer

failed to get some kind of data - not direct quote. 

Any way to stop it ? The command fails every time and lack of "missing data"  does not seems to affect anything in particular.
It is just annoying, that's all.

---

### Post by howefield on 2016-12-18
Have you got the fonts downloaded, you should have Andale Mono, Arial Black, Arial, Comic Sans MS, Courier New, Georgia, Impact, Times New Roman, Trebuchet, Verdana and Webdings ?

Try..

```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```

If that fails I'd suggest purging the package and installing the 3.6 version of the package.

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

will download the package to your Downloads folder, and
 
```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

will install the package.

---

### Post by Autodave on 2016-12-18
Here is the link that I have used: works everytime for me:

[https://ubuntuforums.org/showthread.php?t=2323229](https://ubuntuforums.org/showthread.php?t=2323229)

---

### Post by jim Kane on 2016-12-18
see this post
[https://ubuntuforums.org/showthread.php?t=2344990](https://ubuntuforums.org/showthread.php?t=2344990)

---

### Post by Vaclav Vasek on 2016-12-18
OK, I did this and I understand that the response , actually no repose,  means the package is installed. 

jim-desktop:~$ sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
[sudo] password for jim: 
jim@jim-desktop:~$ 

But on last reboot I did not get the error message either. 
I guess I'll see what develops next.
Not impressed getting errors which come and go and really do not have visible effect.

---

### Post by howefield on 2016-12-19
So, out of interest, did you have all the fonts installed or were any missing ?

---

### Post by SurfaceUnits on 2016-12-22
The location of the fonts store has been changed on the sourceforge server

---

### Post by Vaclav Vasek on 2016-12-22
Sorry for the delayed response.
I am no longer receiving the error message on boot. 
As far as knowing if I have the fonts in question installed - I do not know and have no reason  trying to find out if they are on my system. 
I suppose if i ever use anything but defaults fonts I will find out. 
I hope you understand my position.

---

### Post by howefield on 2016-12-23
> **Vaclav Vasek said:**
> I am no longer receiving the error message on boot.

Great, feel free to mark the thread as solved if you wish.
 
> As far as knowing if I have the fonts in question installed - I do not know and have no reason  trying to find out if they are on my system.

Installing a non default package on to your system might be reason enough to make sure it worked ;)
 
> I hope you understand my position.

Of course, your machine, your choices :)

---

