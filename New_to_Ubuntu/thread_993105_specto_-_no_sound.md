---
title: "specto - no sound"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by LeeU on 2008-11-25
I have installed specto (great program!) and set up a sound file (.wav format) but it doesn't sound when an update is given. Any ideas what is happening?

---

### Post by Crafty Kisses on 2008-11-25
What are the results of this command?
```
lspci
```

---

### Post by LeeU on 2008-11-25
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 GS (rev a1)

```

---

### Post by G|N| on 2008-11-26
Hello,

Thank you for using specto :)

This is how we play a sound file in specto, so can you try this code?

1) Open a terminal and enter this command:
```
python
```
Now you are using the python shell (press ctrl + d if you want to go back to the normal shell)

2) enter the following commands:
```

import gnome

```

```

gnome.sound_play("/home/you/yourwavfile.wav")

```

Can you hear sound now?
And does your soundcard work when playing music?
If you see some error when executing this code, please post it here.

I hope we can solve your problem :)

---

### Post by LeeU on 2008-11-26
> **G|N| said:**
> Can you hear sound now?

Entering the code above, no.

> **G|N| said:**
> And does your soundcard work when playing music?

Yes, just fine.

> **G|N| said:**
> If you see some error when executing this code, please post it here.
No, no error codes.

---

### Post by G|N| on 2008-11-26
And do you have other programs that play music running at the same time?

edit: [There seems to be a problem with gnome_play on gutsy]("https://bugs.launchpad.net/ubuntu/+source/gnome-python/+bug/153704") ... maybe this is your problem

---

### Post by LeeU on 2008-11-26
I have tried it both ways and it doesn't work.


EDIT: Okay, I guess I'll just have to keep an eye out for the popup alerts. Great product. Thanks! I may review it for our site.

---

### Post by G|N| on 2008-11-27
Another solution is to use the development version from specto.
It is stable  enough and it allows you to use a custom command when a watch is changed so you can use your own command to play a sound (or even espeak to actually say that you have an update :))

Installation instructions: 

**Getting Specto from Bazaar (bzr)**

If you want to take a look at all the branches related to Specto (some of which could be made by third parties), visit our [launchpad bazaar branches page]("https://code.launchpad.net/specto").

To get the official main development branch (named specto-main), grab it with this command:
```

bzr branch lp:specto

```
Note that the SVN version of Specto on google code hosting is deprecated and should not be used.

You may want to keep your bzr version of Specto updated from time to time. Assuming you are in the directory where you keep the Specto bzr trunk (specto-main):
```

bzr pull

```

To run specto without installing it: just run the script
```

launch.sh

```
To install specto system-wide (do this if you have multiple users doing it, if you are a package maintainer or if you want the translations to work). You need to run the setup script as a super-user. Do this in the folder where you extracted Specto:
```

sudo python setup.py install
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

```

Try it if you want and also give us some feedback about features, bugs,...

---

### Post by frenchn00b on 2009-11-08
> **G|N| said:**
> Hello,

Thank you for using specto :)

This is how we play a sound file in specto, so can you try this code?

1) Open a terminal and enter this command:
```
python
```
Now you are using the python shell (press ctrl + d if you want to go back to the normal shell)

2) enter the following commands:
```

import gnome

```

```

gnome.sound_play("/home/you/yourwavfile.wav")

