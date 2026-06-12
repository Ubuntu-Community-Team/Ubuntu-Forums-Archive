---
title: "Azureus Vuze 4.0 on Ubuntu 8.10 64 bit"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by lbarnes on 2008-11-05
Has anyone been able to do this?
the auto upgrade does not want to install
and just wants to restart azureus 3.x constantly.
i use 4.0 on vista and definitely like the layout better.
thanks guys

---

### Post by talsemgeest on 2008-11-05
I've been wanting to do this. As soon as I get around to it I will tell you how it went.

---

### Post by taiji_jian on 2008-11-07
I have this same problem in Intrepid-i386. Vuze 3 wants to upgrade to Vuze 4, downloads a package, and constantly wants to restart.

---

### Post by talsemgeest on 2008-11-07
Ok, I tried installing Vuze 4 manually, but it gives me a bunch of errors and doesn't start.

---

### Post by Divizix on 2008-11-08
Having the same problem on 8.10 64bit, hopefully someone will figure out how to make it work soon.

---

### Post by daetsy on 2008-11-08
I had it working on a clean install of 8.10, but wasn't over impressed with it, so I went back to the version in synaptic.
I D/L'd the tar/gz2 file from Sourceforge, double clicked to extract it, then in Terminal cd'd to /home/vuze (or where you save it) then in Terminal just enter./azureus. If you completely remove Vuze in synaptic, it might install. I haven't tried because I don't want it back :)

---

### Post by MrSootentai on 2008-11-13
Here's the method I used that is currently working for me (albeit it is on 32bit):
1) Download the 4.0 Vuze from here [http://www.vuze.com/Download.html](http://www.vuze.com/Download.html)
2) Move the .tar.bz2 to a folder where you want to run the app.
3) Open the Terminal and cd into the directory, and > tar xvf Vuze_Installer.tar.bz2 .
4) Then cd into the 'vuze' directory.
5) Now to run the app simply type into the terminal > ./azureus
6) Success!!
If you want to make a menu item just right click on 'Applications' and click 'Edit Menus'. Create a new item, and browse to where the 'azureus' file you ran is located.
That should be it.
Hope that helps it a bit this guide was a bit rushed because I am currently in class.

---

### Post by icedfusion on 2008-11-13
I have the same issue.
Each time vuze restarted it wanted to download the update again.
I uninstalled and reinstaled vuze and now it just wants to restart in a loop.
system is ubuntu 8.10 upgraded from 8.04 (upgraded from 7.10, etc) AMD 64bit

any success stories will be gratefully received..

---

### Post by talsemgeest on 2008-11-13
> **MrSootentai said:**
> Here's the method I used that is currently working for me (albeit it is on 32bit):
1) Download the 4.0 Vuze from here [http://www.vuze.com/Download.html](http://www.vuze.com/Download.html)
2) Move the .tar.bz2 to a folder where you want to run the app.
3) Open the Terminal and cd into the directory, and .
4) Then cd into the 'vuze' directory.
5) Now to run the app simply type into the terminal 
6) Success!!
If you want to make a menu item just right click on 'Applications' and click 'Edit Menus'. Create a new item, and browse to where the 'azureus' file you ran is located.
That should be it.
Hope that helps it a bit this guide was a bit rushed because I am currently in class.
No, that doesn't seem to work under 64 bit, that was the first thing I tried.

---

### Post by Khamin on 2008-11-16
> No, that doesn't seem to work under 64 bit, that was the first thing I tried.

Use **64bit** version. Visit [vuze downloads page]("http://azureus.sourceforge.net/download.php") for more information. Download **AMD64 build** and try again as *MrSootentai* said.

---

### Post by talsemgeest on 2008-11-16
Wow, I thought I had downloaded the 64bit version. I guess I was wrong.

Thanks, it works now for me.

---

### Post by mnial on 2008-11-17
so is vuze 4.0 worth it?

i mean this is a complete FAIL for the vuze devrlopers to create an update that is causing an infinity loop...

