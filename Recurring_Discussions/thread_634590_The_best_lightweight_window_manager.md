---
title: "The best lightweight window manager?"
date: 2007-12-07
forum: Recurring Discussions
---

### Post by master_kernel on 2007-12-07
What do you think the best lightweight window manager is?

To me, the top seats belong to XFCE and Enlightenment, maybe IceWM. So, how about you?

---

### Post by -grubby on 2007-12-07
well technically XFCE isn't a WM so it doesn't count...but it wins best DE in my book (although I still use GNOME). I would say my Favorite WM is Fluxbox or E17. next comes what is it....ICEWM

---

### Post by p_quarles on 2007-12-07
I have absolutely nothing against any of the other lightweights, but I'm currently in love with Fluxbox. Simple, takes few resources, and takes all its cues from human-readable text files.

---

### Post by D-EJ915 on 2007-12-07
Sawfish, pure awesomeness.  I love all of them...FVWM, CTWM, Windowmaker, etc.  They do different things and work in different ways that I like using all of them.

But as for brainless configuration and stuff, Sawfish wins by far.

---

### Post by herbster on 2007-12-07
I was using Openbox for a while, looove it. Now trying Fluxbox, just felt like giving it a go, and really digging it too.

---

### Post by Medieval_Creations on 2007-12-07
+1 Fluxbox.  I've been using it for years now.  I've checked out and play with some of the others, but still seem to always come back to Flux.

---

### Post by RAV TUX on 2007-12-07
> **master_kernel said:**
> What do you think the best lightweight window manager is?

To me, the top seats belong to XFCE and Enlightenment, maybe IceWM. So, how about you?

1. e17(specifically the ["e17 CVS Deb" for OzOs]("http://cafelinux.org/forum/index.php/board,91.0.html"))
2. Fluxbox

---

### Post by blithen on 2007-12-07
> **D-EJ915 said:**
> Sawfish, pure awesomeness.  I love all of them...FVWM, CTWM, Windowmaker, etc.  They do different things and work in different ways that I like using all of them.

But as for brainless configuration and stuff, Sawfish wins by far.
DDDDDDD:!! I didn't work for me.... ._. :(

---

### Post by LookTJ on 2007-12-07
OpenBox, BlackBox, IceWM? I don't know which is the lightest and best, but I use GNOME/OpenBox.

---

### Post by crimesaucer on 2007-12-07
> **nathangrubb said:**
> well technically XFCE isn't a WM so it doesn't count...but it wins best DE in my book (although I still use GNOME). I would say my Favorite WM is Fluxbox or E17. next comes what is it....ICEWM

Actually, the xfce4 window manager is **xfwm4**, and it has many features like composting and transparency. For a lightweight browser, xfwm4 is pretty damn good.

---

### Post by vishzilla on 2007-12-07
Which is better Openbox or Fluxbox? I am thinking of switching over to one of these...

---

### Post by IYY on 2007-12-07
I vote for IceWM. It's the simplest, and can actually look the best with the proper themes.

Besides, I love Meta+Space shortcut to activate the commandline.

---

### Post by ~LoKe on 2007-12-07
DWM, simply brilliant!

---

### Post by herbster on 2007-12-07
> **vishzilla said:**
> Which is better Openbox or Fluxbox? I am thinking of switching over to one of these...

How about installing both and giving them a go :)

---

### Post by SunnyRabbiera on 2007-12-07
I like windowmaker, very customizable

---

### Post by ~LoKe on 2007-12-07
> **vishzilla said:**
> Which is better Openbox or Fluxbox? I am thinking of switching over to one of these...

You really would have to try them both.

---

### Post by smartboyathome on 2007-12-07
> **nathangrubb said:**
> well technically XFCE isn't a WM so it doesn't count...but it wins best DE in my book (although I still use GNOME). I would say my Favorite WM is Fluxbox or E17. next comes what is it....ICEWM

Enlightenment 17 is also a desktop environment, so it doesn't count either. Though it is the lightest DE I have seen in a while (is also one of the prettiest :lolflag:).