```

Can you hear sound now?
And does your soundcard work when playing music?
If you see some error when executing this code, please post it here.

I hope we can solve your problem :)

I too have no sound.

is it possible that he codes specto with aplay , instead of gnome and python. it is fully not working that way.

Also, the aplay is far more stable. 

man, nothing works :( like windows

the time for refresh is not present in the configuration under X, ie. preferences window
no sound if you have fluxbox, or light weight managers
the date/time in xterm when it is refreshed automatically into the logs is not present
aplay use is not present
a sound test button, not present in the preferences window
a settings for each range of error is not present
the settings of 0.02 is based on the filesize apparently, it is too high. it should be reduced to 0.003
the error detection default of 0.02 and the error in percent display in the logs are not corresponding to the ini files
the error range for detecting the differences is not in percentage, apparently. A value of error detection, working, of 0.003 is kind of too low
the presence of the little icon into the trayer shall be selected by default, in the config
Running a special scripts or command line after detection ought to be added for human enhanced and flexibility of the application
The add watch and edit are useful and can select the time to auto update
In the icon, in the trayer, when one right click on it, it is not displaying Refresh, it should otherwise it has no senses to have an icon.   
The time in the config, into digging, of 3600000 is not really easy for being setup, it ought to be in seconds, for remaining human,
kill the processes, ie.. as he called murdering, with CTRL + C is not working
murdering shall be replaced by killing, or something that is normally used under linux
and finally it shall be ran from console/command line to play sounds on server, without X
 

Conclusion: 
great program since it is one of the first for ports, ftp, ... so much things
 but 
still lot of work to be giving to be entering into Debian stable!

---

### Post by frenchn00b on 2009-11-08
> **G|N| said:**
> Another solution is to use the development version from specto.
It is stable  enough and it allows you to use a custom command when a watch is changed so you can use your own command to play a sound (or even espeak to actually say that you have an update :))

Installation instructions: 

**Getting Specto from Bazaar (bzr)**

If you want to take a look at all the branches related to Specto (some of which could be made by third parties), visit our [launchpad bazaar branches page]("https://code.launchpad.net/specto").

To get the official main development branch (named specto-main), grab it with this command:
```

bzr branch lp:specto

```
Note that the SVN version of Specto on google code hosting is deprecated and should not be used.

You may want to keep your bzr version of Specto updated from time to time. Assuming you are in the directory where you keep the Specto bzr trunk (specto-main):
```

bzr pull

```

To run specto without installing it: just run the script
```

launch.sh

```
To install specto system-wide (do this if you have multiple users doing it, if you are a package maintainer or if you want the translations to work). You need to run the setup script as a super-user. Do this in the folder where you extracted Specto:
```

sudo python setup.py install
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

```

Try it if you want and also give us some feedback about features, bugs,...

Seems worst
because 
INTERNET > GOOGLE READER  is the only thing
you forgot the most important again: the Internet URL. One cannot check the webpages, and it is target of your program.

into
 GOOGLE READER , if one enter a webpage, it doesnt want to go further, asking a login and password... pfpff

---

### Post by frenchn00b on 2009-11-08
> **G|N| said:**
> Another solution is to use the development version from specto.
It is stable  enough and it allows you to use a custom command when a watch is changed so you can use your own command to play a sound (or even espeak to actually say that you have an update :))

Installation instructions: 

**Getting Specto from Bazaar (bzr)**

If you want to take a look at all the branches related to Specto (some of which could be made by third parties), visit our [launchpad bazaar branches page]("https://code.launchpad.net/specto").

To get the official main development branch (named specto-main), grab it with this command:
```

bzr branch lp:specto

```
Note that the SVN version of Specto on google code hosting is deprecated and should not be used.

You may want to keep your bzr version of Specto updated from time to time. Assuming you are in the directory where you keep the Specto bzr trunk (specto-main):
```

bzr pull

```

To run specto without installing it: just run the script
```

launch.sh

```
To install specto system-wide (do this if you have multiple users doing it, if you are a package maintainer or if you want the translations to work). You need to run the setup script as a super-user. Do this in the folder where you extracted Specto:
```

sudo python setup.py install
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

