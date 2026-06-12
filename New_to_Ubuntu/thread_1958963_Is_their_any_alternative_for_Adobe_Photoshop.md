---
title: "Is their any alternative for Adobe Photoshop"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by sabarinadh on 2012-04-15
Hai i am newbie to Ubuntu.is their any software alternative for adobe photoshop. I want to edit the photos as easy as Photoshop.Suggest me and where should i get that
Thanks in advance:p:p:p

---

### Post by d2btoo on 2012-04-15
Gimp

---

### Post by zombifier25 on 2012-04-15
The closest (and most powerful) alternative to Photoshop available is [GIMP](http://www.gimp.org/).
To install it type this in the terminal:
```
sudo apt-get install gimp
```
Or do so the graphical way via Ubuntu Software Center (the command line way is quicker however)

---

### Post by audiomick on 2012-04-15
One more for Gimp. I gather there are a couple of functions that Photo Shop has the Gimp doesn't, but it is close, and the best alternative that I know of.

---

### Post by Quackers on 2012-04-15
+1 for the gimp. It does a lot more than I thought! :-)

---

### Post by rima on 2012-04-15
Gimp all the way! 

Although I heard there's also Inkscape or something...? Correct me if I'm wrong

---

### Post by bbemmerful on 2012-04-15
Be sure to check out the gimp website there is a plugin that will allow you to use your Ps plugins.

---

### Post by mastablasta on 2012-04-15
> **rima said:**
> 
Although I heard there's also Inkscape or something...? 

Inkscape is for vector graphics.

Also to increase the options in Gimp there are extensions/plugins one can install

---

### Post by I2k4 on 2012-04-15
If the original poster shoots RAW images, it's necessary to install a plugin for a RAW converter (similar to ACR in Photoshop.)  I like UFRAW plugin the best - clicking on an image brings up GIMP and then the UFRAW interface, and from there you convert to a file format that GIMP can handle.

By the way, it might be of general interest, I just learned that the new GIMP 2.7 beta (one window interface and other new features) can be installed like this - I've tried and existing plugins seem to all work:

To install GIMP 2.7.3 open a terminal window (press Ctrl+Alt+T) and copy+paste the following line: 

sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn
sudo apt-get update
sudo apt-get install gimp

If you have GIMP Installed in your ubuntu before, just add the PPA and upgrade GIMP using the Ubuntu Software Center or the Update Manager.

---

### Post by Jerry N on 2012-04-15
> **sabarinadh said:**
> Hai i am newbie to Ubuntu.is their any software alternative for adobe photoshop. I want to edit the photos as easy as Photoshop.Suggest me and where should i get that
Thanks in advance:p:p:p

As others have said, GIMP is probably the closest thing but it depends on what you are doing with PS.  If you are using 16 bit RAW files, GIMP truncates them to 8 bits before any processing is done.  I consider this to be a major disadvantage.  Your version of PS might run in Wine or Crossover, allowing you to run Photoshop in Linux.  If you a proficient in PS, you will find that almost everything is done differently in GIMP.

Jerry

---

### Post by clive littlewood on 2012-04-15
Hi

For "normal" tasks I use pinta.

Great app and can be found in the SC

Clive

---

### Post by Myrddin Emrys on 2012-04-15
> **Jerry N said:**
> As others have said, GIMP is probably the closest thing but it depends on what you are doing with PS.  If you are using 16 bit RAW files, GIMP truncates them to 8 bits before any processing is done.  I consider this to be a major disadvantage.

Krita is also worth trying. It has fewer features than GIMP, but it does have 16-bit (and higher depth) support, as well as interestingly different UI.

---

