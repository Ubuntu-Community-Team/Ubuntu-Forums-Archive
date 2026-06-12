---
title: "Shrink the Screen Display"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by mariskaoldtina on 2014-08-13
I have hooked up my PC to a TV.  For whatever reason, all the TV settings still have portions of the display off the screen.  So, I can't see the edges of my display. Makes it so I can't see the top menu bar, only the edges of the side icons, etc... Very annoying. 

Can someone please help me understand if it is possible to "shrink" the screen size in Ubuntu so that I can see the entire display?  Maybe add a border or something like that?  I tried searching, but could not find any instruction on how to do this. 

I tried different resolutions, but all of them still had portions of the display off the screen.  Any help would be appreciated. 

Thanks.

---

### Post by JKyleOKC on 2014-08-13
In at least some of the many flavors of *buntu, it's possible to drag the display around by putting the mouse pointer in an empty area of the window, holding down the ALT key, then moving the mouse in the desired direction. I've used this several times to solve the problem you are seeing.

If it's happening to almost all screens you see, it's likely that your system has automatically set itself to a smaller resolution size than that for which the screens were designed. In these days of very high resolution monitors, many developers create their windows at large sizes for the best experience on their huge monitors. Then, when displayed on a system configured for a much smaller size, much of the window is off the screen. It's possible, though sometimes quite difficult, to change the system configuration to be more accepting of such programs (that is, to shrink the screen size as you ask) but in order to start we need to know quite a bit more about your hardware, starting with the make and model of your video adapter and of the TV you are using, plus a list of the resolutions you have tried already.

---

### Post by mariskaoldtina on 2014-08-14
Thanks for the response.  So here is what I have for hardware:

Graphics card = Diamond Radeon 4670
TV = MAGNAVOX 37MD350B/F7
They are connected via HDMI cable (using my PC as a server/media center)
Ubuntu 14.04

Instead of just trying a few resolutions, I tried all available ones.  The one that worked was 1360 x 768.  Guess I missed it in my previous attempts. 

So, at higher resolutions (1920 x 1080), it does not work.  Stuff is off the screen.  Does that mean I can't use the higher res?

thanks.

---

### Post by sotiris2 on 2014-08-14
If you want to use higher resolution but you have overscan issues you can use xrandr scaling. 

In a terminal type
```
xrandr --current
```
It will give you a list of interfaces , and if they are connected. Note your hdmi name (probably HDMI-0) it will be the one connected. 
Then do
```
xrandr --output HDMI-0 --scale 0.95x0.95
```
Play around with values but do not make dramatic changes as in 0.7x0.7 , make minor increasements/decreasements. 1x1 will return to default.

---

### Post by Vladlenin5000 on 2014-08-14
Please disregard previous posts. Although with good intentions they all missed the point. The settings you need to change are at your TV: _disable OverScan_.

You need to check in your TV's user manual how to do this and/or contact its tech support. It's quite different from brand to brand.

---

### Post by JKyleOKC on 2014-08-14
> **mariskaoldtina said:**
> The one that worked was 1360 x 768.  Guess I missed it in my previous attempts. 

So, at higher resolutions (1920 x 1080), it does not work.  Stuff is off the screen.  Does that mean I can't use the higher res?I looked up the specs for your TV on Google, and found that its native resolution is 1366 x 768. Any flat-panel type of display, which includes almost all current TV models, works best at its native resolution, so that's where you'll get the best results.

I couldn't find any kind of user manual on line so that I could look up the overscan settings. It's possible that the 6-pixel discrepancy between the native 1366 and your setting of 1360 might be contributing slightly but that's less than one character's width in most typefaces so I would not expect it to matter.

Using the "xrandr" command that Vladlenin5000 suggested might help; it's extremely powerful and has a number of other capabilities besides what he suggested. If you type "man xrandr" at a command-line prompt you'll get a long and highly technical explanation of what it does and how you can use it, but the first version he suggests will tell you the current setting of your video adapter in detail without making any changes.

At this point there's not much more I can offer but I'll be watching this thread; I'm learning a bit more about these problems too! If you do find a solution, we can probably help you make it permanent.

