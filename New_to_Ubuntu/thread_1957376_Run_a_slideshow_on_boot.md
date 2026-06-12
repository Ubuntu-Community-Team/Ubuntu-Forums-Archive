---
title: "Run a slideshow on boot"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by DHinton on 2012-04-12
I am trying to set-up a computer to run a slide on boot, I am using Ubuntu 12.  Any help would be greatly appreciated.

---

### Post by roelforg on 2012-04-12
> **DHinton said:**
> I am trying to set-up a computer to run a slide on boot, I am using Ubuntu 12. Any help would be greatly appreciated.
 
Be more specific,
want it when the desktop appears?
or when the login screen shows?
or when the ubuntu logo with the dots show?
or even the bootloader?
should it be back- or foreground?

---

### Post by DHinton on 2012-04-12
> **roelforg said:**
> Be more specific,
want it when the desktop appears?
or when the login screen shows?
or when the ubuntu logo with the dots show?
or even the bootloader?
should it be back- or foreground?

I guess I am looking for it to run when the desktop appears but what ever way is easiest, it should be full screen in the foreground. (I am a novice on Ubuntu, but trying to learn!)

---

### Post by roelforg on 2012-04-12
> **DHinton said:**
> I guess I am looking for it to run when the desktop appears but what ever way is easiest, it should be full screen. (I am a novice on Ubuntu, but trying to learn!)
 
Search in the launcher menu for "Startup application"
One of the entries should be the startup application config (can't remember full name).
That app will let you add commands that are run after logging in for the user you're using.

---

### Post by DHinton on 2012-04-12
> **roelforg said:**
> Search in the launcher menu for "Startup application"
One of the entries should be the startup application config (can't remember full name).
That app will let you add commands that are run after logging in for the user you're using.

Okay got a bit farther, it will launch f-spot (the slideshow program I found) but I cannot seem to get it to run a slide show automatically.

---

### Post by roelforg on 2012-04-12
> **DHinton said:**
> Okay got a bit farther, it will launch f-spot (the slideshow program I found) but I cannot seem to get it to run a slide show automatically.
 
Did you use the --slideshow argument?
See: [http://manpages.ubuntu.com/manpages/lucid/man1/f-spot.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/f-spot.1.html)

---

### Post by DHinton on 2012-04-12
> **roelforg said:**
> Did you use the --slideshow argument?
See: [http://manpages.ubuntu.com/manpages/lucid/man1/f-spot.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/f-spot.1.html)

That worked, but it runs in a window, I don't see a run full screen option? Any ideas?

---

### Post by DHinton on 2012-04-16
> **DHinton said:**
> That worked, but it runs in a window, I don't see a run full screen option? Any ideas?

I know in windows I can get it to work by putting a *.ppsx file in the start-up folder, but I cannot seem to get this to work in Ubuntu.

---

### Post by Mark Phelps on 2012-04-16
> **DHinton said:**
> I know in windows I can get it to work by putting a *.ppsx file in the start-up folder, but I cannot seem to get this to work in Ubuntu.

That file is a PowerPoint XML file -- which doesn't work in Linux, at that is MS Office.

---

### Post by perspectoff on 2012-04-16
You can set Ubuntu to start in screensaver mode.

Basically, you would set up the Login manager to enable auto-login to a specific user account, enabling the "Lock session" option (which starts the screensaver at boot).

Then, there are screensaver modules that will play any media. 

Screensaver -> Banners & Pictures -> Media Screen Saver -> Setup... -> Add.. 

That is the easiest way to do that.

I know how to do this in Kubuntu, but the specific steps in Ubuntu may be slightly different, so you'll have to hunt for them a bit.

---

### Post by DHinton on 2012-04-16
> **Mark Phelps said:**
> That file is a PowerPoint XML file -- which doesn't work in Linux, at that is MS Office.
Libre Office reads the file, put it I can't get it auto launch the file on start-up.

---

### Post by callmemahavir on 2012-04-16
1. You can develop an slide show in libre office and call it form shell script to run the slide show.

2. Write the line in file runslides.sh as ...

libreoffice -show ~/Documents/test.odp

2. I assume that the script file is runslides.sh

3. issue the following command in terminal...

chmod +x runslides.sh

update-rc.d runslides.sh defaults

4. now whenever you boot the slides are run.

---

### Post by Bobhuber on 2012-04-16
> **DHinton said:**
> I am trying to set-up a computer to run a slide on boot, I am using Ubuntu 12.  Any help would be greatly appreciated.
Take a look at xwinwrap and this.
[http://electricsheep.org/](http://electricsheep.org/)

---

### Post by stinkeye on 2012-04-16
The default image viewer will run a slideshow.
```
eog -f -s /home/glen/Pictures/seabreeze.png
```
Just need the path to an image in the folder to use for the slideshow.

To add to start up applications use a sleep command to allow the window manager time to load
eg
```
sh -c "sleep 5 && eog -f -s /home/glen/Pictures/seabreeze.png"
```

For your desktop background as a slideshow use **Wallch** in the
software centre.

---

### Post by DHinton on 2012-04-18
> **stinkeye said:**
> The default image viewer will run a slideshow.
```
eog -f -s /home/glen/Pictures/seabreeze.png
```
Just need the path to an image in the folder to use for the slideshow.

To add to start up applications use a sleep command to allow the window manager time to load
eg
```
sh -c "sleep 5 && eog -f -s /home/glen/Pictures/seabreeze.png"
```

For your desktop background as a slideshow use **Wallch** in the
software centre.
I would prefer not to use the background option, could I use wildcards to run multiple images, i.e.,/home/glen/Pictures/*.png?

---

### Post by stinkeye on 2012-04-18
> **DHinton said:**
> I would prefer not to use the background option, could I use wildcards to run multiple images, i.e.,/home/glen/Pictures/*.png?

The example I gave starts with a specified image, running a slideshow
using multiple images of any type from the same folder.
Using ***.png** seems to work.

---

### Post by Mark Phelps on 2012-04-19
> **DHinton said:**
> Libre Office reads the file, put it I can't get it auto launch the file on start-up.

OK, but from what the others have said, you would have to somehow convert the graphics images in the PPTX file to .png files.

I thought you were asking about how to use the PPTX file in native form.

---

### Post by DHinton on 2012-04-24
> **stinkeye said:**
> The example I gave starts with a specified image, running a slideshow
using multiple images of any type from the same folder.
Using ***.png** seems to work.

OK that works, but can I hide the toolbar?

---

### Post by DHinton on 2012-04-24
> **DHinton said:**
> OK that works, but can I hide the toolbar?

I found the setting to hide the launch bar.  It seems to be working perfectly now!  Thank you everyone for your help!

---