---

### Post by talsemgeest on 2008-11-17
> **mnial said:**
> so is vuze 4.0 worth it?

i mean this is a complete FAIL for the vuze devrlopers to create an update that is causing an infinity loop...
No, that is Vuze 3 that is in the ubuntu repositories. Vuze 4 fixes most of the problems of 3, and adds some nice features of its own. I would strongly recommend it.

---

### Post by AlejandroDelLoco on 2008-11-17
> **mnial said:**
> so is vuze 4.0 worth it?

i mean this is a complete FAIL for the vuze devrlopers to create an update that is causing an infinity loop...

I think the infinity loop is actually being caused by the way that it's packaged for ubuntu. Sigh.

[COLOR="Red"]EDIT:[/COLOR] Poking around Launchpad I found a packaged version of Vuze 4.0.0.2 in [Stefano Maioli's PPA]("https://launchpad.net/~smaioli/+archive"). Use at your own risk etc. etc.

---

### Post by mobrien118 on 2008-11-22
I figured this one out.

If you extract the "Azureus2.jar" from the tar.gz file, or simply copy the Azureus4.0.0.x.jar OVER /usr/share/java/Azureus2.jar, you will be halfway. At this point, you will get an error that the main class isn't found. Then edit /usr/bin/azureus so the classpath is "org.gudy.azureus2.ui.swt.Main" instead of whatever it was before (org.gudy.ui.azureus2.[something]).

That has me up and running.

So, to reiterate with sweet numbers:
1. Copy new Azureus2.jar file over /usr/share/java/Azureus2.jar
2. Edit /usr/bin/azureus and replace the classpath (on the last line) with "org.gudy.azureus2.ui.swt.Main"

Done!

Hope this is helpful!

---

### Post by talsemgeest on 2008-11-22
I'm quite sure it is.

Thanks!

---

### Post by colo505 on 2008-11-23
> **AlejandroDelLoco said:**
> I think the infinity loop is actually being caused by the way that it's packaged for ubuntu. Sigh.

[COLOR="Red"]EDIT:[/COLOR] Poking around Launchpad I found a packaged version of Vuze 4.0.0.2 in [Stefano Maioli's PPA]("https://launchpad.net/~smaioli/+archive"). Use at your own risk etc. etc.

Looking for a packaged version of v.4.0.0.4. If you have a link, it would be great if you could share it with us. Thanks

---

### Post by Stephen_at on 2008-11-23
That worked for me.

Thanks - it was driving me mad.

---

### Post by luis.torres.gomez on 2008-11-23
> **mobrien118 said:**
> I figured this one out.

If you extract the "Azureus2.jar" from the tar.gz file, or simply copy the Azureus4.0.0.x.jar OVER /usr/share/java/Azureus2.jar, you will be halfway. At this point, you will get an error that the main class isn't found. Then edit /usr/bin/azureus so the classpath is "org.gudy.azureus2.ui.swt.Main" instead of whatever it was before (org.gudy.ui.azureus2.[something]).

That has me up and running.

So, to reiterate with sweet numbers:
1. Copy new Azureus2.jar file over /usr/share/java/Azureus2.jar
2. Edit /usr/bin/azureus and replace the classpath (on the last line) with "org.gudy.azureus2.ui.swt.Main"

Done!

Hope this is helpful!

This Works for 8.10 x86 too

---

### Post by claypole on 2008-11-26
Works perfectly on Intrepid, thanks! :)

---

### Post by neopas on 2008-11-27
> **mobrien118 said:**
> I figured this one out.

If you extract the "Azureus2.jar" from the tar.gz file, or simply copy the Azureus4.0.0.x.jar OVER /usr/share/java/Azureus2.jar, you will be halfway. At this point, you will get an error that the main class isn't found. Then edit /usr/bin/azureus so the classpath is "org.gudy.azureus2.ui.swt.Main" instead of whatever it was before (org.gudy.ui.azureus2.[something]).

That has me up and running.

So, to reiterate with sweet numbers:
1. Copy new Azureus2.jar file over /usr/share/java/Azureus2.jar
2. Edit /usr/bin/azureus and replace the classpath (on the last line) with "org.gudy.azureus2.ui.swt.Main"

Done!

Hope this is helpful!

you rock my friend :)

