---
title: "Resolution"
date: 2017-07-25
forum: New to Ubuntu
---

### Post by godzirraog on 2017-07-25
hi all, was wondering if i could get some help. New to linux so i decided to install lunbuntu 17.04 on a dell inspirion 7547 with the i5 and integrated graphics. I was wondering if there was a way to switch from 16:9 1080p to 4:3 800x600 with stretched resolution meaning no black bars. Could someone help me please? Thanks!

---

### Post by TheFu on 2017-07-25
Welcome to the forums.  I don't know of a trivial way to do what you want.
But there is a way: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
You'll need to manually add the resolution and monitor timings required.

---

### Post by him610 on 2017-07-26
Not quite sure how Lubuntu does it, but all *buntus are similar in the way the Monitor/Display resolution is changed.

Have you tried changing your resolution by going to Settings > Display  where you should see options for setting the Resolution.

---

### Post by BenginM on 2017-07-26
xander is your toy ..

---

### Post by QIII on 2017-07-26
> **BenginM said:**
> xander is your toy ..

I'm sure you would be willing to expand on that so that the OP has some idea what the answer means and how to implement it?

---

### Post by BenginM on 2017-07-26
> **QIII said:**
> I'm sure you would be willing to expand on that so  that the OP has some idea what the answer means and how to implement  it?

actually , all the OP's need to do is selected whatever resolution they wanted and it stretched on it's own. unless they want that for a game that would be an ingame mode , or from additional settings ..

You should ask the OP to clarify and give more informations on their setup and what's it for ..

---

### Post by QIII on 2017-07-27
Should I?

You said to use xrandr.  TheFu had already directed the OP to the link.  Your answer was unnecessary and without any point.

---

### Post by BenginM on 2017-07-27
> **QIII said:**
> Should I?

You said to use xrandr.  TheFu had already directed the OP to the link.  Your answer was unnecessary and without any point.

I said xander is your toy .. i didn't even open the link pointed by TheFu .. feel free to delete that post .. you think am trying to grow my forums posts! i can care less .. and next time you have a personal bone with me take it to a query PM! Now see my new post and watch the OPs responds ..

---

### Post by BenginM on 2017-07-27
> **godzirraog said:**
> hi all, was wondering if i could get some help. New to linux so i decided to install lunbuntu 17.04 on a dell inspirion 7547 with the i5 and integrated graphics. I was wondering if there was a way to switch from 16:9 1080p to 4:3 800x600 with stretched resolution meaning no black bars. Could someone help me please? Thanks!

Hiya , are you trying to achieve this with the native laptop screen or an external monitor ..!

First thing to do is issue the command to show the available video modes. If it's not listed, there's nothing you can do. if it's listed Try first setting scaling mode on the display to "Full aspect" 

Open a terminal and type:


xrandr --prop


paste the output in a [CODE] Tag .. thanks.

---

### Post by QIII on 2017-07-27
> **BenginM said:**
>  and next time you have a personal bone with me take it to a query PM!

There is no personal bone to be picked.  Your answer was of no use to the OP.  And I will choose how to address such matters, thanks.

---

### Post by godzirraog on 2017-07-27
> **BenginM said:**
> Hiya , are you trying to achieve this with the native laptop screen or an external monitor ..!

First thing to do is issue the command to show the available video modes. If it's not listed, there's nothing you can do. if it's listed Try first setting scaling mode on the display to "Full aspect" 

Open a terminal and type:


xrandr --prop


paste the output in a ```
 Tag .. thanks.


Hi thanks for your reply! I got: 
[CODE]Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
    EDID: 
        00ffffffffffff0006afed1000000000
        001801049522137802e295a354529926
        0f505400000001010101010101010101
        010101010101143780b8703824401010
        3e0058c11000001a102c80b870382440
        10103e0058c11000001a000000fe0039
        46384338834231353648415400000000
        000041229e011000000a010a2020008b
    scaling mode: Full aspect 
        supported: None, Full, Center, Full aspect
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
   1920x1080     60.05*+  59.93    48.04  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
HDMI-1 disconnected (normal left inverted right x axis y axis)
    aspect ratio: Automatic 
        supported: Automatic, 4:3, 16:9
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on


```

