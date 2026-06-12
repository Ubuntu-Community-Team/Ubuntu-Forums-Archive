---
title: "package rpm is not available"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by strakajagr on 2008-09-11
I am trying to install rpm, and I seemingly cannot.  

I read a post that said this:
"In addition to all the rightly stated use deb not rpm posts above, the reason rpm doesn't install is that your sources.list file is broken. The installer makes some dumb assumptions about internet connectivity during the install process, specifically that if you don't have an active internet connection when installing you never will, so based on this it disables all the software repositories. To reactivate them go to System > Administration > Software Sources, and make sure that all 4 sections are enabled, the source entry down at the bottom is optional but worth making note of if you ever want it."

Unfortunately, I don't know where find System > Administration > Software Sources.

There not part of Ubuntu's drop down menus.  Can anyone help?  At the end of the day, all I want is to install rpm.

---

### Post by iaculallad on 2008-09-11
You need the alien application w/c is use to convert your RPM format to DEB file format.

```
sudo apt-get update
sudo apt-get install alien

```

To convert the RPM file to DEB and install it.

```
sudo alien -i filename.rpm
```

---

### Post by strakajagr on 2008-09-11
Now it's saying, "couldn't find package alien"

---

### Post by iaculallad on 2008-09-11
> **strakajagr said:**
> Now it's saying, "couldn't find package alien"

Alien application is available in the repository. Make sure that you enabled Universe and Multiverse in your Ubuntu Software Sources.

System->Administration->Software Sources, under "Ubuntu Software" tab, place a check mark on Main, Universe, Restricted, and Multiverse. Click on Close and Click on Reload on the next window that pops out.

Then again, on your terminal:

```
sudo apt-get update
sudo apt-get install alien

```

```
sudo alien -i filename.rpm
```

---

### Post by strakajagr on 2008-09-11
I hear what you're saying and that is what started all this... I can't find "System->Administration->Software"  Where is this located?  It's not at the tool bar at the top.  All that's there is an applications drop down menu.

---

### Post by cariboo on 2008-09-12
Right click on Applications, then click edit menus and make sure that Places and System have check marks beside them. If that doesn't work right click anywhere on the top panel and click Add to Panel and scroll down in the window that opens, to **Menu Bar** and click it. This will add the custom menu bar to the top panel

---

### Post by iaculallad on 2008-09-12
> **strakajagr said:**
> I hear what you're saying and that is what started all this... I can't find "System->Administration->Software"  Where is this located?  It's not at the tool bar at the top.  All that's there is an applications drop down menu.

You're missing the the System menu? You could just do it using your terminal. Manually add the repository in your sources.list file.

```
gksudo gedit /etc/apt/sources.list
```

and add the lines of texts below on the last part of the file (just copy and paste):

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed universe main multiverse restricted

Save and Close, and redo the step on my second post.

---

### Post by strakajagr on 2008-09-12
OK I got the menu bar added.  I went to sys>admin>software and I checked all 4 boxes...

I was told my software was out of date and I needed an internet connection (which I don't have... this whole exercise began so I could unzip the new kernel so I could use WiFi)

I proceeded anyway, and I got the following error "Could not download all repository indexes."

I closed this and went back to install alien and the same error occurred.

Do I need an internet connection to do this?

---

### Post by the.phantom on 2008-09-12
> 
Do I need an internet connection to do this?

yes that is where the repositories are at ;-D

and updates

---

### Post by dwhitney67 on 2008-09-12
Yes, you will need an internet connection to download packages.  Carrier pigeons will not deliver to you.

I can understand if you do not have WiFi; do you have the wired-internet working?

Another alternative if you have no networking capabilities under Ubuntu is to find a system that does have networking, so that you can download the individual packages.  You can then copy them to your Ubuntu system (using thumb-drive or whatever), and then install them using 'sudo dpkg -i *.deb'.  The only problem with this approach is satisfying all of the dependencies each package seems to have.

---

### Post by strakajagr on 2008-09-12
by the way... thank you for your help... it's very much appreciated.

---

### Post by strakajagr on 2008-09-12
OK tomorrow, I need to buy a 25 ft network cable... It's not the end of the world... It's just that I was trying to avoid hardwiring it... If that's what I need to do, then so be it.

Thanks for your help.  I'll get back to you with an update after I gain network access and get the appropriate downloads.

---

