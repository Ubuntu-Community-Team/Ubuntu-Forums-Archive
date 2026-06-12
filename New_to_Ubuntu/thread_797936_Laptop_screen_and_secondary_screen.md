---
title: "Laptop screen and secondary screen?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by spacemanps on 2008-05-17
Hello guys... i am brand new to this and just doing a lot of reading. I just have one question, i currently have installed ubuntu on my xps laptop, but i use a seconary acer monitor as my primary (keeping my laptop tucked away in a keyboard roll out) I would like to disable my laptops moniter and just keep the acer going... What i cant figure out is how to get my laptop screen to turn off when its closed but keep my other moniter on. Its currently set up when i close the lid both screens shut off (bc its clone screen) and hwen i move the mouse both turn on. How do i fix this?!?!?!


and how so i get a better resolution for my moniter.. the highest it goes is 1020x768

---

### Post by HotShotDJ on 2008-05-17
> **spacemanps said:**
> Its currently set up when i close the lid both screens shut off (bc its clone screen) and hwen i move the mouse both turn on. How do i fix this?!?!?!

and how so i get a better resolution for my moniter.. the highest it goes is 1020x768Open a terminal (Applications --> Accessories --> Terminal) and run:```
xrandr -q
```Please post the output.

Now, as far as dealing with the two screens FIRST, left click on the power manager icon in your notification area (the icon that lets you know the status of your battery and if you are running on AC or not) and then click on the "On AC Power" tab.  Where it says "When laptop lid is closed" select "Do nothing" and then click "Close".  You should now be able to close the laptop lid without turning off the display.  However, the laptop display will remain on.  To take care of this, from the terminal:```
xrandr --output VGA --auto --output LVDS --off
```

---

### Post by bodhi.zazen on 2008-05-17
Check you laptop keys. On my lap top Fn-F7 toggles between laptop-screen only <-> external screen only <-> both screens.

Activate the external screen only -> Viola.

---

### Post by spacemanps on 2008-05-17
nishan@Nishan:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1920 x 1200
DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9 +   59.9  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       74.8  
   1024x768       75.1     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1200      60.0 +
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)
nishan@Nishan:~$ 



Those are the results of  (xrandr -q)



Oh and i dont that have link to the power manager in my status bar (how do i get it back) but i know where to go, and i already have that done... but i will still turn off and then turn on agian when i move the mouse... ( i have a white screen and wierd lines on the lid screen)

---

### Post by spacemanps on 2008-05-17
oh and i forgot to add that, when i close my lid and i only use my monitor, and then i randomly open my lid agian, the screen on my laptop is white with all these different color lines on it. It wont come back to the mirror screen unless i restart..

---

### Post by HotShotDJ on 2008-05-17
Ok... xrandr seems to be picking up both the laptop (LVDS) and external monitor (VGA-0) properly. You didn't tell me what happens when you run:```
xrandr --output VGA --auto --output LVDS --off
```However, based upon the other symptoms you describe, such as running at the wrong resolution (which is confirmed by the xrandr -q output) and the different color lines on the laptop screen when you open it, I suspect there is something going on at the video card level.  Perhaps that should get sorted first.

What video card does your laptop have? From the terminal, run:```
lspci | grep VGA
```and post the output.

---

### Post by spacemanps on 2008-05-17
What i get when i type in (~$ lspci | grep VGA)

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]


oh and by the way i did an update on the video drivers i guess... what i did is i went to hardware drivers... and i clicked the ati mobility thing and then it updates some things and i keep getting this notification on my status bar.. here look at the screen shot..

---

### Post by HotShotDJ on 2008-05-17
> **spacemanps said:**
> 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]Ok... after more poking around, I believe the following commands should work for you.

To turn the laptop monitor off and use only the external monitor:```
xrandr --output VGA-0 --auto --output LVDS --off
```And then, to turn external monitor off and use only the laptop monitor:```
xrandr --output VGA-0 --off --output LVDS --auto
```

If you are still having problems with the correct resolution, it is possible that you need to restart X after connecting the external monitor in order for xorg to pick up the proper resolutions.  It really shouldn't be necessary, but I've seen it help in some cases.  To do that, make sure all applications are closed, and then press simultaneously ctrl+alt+backspace

---

### Post by spacemanps on 2008-05-17
To turn the laptop monitor off and use only the external monitor:```
xrandr --output VGA-0 --auto --output LVDS --off
```


okay well i found the correct resolution, but those codes didnt do anything for turning off my laptops monitor... its still a clone on both screens..


do i need to have anything else installed to help this process.. cause i have nothing else installed  before all this..

---

### Post by HotShotDJ on 2008-05-17
> **spacemanps said:**
> those codes didnt do anything for turning off my laptops monitor... its still a clone on both screens.:confused:

What happens if you just type```
xrandr --output LVDS --off
```

---

### Post by spacemanps on 2008-05-17
absolutely nothing

---

### Post by HotShotDJ on 2008-05-18
> **spacemanps said:**
> absolutely nothing:confused::confused::confused::confused::confused:

That command is SUPPOSED to turn off the laptop monitor, and works perfectly on my system.  But I have integrated Intel video which leads me to believe that this may be something specific to the ATI card in your system.

Another thing you might try (no guarantee here, I just know it works for me) is, with your laptop powered off, connect the external monitor. Then, press the power button and IMMEDIATELY close the laptop lid.  This may or may not work.

Beyond this, I've run out of ideas for you. :(

---

### Post by spacemanps on 2008-05-18
well thank you very much for you help. you tried and thats all i can ask. If you do think of anything in the future please post it or pm me... i will probably be looking for this solution!! thanks again.

---

### Post by spacemanps on 2008-05-18
any one else have any input?

---

### Post by spacemanps on 2008-05-18
bump

---

### Post by spacemanps on 2008-05-21
another bump just for giggles

---

### Post by kagashe on 2008-05-22
Without trying for higher resolution on the external monitor give this command:
> xrandr --output LVDS --off
This should switch off LVDS.

Then try higher resolution through the command:
> xrandr --output VGA-0 --auto

This may bring back the LVDS. If it comes back it can't be switched off. To know the reason type the following:
> xrandr -q
and compare with previous output of this command. You will find that the output does not show VGA-0 and LVDS as separate entities.

kagashe

---