> **TheFu said:**
> Welcome to the forums.  I don't know of a trivial way to do what you want.
But there is a way: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
You'll need to manually add the resolution and monitor timings required.

The resolution and timing is there, its just not stretching for some reason

> **him610 said:**
> Not quite sure how Lubuntu does it, but all *buntus are similar in the way the Monitor/Display resolution is changed.

Have you tried changing your resolution by going to Settings > Display  where you should see options for setting the Resolution.

I have but I went to 800x600 and the screen doesn't stretch for some reason

> **BenginM said:**
> actually , all the OP's need to do is selected whatever resolution they wanted and it stretched on it's own. unless they want that for a game that would be an ingame mode , or from additional settings ..

You should ask the OP to clarify and give more informations on their setup and what's it for ..

This is for whenever I play an old school game, it switches resolutions but doesnt stretch. Like Starcraft broodwar or CS:source

---

### Post by QIII on 2017-07-27
So, are you saying that you want the game to fill a 1920x1080 screen (stretch) or just maintain the 4:3 aspect ratio and fill from top to bottom?

Your desktop properly rendered at a 16:9 aspect ratio, correct?  It's just the game?

You talk about an "older" game.  Is it designed to render in a wider aspect ratio?

---

### Post by godzirraog on 2017-07-28
> **QIII said:**
> So, are you saying that you want the game to fill a 1920x1080 screen (stretch) or just maintain the 4:3 aspect ratio and fill from top to bottom?

Your desktop properly rendered at a 16:9 aspect ratio, correct?  It's just the game?

You talk about an "older" game.  Is it designed to render in a wider aspect ratio?

Hi! thanks for the reply!

Yes, my desktop renders at 16:9 1080p just fine. Its just the game when put to 800x600 will put black bars on the side instead of stretching to fit the whole screen(stretched will result in no black bars on the left or right). Ive seen alot of people play the game at 4:3 on a 1080p screen and it fills up the whole screen. I would like the game to maintain a 4:3 aspect ratio and fill top to bottom AND left to right.

---

### Post by QIII on 2017-07-28
Then xrandr is not what you are looking for.

I guess I do not understand how you expect a 4:3 aspect ratio to fill a 16:9 screen.  Do you want it stretched and distorted?  Do you want a circle to appear oval horizontally?  Do you want to lose some of the image top and bottom so that it fits side to side?  Do you expect the game software to show you more information on the sides?

---

### Post by godzirraog on 2017-07-28
> **QIII said:**
> Then xrandr is not what you are looking for.

I guess I do not understand how you expect a 4:3 aspect ratio to fill a 16:9 screen.  Do you want it stretched and distorted?  Do you want a circle to appear oval horizontally?  Do you want to lose some of the image top and bottom so that it fits side to side?  Do you expect the game software to show you more information on the sides?

Yes actually, I want a circle to appear ovally. Alot of professionals play like that actually. They play 4:3 on a 16:9 screen essentially with everything stretched.

---

### Post by QIII on 2017-07-28
OK.

*Screen resolution* is not at issue here.  That was the wrong tree to bark up.  You are likely looking for the behavior of the game software on window resize.  

What happens when you maximize the application window?

---

### Post by TheFu on 2017-07-28
I tested 800x600 on my 1920x1080 laptop.  It didn't scale out.  When I want to fill the screen with something like that, I use the monitor controls, not the output controls for the GPU.

---

### Post by godzirraog on 2017-07-29
> **TheFu said:**
> I tested 800x600 on my 1920x1080 laptop.  It didn't scale out.  When I want to fill the screen with something like that, I use the monitor controls, not the output controls for the GPU.

Monitor controls as in actual buttons?

---

### Post by godzirraog on 2017-07-29
> **QIII said:**
> OK.

*Screen resolution* is not at issue here.  That was the wrong tree to bark up.  You are likely looking for the behavior of the game software on window resize.  

What happens when you maximize the application window?

Ah okay. But is it possible to make my desktop resolution 800x600 stretched regardless?

---