---

### Post by Mateo on 2007-12-07
definitely fluxbox.  I've going to buy an old computer just so I won't feel guilty running fluxbuntu on it.

---

### Post by RedSquirrel on 2007-12-08
Fluxbox is my favourite, but I wouldn't call it "the best". I don't think there is a "best" window manager because it really comes down to individual tastes. ;)

---

### Post by TeraDyne on 2007-12-08
I like Windowmaker and AfterSTEP the most. Both are customizable enough for my needs, and they're really fast.

---

### Post by bonzodog on 2007-12-08
I would go for Openbox. I love my openbox, and it is very fast. Openbox also supports gtk theming.

I always used windowmaker before this, but openbox is really something else.

---

### Post by SunnyRabbiera on 2007-12-08
> **TeraDyne said:**
> I like Windowmaker and AfterSTEP the most. Both are customizable enough for my needs, and they're really fast.

afterstep is pretty good, but I feel windowmaker is a bit better in some areas.
But meh they are pretty good in any case

---

### Post by jseiser on 2007-12-08
awesome window manager.  Find it here.  [http://awesome.naquadah.org/](http://awesome.naquadah.org/)

---

### Post by tytyty on 2008-06-05
[-X Oh, please. E17, IceWM, AfterStep, Metacity, kwin, and xfwm are HEAVYWEIGHT WM's. All *box, Sawfish, FVWM, and WindowMaker are MIDDLEWEIGHT. The best LEIGHTWEIGHT is defiantly without a doubt...
wm2:)[http://www.all-dat-breakfast.com/wm2/]("http://www.all-dat-breakfast.com/wm2/"). 

Best WM period is Openbox.:)

---

### Post by cardinals_fan on 2008-06-05
TinyWM is lightweight.  Here's the source code, all 56 lines of it: ```
/* TinyWM is written by Nick Welch <mack@incise.org>, 2005.
 *
 * This software is in the public domain
 * and is provided AS IS, with NO WARRANTY. */

#include <X11/Xlib.h>

#define MAX(a, b) ((a) > (b) ? (a) : (b))

int main()
{
    Display * dpy;
    Window root;
    XWindowAttributes attr;
    XButtonEvent start;
    XEvent ev;

    if(!(dpy = XOpenDisplay(0x0))) return 1;

    root = DefaultRootWindow(dpy);

    XGrabKey(dpy, XKeysymToKeycode(dpy, XStringToKeysym("F1")), Mod1Mask, root,
            True, GrabModeAsync, GrabModeAsync);
    XGrabButton(dpy, 1, Mod1Mask, root, True, ButtonPressMask, GrabModeAsync,
            GrabModeAsync, None, None);
    XGrabButton(dpy, 3, Mod1Mask, root, True, ButtonPressMask, GrabModeAsync,
            GrabModeAsync, None, None);

    for(;;)
    {
        XNextEvent(dpy, &ev);
        if(ev.type == KeyPress && ev.xkey.subwindow != None)
            XRaiseWindow(dpy, ev.xkey.subwindow);
        else if(ev.type == ButtonPress && ev.xbutton.subwindow != None)
        {
            XGrabPointer(dpy, ev.xbutton.subwindow, True,
                    PointerMotionMask|ButtonReleaseMask, GrabModeAsync,
                    GrabModeAsync, None, None, CurrentTime);
            XGetWindowAttributes(dpy, ev.xbutton.subwindow, &attr);
            start = ev.xbutton;
        }
        else if(ev.type == MotionNotify)
        {
            int xdiff, ydiff;
            while(XCheckTypedEvent(dpy, MotionNotify, &ev));
            xdiff = ev.xbutton.x_root - start.x_root;
            ydiff = ev.xbutton.y_root - start.y_root;
            XMoveResizeWindow(dpy, ev.xmotion.window,
                attr.x + (start.button==1 ? xdiff : 0),
                attr.y + (start.button==1 ? ydiff : 0),
                MAX(1, attr.width + (start.button==3 ? xdiff : 0)),
                MAX(1, attr.height + (start.button==3 ? ydiff : 0)));
        }
        else if(ev.type == ButtonRelease)
            XUngrabPointer(dpy, CurrentTime);
    }
}
```

---

### Post by Joeb454 on 2008-06-05
Nice :)

---

### Post by RiceMonster on 2008-06-05
I've tried IceWM, JWM, wmii, E17, Fluxbox, and Openbox. Openbox is by far my favorite, followed by Fluxbox. I still want to try out Awesome, Window Maker, PekWM, and FVWM Crystal.

---

### Post by smartboyathome on 2008-06-06
E17 may be horrid at first, but great when customized. :D

---

### Post by -grubby on 2008-06-06
> **smartboyathome said:**
> E17 may be horrid at first, but great when customized. :D

if anybody thinks E17 is horrid they should try E16. Gah I hated that..

---

### Post by MONODA on 2008-06-06
openbox for me. i also like dwm and wmii

---

### Post by urukrama on 2008-06-06
> **nathangrubb said:**
> if anybody thinks E17 is horrid they should try E16. Gah I hated that..

I much prefer E16 over E17.

---

### Post by orengolan on 2008-06-14
dwm - [http://www.suckless.org/wiki/dwm/](http://www.suckless.org/wiki/dwm/)

can't be faster than this:
"dwm is only a single binary, and its source code is intended to never exceed 2000 SLOC"

---

### Post by cardinals_fan on 2008-06-15
> **orengolan said:**
> dwm - [http://www.suckless.org/wiki/dwm/](http://www.suckless.org/wiki/dwm/)

can't be faster than this:
"dwm is only a single binary, and its source code is intended to never exceed 2000 SLOC"
2000 lines?  TinyWM has 56!

With that said, I consider Xmonad and dwm to be the two best window managers.

---

### Post by kaiju on 2008-06-16
evilwm - another one in the lightweight cathegory
i've been using it for a few weeks now, never had any problems with it.
of the more full-featured window managers, i like fluxbox most.

---

### Post by x1a4 on 2008-06-19
> **~LoKe said:**
> DWM, simply brilliant!

Nice, but I find wmii to be better. :)  Although not having window titles is one advantage dwm has over wmii.

---

### Post by LaRoza on 2008-06-19
I have used wmii for a while, and just a few minutes ago started using xmonad. They aren't that different, and I can't say one is "better".

---

### Post by starcannon on 2008-06-20
I prefer Fluxbox with Rox.

Just my preference, your mileage may vary.

---

### Post by msrinath80 on 2008-06-21
Window Maker, always :-)

---

### Post by jaybee99 on 2008-07-14
No one mentioned windowlab yet, which surprises me. It's a very nice one in the lightweight category, well worth a look. Having said that, I switched to xmonad a year or two ago and would find it hard to switch back to a non-tiling wm now.

---

### Post by collinp on 2008-07-14
For me, has to be either IceWM or Enlightenment.

---

### Post by AnLGP on 2008-07-14
jwm or fluxbox

---

### Post by mrgnash on 2008-07-14
I'd have to say wmii...

---

### Post by LaRoza on 2008-07-14
> **mrgnash said:**
> I'd have to say wmii...

So do I.

---

### Post by cardinals_fan on 2008-07-14
> **mrgnash said:**
> I'd have to say wmii...
You've been assimilated!

---

### Post by brunovecchi on 2008-07-14
> **jseiser said:**
> awesome window manager.  Find it here.  [http://awesome.naquadah.org/](http://awesome.naquadah.org/)

+1. I like awesome.

---

### Post by AnLGP on 2008-07-14
awesome was alright.  i'm not used to tiling WMs but I think I could prob. get the hang of it.

---

### Post by Lord DarkPat on 2008-07-14
Openbox

---

### Post by LaRoza on 2008-07-14
> **cardinals_fan said:**
> You've been assimilated!

Just wait until I figure out how to say that!

---

### Post by dizee on 2008-07-14
> **Lord DarkPat said:**
> Openbox
i concur.

---

### Post by cardinals_fan on 2008-07-14
> **LaRoza said:**
> Just wait until I figure out how to say that!
...must...retain...control...of...mind... :)

---

### Post by |{urse on 2008-07-14
Wow, you guys consider e17 lightweight?

---

### Post by LaRoza on 2008-07-14
> **cardinals_fan said:**
> ...must...retain...control...of...mind... :)

&#2346;&#2381;&#2352;&#2340;&#2367;&#2352;&#2379;&#2343; &#2357;&#2381;&#2351;&#2352;&#2381;&#2341; &#2361;&#2376;

In reality, they aren't that different :-) I could use xmonad without any trouble (besides changing background colour) and it was essential wmii in use.

---

### Post by ryaxnb on 2008-07-15
JWM, FLWM. Here's Why:
[LIST=1]
[*]JWM: Xlib direct
[*]JWM: Easy Interface
[*]JWM: Nice taskbar
[*]JWM: themable
[*]JWM: Takes up ~3MB RAM
[*]JWM: GNOME hints
[*]JWM: Uses Debian Menu
[*]Flwm: Uses Debian Menu
[*]Flwm: Uses ~4.5MB RAM
[*]Flwm: Handy one-direction maximize
[*]Flwm: Neat widget setup
[*]Flwm: Nostalgic
[/LIST]

---

### Post by RiceMonster on 2008-07-15
Eck, I always hated the debian menu. It's so ugly and messy. I tried it in Fluxbox and Openbox (which I use now with Arch), and I much preferred to build the menu myself in both cases.

---

### Post by LaRoza on 2008-07-15
> **ryaxnb said:**
> JWM, FLWM. Here's Why:


TinyWM and Ratpoison are lighter :-)

I don't know how much DWM, wmii, and xmonad take up though, although I know wmii has less than 10000 lines of code and is the largest.

---

### Post by RiceMonster on 2008-07-15
Yeah, wmii was only 1 MB when I installed it. It's my favorite tiling wm now, but I still prefer to use Openbox. I can't get comfortable in a tiling wm :(.

---

### Post by ryaxnb on 2008-07-15
> **RiceMonster said:**
> Eck, I always hated the debian menu. It's so ugly and messy. I tried it in Fluxbox and Openbox (which I use now with Arch), and I much preferred to build the menu myself in both cases.

don't have the time

---

### Post by LaRoza on 2008-07-15
> **RiceMonster said:**
> Yeah, wmii was only 1 MB when I installed it. It's my favorite tiling wm now, but I still prefer to use Openbox. I can't get comfortable in a tiling wm :(.

I can only be comfortable. You should see me in Windows/GNOME/KDE or whatever! Luckily, the keyboard shortcuts don't do anything special in those DE's so I don't do anything I can't undo.

---

### Post by ryaxnb on 2008-07-15
> **LaRoza said:**
> TinyWM and Ratpoison are lighter :-)

I don't know how much DWM, wmii, and xmonad take up though, although I know wmii has less than 10000 lines of code and is the largest.
It's not about who's lightest it's about who's best. Best ultra-ultra-light? dwm. But I want a .conf file, Debian menu support, and a nice titlebar and taskbar, being a Windows convert, I'm used to those features, except the .conf file, which I'll grow in to. :D.

---

### Post by LaRoza on 2008-07-15
> **ryaxnb said:**
> It's not about who's lightest it's about who's best. Best ultra-ultra-light? dwm. But I want a .conf file, Debian menu support, and a nice titlebar and taskbar, being a Windows convert, I'm used to those features, except the .conf file, which I'll grow in to. :D.

I would consider those strikes against them to some. "Best" is too relative I think.

---

### Post by ryaxnb on 2008-07-15
> **LaRoza said:**
> I would consider those strikes against them to some. "Best" is too relative I think.

Of course. "Best" for me, right now. :)

---

### Post by mrgnash on 2008-07-15
> **cardinals_fan said:**
> You've been assimilated!

My reprogramming has been thorough indeed :( I'm even using Opera :confused:

---

### Post by LaRoza on 2008-07-15
> **mrgnash said:**
> My reprogramming has been thorough indeed :( I'm even using Opera :confused:

Good. Now use Vim!

---

### Post by Dr Small on 2008-07-15
Openbox. ;)

---

### Post by cardinals_fan on 2008-07-15
> **LaRoza said:**
> &#2346;&#2381;&#2352;&#2340;&#2367;&#2352;&#2379;&#2343; &#2357;&#2381;&#2351;&#2352;&#2381;&#2341; &#2361;&#2376;

In reality, they aren't that different :-) I could use xmonad without any trouble (besides changing background colour) and it was essential wmii in use.
I don't need to change the defaults with Xmonad, because they're perfect for me.  Wmii has window titles, a weird little taskbar thingy, and a couple other "features" that I would need to turn off.  And since when is changing the background the responsibility of the **_window_** manager? :)
> **mrgnash said:**
> My reprogramming has been thorough indeed :( I'm even using Opera :confused:
That's fine; Opera is perfect.  As is Vim :)

---

### Post by RiceMonster on 2008-07-15
Meh, Opera's alright. Firefox + vimperator is the way to go. What's better than a vim style web browser? :D

---

### Post by LaRoza on 2008-07-15
> **cardinals_fan said:**
> I don't need to change the defaults with Xmonad, because they're perfect for me.  Wmii has window titles, a weird little taskbar thingy, and a couple other "features" that I would need to turn off.  And since when is changing the background the responsibility of the **_window_** manager? :)

I don't need to change the default of wmii. Ok, why did xmonad have a bright orange background? That was very annoying. It also didn't give a way to change it.

---

### Post by cardinals_fan on 2008-07-15
> **LaRoza said:**
> I don't need to change the default of wmii. Ok, why did xmonad have a bright orange background? That was very annoying. It also didn't give a way to change it.
Eh?  What distro is this on?

---

### Post by LaRoza on 2008-07-15
> **cardinals_fan said:**
> Eh?  What distro is this on?

Ubuntu.

---

### Post by cardinals_fan on 2008-07-15
> **LaRoza said:**
> Ubuntu.
Xmonad didn't set your wallpaper orange.  It was made orange either a) by default, or b) by a login manager.  Use a tool such as xsetroot, xsri (the best!), or feh to change it.

BTW, I just found a new WM to use.  Xfce can be customized to be very lightweight, minimal, and keyboard-oriented, and I like the hybrid I've come up with.

---

### Post by LaRoza on 2008-07-15
> **cardinals_fan said:**
> Xmonad didn't set your wallpaper orange.  It was made orange either a) by default, or b) by a login manager.  Use a tool such as xsetroot, xsri (the best!), or feh to change it.
At the time, I tried the "xsetroot" but it just made flickering snow instead of black.

> BTW, I just found a new WM to use.  Xfce can be customized to be very lightweight, minimal, and keyboard-oriented, and I like the hybrid I've come up with.
Traitor.

---

### Post by cardinals_fan on 2008-07-15
> **LaRoza said:**
> 
Traitor.
Heh.  I didn't really find tiling that useful (even though I thought that I did).  I just appreciated the keyboard control available in most tiling WMs.  My slimmed-down Xfce (which is more like Xfwm4 alone, because there are few remnants of the DE left) has the same keyboard-friendliness and works better with apps like the GIMP.

---

### Post by LaRoza on 2008-07-15
> **cardinals_fan said:**
> Heh.  I didn't really find tiling that useful (even though I thought that I did).  I just appreciated the keyboard control available in most tiling WMs.  My slimmed-down Xfce (which is more like Xfwm4 alone, because there are few remnants of the DE left) has the same keyboard-friendliness and works better with apps like the GIMP.

Ah, I use browser and terminals mostly, so tiling is important.

---

### Post by cardinals_fan on 2008-07-15
> **LaRoza said:**
> Ah, I use browser and terminals mostly, so tiling is important.
My main apps are Opera, a tabbed terminal, Kphotoalbum, the GIMP, and Gnumeric.  I very rarely open more than one of these in a workspace.  So, what I need is easy workspace management.  I can get that with Xfce or a tiling WM, and the GIMP tips me towards Xfce.  I still like Xmonad though :)

---

### Post by LaRoza on 2008-07-15
> **cardinals_fan said:**
> My main apps are Opera, a tabbed terminal, Kphotoalbum, the GIMP, and Gnumeric.  I very rarely open more than one of these in a workspace.  So, what I need is easy workspace management.  I can get that with Xfce or a tiling WM, and the GIMP tips me towards Xfce.  I still like Xmonad though :)

Opera (of course), and many terminals. Sometimes thunar (when I am not using mc) and vlc for the odd video.

---

### Post by RedSquirrel on 2008-07-15
> **cardinals_fan said:**
> Xmonad didn't set your wallpaper orange.  It was made orange either a) by default, or b) by a login manager.  Use a tool such as xsetroot, xsri (the best!), or feh to change it.

BTW, I just found a new WM to use.  Xfce can be customized to be very lightweight, minimal, and keyboard-oriented, and I like the hybrid I've come up with.

... and xfwm4 has fancy compositing. (Not a priority for me, but hey, some people like it.) :)

The last time I used Xfce, I found that it was somewhat limited in terms of what you could do with key bindings. Some of the defaults were not easily changed.

These days, I seem to be alternating between dwm and Openbox (dwm tonight, but all I did was watch [The Best of Both Worlds]("http://en.wikipedia.org/wiki/The_Best_of_Both_Worlds_%28TNG_episode%29") with mplayer). There's something synergistic about watching Star Trek on a Linux box.

---

### Post by cardinals_fan on 2008-07-16
> **RedSquirrel said:**
> ... and xfwm4 has fancy compositing. (Not a priority for me, but hey, some people like it.) :)

The last time I used Xfce, I found that it was somewhat limited in terms of what you could do with key bindings. Some of the defaults were not easily changed.

These days, I seem to be alternating between dwm and Openbox (dwm tonight, but all I did was watch [The Best of Both Worlds]("http://en.wikipedia.org/wiki/The_Best_of_Both_Worlds_%28TNG_episode%29") with mplayer). There's something synergistic about watching Star Trek on a Linux box.
Xfce key bindings are very configurable :)

---

### Post by urukrama on 2008-07-16
> **cardinals_fan said:**
> Xfce key bindings are very configurable :)

Xfce doesn't support keychains, though, does it? I've started using them in Openbox (and Pekwm) in the last few months, and they are absolutely great!

---

### Post by |{urse on 2008-07-16
wo0t! I thought i was the only one who swore by Opera's superiority (the program's better, idk about the ethos of the company) +1 to opera users ^^

---

### Post by LaRoza on 2008-07-16
> **|{urse said:**
> wo0t! I thought i was the only one who swore by Opera's superiority (the program's better, idk about the ethos of the company) +1 to opera users ^^

[http://ubuntuforums.org/group.php?groupid=175](http://ubuntuforums.org/group.php?groupid=175)

---

### Post by RedSquirrel on 2008-07-16
> **cardinals_fan said:**
> Xfce key bindings are very configurable :)

True, but there was something about the key bindings that didn't work for me. It may have had something to do with workspaces, but it was a while ago now so the details are fuzzy... anyway, doesn't matter. :neutral:

---

### Post by cardinals_fan on 2008-07-16
> **RedSquirrel said:**
> True, but there was something about the key bindings that didn't work for me. It may have had something to do with workspaces, but it was a while ago now so the details are fuzzy... anyway, doesn't matter. :neutral:
I know what it is!  Most Xfce keybindings (for app launching) are changed (graphically, that is) through the keyboard window.  They are controlled by xfce-mcs-manager, and **do not depend on Xfwm**.  You can launch xfce-mcs-manager in Fluxbox or dwm and still have these settings work.  That's what makes Xfce a DE rather than a WM (in my book anyway).  Settings for Xfwm, on the other hand, are edited through the window manager settings window.  This actually makes a lot of sense, because it makes the DE extremely modular.  You can swap out the WM and know exactly which settings to change, because you can tell which settings depend on Xfwm.

---

### Post by urukrama on 2008-07-17
**cardinals_fan**, will we get to see a screenshot of your bare xfce setup? I'm curious to see what you did with it. :)

I love XFCE too, and use it as my DE at work. I too like its modular approach!

---

### Post by Canis familiaris on 2008-07-17
IceWM

---

### Post by RedSquirrel on 2008-07-17
> **cardinals_fan said:**
> I know what it is!  Most Xfce keybindings (for app launching) are changed (graphically, that is) through the keyboard window.  They are controlled by xfce-mcs-manager, and **do not depend on Xfwm**.  You can launch xfce-mcs-manager in Fluxbox or dwm and still have these settings work.  That's what makes Xfce a DE rather than a WM (in my book anyway).  Settings for Xfwm, on the other hand, are edited through the window manager settings window.  This actually makes a lot of sense, because it makes the DE extremely modular.  You can swap out the WM and know exactly which settings to change, because you can tell which settings depend on Xfwm.

I'd really have to install Xfce to refresh my memory of the specific issue I was dealing with the last time I used it. I remember looking through the entire set of categories under Xfce's configuration, but I couldn't get it to do what I wanted.

I have no plans to install Xfce in the near future. It's a great DE, but I simply don't require all of the stuff that comes with a DE. ;)

---

### Post by akiratheoni on 2008-07-17
I tried wmii for awhile. I loved it but there were several issues that I wasn't able to figure out (for one, I couldn't find a for-dummies document... I read the documentation but I was still confused, and there was an issue with VirtualBox) so I switched back to Openbox.

---

### Post by LaRoza on 2008-07-17
> **akiratheoni said:**
> I tried wmii for awhile. I loved it but there were several issues that I wasn't able to figure out (for one, I couldn't find a for-dummies document... I read the documentation but I was still confused, and there was an issue with VirtualBox) so I switched back to Openbox.

Could you say what you had trouble with? Might be something simple.

---

### Post by cardinals_fan on 2008-07-20
> **urukrama said:**
> **cardinals_fan**, will we get to see a screenshot of your bare xfce setup? I'm curious to see what you did with it. :)

I posted a pic in the .conkyrc thread along with my new conky config.  Here's [the link]("http://ubuntuforums.org/showpost.php?p=5400157&postcount=2912").

Sorry that I haven't replied for a while - our ISP decided to "upgrade" the system without telling us - so I've had no internet access for three days.
> **urukrama said:**
> I love XFCE too, and use it as my DE at work. I too like its modular approach!
From the Xfce home page: > Xfce 4.4 embodies the traditional UNIX philosophy of modularity and re-usability. It consists of a number of components that together provide the full functionality of the desktop environment. They are packaged separately and **you can pick and choose** from the available packages to create the best **personal** working environment.That says it all :)

---

### Post by cardinals_fan on 2008-07-23
*bump*

This was a good thread, I don't want it to die :)

---

### Post by Yes on 2008-07-23
Does anybody still use those really old window managers, like CTWM or twm?  I tried CTWM out just for fun, but I couldn't figure out how to close anything.  It was really fast, though :) .

---

### Post by cardinals_fan on 2008-07-23
> **Yes said:**
> Does anybody still use those really old window managers, like CTWM or twm?  I tried CTWM out just for fun, but I couldn't figure out how to close anything.  It was really fast, though :) .
I used twm for a week on a minimalist NetBSD install :)

---

### Post by RiceMonster on 2008-07-23
I tried twm for a bit on a Slackware install. I didn't see much of an advantage to using it.

---

### Post by hessiess on 2008-07-23
DWM, dosn't waste screen space.

---

### Post by LaRoza on 2008-07-23
> **hessiess said:**
> DWM, dosn't waste screen space.

Yes it does, try something like xmonad ;)

---

### Post by jaybee99 on 2008-07-23
> **LaRoza said:**
> Yes it does, try something like xmonad ;)
dwm is a tiling wm like xmonad that adds no furniture to windows, no? What are you on about?

---

### Post by RiceMonster on 2008-07-23
I guess he's talking about the bar/panel dwm has. Xmonad doesn't have one of those, and no window decorations, which dwm doesn't have either.

---

### Post by cardinals_fan on 2008-07-23
> **RiceMonster said:**
> I guess he's talking about the bar/panel dwm has. Xmonad doesn't have one of those, and no window decorations, which dwm doesn't have either.
Correct.> dwm contains a small status bar which displays all available tags, the layout, the title of the focused window, and text read from standard input

---

### Post by mysticrider92 on 2008-07-23
> **RiceMonster said:**
> I tried twm for a bit on a Slackware install. I didn't see much of an advantage to using it.

I find it useful when installing Gentoo. When I don't feel like waiting all night for Gnome to compile, X11+TWM gets a usable environment up in about 1.5 hours on my computer.

Personally, I don't regularly use any really lightweight window manager. I like to play around with them occasionally, just to try something different, but I prefer a full-featured (read: without a terminal where possible) desktop.

---

### Post by NullHead on 2008-07-23
> **mysticrider92 said:**
> I find it useful when installing Gentoo. When I don't feel like waiting all night for Gnome to compile, X11+TWM gets a usable environment up in about 1.5 hours on my computer.

Personally, I don't regularly use any really lightweight window manager. I like to play around with them occasionally, just to try something different, but I prefer a full-featured (read: without a terminal where possible) desktop.

You should try wmii. It's the best light weight WM I've used! Very powerful.

---

### Post by LaRoza on 2008-07-23
> **jaybee99 said:**
> dwm is a tiling wm like xmonad that adds no furniture to windows, no? What are you on about?

The little bar :-) xmonad has no title bar or panels.

> **NullHead said:**
> You should try wmii. It's the best light weight WM I've used! Very powerful.

I used wmii and switched to xmonad recently. They are the same in use, with minor differences.

---

### Post by hessiess on 2008-07-24
> 
dwm contains a small status bar which displays all available tags, the layout, the title of the focused window, and text read from standard input

which can be hidden using alt+b or completly removed by editing the source.
```

static Bool showbar                 = True;     /* False means no bar */
```

---

### Post by jman6495 on 2009-07-06
the fastest window manager i know is JWM

---

### Post by stanca on 2009-08-02
The best window manager is the one you like the most and works in the best way for you.I'm using and voting for E17 and Fluxbox.Rarely over 5% from cpu and ram.8-)

---

### Post by Mark76 on 2009-08-02
OroboROX (the window manager for the ROX desktop) uses only 0.5% of RAM on my system.

Not sure if it works outside a ROX environment though :(

---

### Post by ThaDoctor99 on 2009-08-03
to me any *box is great, I have played with a lot of different things, for laptops I really dig ratpoison, that is really good at what it is made for, that is keyboard control if you just like emacs already that makes it even better. Well else I have fooled around with Enlightenment, but I really did not like that, with eye candy I think something like fvwm-crystal is great.
My absolute favorite will have to be either openbox or ratpoison. (depending on whether it is a laptop or stationary I am working on.) However I still use gnome all the time, I have set up openbox so that I really like the look of it. But need some small things for making it work really good.

But I really dig *box.
Fluxbox is suddenly also a very nice alternative.

---

### Post by gypsumwolf on 2009-09-16
I do not like: XFCE or Thunar.

I use: Openbox + feh + fbpanel. I do not use a "Desktop Environment".

---

### Post by stanca on 2009-10-03
That who likes you the most!;)

---

