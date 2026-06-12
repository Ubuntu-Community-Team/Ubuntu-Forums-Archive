---
title: "How to: Use Compiz"
date: 2010-02-23
forum: Outdated Tutorials &amp; Tips
---

### Post by adam22 on 2010-02-23
I wrote this up a few weeks ago and thought it might be useful for some people here.

I'm pretty bored, and I thought this might be helpful. In this guide, I'll show you the various effects with Compiz and tell you how to configure them to your liking. I'm sure most have figured this stuff out, but it took time and trial and error for me, and I think it will help some people. As always, try not to break anything. Let's begin.

1. First, we need to enable special effects. To do this, use the menu and click **System>Preferences>Appearances** and click the *Visual Effects* tab. 
[color=#FF0000]**You will need to have a graphics driver activated for this to work. It will try to do this for you if you have not already done so, but if it does not work, simply go to _System>Administration>Hardware Drivers_ and select the recommend driver. Make sure all other windows are closed before activating the driver. You may need reboot for changes to take effect.*[/color] 

[[img]http://img51.imageshack.us/img51/9963/effects.th.jpg[/img]](http://img51.imageshack.us/i/effects.jpg/)

2. Now, by default, some effects will be turned on. However, we can do much more by installing the **CompizConfig Settings Manager (CCSM)**. Simply go to your terminal (Applications>Accessories>Terminal) and type in **sudo aptitude install compizconfig-settings-manager**. We also want the unsupported extras, so now use the command **sudo apt-get compiz-fusion-plugins-extra**. After it is done, exit the terminal and we will move on to the next step.

[[img]http://img535.imageshack.us/img535/2686/synaptic.th.jpg[/img]](http://img535.imageshack.us/i/synaptic.jpg/)

3. It's time to start getting those effects turned on. I'll go through my favorite ones here and explain how to configure them. To access your new control panel for Compiz, simply click **System>Preferences>CompizConfig Settings Manager**.

A. Basic Window Effects
      -First, we need to enable animations, and the unsupported animations. To do this, simply click to place a checkmark in the Animations Add-On. Now, click on Animations, and you will see several tabs at the top. Make sure the **Open** tab is selected, and double click the first effect that is listed. A new box will appear, and you can select the new effect from the Open Effect drop down list. I personally use Beam Up. You can also select the length of each effect via the horizontal Duration bar.
     -We can repeat this process for the Close, Minimize, Shade, and Focus animations.

[[img]http://img190.imageshack.us/img190/9260/animationsv.th.jpg[/img]](http://img190.imageshack.us/i/animationsv.jpg/)

B. Altering the Basic Window Effects
     -While it was nice to just enable the effects and change the time, we can do more with these. Simply click Animations and select the **Effect Settings** tab. You will see a ton of options come up. I will use the Animations Add-On as an example. If you have enabled the Burn effect, you will be able to change the flame color and particle size, as well as choose 'Randomly Colored Fire.' It's entirely up to you how you want to customize these effects, so I'll leave you to do the experimenting here.
[color=#3333FF]**Note: If at any time you have made an unwanted change and cannot remember what the default setting was, you can click the right most button for the effect to restore default settings.*[/color]

C. The Desktop Cube
     -Perhaps the most interesting effect is the Compiz Cube. Let me start by warning you that you may have to resolve conflicts while configuring the cube and other effects from here on out. Since each individual's settings are unique, I cannot predict which conflicts you will run into. However, either disable the existing effect to enable the new ones, or select new key bindings, depending on which "error" message you are given.

      -I know you want to just enable the cube, but don't do that yet. First, go up to **General Options** and select the **Desktop Size** tab. Now, I prefer to increase the **Horizontal Virtual Size** to 4, however, I would not go any higher than six.

       -Now, let's enable the Desktop Cube by placing a checkmark in the appropriate box. You will likely have to **disable** Desktop Wall in order to enable the cube. If you click on the menu for Desktop Cube, you can select the *Transparent Cube* tab and change the opacity. I use 80.00 for Opacity During Rotation. There is also an **Appearance** tab that will allow you to change the cube caps, as well as the Skydome (the background when rotating the cube). Simply save an image and use the file browser for the setting to select your custom image.

[[img]http://img685.imageshack.us/img685/8020/transparent.th.jpg[/img]](http://img685.imageshack.us/i/transparent.jpg/)

          -Now, let's enable **Rotate Cube**. You can change the key bindings for this, but by default, you should be able to access the different workspaces by _holding_ **ctrl+alt** and then left-clicking (and holding that down) and moving the mouse in any direction.

            -This part is optional, but I like to enable **Cube Reflection and Deformation**. Doing this will add a little more flavor to the cube, and if you choose to, you can select the **Deformation** tab and change the cube into either a cylinder or a sphere. By default, it will add new cube caps as well.

[[img]http://img198.imageshack.us/img198/5709/cubeg.th.jpg[/img]](http://img198.imageshack.us/i/cubeg.jpg/)

4. Expo

This is a handy plugin for navigating your different workspaces. It will zoom out to show all the workspaces on the screen, which will allow you to simply click on the one you want to use. Enable the **Expo Plugin** and click it to bring up its menu.

 -First, in the **Bindings** tab, select **Expo edge**. I personally prefer to use *BottomRight* but it's up to you.

[[img]http://img10.imageshack.us/img10/2893/expozm.th.jpg[/img]](http://img10.imageshack.us/i/expozm.jpg/)

  -Now, under the **Behavior** tab, you can change the Expo Animation. I use plain old Zoom, but there are a few to choose from. Just select it and then go to your binded edge and see if you like the effect.

   -Lastly, we can play with some settings under the **Appearance** tab. You can experiment here, but the only change I make is to add a **Reflection** and a *Curve* **Deformation**.

[[img]http://img192.imageshack.us/img192/6760/expo1.th.jpg[/img]](http://img192.imageshack.us/i/expo1.jpg/)


5. Ring Switcher

There are several application switchers available, but the most elegant one in my opinion is the Ring Switcher. I would advise turning off any other application switchers if you want to enable this one. By default, the key bindings should be **Super (Windows Key)+Tab**.

[[img]http://img199.imageshack.us/img199/2484/switcher.th.jpg[/img]](http://img199.imageshack.us/i/switcher.jpg/)

6. Miscellaneous

-These are totally optional, but look really nice. I would enable **Reflection** and **Window Decoration**. which will add shadows and other eye candy for you. There are options to play with in both.

-**Paint fire on the screen, Water Effect,** and **Window Previews** are some other fun plugins to enable. The first lets you draw on the screen while the second has raindrops falling and an optional windshield wiper. The last one is pretty useful. You can change the size of the preview if you wish.

You can pretty much restore defaults on all effects and you can uncheck them to revert back to the way things were before. I'll be happy to answer any questions.

---

### Post by Jart44 on 2010-05-25
Thanks for taking the time to put this together. It must have taken alot of effort. Although I have Compiz up and running your tut was helpful in a few areas. Can I ask how you took the photos in your tut? Was it recordmydesktop?

Thanks

---

### Post by Trilby on 2010-05-31
Thanks mate, I've been trying to work out how to use the burn and desktop cylinder effects for a while.
:-)

---

### Post by azertyh on 2010-05-31
hi,
how to use compiz with xfce?
just install ccsm?

---

### Post by Trilby on 2010-06-15
> **adam22 said:**
> ... and Window Previews are some other fun plugins to enable ... The last one is pretty useful. You can change the size of the preview if you wish.

At the moment, I can only get a preview if the window is not minimised. How do I set it so that the window preview will always appear, like in Windows 7?

Thanks

---

### Post by realzippy on 2010-06-15
> **Trilby said:**
> At the moment, I can only get a preview if the window is not minimised. How do I set it so that the window preview will always appear, like in Windows 7?

Thanks

Have a look at the compiz wiki.It is nearly complete..

[http://wiki.compiz.org/Plugins/Thumbnail](http://wiki.compiz.org/Plugins/Thumbnail)

---

### Post by Trilby on 2010-06-15
> **realzippy said:**
> Have a look at the compiz wiki.It is nearly complete..

[http://wiki.compiz.org/Plugins/Thumbnail](http://wiki.compiz.org/Plugins/Thumbnail)

The first line of that page says it only works for non-minimised windows. :(

---

### Post by realzippy on 2010-06-15
> **Trilby said:**
> The first line of that page says it only works for non-minimised windows. :(

Yep.This answers your question. :D
But there seems to be some python script which does the job:
[http://swiss.ubuntuforums.org/showthread.php?t=976002](http://swiss.ubuntuforums.org/showthread.php?t=976002)
Will check this out,never missed the minimized windows,but its a good idea to include them.

Edit:

It works!
(python-gnome2-extras has to be replaced)

---

### Post by Trilby on 2010-06-15
I've never used Python before. I'm not sure I'd be able to implement that without breaking my system in away that I wouldn't be competent enough to fix.

It's a shame really; window previews become a lot more useful when they include minimised windows.

---

### Post by realzippy on 2010-06-15
You do not have to implement something to your system,just install
some stuff and run a script.  ??

It will not break anything...it just works.Tested it.


BTW,
it is not a shame,it is a feature.Normally windows are minimized 'cause you do not need them in the moment;otherwise maximize them  ;-)

---

### Post by Trilby on 2010-06-15
> **realzippy said:**
> it is not a shame,it is a feature.Normally windows are minimized 'cause you do not need them in the moment;otherwise maximize them  ;-)

I thought the point of a preview was to save you from doing that.

---

### Post by realzippy on 2010-06-15
Anyhow.The [script]("http://swiss.ubuntuforums.org/attachment.php?attachmentid=131282&d=1255060694") does exactly what you want...

---

### Post by Chame_Wizard on 2010-06-15
Nice to read.:guitar:

---

### Post by yossell on 2010-06-15
I, too, had wondered about minimised windows. Thanks for that, realzippy, it looks very helpful.

---

### Post by carvish on 2011-03-22
Hello, I have a desktop with ubuntu 10.10, I have compiz working on it, I have the cube, write with fire, and even installed my favorite picture on the top of the cube, I would like to open a window with the genie effect, and close/minimize with fire, I have the genie working but there is no flame/fire effect listed in the dropdown menu to select in open or close window, any ideas?

---

### Post by adam22 on 2011-03-24
> **carvish said:**
> Hello, I have a desktop with ubuntu 10.10, I have compiz working on it, I have the cube, write with fire, and even installed my favorite picture on the top of the cube, I would like to open a window with the genie effect, and close/minimize with fire, I have the genie working but there is no flame/fire effect listed in the dropdown menu to select in open or close window, any ideas?

Hi, carvish. First, let's make sure you have everything you need installed. Open up the Synaptic Package Manager and type in 'compiz.' Make sure you have **compiz-fusion-plugins-extra** installed.

[[IMG]http://img546.imageshack.us/img546/4818/xtrak.th.png[/IMG]](http://img546.imageshack.us/i/xtrak.png/)

In CCSM make sure the _Animations add-on_ is enabled.

[[IMG]http://img848.imageshack.us/img848/3604/screenshotme.th.png[/IMG]](http://img848.imageshack.us/i/screenshotme.png/)

Then go into the animations tab in CCSM and select the **burn** effect.

[[IMG]http://img812.imageshack.us/img812/5920/screenshotnhe.th.png[/IMG]](http://img812.imageshack.us/i/screenshotnhe.png/)

---

### Post by carvish on 2011-03-26
Thanks for the info, I went to the SPM and did a re-install of the package and now it is there and working well.
Thank you

---

### Post by jcer93705 on 2011-03-26
> **adam22 said:**
> Hi, carvish. First, let's make sure you have everything you need installed. Open up the Synaptic Package Manager and type in 'compiz.' Make sure you have **compiz-fusion-plugins-extra** installed.

[[IMG]http://img546.imageshack.us/img546/4818/xtrak.th.png[/IMG]](http://img546.imageshack.us/i/xtrak.png/)

In CCSM make sure the _Animations add-on_ is enabled.

[[IMG]http://img848.imageshack.us/img848/3604/screenshotme.th.png[/IMG]](http://img848.imageshack.us/i/screenshotme.png/)

Then go into the animations tab in CCSM and select the **burn** effect.

[[IMG]http://img812.imageshack.us/img812/5920/screenshotnhe.th.png[/IMG]](http://img812.imageshack.us/i/screenshotnhe.png/)

Hi wow I'm gonna try you're steps. Thanks for posting these. Can you also post what os you're using and what theme are you using?  Man you're os looks nice. What version of gnome is it? Can you share us all that information? Thank you, you da MAN!!

---

### Post by adam22 on 2011-03-26
Hi jcer93705.

I'm using Ubuntu 10.10 64 bit with whatever version of GNOME it came with. However, I've made a few key changes, which I think calls for a new howto tutorial that I will link back to in this thread.

---

### Post by jcer93705 on 2011-03-26
> **adam22 said:**
> Hi jcer93705.

I'm using Ubuntu 10.10 64 bit with whatever version of GNOME it came with. However, I've made a few key changes, which I think calls for a new howto tutorial that I will link back to in this thread.

I hope you do make the tutorial because that theme and how you're os look is so beautiful. Sometimes we get tired of stock looks and taskbar. You're task bar looks hot stuff.

---

### Post by adam22 on 2011-03-27
It took a couple hours but it has been made. I submitted it, as soon as it is approved you will see it.

---

### Post by jcer93705 on 2011-03-27
> **adam22 said:**
> It took a couple hours but it has been made. I submitted it, as soon as it is approved you will see it.

I saw you're other pimp you're gnome something like that and pretty cool but older version. I'll wait until you're how to thread is 
available. Thanks for doing this for me and the rest of the people. We need people like you that explain stuff. Thanks

---

### Post by adam22 on 2011-03-27
That tutorial implements some more basic changes and although it was created back in late 2009 or early 2010, it still works just fine for the current version of Ubuntu. However, I see your point, that was a more standard/traditional look compared to what I have going on now. Hopefully the new tutorial gets approved soon so you can use it.

It's no problem making these tutorials. I do it to help, and kind works like you are what keep me going. If you have any questions feel free to ask (Skype might be the quickest way), I'll help if I'm able to.

Cheers.

Edit: the new tutorial is available, [here](http://ubuntuforums.org/showthread.php?t=1715174) it is.

---

