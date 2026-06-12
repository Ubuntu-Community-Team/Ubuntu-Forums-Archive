---
title: "Blurred fonts on Ubuntu comparing to Windows"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by nirfun1 on 2008-09-30
Hi, 
I have Ubuntu 8.04 and I'm using Firefox 3.0.3 as my browser.
The fonts looks very bad on most websites.

This screenshot from ubuntu:
[img]http://xs431.xs.to/xs431/08402/screenshot883.png[/img]

This screenshot from Windows Vista:
[img]http://uploads.screenshot-program.com/upl8918239726.png[/img]

any ideas how to fix this problem?
I already installed msttcorefonts.

Thanks.

---

### Post by dangermouse28 on 2008-09-30
That's odd - looking at your screenshots, I would have said that the Vista fonts were more blurred than the Ubuntu ones :-k

Must be my eyes....

---

### Post by kpkeerthi on 2008-09-30
System -> Preference -> Appearance -> Font -> Subpixel Smoothing. You may also want to adjust hinting.

---

### Post by wilsong on 2008-09-30
Are there different resolutions in the two computers? Maybe in Linux try CTRL  +   ( control plus ) to increase txt size... I do believe there is a difference depending too on monitor, unless its on the same computer, and again on the person observing. To me the linux one looks easier to read (except its not as bright) as the windows one. (and thats not just the linux partial side of me talking :).

---

### Post by nirfun1 on 2008-09-30
> **kpkeerthi said:**
> System -> Preference -> Appearance -> Font -> Subpixel Smoothing. You may also want to adjust hinting.

I already tried this. The screenshot was captured with those settings.

The resolution is the same (1440x900) on Samsung 940BW.
both screenshots were captured from the same computer.

---

### Post by fballem on 2008-09-30
You might want to change some settings in the Desktop Settings - Appearance window.

To get there, please right-click on an empty portion of the Desktop. From the menu that will appear, please select Change Desktop Background (Screenshot-Desktop.png). This will produce a tabbed window (Screenshot-Appearance Preferences.png). If you then select the Fonts tab, you will be able to change your font settings (Screenshot-Appearance Preferences-2.png)

If you have an LCD Monitor, you should select the Subpixel Smoothing (LCD) option, which will provide a crisper resolution.

As for the fonts, you may want to consider two options:

1. Install the Liberation fonts. This can be done through Synaptic: 1) search for 'Liberation' in Synaptic. One of the options will be ttf-liberation, which you can then install. These are free fonts that have the same metrics as the Microsoft fonts.

2. Use the MS Core Fonts, which you have already installed. If you go with this option, select Arial as the font to be used.

There _may_ be some legal 'grey area' around the use of the MS Core Fonts, which is why in my case, I've chosen the first option for my setup.

Hope this helps,

---

### Post by SupaSonic on 2008-09-30
> **nirfun1 said:**
> I already tried this. The screenshot was captured with those settings.

The resolution is the same (1440x900) on Samsung 940BW.
both screenshots were captured from the same computer.

Some people suggested restarting FireFox after this would help.

Although I really don't see anything blurry on the Ubuntu screenshot.

---

### Post by surelock22 on 2008-09-30
maybe it's me, but I've been staring and staring at the screen shots, and I don't see any blurryiness. Must be my eyes (I don't think I've changed my contact lenses in 3 months).

---

### Post by 3rdalbum on 2008-09-30
Information from the Microsoft Knowledgebase:

