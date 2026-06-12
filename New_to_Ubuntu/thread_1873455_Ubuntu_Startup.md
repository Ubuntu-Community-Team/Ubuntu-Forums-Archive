---
title: "Ubuntu Startup"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by rahbz on 2011-11-01
HELP..!!!!:(
I installed ubuntu 11.04 from live usb.
After loading of grub,it gets struck at the black blank screen,But when I press ctrl+alt+f2 or f3.... I get normal virtual terminal.
I didnt even install ATI graphic card on first startup.
Didnt get any problem with 10.10 at all.

---

### Post by WasMeHere on 2011-11-01
Hi rahbz,

- What flavour do you use: ('vanilla', kubuntu, lubuntu, xubuntu)?
- Did you run it live or did you install or both?
- Did you have good graphics running a live session?
- Are you sure it is 11.04 natty and not 11.10 oneiric?

Have fun finding out about Ubuntu :-)
Olle

---

### Post by rahbz on 2011-11-04
Hi Olle,
I use ubuntu(natty).
and I installed it,
I have ATI mobility radeon graphics,
and after going through [http://askubuntu.com/questions/60099/unable-to-start-on-a-hp-pavilion-dv6-3049tx](http://askubuntu.com/questions/60099/unable-to-start-on-a-hp-pavilion-dv6-3049tx)
I could perfectly run ubuntu but why cant I run using graphic card.

---

### Post by WasMeHere on 2011-11-04
I know there has been problems with ATI graphics cards and drivers in the new Ubuntu versions. In some cases they have been solved. See
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1874215_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1874215")

I still don't really understand when you have problems and what it is. Let me guess: At first you had no graphics when running Ubuntu 11.04 (natty), only text screen (full window is terminal). Then you went through Askbuntu and now you have graphics but only with the standard graphics driver, not the proprietary ATI driver. Tell me how it really works now!

It will also help if you can tell us if you get good graphics running a live session (with the installation disk).

Maybe someone here at the Ubuntu Forums can help you, if you also tell us exactly which card you have. Write the output of the command
```
glxinfo | grep -i opengl
```

---

### Post by rahbz on 2011-11-05
~$ glxinfo | grep -i opengl
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT 
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
OpenGL extensions:
This is the output while running through after disabling the graphic card i.e.,radeon.modeset=0 in grub menu.

---

### Post by WasMeHere on 2011-11-05
The computer does not use your ATI card, instead it uses Tungsten Graphics, which is what you intend. What about the graphics now: are you satisfied with the resolution and overall quality?

If yes, just sit back and enjoy :-)

If no, please post the complete name and version of your ATI card! If you know it or can read it from the box or manual, that is easy, otherwise reset your computer to run the ATI card and run
```
glxinfo | grep -i opengl
``` Then search the Ubuntu Forums and in general the internet for 'that card and linux'. Let us hope someone who has the same kind of card reads your post and can help you.

---

### Post by rahbz on 2011-11-05
I couldn't run while using radeon graphics.So, after searching I got to know about radeon.modeset=0 command to be run in grub.
ATI Mobiliy Radeon HD 5650 Graphics Card, I cannot run every time using the command into grub.So,I asked is there any alternative way for this.
I could get all the open GL settings for my laptop.

---

### Post by WasMeHere on 2011-11-06
> **rahbz said:**
> I couldn't run while using radeon graphics.So, after searching I got to know about radeon.modeset=0 command to be run in grub.
ATI Mobiliy Radeon HD 5650 Graphics Card, I cannot run every time using the command into grub.So,I asked is there any alternative way for this.
I could get all the open GL settings for my laptop.

The following thread found a solution for your ATI card
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1422762_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422762")
so if you are not satisfied with the performance of your graphics now, I suggest that you read and try what was done in that thread.

Have fun finding out :-)
Olle

---

### Post by rahbz on 2011-11-07
Olle, I think that the ATI graphic card problem cannot be solved in the ubuntu. As I had installed it for more than thrice. Whenever I install my openGL settings disappear.Then after removing the installed card my openGL settings restore.
So, I think I continue without my graphic card installed, as that even creating some problems.

---

### Post by WasMeHere on 2011-11-07
How did you install it? Did you do something similar to the threads that I was linking to?

---

### Post by rahbz on 2011-11-09
I installed through System->Adminstration->Additional Drivers
After installing the driver and restarting the computer It shows as

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
and all my openGL setting disappear.

---

### Post by WasMeHere on 2011-11-09
> **Robster2 said:**
> Ubuntu 9.10  Acer Aspire 5740G Notebook.  ATI Mobility Radeon 5650

This is a weird one.  I installed ubuntu 9.10  it detected Wifi everything and suggested I install the ATI/AMD proprietary FGLRX graphic driver.

Well every thing appears to work fine. Got the Compiz cube rotating,  The effects for opening windows tried them all worked fine.

Except there is this watermark on the corner of the screen that says "AMD Unsupported hardware".

Interestingly ATI Catalyst control center has appeared in the menus.  Changing the settings does not appear to do anything.
There is an Administration menu that appears to not run.

The AMD website does not appear to have a Linux driver for this video card.  

Should I leave the current driver, remove the current driver and live without the eye candy, try and wrap the windows driver or do something else.

I suggest that you install the ATI/AMD proprietary FGLRX graphic driver, like Robster2 did :-)

You may get some more good tips reading the rest of that thread.

Olle

---

### Post by rahbz on 2011-11-10
[http://askubuntu.com/questions/63713/hp-pavilion-dv6-is-not-booting-with-switchable-graphics](http://askubuntu.com/questions/63713/hp-pavilion-dv6-is-not-booting-with-switchable-graphics)
saying that AMD doesn't support switchable graphics in Linux.
So,that is why I couldn't able to install I think.

---

### Post by WasMeHere on 2011-11-10
I see. Let us hope there will be a working driver for your configuration in the near future.

Sorry I could not help you
Olle

---

### Post by rahbz on 2011-11-10
Yah, Its fine but thanks Olle.

rahbz

---

