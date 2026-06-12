---
title: "Mouse-wheel way too fast"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by duckfeet on 2008-07-20
I've installed 8.04 Hardy, and in Firefox--and everywhere--my mouse wheel just zips thru the pages...I did the search, and entered Firefox about:config, and changed mousewheel.withnokey.numlines to 1, and mousewheel.withnokey.sysnumlines to false, the way the one poster suggested... didn't work: still too fast ... Mouse I have is MS wireless Optical Mouse 2.0, and I've been searching thru the forums, but so far nothing works...any help would be much appreciated...

---

### Post by reahjw6 on 2008-07-20
Hey
Have you changed the mouse movement in system/ preferences/ mouse.
Reah

---

### Post by FreewheelinFrank on 2008-07-20
Run this command in a terminal:

```
xev
```

A little widow appear plus a slightly larger window.

Position the cursor over the small window and click the mouse buttons and rotate the wheel: the mouse output will appear in the larger window. (Try to keep the mouse still as mouse movement also appears.)

The mouse wheel 'up' and 'down' are actually buttons with numbers (4 & 5 on mine). 

The output is quite verbose, but just try to establish that each notch up or down on the wheel produces one ButtonPress event:

```
ButtonPress event, serial 27, synthetic NO, window 0x3c00001,
    root 0x87, subw 0x3c00002, time 3498165, (51,42), root:(56,91),
    state 0x0, button 5, same_screen YES

EnterNotify event, serial 27, synthetic NO, window 0x3c00001,
    root 0x87, subw 0x0, time 3498165, (51,42), root:(56,91),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 4096

KeymapNotify event, serial 27, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 27, synthetic NO, window 0x3c00001,
    root 0x87, subw 0x3c00002, time 3498165, (51,42), root:(56,91),
    state 0x1000, button 5, same_screen YES

LeaveNotify event, serial 27, synthetic NO, window 0x3c00001,
    root 0x87, subw 0x0, time 3498165, (51,42), root:(56,91),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0
```


If each wheel notch is producing more than one ButtonPress event, it's a mouse problem.

If each wheel notch is producing only one ButtonPress event, it's a system problem (not Firefox).

---

### Post by duckfeet on 2008-07-20
Yep, doesn't seem to make any difference, and since they don't have mouse-wheel settings...

> **reahjw6 said:**
> Hey
Have you changed the mouse movement in system/ preferences/ mouse.
Reah

---

### Post by duckfeet on 2008-07-20
Yes, mine too, are 4 and 5...any way to set them, at say, 1 and 2, as for some reason, with me, this is very fast scrolling...or am I missing something here? ohhh, and I checked again: looks like I'm producing only one even, and I'm pretty sure this happens in system, not just firefox: I had similar problem in Opera, but I was in XP, and had loaded software, that allowed for adjusting wheel...

Well, off to bed for tonight, will check in again tomorrow, again, much appreciated...so excited at my successful loading of linux, did not want to be hassling w/silly mouse ;-)

Thankyou!


> **FreewheelinFrank said:**
> Run this command in a terminal:

```
xev
```

A little widow appear plus a slightly larger window.

Position the cursor over the small window and click the mouse buttons and rotate the wheel: the mouse output will appear in the larger window. (Try to keep the mouse still as mouse movement also appears.)

The mouse wheel 'up' and 'down' are actually buttons with numbers (4 & 5 on mine). 

The output is quite verbose, but just try to establish that each notch up or down on the wheel produces one ButtonPress event:

```
ButtonPress event, serial 27, synthetic NO, window 0x3c00001,
    root 0x87, subw 0x3c00002, time 3498165, (51,42), root:(56,91),
    state 0x0, button 5, same_screen YES

EnterNotify event, serial 27, synthetic NO, window 0x3c00001,
    root 0x87, subw 0x0, time 3498165, (51,42), root:(56,91),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 4096

KeymapNotify event, serial 27, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 27, synthetic NO, window 0x3c00001,
    root 0x87, subw 0x3c00002, time 3498165, (51,42), root:(56,91),
    state 0x1000, button 5, same_screen YES

LeaveNotify event, serial 27, synthetic NO, window 0x3c00001,
    root 0x87, subw 0x0, time 3498165, (51,42), root:(56,91),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0
```


If each wheel notch is producing more than one ButtonPress event, it's a mouse problem.

If each wheel notch is producing only one ButtonPress event, it's a system problem (not Firefox).

---

