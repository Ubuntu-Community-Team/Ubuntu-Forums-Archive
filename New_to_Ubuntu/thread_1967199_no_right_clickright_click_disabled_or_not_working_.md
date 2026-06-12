---
title: "no right click/right click disabled or not working 12.04"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by steviematt on 2012-04-27
Hello,

I have been waiting for the 12.04 LTS for a few months now because i found that Ubuntu is the most widely used and beginner friendly distro. I'm quite an experienced user of Winodows and Macs but i realise Linux will take some time to learn and it is... different.

I installed the stable 12.04 (64-bit) on to my Samsung SF310(with nvidia graphics) via USB using the pendrive linux program yesterday and it was all pretty straight forward. I installed 12.04 beside windows 7 in a partition of around 150GB.

The first thing i noticed was a burning sensation in my eyes when Ubuntu loaded with full brightness, i tried lowering the brightness in system settings but this is never remembered when i reboot. I looked for fixes to this problem but the fixes seemed to be aimed at non-beginners. I figured out that the function button and arrow down key will lower the brightness quickly so i'm using that to stop my retinas from decaying for the time being.

**My MAIN problem is that right click seems to be disabled or simply not working. **
I have looked all over the internet for answers to this problem but it always involves typing in a lot of things in the command line... i tried one fix and spent an age writing things in the command line and managed to download some kind of tar.gz2 to fix some synaptics drivers but i could only complete half of the task because i didn't know the version number i needed and when i typed in an older version number it was not found...

So here i am... in need of help, already tried to follow some instructions and typing in the terminal from another website but it failed.

Is there an easier fix to this terrible problem of having no right click functionality in Ubuntu? Please remember I have been using Ubuntu for just over 24 hours now, my skills and knowledge is limited, so your answers will need to be somewhat detailed. Thanks.

---

### Post by danielgrosvenor on 2012-04-27
Are you using a mouse or the trackpad? When I first installed 12.04 I found I was having problems with it recognising my trackpad, so I plugged in a USB mouse. After running all updates (the cog icon in the top-right corner) and rebooting the problem went away.

Might be worth a try.

---

### Post by forrestcupp on 2012-04-27
Just a couple of things. Where are you trying to right-click? Is it on the desktop, or in certain programs, or what? Telling us that will help us figure out how to help you.

Also, one big reason people give terminal commands instead of GUI instructions is to make it easier on beginners. You don't need to retype everything or even know what it means. If you trust the source, just copy/paste the commands. If you don't know the correct version number for something, try opening the Ubuntu Software Center and searching for the name of what you're trying to install. If it's in there, it will come up in the search, and you won't need to know what version it is.

---

### Post by steviematt on 2012-04-28
> **danielgrosvenor said:**
> Are you using a mouse or the trackpad? When I first installed 12.04 I found I was having problems with it recognising my trackpad, so I plugged in a USB mouse. After running all updates (the cog icon in the top-right corner) and rebooting the problem went away.

Might be worth a try.

 I'm using my trackpad right now, i'm teaching in china right now and my usb mouse broke, haven't bought a new one yet so i'm stuck with my trackpad for now. I have all of the updates installed and rebooted many times...

---

### Post by steviematt on 2012-04-28
> **forrestcupp said:**
> Just a couple of things. Where are you trying to right-click? Is it on the desktop, or in certain programs, or what? Telling us that will help us figure out how to help you.

Also, one big reason people give terminal commands instead of GUI instructions is to make it easier on beginners. You don't need to retype everything or even know what it means. If you trust the source, just copy/paste the commands. If you don't know the correct version number for something, try opening the Ubuntu Software Center and searching for the name of what you're trying to install. If it's in there, it will come up in the search, and you won't need to know what version it is.

 I'm trying to right-click everywhere... noticed it wasn't working when i tried to remove some programs from unity launcher, i read instructions that i just right-click and select remove... right-click for me just opens the program the same as left click.   I've tried right clicking the desktop, in files and on folders, even on webpages to ermmm copy and paste text into terminal but that isn't working. I can ctrl+c it but pasting ala ctrl+v into terminal produces nothing so i can't even copy and paste commands you give me, the whole no right-click thing is making my life a misery.

---

### Post by cdo on 2012-04-28
Had the same issue yesterday with right click to delete not working . Today seemed to be ok until i just tried to right click and delete a bookmark . Same thing again as right clicking just activated the bookmark . Seems to delete some times and not others . Maybe depends on where it's being used . Right clicked a movie downloaded and that delete did work .

---

### Post by cdo on 2012-04-28
> **cdo said:**
> Had the same issue yesterday with right click to delete not working . Today seemed to be ok until i just tried to right click and delete a bookmark . Same thing again as right clicking just activated the bookmark . Seems to delete some times and not others . Maybe depends on where it's being used . Right clicked a movie downloaded and that delete did work .


Right click , delete in bookmark solved . Had to display via All Bookmarks in order to delete . That doesn't help those with the issue elsewhere though...

---

### Post by forrestcupp on 2012-04-28
> **steviematt said:**
> I can ctrl+c it but pasting ala ctrl+v into terminal produces nothing so i can't even copy and paste commands you give me, the whole no right-click thing is making my life a misery.
Unfortunately, I don't know what to tell you about your right click issue. You're sure it's not a hardware problem, right?

But I can tell you that in a terminal, you have to use Shift+Ins to paste instead of Ctrl+V. I don't know why it's non-standard like that.

---