EDIT: An additional search turned up this page: [http://www.manualslib.com/manual/258490/Magnavox-32md350b.html?page=16#manual](http://www.manualslib.com/manual/258490/Magnavox-32md350b.html?page=16#manual)

Note halfway down the page it lists the possible resolutions; I fear that 1360x768 is the best you'll be able to do!

---

### Post by mariskaoldtina on 2014-08-14
Thanks to everyone for the replies.  So, I did check the TV manual, and there is no way to disable Overscan.  I even contacted tech support - and they said you have to manage it on the PC side for that higher resolution.

i also tried the xrandr commands.  When you do scale < 1, it crops the viewable area.  It does not scale.  However, when you go > 1, it scales...but makes it even bigger....lol.  So, that did not work.

i looked at the "man xrandr", and it had a few other options.  However, I was nervous to try them since they often did not mention how to reset if you screw something up.  If anyone has more experience with xrandr, maybe they could help advise?

thanks

---

### Post by JKyleOKC on 2014-08-14
You might find this blog entry useful: [http://sfxpt.wordpress.com/2011/02/02/panning-using-xrandr/](http://sfxpt.wordpress.com/2011/02/02/panning-using-xrandr/) 

Toward the end of it there's mention of a way to undo things, and it's helpful to remember that changes made by xrandr vanish when the power goes away. To make them permanent, you have to embed the xrandr commands in a script automagically executed either at boot time, or at login.

Also, have you tried the drag-while-holding-ALT-down method to "move the display behind trhe screen" that I mentioned in my initial message yet? It might work for you, and won't hurt anything if it doesn't.

---

### Post by mariskaoldtina on 2014-08-15
Thanks a lot for the info, especially knowing that the settings won't be saved.  I'll play around with xrandr more tonight/tomorrow.  Hopefully I'll be able to find the correct command to tweak the screen.  Seems like there are so many control options for the display, so there should be something in there that I'm looking for.  I'll post later on if I figure it out.

I did try the Alt + drag, and it did not move anything.  I'm running Ubuntu 14.04.

---

### Post by thatsmyboy on 2014-08-20
I'm interested in this thread too. Different box / monitor (TV really) but same problem. The issue I have is with a Zotac Mini ZBOX ID12 PLUS computer and a Polaroid  TLAC-02255 22" TV . I'll try it out and post the results.

---

### Post by david-9ei9nyjpwdexg on 2014-11-15
> **mariskaoldtina said:**
> Thanks a lot for the info, especially knowing that the settings won't be saved.  I'll play around with xrandr more tonight/tomorrow.  Hopefully I'll be able to find the correct command to tweak the screen.  Seems like there are so many control options for the display, so there should be something in there that I'm looking for.  I'll post later on if I figure it out.

I did try the Alt + drag, and it did not move anything.  I'm running Ubuntu 14.04.

I figured it out - at least for my setup. I found out I had to use a combination of 2 settings for xrandr. One to "reset" the resolution to a smaller size, and one to "adjust" the top left corner to the proper spot:

```
xrandr --output HDMI2 --fb 1240x700 --transform 1,0,-20,0,1,-10,0,0,1
```

So to read into the command, the --fb switch, resizes the resolution of the framebuffer down to shrink the output, but the resolution sent out to the TV is still 1280x720. And the --transform switch moves the top left corner from beyond the edge of the TV down to the visible part of the TV.

Note that the numbers I have are different than the ones found googling the overscan subject. Apparently my TV's overscan is approximately 20 pixels on the sides, and 10 pixels at the top and bottom. So the framebuffer is reduced by 40 width and 20 height.

Using xrandr this way eliminated the issue where the mouse cursor would think the edge of the screen wasn't wide enough when using the --scale switch, or other combinations I tried.

To make this change permanent, I created it as a simple script, placed it in /etc/lightdm/ and set it as "session-setup-script" in lightdm.conf. Note, I tried many combinations of greeter-setup-script and display-setup-script and both of them would cause issues, so I think these switches are broken in respect to using them to modify the display.

This machine is also running XBMC from an XBMC session, so I was able to use XBMC's alignment tools to make the adjustments for it when I'm using it instead of a LXDE or Unity session.

HTH!

---

