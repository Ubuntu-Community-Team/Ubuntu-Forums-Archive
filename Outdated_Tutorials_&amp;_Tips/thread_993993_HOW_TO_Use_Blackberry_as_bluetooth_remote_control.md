---
title: "HOW TO: Use Blackberry as bluetooth remote control"
date: 2008-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by SZ07 on 2008-11-26
**[SIZE=4]INTRODUCTION[/SIZE]**
I hook up my laptop to the tv to watch my videos. One thing that always bugged me was that I would have to get up if I wanted to forward, change audio or subtitles, etc. Then I read some guides of people using Nokia and Sony Ericsson phones as bluetooth remote controls. Since my Blackberry Pearl has bluetooth, I decided to try it out but had no luck in Windows. After some hard work and research, I was finally able to make this happen in Ubuntu.

This guide is written specifically for the Blackberry Pearl 8100 but should be applicable to other Blackberry phones as well. Also it can probably be adapted to work with other cellphones as well. Lastly, I accomplished this on Ubuntu 8.10 Intrepid Ibex, so I have no idea if it will work with other versions too.

**[SIZE=4]PREREQUISITES[/SIZE]**
"Your cell phone should support JSR-82 or event-reporting feature. If You do not have any information just try to use anyRemote, firstly in Server mode, then in AT-mode" -anyRemote website.

Basically your phone has to be able to use Java with bluetooth (most modern phones with BT will probably have no problem). As far as I know, the 8xxx Blackberry phones have support for this.