```

Try it if you want and also give us some feedback about features, bugs,...

beta testing thsi new version:

this DOES NOT solve the issue you have with the sound. Please make it simple. use aplay !

second the internet web pages checking arent present

good that you started to add few features.
the action after watching is working !! Hurra !

the action before watching is NOT working. The text is not clear in this window, BEFORE would be the right word.
I put :
wget "mywebpage" -O page.htm
and did a check with teh FILE module checking.
so so update of the file page.htm
 
pfff 
pffffff

Need a backend for crontab or running as daemon, think servers ;)

You have got huge huge amount of work to make it stable.

---

### Post by kiddo on 2009-11-08
> this DOES NOT solve the issue you have with the sound. Please make it simple. use aplay !

Complaining in the Ubuntu forums is not helpful, you need to file bugs in the official bug tracker, otherwise I'll never notice or lose track pretty quickly. Here, I filed one for you: [http://code.google.com/p/specto/issues/detail?id=289](http://code.google.com/p/specto/issues/detail?id=289)

> second the internet web pages checking arent present

They work fine for me as always. If the issue persists, please file bug reports with detailed info on how to reproduce the problem, activate the debug log and provide ~/.config/specto/error.log, etc.

> the action before watching is NOT working. The text is not clear in this window, BEFORE would be the right word.
I put :
wget "mywebpage" -O page.htm
and did a check with teh FILE module checking.
so so update of the file page.htm

I have problems understanding what you mean, please clarify (and preferrably in a real, clean bug report... forum threads get confusing/cluttered quickly)

> pfff 
pffffff

Des commentaires comme ça n'aident aucunement :KS

> You have got huge huge amount of work to make it stable.

Thanks for reminding me. By the way, I am not a professional programmer, patches are very welcome (actually, make your own bazaar branches of the code and see if you can make it better). I'll go back to my student life for the time being :)

---

### Post by frenchn00b on 2009-11-08
> **kiddo said:**
> Complaining in the Ubuntu forums is not helpful, you need to file bugs in the official bug tracker, otherwise I'll never notice or lose track pretty quickly. Here, I filed one for you: [http://code.google.com/p/specto/issues/detail?id=289](http://code.google.com/p/specto/issues/detail?id=289)



They work fine for me as always. If the issue persists, please file bug reports with detailed info on how to reproduce the problem, activate the debug log and provide ~/.config/specto/error.log, etc.



I have problems understanding what you mean, please clarify (and preferrably in a real, clean bug report... forum threads get confusing/cluttered quickly)



Des commentaires comme ça n'aident aucunement :KS



Thanks for reminding me. By the way, I am not a professional programmer, patches are very welcome (actually, make your own bazaar branches of the code and see if you can make it better). I'll go back to my student life for the time being :)

ups sorry... If you are student, that's something else. 
Studies, first, ... diplomas first. When I was student, I had limited access to computer at home, during 3-4 years, and hardly time to touch the keyboard once home. That worked very good.Diplomas first.

---

### Post by kiddo on 2009-11-08
Thanks for understanding, I indeed have very little time to help maintain Specto (I rarely code, partly because I'm not very proefficient at it), and Wout is also quite busy these days I think. Add to that the fact that the app just seems to work without much problems on our ends, so if bugs are not filed, we won't know that something is wrong.

Hopefully *one day* that issue could be fixed... but without patches, it may take a long time for the reason mentioned above ;)

By the way, if anyone reading this is looking for a small project to join to learn Python, this can be an interesting learning experience ;)

---

### Post by frenchn00b on 2009-11-08
> **kiddo said:**
> Thanks for understanding, I indeed have very little time to help maintain Specto (I rarely code, partly because I'm not very proefficient at it), and Wout is also quite busy these days I think. Add to that the fact that the app just seems to work without much problems on our ends, so if bugs are not filed, we won't know that something is wrong.

Hopefully *one day* that issue could be fixed... but without patches, it may take a long time for the reason mentioned above ;)

By the way, if anyone reading this is looking for a small project to join to learn Python, this can be an interesting learning experience ;)

Somehting that I do not understand is why there is lot of coders that are student under Linux. It would take few days, only, for an experienced and old debian/ubuntu informatician. They usually do big developments, kde, gnome, ... 
Well your program is very useful, I am sure for a lot. Such novel ideas are always appreciated. Little programs but they are gorgeous.

---

### Post by aazan on 2011-01-04
> **LeeU said:**
> I have installed specto (great program!) and set up a sound file (.wav format) but it doesn't sound when an update is given. Any ideas what is happening?

You may run a sound in another program like sound player. I solved this problem by adding following line in advance options (Edit->Advanced Options-> Run a custom command).

[FONT="Tahoma"][SIZE="1"]rhythmbox MySound.avi; google-chrome MyWebSile.html[/SIZE][/FONT]

---

