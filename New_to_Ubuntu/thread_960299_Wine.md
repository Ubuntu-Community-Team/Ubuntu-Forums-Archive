---
title: "Wine"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by SolarKoka on 2008-10-27
I have downloaded Wine, and it selfinstalled.

What now? How do I operate it? :confused::confused::confused:

I am asking this in the forums instead of looking for a help file or something, simply because I recently installed Ubuntu because from a friend I heard it ran smoother than windows, so I decided to test that out.

Thank you in advance for the assistance.

---

### Post by sepz on 2008-10-27
Do winecfg at the prompt to setup your audio/video settings and so forth.
Then to run you would do something like 

```
wine /home/username/program.exe
```

or you can use 

```
wine ~/program.exe
```

Change this to wherever your file is located eg ~/Desktop/program.exe etc) at the terminal or alt+f2 and input the above.

You should also have a wine folder under the Applications menu if you are using gnome Applications -> Wine   which gives you options to configure and run your installed programs.

---

### Post by roger_1960 on 2008-10-27
Hi

Read this post

[http://ubuntuforums.org/showthread.php?t=871535](http://ubuntuforums.org/showthread.php?t=871535)

---

### Post by drakeman007 on 2008-10-27
> **SolarKoka said:**
> I have downloaded Wine, and it selfinstalled.

What now? How do I operate it? :confused::confused::confused:

I am asking this in the forums instead of looking for a help file or something, simply because I recently installed Ubuntu because from a friend I heard it ran smoother than windows, so I decided to test that out.

Thank you in advance for the assistance.


Hello, wine is great, you can use grafical mode tu configure it, just go the applications menu then the wine launcher and u will see the wine config settings, and when you want to intall new windows or exe application just do it like windows with double click....:)

---

### Post by SolarKoka on 2008-10-27
> **sepz said:**
> Do winecfg at the prompt to setup your audio/video settings and so forth.
Then to run you would do something like 

```
wine /home/username/program.exe
```

or you can use 

```
wine ~/program.exe
```

Change this to wherever your file is located eg ~/Desktop/program.exe etc) at the terminal or alt+f2 and input the above.

You should also have a wine folder under the Applications menu if you are using gnome Applications -> Wine   which gives you options to configure and run your installed programs.

what is winecfg? what is the "so forth"? specify please, sepz, otherwise all you did was increase your post count with no usefulness.

Also, the howto link you gave is useless, all it gives are links as to where to download wine not exact guides how to set it up after installation and how to use it. so roger`s post is useless.

---

### Post by roger_1960 on 2008-10-27
Hmm

Try this one

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Its pretty specific

---

### Post by bodhi.zazen on 2008-10-27
To "set up" wine you use winecfg.

To run an application you use

wine /path/to/application.exe

either in the command line or you can make a launcher. Many times you can also navigate to the .exe in nautilus and double click it.

What is it you are wanting to do ?

FYI for all things wine, follow the guides at wineHQ

Search on you application in the application data base :

[http://www.winehq.org/](http://www.winehq.org/)

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Valok on 2008-10-27
By winecfg, people mean put that into a terminal and hit enter.  This will bring up the wine configuration menu where you can play around with settings.  This needs to be done at least once before you try to install programs.

---

### Post by Jerriy on 2008-12-28
> **Valok said:**
> By winecfg, people mean put that into a terminal and hit enter.  This will bring up the wine configuration menu where you can play around with settings.  This needs to be done at least once before you try to install programs.

Just did that: installed wine (& the whole of ubuntu ibex by the way) 

but when the Wine config menu shows up, the tab "Audio" failed to get the sound right. It claims to not have detected any sound (despite ubuntu itself having detected and tedted OK (so far at least)

It then suggested for me to "select one of the following sound drivers:

ALSA
OSS
NAS and
ESounD

I tested all of them (pressed the provided "test sound" button) but all of the drivers resulted in a negative "Audio test failed" message.

Pressing the button right next door ("control panel") resulted in the negative message that launching it "was not implemented yet".

---

### Post by Jerriy on 2008-12-28
I've got sound in ubuntu
How come "Wine" didn't detect that?

Any help will be appreciated

---

### Post by Jerriy on 2008-12-28
Wine configuration is automatically of "Windows xp" version. Is that the reason? (my "real" windows is Vista)

---

### Post by Jerriy on 2008-12-28
I couldn't find anything in the [community ubuntu documentation]("https://help.ubuntu.com/community/Wine") about audio settings

---