[http://support.microsoft.com/kb/555778](http://support.microsoft.com/kb/555778)

SUMMARY
The Web Fonts in Internet Explorer 7 may Blurry and Anti-Aliased. This is not an issue and disabling an option in Internet Explorer will resolve the issue. 

CAUSE
IE7 use ClearType font rendering in the browser. With ClearType enable the font will appear Anti-Aliased (Smoother or Blurry).

RESOLUTION
1. Click on &#8220;Tool&#8221;
2. Click &#8220;Internet Options&#8220;
2. Click &#8220;Advanced&#8221; Tabs.
3. Under Multimedia, Uncheckthe &#8220;Always Use ClearType for HTML&#8221;.
4. Click OK
5. Close and Restart Internet Explorer 7.

---

### Post by surelock22 on 2008-09-30
Actually, looking again, the guy who said that the Windows Vista screen shots looked more blurry seems correct (at least to me).

I'm reading this from a Windows machine, so that's probably my problem...

---

### Post by CJ56 on 2008-09-30
It may sound a bit extreme, but have you tried a different browser? I used to get that annoying effect on Firefox but less so on Epiphany (in the Repositories, & a very nice little browser) and Opera. Just something about the way it's made I guess.

If the fonts look okay in other applications like OpenOffice, it might be worth experimenting -

---

### Post by nirfun1 on 2008-09-30
I tried to set Arial as the font on all categories except monospace font and there is no real change.

Take a look at this screenshot:
[img]http://xs131.xs.to/xs131/08402/vistavslinux719.png[/img]

What would you prefer to see?

And I'm not going to use another browser for this...

---

### Post by SupaSonic on 2008-09-30
> **nirfun1 said:**
> I tried to set Arial as the font on all categories except monospace font and there is no real change.

Take a look at this screenshot:
[img]http://xs131.xs.to/xs131/08402/vistavslinux719.png[/img]

What would you prefer to see?

And I'm not going to use another browser for this...

Sorry I'm not helping, but I prefer the second one. I get a headache just looking at the first one.

---

### Post by 3rdalbum on 2008-09-30
> **nirfun1 said:**
> I tried to set Arial as the font on all categories except monospace font and there is no real change.

Take a look at this screenshot:
[img]http://xs131.xs.to/xs131/08402/vistavslinux719.png[/img]

What would you prefer to see?

And I'm not going to use another browser for this...

Sorry, I just realised that you're complaining that Ubuntu's fonts are blurry, not Vista's. Unusual.

If you want to blur up Ubuntu's font rendering, go to System > Preferences > Appearance > Fonts and click Details. Turn the "Hinting" down to "Slight". Finally, install the "msttcorefonts" package from Synaptic Package Manager.

But seriously dude, for the brief period that we used IE 7 at my workplace, I got sore eyes. Anti-aliasing is great on CRT monitors, but it bites on LCDs.

If the fonts on Ubuntu really do appear more *blurry* than the Vista ones, your monitor might not be running at its "native resolution". Look in your monitor's manual to find the native resolution of the screen, and adjust Ubuntu's Screen Resolution to suit.

---

### Post by seshomaru samma on 2008-09-30
do you an nvidia card?

---

### Post by kaspar_silas on 2008-09-30
I thought I was going loopy as I seen no difference in your images (other than colour). So I copied the screen shots and compared values after some simple edge detection. 

From this I can confirm that on my computer they are identically sharp. Whilst this is no doubt mostly useless to you (thou I guess it's another clue) me and surelock22 can sleep a little easier.

---

### Post by nirfun1 on 2008-09-30
> **seshomaru samma said:**
> do you an nvidia card?

Yes, I have GeForce 7600GT

---

### Post by seshomaru samma on 2008-09-30
the reason i'm asking is that I had a box with an nvidia card i used the restricted drivers and the fonts looked blurred (on the ubuntu menus), i had a samsung wide screen monitor and the fonts looked smooth only when i disabled nvidia 
but if the problem only occurs on your browser ,try to play with the font setting in firefox  ,in my version (firefox 2.0) its in edit>preferences>content

---

### Post by nirfun1 on 2008-09-30
seshomaru, I use restricted drivers.
How can I "disable nvidia"?

---

### Post by kpkeerthi on 2008-09-30
Go to System -> Admin -> Hardware Drivers to disable nvidia

---

### Post by nirfun1 on 2008-09-30
> **kpkeerthi said:**
> Go to System -> Admin -> Hardware Drivers to disable nvidia

When I disable the driver, I can't set resolution higher than 800x600, so everything looks bad...

---

### Post by nirfun1 on 2008-09-30
I tried to follow this How-To guide:
[http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)

and I have 2 problems:
1. on xorg.conf there is no entry for 1440x900 (my screen resolution)
2. the command "xdpyinfo | grep resolution" returns:
  resolution:    44x43 dots per inch

and it should be 96x96 dots per inch.

how can I fix those problems?

---

### Post by seshomaru samma on 2008-10-01
the HOWTO you are using is for ubuntu Hoary from 3 years ago, in Linux terms this is ancient . Modern versions of Ubuntu are designed differently.
I suggest enabling your nVidia drivers first and working from there, after you are more confident with Linux you can try disabling them and work with command line (sorry this is my fault in a way, so sorry...)
Did you try tweaking the fonts on your browser? 
Also have a look[ here]("http://rewind.themasterplan.in/2007/07/15/sexy-smooth-fonts-on-kubuntu/") from a more up-to-date HOWTO for smoother fonts on Ubuntu 
Ultimately I think it's a problem with Ubuntu's nVidia settings (I had a similar problem, which happened on XP as well) , but let's try a few simpler workarounds before we try more extreme methods.

---

### Post by hugmenot on 2008-10-02
> **wilsong said:**
> are there different resolutions in the two computers? Maybe in linux try ctrl  +   ( control plus ) to increase txt size... I do believe there is a difference depending too on monitor, unless its on the same computer, and again on the person observing. To me the linux one looks easier to read (except its not as bright) as the windows one. (and thats not just the linux partial side of me talking :).

lol

---

### Post by hugmenot on 2008-10-02
> **surelock22 said:**
> actually, looking again, the guy who said that the windows vista screen shots looked more blurry seems correct (at least to me).

I'm reading this from a windows machine, so that's probably my problem...

lol

---

### Post by vladokov on 2008-12-29
I had also blurry fonts on opensuse with proprietary "nvidia" driver (Geforce2 Titan), not opensource "nv" driver.
I played a bit with HSync and VSync in "Modeline" in "Modes" section of /etc/X11/xorg.conf.
I had blurry fonts with "Modeline" where I had no HSync and VSync. Now I have sharp fonts for LCD monitor with 1680x1050 resolution with this "Modes" section:

> 
Section "Modes"
  Identifier   "Modes[0]"
  Modeline      "1680x1050" 146.00 1680 1784 1960 2240 1050 1053 1059 1089 -HSync
EndSection


---