---

### Post by comradekingu on 2008-12-03
If you just want 4.0.0.4 without going via the route of installing 3.1.1.1 from the repos you can 

1.download [Vuze_4.0.0.4_linux-x86_64.tar.bz2]("http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=280700&release_id=641819")

2. Unzip

3 sudo apt-get build-dep azureus (This will install all azureus dependencies without downloading azureus itself)


This wont be updated whenever the repo version is, so consider it to be a quick fix. It isnt ideal, but until the azureus MOTU can fix things this will be it i guess.

---

### Post by acalafra on 2008-12-07
to solve the problem of version 3.whaterver restarting after update indefinetly you must run it once as root.

go to terminal and type:

gksudo vuze

or

gksudo azureus

it should be able to apply the update and restart one last time then you can run it from the gui as normal user again

---

### Post by talsemgeest on 2008-12-07
That was one of the first things I tried, but it makes no difference. Just download vuze from the main website and run it from there, that way you get the very latest vuze with no trouble updating.

---

### Post by jamesstansell on 2008-12-07
> **talsemgeest said:**
> That was one of the first things I tried, but it makes no difference. Just download vuze from the main website and run it from there, that way you get the very latest vuze with no trouble updating.

It would be nice if they had it packaged as a jnlp application.  (One can wish anyway!)

---

### Post by mnial on 2008-12-08
> **mobrien118 said:**
> 
That has me up and running.

So, to reiterate with sweet numbers:
1. Copy new Azureus2.jar file over /usr/share/java/Azureus2.jar
2. Edit /usr/bin/azureus and replace the classpath (on the last line) with "org.gudy.azureus2.ui.swt.Main"

Done!

Hope this is helpful!

Thank You very much!
This really helped!

---

### Post by Tom--d on 2008-12-08
Remove the Vuze from Synpatic.

Download a 64bit .deb here and double click it:

