---
title: "Download and install"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by webbdawg on 2008-05-31
I just got the latest v of Ubuntu installed on an amd64 semperon. Everything seems ok except that I cannot get Rythumbox to see my sansa e250. 

So I downloaded Songbird and it is sitting on my desktop waiting for me to install it.

I tried several extractions to the /etc folder where it seems all of the applications are residing.

I keep getting errors.

How the hell to you install programs in linux?

I'm not a dummy. I do program with PHP and other languages but as always with something new there is a curve.

I gotta go jacuzzi. Check back later

Thanks
Dave

---

### Post by Maestro23 on 2008-05-31
Installing in Ubuntu:

*How To Install Anything: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
*Psychocats: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

For Songbird, after downloading to my Dekstop, I copied it to my **/home/username** directory and:

> tar -xvf  Songbird_0.5_linux-x86_64.tar.gz

cd Songbird (directory)

./songbird (runs the program)

You can create a launcher for it as well with an Icon, add it to your Apps menu, etc...

---

### Post by IHATEDLINK on 2008-05-31
Songbird isn't a installable app!
:P
It's just the hole app compressed on a tar.gz (tar.gz is the zip of linux). That's because it's only for developpers for the moment.
Usually for installing something on ubuntu you go to Applications>Add/Remove.. or browse the net for .deb files! You can also type in terminal:
```
sudo apt-get install YOUR_APP_HERE 
```
But this will only work with stuff on the repositories, for **uninstalling**:
```
sudo apt-get remove YOUR_APP_HERE 
```

---

### Post by candive on 2008-05-31
Add programs.
1.) Applications (top left)
2.) Add/Remove
3.) Choose category on left. All, Accessories, Internet, etc.
4.) To see program details left click on one (not little square Box)
5.) If you want one left click in little white box.
6.) Choose as many as you wish.
7.) I would stick to "Supported Applications" until you are more comfortable.
8.) Apply Changes.
9.) Apply.
10.) Enter your password, verify.
11.) "Close" will appear when its done.

Updates.
1.) Top left "System"
2.) Admin
3.) Update Manager
4.) Check
5.) Install Updates (if any listed)
6.) No updates shown "Close"

Hope that helps.

---

### Post by webbdawg on 2008-05-31
> **IHATEDLINK said:**
> Songbird isn't a installable app!
:P
It's just the hole app compressed on a tar.gz (tar.gz is the zip of linux). That's because it's only for developpers for the moment.



So are you saying that Songbird is not a good choice?

I am only interested in getting a different player than the default Rhythmbox which does not see my Sansa. From what I read on the FAQ's, there is a bug but I cannot seem to find the fix. They also said to put some file in my players root, but I do not seem to be able to access the root of the Sansa.

I did look and find a player called Banshee. Any comments on this one?

Thanks
Dave

---

### Post by IHATEDLINK on 2008-06-01
> **webbdawg said:**
> So are you saying that Songbird is not a good choice?

I am only interested in getting a different player than the default Rhythmbox which does not see my Sansa. From what I read on the FAQ's, there is a bug but I cannot seem to find the fix. They also said to put some file in my players root, but I do not seem to be able to access the root of the Sansa.

I did look and find a player called Banshee. Any comments on this one?

Thanks
Dave

Songbird is in development right now, but that doesn't mean you can't use it! Just create a launcher on your applications menu and place the file wherever you want to. 
It's gonna be buggy thought, very buggy.
I didn't tried Banshee, but it looks fine, it should do the work.
There's Amarok to... I personally **_HATE IT_** but many people doesn't, although it isn't a native GNOME* app, so it will look weird. 
**I will go for Banshee, but be sure to try Amarok,** it's worth the shot.

*GNOME is the "flavor", the desktop environment, of Ubuntu. KDE is the one of Kubuntu and the same goes for Xfce and Xubuntu, it's just a matter of taste. Amarok is a KDE app. Usually apps are named with the letter of their flavor, for instance: **G**Parted for **G**nome and Amaro**K** and **K**onqueror for **K**DE

---

### Post by cariboo on 2008-06-01
Try this:

[http://www.howtoforge.com/sandisk_mp3_player_linux](http://www.howtoforge.com/sandisk_mp3_player_linux)

It looks pretty simple

Jim

---