### Post by nizamibilal1064 on 2012-04-28
> **steviematt said:**
> I'm trying to right-click everywhere... noticed it wasn't working when i tried to remove some programs from unity launcher, i read instructions that i just right-click and select remove... right-click for me just opens the program the same as left click.   I've tried right clicking the desktop, in files and on folders, even on webpages to ermmm copy and paste text into terminal but that isn't working. I can ctrl+c it but pasting ala ctrl+v into terminal produces nothing so i can't even copy and paste commands you give me, the whole no right-click thing is making my life a misery.
Try system setting> mouse and touchpad> and see if some change in setting might work:)

---

### Post by bogan on 2012-04-28
**Hi!**

In a terminal 'copy' & 'paste' need 'Shift' as well as Ctrl+C or V: or use Edit menu items.That is needed because 'Ctrl+c' has a specific meaning in a terminal, displays a  '^' symbol and shuts down any procedure that is running in the terminal.

In some examples, in recent releases, in certain places, like the TopBar or a Panel, the Right-Click needs: 'Alt+Right-Click' or 'Super+Right-Click' or even 'Alt+Super+Right-Click'. Try them and see which works, if any: but your problem sounds like something more than that.

['Super' key is the MS logo key in Windows talk.]

Edit: In ubuntu-tweak there is a set of options to set various mouse buttons settings, middle button as well as the others and double-clicks.

Chao!,** bogan**.

---

### Post by verymadpip on 2012-04-28
I'll be watching this closely as I have a similar issue.

I think that mine may be related to changing the colour of the light on my illuminated keyboard though...weird

I'll also be trying some of the suggestions.

---

### Post by steviematt on 2012-04-28
I have tried fiddling around with my keyboard and mouse a little and think i have found the root of the problem.

I changed my trackpad from a right handed to a left handed in the mouse and trackpad system settings and now right click brings up the right click menu BUT so does left click and any click at all for that matter.

This would be fine because i can still select things ala left click by tapping my trackpad but because all clicks on the touchpad now produce the right click menu, it had became impossible to select text by highlighting, drag and drop and anything else your going to need your left click for.

How could i go about fixing this? 

The problem is clearly my trackpad only picks up one type of click right now depending on if its right handed or left handed:confused:

---

### Post by forrestcupp on 2012-04-29
I'm probably wrong, but it sounds like a hardware problem. I've seen that happen, especially if it's the type that has one long button that does both right and left clicks. Do you still have a dual boot Windows install that you could verify if it works in Windows?

You would probably save yourself a lot of headaches if you just go spend $10 on a cheap wireless mouse.

---

### Post by steviematt on 2012-04-30
My touchpad works fine in windows 7, left click and right click both behave like a normal windows touchpad...

What i figured out though is that my trackpad in ubuntu behaves like a macbook touchpad, two finger scroll and in a moment of absolute frustration i realised** i can do right clicks by tapping the touchpad with my index finger quickly followed by my ring finger** ala mac touchpad and magic trackpad.

I'm very happy with this, although it took me an age to realise, the mac style touchpad is far more intuitive and will help me fall in love with ubuntu... something i've never felt for windows.

So no hardware problems... just lack of information on how my touchpad's functionality would change (for the better) in ubuntu.

---

### Post by forrestcupp on 2012-04-30
> **steviematt said:**
> My touchpad works fine in windows 7, left click and right click both behave like a normal windows touchpad...

What i figured out though is that my trackpad in ubuntu behaves like a macbook touchpad, two finger scroll and in a moment of absolute frustration i realised** i can do right clicks by tapping the touchpad with my index finger quickly followed by my ring finger** ala mac touchpad and magic trackpad.

I'm very happy with this, although it took me an age to realise, the mac style touchpad is far more intuitive and will help me fall in love with ubuntu... something i've never felt for windows.

So no hardware problems... just lack of information on how my touchpad's functionality would change (for the better) in ubuntu.

That's weird. My touchpad doesn't work like that; it works just like it does in Windows. I wonder if there's some setting to change it to work like you're describing.

---

### Post by youpi boudin tralala on 2012-08-17
> **steviematt said:**
> My touchpad works fine in windows 7, left click and right click both behave like a normal windows touchpad...

What i figured out though is that my trackpad in ubuntu behaves like a macbook touchpad, two finger scroll and in a moment of absolute frustration i realised** i can do right clicks by tapping the touchpad with my index finger quickly followed by my ring finger** ala mac touchpad and magic trackpad.

I'm very happy with this, although it took me an age to realise, the mac style touchpad is far more intuitive and will help me fall in love with ubuntu... something i've never felt for windows.

So no hardware problems... just lack of information on how my touchpad's functionality would change (for the better) in ubuntu.

Well done !

---

### Post by mgmiller on 2012-08-27
I have an Apple Magic Trackpad hooked up to Ubuntu and I tried your index/ring finger trick and it does work like a right click.  However, I think you are just doing a 2 fingered tap, which is the "right way" to simulate a right click.  Just tap the pad with 2 fingers simultaneously and you should get the right click dialog to open up.  I use this all the time for a quick back/forward in Firefox.

Have you tried 3 finger tap?  It brings up the move window grab handles and you just slide the window around with the 3 fingers.

4 finger tap brings up the Unity Dash.

I understand the multi-gesture support will be configurable starting in Ubuntu 12.10.  Should be fun.

---

### Post by elnetotaca on 2012-09-29
works on Ubuntu 12.04
NO, what you have to do is;

open Ubuntu tweak
go to; tweaks

activate the first option "show desktop Icons"

and there you go!

---