[http://www.getdeb.net/download/3309/0](http://www.getdeb.net/download/3309/0)

---

### Post by mobrien118 on 2008-12-08
> **acalafra said:**
> to solve the problem of version 3.whaterver restarting after update indefinetly you must run it once as root.

go to terminal and type:

gksudo vuze

or

gksudo azureus

it should be able to apply the update and restart one last time then you can run it from the gui as normal user again


Did you actually try this? That is how I used to do it, but it doesn't work in this situation. That's why I found "Another way".

--mobrien118

---

### Post by acalafra on 2008-12-15
yeah it worked for me but i ended up removing it anyway and installing 4.0

---

### Post by ahusain on 2008-12-17
> **mobrien118 said:**
> I figured this one out.

If you extract the "Azureus2.jar" from the tar.gz file, or simply copy the Azureus4.0.0.x.jar OVER /usr/share/java/Azureus2.jar, you will be halfway. At this point, you will get an error that the main class isn't found. Then edit /usr/bin/azureus so the classpath is "org.gudy.azureus2.ui.swt.Main" instead of whatever it was before (org.gudy.ui.azureus2.[something]).

That has me up and running.

So, to reiterate with sweet numbers:
1. Copy new Azureus2.jar file over /usr/share/java/Azureus2.jar
2. Edit /usr/bin/azureus and replace the classpath (on the last line) with "org.gudy.azureus2.ui.swt.Main"

Done!

Hope this is helpful!

this worked perfectly

---

### Post by costis on 2008-12-31
I think the problem is that /usr/share/vuze/ is not writable to the user. 
So I did ```
# chown root:MyUsername /usr/share/vuze/ && chmod g+w /usr/share/vuze/
```
in order to get
```

drwxr-xr-x    3 root root        4096 2008-12-14 19:46 ???
drwxrwxr-x    3 root MyUsername  4096 2009-01-01 03:12 vuze
drwxr-xr-x    2 root root        4096 2008-10-29 23:46 ???

```
At least in my case the problem was solved that-way, after installing the version4 amd64 deb file.

---

### Post by rocketero on 2009-01-22
thanks for the advice here, Now I'm running Azureus (VuZe) 4.0.0.4 on Ubuntu Intrepid 8.10 Amd64-bit KDE 4.1.3 and GDM 2.24.1

---

### Post by foska on 2009-01-23
Thanks Mob,

It worked for me!

> **mobrien118 said:**
> I figured this one out.

If you extract the "Azureus2.jar" from the tar.gz file, or simply copy the Azureus4.0.0.x.jar OVER /usr/share/java/Azureus2.jar, you will be halfway. At this point, you will get an error that the main class isn't found. Then edit /usr/bin/azureus so the classpath is "org.gudy.azureus2.ui.swt.Main" instead of whatever it was before (org.gudy.ui.azureus2.[something]).

That has me up and running.

So, to reiterate with sweet numbers:
1. Copy new Azureus2.jar file over /usr/share/java/Azureus2.jar
2. Edit /usr/bin/azureus and replace the classpath (on the last line) with "org.gudy.azureus2.ui.swt.Main"

Done!

Hope this is helpful!

---

### Post by McR on 2009-02-13
> **ahusain said:**
> this worked perfectly

4Me2

:guitar:

---

### Post by rvgeelen on 2009-02-17
this is driving me nuts! I've done the replacing of azureus2.jar and the linechanching. Even rebooted! nothing! still starts with version 3.10. Also I can't get a green light, even though I opened the ports in Iptables and on my router and firewallbox running on m0n0wall.
Time for a new tutorial I suppose for Ubuntu 8.10

Can anyone please help. I've been at it for days!!!

edit: Can you believe it!!!!! I made a typo in the portforwarding rules!!! I feel like a n00b

---

### Post by mtinman on 2009-05-27
For anyone interested, this also works on Jaunty (9.04) x86_64-bit version too, thanks for the fix!:popcorn:

---

### Post by Jessberto on 2009-07-08
Great Help! i was having the usr/share/vuze not writable problem and i did what the person above said.

# chown root:MyUsername /usr/share/vuze/ && chmod g+w /usr/share/vuze/ 
I have vuze 4.2.0.2 Ubuntu 9.04  and its working perfect, thanks a lot.

---

### Post by BUGabundo on 2009-08-02
use this ppa [https://launchpad.net/~knorr/+archive/ppa](https://launchpad.net/~knorr/+archive/ppa)

$ sudo add-apt-repository ppa:knorr/ppa

---

### Post by Zennmaster on 2009-08-16
A big, belated "THANK YOU" to you kind folks!

Also, in Jaunty,after installing 4.2.0.4, I got a pop-up error message stating that swt.jar could not be auto updated, and that it was looking in /home/user/.azureus.

I just copied the swt.jar file from the download into my .azureus directory and everyone was happy.

Thanks again!

---

### Post by Weidbrewer on 2009-09-02
This post is not a bookmark so that my dumba$$ can find this thread later and maybe finally get Vuze to work on my 64-bit install...

---

### Post by kevinindia on 2009-09-05
> **costis said:**
> I think the problem is that /usr/share/vuze/ is not writable to the user. 
So I did ```
# chown root:MyUsername /usr/share/vuze/ && chmod g+w /usr/share/vuze/
```in order to get
```

drwxr-xr-x    3 root root        4096 2008-12-14 19:46 ???
drwxrwxr-x    3 root MyUsername  4096 2009-01-01 03:12 vuze
drwxr-xr-x    2 root root        4096 2008-10-29 23:46 ???

```At least in my case the problem was solved that-way, after installing the version4 amd64 deb file.


This works except that had to add -R flag to do it recursively. else will keep complain for each update/plugin installation.

---