For getting Java files on Nokia phones, you might want to read this: [http://www.tim.id.au/blog/2007/05/25/anyremote-on-ubuntu/](http://www.tim.id.au/blog/2007/05/25/anyremote-on-ubuntu/)

**[SIZE=4]GENERAL IDEA[/SIZE]**
To get the computer and the phone talking to each other you need to make sure the bluetooth service is active (if it is you'll see a bluetooth icon in the panel). Next you will need to install a program on your phone and on your computer (this program will translate your phone keystrokes to commands in Ubuntu).

**[SIZE=4]SETTING UP THE PHONE[/SIZE]**
1. Go to [http://anyremote.sourceforge.net/dload.html](http://anyremote.sourceforge.net/dload.html). Go to the 'Java Client for WAP download' and from there download any of the jar files (they are all the same program - the only difference is that the files have different icon sizs - I used the file with 16x16, 32x32, and 64x64 icon sets).

2. After getting the jar file, transfer it to your Blackberry. If you have a media card, you should be able to use the 'massive USB storage feature' to get it on there. You might even be able to transfer the file via bluetooth, although it will probably be slow.

3. On your phone, go to Media, click the menu button, and select explore. Browse to the jar file and select it. Click 'Download' to install the application.

**[SIZE=4]SETTING UP THE COMPUTER[/SIZE]**
1. Open Synaptic, search for 'anyremote', and mark it for installation. Also search for 'pybluez' and mark it for installation as well. Then hit apply to install. (Note: the anyRemote package from the website is newer but depends on libbluetooh2. Ubuntu 8.10 has libbluetooh3)

2. Go back to the anyRemote site ([http://anyremote.sourceforge.net/dload.html](http://anyremote.sourceforge.net/dload.html)) and download the following (.deb packages):
-gAnyRemote (kAnyRemote if using Kubuntu)
-anyRemote2html
-java client
After downloading, double click on the .deb packages to install.

**[SIZE=4]CONNECTING[/SIZE]**

1. After installing everything, pair up the phone with the computer (For Blackberrys go to 'Set Up Bluetooth' and follow the directions. It should be able to find your computer after which it will ask you to enter a PIN. Enter any PIN and press ok. You should now see a popup in Ubuntu asking for the PIN. Click on it and enter the same PIN and your devices should be paired up.

2. Start up gAnyRemote (Applications > System Tools). If it gives a message about the Bluetooth service not being active just ignore it. You should see a remote icon in the panel. Click on it to bring up the anyRemote window. Go to Setup > Preferences and under 'Show in list' check 'all.' Click OK.

3. Select the application you want to run and click start (more on this later).

4. In your phone, start up anyRemote, and from the menu, select search. It should find your computer and any other bluetooth devices you may have. Then select your computer device and from the menu click connect.



Now key presses on your phone should translate into actions on your computer.

**[SIZE=4]CONFIGURING ANYREMOTE[/SIZE]**
This application is very powerful and has a load of configurations that will allow you to control a variety of applications, keyboard, and even mouse movements. The key to configuring to your liking is to get familiar with the configuration files in /usr/share/anyremote/cfg-data. There is thorough documentation available on the anyRemote website.

I have attached my personal gnome-mplayer configuration below, which was edited from the mplayer configuration file. With this I can browse media files on my phone, open them up and play them in gnome-mplayer. Since I mostly watch dual-audio .mkv files, I added the option to change audio language and subtitles. My configuration is below:

1 2 3   
4 5 6
7 8 9
* 0 #

1: Seek back (equivalent to down key)
2: Change audio track
3: Seek forward (equivalent to up key)
4: Rewind (equivalent to left key)
5: Pause
6: Forward (equivalent to right key)
7: Toggle fullscreen
8: Toggle/change subtitles
9: Toggle control ((equivalent to C key)
*: Help
0: In-phone file browser
#: Quit player

If you want to use this configuration, download it to any directory and, in gAnyRemote, go to Setup > Preferences and add the directory containing the configuration file. The application will be available in the main window. Just start it, connect your phone to your computer and you will be good to go.

Any comments, suggestions, and questions are appreciated.

Sources:
[http://anyremote.sourceforge.net/index.html](http://anyremote.sourceforge.net/index.html)
[http://www.tim.id.au/blog/2007/05/25/anyremote-on-ubuntu/](http://www.tim.id.au/blog/2007/05/25/anyremote-on-ubuntu/)

---

### Post by Maheriano on 2008-12-15
Definitely going to try this when I get a new dongle. Thank you!

---

### Post by Maheriano on 2009-01-11
.

---

### Post by lazysarah on 2009-01-16
you should read some more about [Blackberry 8100 facts]("http://www.10facts.com/article/Technology/Mobile-Phones/BlackBerry/BlackBerry-8100.html") , good luck

---

### Post by StaticIp on 2009-01-21
I am unable to find the package "anyremote" any help??
~~Gabe~~

---

### Post by Maheriano on 2009-01-21
> **StaticIp said:**
> I am unable to find the package "anyremote" any help??
~~Gabe~~

Are you going to Add/Remove to find it? You have to go to Administration and open Synaptic to find it.

---

### Post by Dj TweeX on 2009-01-21
> **Maheriano said:**
> Are you going to Add/Remove to find it? You have to go to Administration and open Synaptic to find it.

Sorry i was logged in on my friends name.
I went to Administration then the synaptic package manager. i also tried using add/remove & even apt-get.
nothing. could it be that im running 8.04? any other information i will gladly share
~~Gabe~~

---

### Post by Dj TweeX on 2009-01-22
Ok so i just went to the site & downloaded it manually. i got gAnyremote installed no problems.
so i tried Anyremote.
& it configures them when i try to make it says this

```
gabe@hp-mini:~/Desktop/anyremote-4.15$ sudo make
Making all in src
make[1]: Entering directory `/home/gabe/Desktop/anyremote-4.15/src'
gcc -DUSE_BLUEZ=1 -DHAVE_GETLINE=1 -DUSE_XTEST=1 -DDATADIR=\"/usr/local/share\" -g -O2 -I/usr/local/include -Wall -D_REENTRANT -O2 -g  -L/usr/X11R6/lib -o anyremote atsend.o btio.o pr_l2cap.o main.o cmds.o parse.o utils.o xemulate.o conf.o -lbluetooth -lXtst 
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[1]: *** [anyremote] Error 1
make[1]: Leaving directory `/home/gabe/Desktop/anyremote-4.15/src'
make: *** [all-recursive] Error 1
gabe@hp-mini:~/Desktop/anyremote-4.15$ 
```

ive tried this,
[http://ubuntuforums.org/showthread.php?t=161330](http://ubuntuforums.org/showthread.php?t=161330)
Cause it seemed to be directly what my problem was but the solution there did not help. there is a newer version for that package out & it ways i already have it installed.
Please guys help me out.
~~Gabe~~

---

### Post by Dj TweeX on 2009-01-22
Ok guys right now im feeling geat. i think this is the first problem with ubuntu i have had & fixed myself. i did a little research
downloaded the package from here

[http://packages.debian.org/sid/libxtst-dev](http://packages.debian.org/sid/libxtst-dev)

& everything went smooth.
you were all there with me. lmao
Thanks for your help.
~~Gabe~~

---

### Post by Dj TweeX on 2009-01-22
ok i think im about to give up... haha
im stuck at installing the java client.

---

### Post by Dj TweeX on 2009-01-22
Ok so im still trying to install the Java Client. it keeps saying it cant find the java interpretor
please help?

---

### Post by SZ07 on 2009-02-03
> **Dj TweeX said:**
> Ok so im still trying to install the Java Client. it keeps saying it cant find the java interpretor
please help?

Can you provide some more information? Also, please tell us what phone specifically you are using and how far along in the process of the  Java Client install you are (e.g. have you moved the .jar file to your phone etc?)

By the sound of it, I'm guessing that the phone can't understand/process the java file. If you are using a blackberry, make sure that you have the latest operating system installed (v4.2.1.1xx or higher)

---

### Post by Dj TweeX on 2009-02-12
Sory for the delayed response,
I am useing a Blackberry Curve 8330
i manag3ed to get everything installed but when i search for services, it says its found some but doesn't show my computer.
I am able to manually connect my phone to my computer by entering the BT Address. but when it connects the application on my phone freezes.
Anyremote says my phone is connected but its frozen.
i am running 4.5 on my phone so its not that.

---

### Post by SZ07 on 2009-02-13
Ok so from what you have said I just want to make sure this is right. So far you have:

-installed anyremote, ganyremote and other required packages
-installed the java client on your 8330
-when you open anyremote on your phone and search, your computer is not available on the list of connectible bluetooth devices.
-when you manually connect the 8330 to your computer (via bluetooth) and then startup anyremote on your phone, it (anyremote application) freezes.
-the computer application (ganyremote) says that it is connected to the phone.

It is strange that your 8330 can pair up with the computer but when you use anyremote on the phone to search for the computer it doesn't show up. Maybe you can try to manually add the BT address in anyremote and then see what happens.

From your previous posts, it looks like you compiled anyremote yourself. I dont know if that is the reason for your troubles but it could be worth looking into. The anyremote website claims that the official repository package has problems. Maybe you could try removing you compiled package and installing the ones available on the Launchpad PPA ([https://launchpad.net/~anyremote/+archive/ppa](https://launchpad.net/~anyremote/+archive/ppa))

When you get past the connecting screen in anyremote (on your phone) and then the application freezes, is there any error message? Also, which application within ganyremote are you running?

When I have time, I will remove and then install all of the updated files (from Launchpad and the website) on my phone and computer and then see if I run into any issues. Until then you could try some of the stuff I mentioned and tell me if anything changes or not.

---

### Post by britline on 2009-07-24
how bout socket, i cant connect with wifi connection... anyone can help...????

---

### Post by dlbrando on 2009-12-14
I am having a hard time installing the java client on my laptop, is there a better way?

I downloaded anyremote-j2me-client-4.18.tar.gz and extracted it.  Inside I found the install text file and executed this command:

>  ./configure --prefix=/usr --with-wtk=<path to WTK> --with-proguard=<path to ProGuard>
        su -c "make install"

then type my password, and it returns this:

> su: Authentication failure


I have tried it a few times to make sure, but I get the same error.  Any help?

---