### Post by FreewheelinFrank on 2008-07-20
> Yes, mine two, are 4 and 5...any way to set them, at say, 1 and 2, as for some reason, with me, this is very fast scrolling...or am I missing something here?

Don't confuse the button number with the number of ButtonPress events.

Button 1 is usually a left click, and if you left click once, you see one ButtonPress event for button one.

Wheel up may be button 4, but if you wheel up one notch, you should only see one ButtonPress event for button 4.

I had a mouse that registered two ButtonPress events for every left click I made because the micro switch was faulty. If you mouse is registering more than one ButtonPress event for every notch of the wheel, scrolling will happen too quickly.

Alternatively, try another mouse. Don't assume your mouse is OK.

---

### Post by duckfeet on 2008-07-20
No, I did figure that out, and that's why i edited original post: I was just curious if there was a way,  since mine was 3 on the downswing, 4 going up, and wondered if I could slow them down, even if it's just FF....  

If I understand you correctly, I am seeing one buttonpress even, so it's systemwide, not just Firefox, but of course, the main area where I use mousewheel is on FF...but again, I appreciate the help,  I know that it did work on XP, after I loaded the CD they included...I thought I'd ask, just in case there was somewhere a command line function for the wheel...  also I can barely feel the "notch" and I don't know if that is part of the problem, but I just figured that's way mouse was made...not a major issue, I'll pick up another tomorrow or monday...thanx again




QUOTE=FreewheelinFrank;5422043]Don't confuse the button number with the number of ButtonPress events.

Button 1 is usually a left click, and if you left click once, you see one ButtonPress event for button one.

Wheel up may be button 4, but if you wheel up one notch, you should only see one ButtonPress event for button 4.

I had a mouse that registered two ButtonPress events for every left click I made because the micro switch was faulty. If you mouse is registering more than one ButtonPress event for every notch of the wheel, scrolling will happen too quickly.

Alternatively, try another mouse. Don't assume your mouse is OK.[/QUOTE]

---

### Post by FreewheelinFrank on 2008-07-20
I'm not aware of any system-wide setting that increases the scroll rate when using the mouse wheel in Ubuntu, but that's not to say it does not exist.

With an optical mouse, the 'notch' may just be a 'gate' passing a beam, so perhaps imperceptible.

hope you find the answer anyway.

---

### Post by duckfeet on 2008-07-20
Certainly nothing major: I have a lot to learn, and this is just something I'll keep an eye on, as I get more familiar w/linux.  When I loaded 7.10 on my laptop, about a month ago, I had all kinds of problems...this time, I downloaded 8.04 to a new HD, on a homemade windows tower, and made a mirror image of it, and loaded it right into a spare HD without a glitch, w/out making a cd, and I'm still amazed at how well it all went, so if this is all I have to complain about, I'm doing good...but I do appreciate the help...I did find some software last night, said it was for linux, for mouses that weren't working right....but it didn't seem quite right, and in every other aspect, the mouse works fine, and some of these pages, I *need* to scroll thru'em quickly, so I'll let it be....

Anyway, I'm an old Furry Freak Bro fan, so like the monikor, FF rules, and appreciate the help...

df




> **FreewheelinFrank said:**
> I'm not aware of any system-wide setting that increases the scroll rate when using the mouse wheel in Ubuntu, but that's not to say it does not exist.

With an optical mouse, the 'notch' may just be a 'gate' passing a beam, so perhaps imperceptible.

hope you find the answer anyway.

---

### Post by Alfionso on 2008-11-12
The posts above were quite helpful.
I've had trouble on and off with my cordless mouse scrolling way too fast intermittently.

The solution was pretty simple; I unplugged it and re-plugged it.

Thanks to FreewheelinFrank for pointing out that it was most likely a hardware problem!

---

### Post by ice21 on 2012-04-16
Hi ubuntu people

I can confirm what Alfionso wrote:

I have a microsoft arc wireless mouse. In firefox one scroll wheel unit scrolled almost all the scroll bar, even if the page was several screenas long ;(

[COLOR="Orange"]Solution[/COLOR]: Unplug the usb receiver, fold up the mouse, unfold the mouse again, plugging back in the usb receiver, and tadaaa, scrolls nice and smooth again =)

Still it were nice to have a system setting under "mouse" which would set the scroll intensity per unit of wheel scroll...

cheers

---

### Post by jwbrase on 2012-04-16
This thread was 3 and a half years old...

---

### Post by oldos2er on 2012-04-16
Closed, necromancy.

---

