---
title: "Firefox Fonts with Ubuntu?"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by JK700 on 2013-07-18
I'm new to using Ubuntu/Linux and I have been trying to get the right font for a few days now but am still struggling.

Some websites are tolerable but more often than not it is a real battle to read text on websites and it just doesn't look or feel good. I think I am using "Unity" ?

I don't know whether it is Ubuntu or the fact that this laptop I have acquired is just a 13.3" screen (I am used to a bit bigger than that), or could be both.

I have the microsoft core fonts installed and another thing which was reccomended to me is ubuntu-restricted-extras but it still isn't what I'm looking for.

I want to remain using Firefox if possible, and just to test I tried out a few of the same pages in Chromium Web Browser but it looks near identical to what it does in Firefox.

Any suggestions? Thanks.

---

### Post by silconsystem on 2013-07-18
Hi,

If Unity is the issue you can enter: ```
[FONT=Ubuntu Mono]gnome-session --session=ubuntu-2d
[/FONT]
``` in the terminal. You should also have had an option at startup to use 2d mode.
some more info on unity 2d: [https://wiki.ubuntu.com/Unity2D](https://wiki.ubuntu.com/Unity2D)

If you only have problems with fonts it could be a different problem aswell, theres lots of font settings to tweak in your appearance settings aswell.

new fonts you can add to /usr/share/fonts/ directory.


If this all doesnt work try posting some screens and some info about your computer, ubuntu and kernel for further diagnosis.


Cheers,


Rob

---

### Post by Frogs Hair on 2013-07-18
Setting locations my vary so post what version of Ubuntu you are using. If you are not sure open the details application and it will be displayed there.

As you may know custom fonts can be used in Firefox which by default allows web pages to use their own settings  . In  Preferences > Content > Fonts > Advanced you can select a preferred font .  If the Gnome Tweak Tool is installed under fonts there is an anti-aliasing setting which can change the quality of the displayed font.

---

### Post by JK700 on 2013-07-18
[http://i43.tinypic.com/2hwpwjn.jpg](http://i43.tinypic.com/2hwpwjn.jpg)

[http://i40.tinypic.com/10fyryq.png](http://i40.tinypic.com/10fyryq.png)

UBUNTU 13.04

The links above are Screens to what pages/text looks like for me. I don't think they do it justice though to be honest, it doesn't actually look that bad on those screens.

I attempted the terminal thing but it didn't work and came up with this error message

"Could not acquire name on session bus"

---

### Post by oldos2er on 2013-07-18
If you want to increase the font size use Ctrl +
That is, hold down Ctrl and press +

---

### Post by silconsystem on 2013-07-18
Ah yes, after seeing the screens it must be just down to your browsers zoom or font-size.

Does adjusting zoom fix your problem ?

---

### Post by maddogz007 on 2013-07-18
Have you tried the NoSquint add for firefox??? 

[https://addons.mozilla.org/en-us/firefox/addon/nosquint/](https://addons.mozilla.org/en-us/firefox/addon/nosquint/)

---

### Post by Buntu Bunny on 2013-07-18
Under Firefox Preferences, you can set a default font and font size. 

Edit > Preferences > Content

---

### Post by buzzingrobot on 2013-07-18
There's a setting someplace, either in Gnome-Tweak-Tool or Unity settings, to adjust the font scale up or down, while leaving the selected font sizes alone.  A high resolution 13-inch screen is going to have smaller fonts.

It's difficult to create an accurate representation of how fonts render on your screen via an image that's displayed on other machines because the image has a different resolution than the original screen, as do the other displays.

Font rendering on Ubuntu is considered very good, but it is not like the default Windows rendering that some prefer.  Install Gnome-Tweak-Tool and experiment with the different combinations of settings under "Fonts".

---

### Post by JK700 on 2013-07-18
The trouble with increasing font size or zooming in too much messes up pages where there are images - the text goes all over the place and really makes websites look messy

And yes I tried NoSquint yesterday but that didn't seem to help much. I'm really confused as to how best proceed from here.

Which specific font(s) would you reccomend? In Firefox think I was using Times New Roman on my old Vista Laptop which was perfectly fine, but the same on Ubuntu just isn't working for me.

---

### Post by buzzingrobot on 2013-07-18
I use either the default Sans face or Liberation Sans, Liberation Serif, and Liberation Mono, setting the default proportional font in Firefox to Liberation Sans. Note that I do not force Firefox to override the font specs in a site's CSS, so specifying LIberation probably has little direct impact because very few designers are going to specify Liberation in their designs.

However, they will always add "Sans" as a sans-serif fallback, and Arial is specified very, very widely. (You will often see font specs in the CSS like "Helvetica, Arial, Sans-serif".   Helvetica will be used on Macs, Arial on Windows, and Sans elsewhere.  Liberation is an open source font intended to mimic Arial well on Linux. Here, Arial is mapped to Liberation, so the latter is used when CSS calls for Arial.

The default Sans font here is Dejavu Sans, mapped via fontconfig. Run "fc-match sans" in a terminal to see what's used for Sans on your machine. I don't use Windows fonts on Linux.

---

### Post by silconsystem on 2013-07-18
Hi, shame to hear that no suggestions have cured ur fox yet. Maybe you have to experiment a bit with your display resolution. a 13.3 inch screen is quite small maybe the browsers have some problems fitting it all on your screen.
Did u run Vista on this same laptop or is this a different one? Do other browser have the same issues? If all browsers have the same issues the problem must be somewhere else and not with the browser itself.
Maybe u could try a live cd with an older version of Ubuntu or a different Linux OS and see how your laptop renders things there. It could be that ur hardware is missing some drivers or something along these lines.

---

### Post by nerdtron on 2013-07-19
> **JK700 said:**
> The trouble with increasing font size or zooming in too much messes up pages where there are images - the text goes all over the place and really makes websites look messy

And yes I tried NoSquint yesterday but that didn't seem to help much. I'm really confused as to how best proceed from here.

Which specific font(s) would you reccomend? In Firefox think I was using Times New Roman on my old Vista Laptop which was perfectly fine, but the same on Ubuntu just isn't working for me.

I'm using DejaVu Sans size 14.
I think the key here is not the font, but the size. The default size of 16 is too big.

---

### Post by JK700 on 2013-07-19
> **buzzingrobot said:**
> The default Sans font here is Dejavu Sans, mapped via fontconfig. Run "fc-match sans" in a terminal to see what's used for Sans on your machine. I don't use Windows fonts on Linux.

This is what it said...

[B]DejaVuSans.ttf: "DejaVu Sans" "Book"


[/B]Yes, it was my previous laptop (Vista) where it had the exact same font as I used on Ubuntu which was fine. This laptop I am using I have never been able to get it quite right.

I keep playing around changing fonts but no luck as of yet.

---

### Post by buzzingrobot on 2013-07-19
> **JK700 said:**
> 

I keep playing around changing fonts but no luck as of yet.

Adjusting size or changing fonts won't change the overall rendering style of the display. You'll need to adjust antialiasing, hinting, hintstyle, etc.  By default, Ubuntu is optimzed for LCD screens, but perhaps that doesn't work well with your hardware.

Long shot: If the laptop has a sharpness control, play with that. Makes a very big difference on my desktop.

---

### Post by JK700 on 2013-07-19
> **buzzingrobot said:**
> Adjusting size or changing fonts won't change the overall rendering style of the display. You'll need to adjust antialiasing, hinting, hintstyle, etc.  By default, Ubuntu is optimzed for LCD screens, but perhaps that doesn't work well with your hardware.

Long shot: If the laptop has a sharpness control, play with that. Makes a very big difference on my desktop.

Thanks. I'll try and find a sharpness control option.

I've been using "Unity Tweak Control" to play around with rendering etc but haven't been successful yet and more times than not it actually makes it worse.

---

### Post by JK700 on 2013-07-19
Sorry to double-post (if that's not allowed?) but I didn't want to start a new topic for this. I have found from an internet search and old response to the font problem thing...

> What I think really helped out my font smoothness was from adjusting the dpi.

  First, open a terminal and type:
  
xdpyinfo | grep resolution   It'll give you a number like "96x96".
  Now go to the Fonts tab in the Appearance settings. Click the details  button in the bottom right corner. At the top of this new window it has a place to put a number. Put the  first number that terminal command gave you. For example, it gave me  "108x106" so I put 108 there.
  Doing this will get you closer to those smooth fonts you're looking for.
 


When I did it, mine came up with 
**"resolution:    119x121 dots per inch "**

The problem is I don't have a Fonts Tab in my Appearance settings, so I can't follow those instructons. How could I do it instead, to see if it helps?

And is 119x121 dots per inch reasonable for my screen size? (13"5)

Thanks

---

### Post by buzzingrobot on 2013-07-19
This thread ([http://crunchbang.org/forums/viewtopic.php?id=5617](http://crunchbang.org/forums/viewtopic.php?id=5617)) at the excellent Crunchbang forums might help with that dpi issue.

You will see many examples referring to a dpi of 96, which is more or less a standard for a lot of hardware, but it's best to set it at a screen's actual number (what you got from xpdyinfo).

---

### Post by JK700 on 2013-07-20
> **buzzingrobot said:**
> This thread ([http://crunchbang.org/forums/viewtopic.php?id=5617](http://crunchbang.org/forums/viewtopic.php?id=5617)) at the excellent Crunchbang forums might help with that dpi issue.

You will see many examples referring to a dpi of 96, which is more or less a standard for a lot of hardware, but it's best to set it at a screen's actual number (what you got from xpdyinfo).

Thankyou very much, but I don't know how to "create a ~/.Xdefaults file" ? (as instructed)


I did decide to put **"Xft.dpi: 119**" in the terminal anyway, but it came up "command not found"

---

### Post by buzzingrobot on 2013-07-20
You need to create the file in a text editor, say, gedit or nano. Give it that name.  Save it in your home directory. (For example, if your home directory is named "jk700", then save it in /home/jk700.)  The "~" is shorthand for that directory. Preceding the filename with a period means it will be "hidden", i.e., by default not displayed in a listing of files in that directory.  That's a Unix/Linux convention. File managers have an option to show hidden files, and an "ls -a" in a terminal will, also.

Then, logout and back in, or reboot.  It's essentially a configuration file that will be read every time you log in, adjusting the dpi setting.

---

### Post by JK700 on 2013-07-20
Thanks. I did it, but unfortunately after a reboot it hasn't had the desired effect and I've noticed very little change to be honest with you.

It's really infuriating because I can read documents perfectly well on this laptop, it's just when on web pages. (Both Firefox & Chrome) it just looks horendous and sometimes difficult to read. I think I just need to find some firefox extension that can render/smooth fonts?

---

### Post by silconsystem on 2013-07-20
I've looked around at google and found that there are some people having similar issues as you with specific hardware combinations.
Ubuntu 13.04 should have fixed most of these bugs but maybe you have just this one laptop that does make some problems.
Also maybe you just have to get used to some minor differences in MS Windows and Ubuntu, the screens you posted dont look that bad, but anyway you said that they look much worse when u see em real-life, maybe make some screenshots with a cam or mobile for comparison?

As for fonts, this is just up to taste I like Verdana for webpages and blogs I want other people to read but my on my own system use all kinds of sci-fi fonts since you can customize everything you  can imagine on Ubuntu and thats just why its superior to MS Windows and worth the stretch to learn how to use Linux.


Check in if u can still not find a solution, there's always is a solution !!


Cheers,


rob

---

### Post by buzzingrobot on 2013-07-20
Did you confirm with xpdyinfo that the dpi changed?

Changing DPI, altering hinting settings,  etc., should have obvious and easily visible impacts on how fonts are rendered. 

For example, my monitor's actual DPI is 94.  When I change the default 96 (which is what most hardware actually is) to 94, even that tiny change is evident. Flipping sub-pixel rendering on and off has a dramatic affect.

So, if you aren't seeing changes on your hardware, something else is probably going on.

[When I look at the raw image of the second pic you posted, that, to me, looks like typical Ubuntu font rendering and font smoothing.  Out of the box, fonts in Ubuntu will not render as in Windows, which doesn't do as much smoothing, even if you use Windows fonts.  When I look at someone else's Windows' screen, I often see spidery fonts with the individual pixels just on the edge of visibility.  They like that, I don't.]

---

### Post by JK700 on 2013-07-20
Hi. Yes I do notice slight subtle changes sometimes when I play around with that stuff but it's no where near what I would like it to be.

I just think it's probably mainly down to me **a.)** not being used to such a small screen (13.5") and** b.)** not being used to Ubuntu/Linux

Some websites are better than others but in the main I find it dreadful to read, and I think I am going to save up for a Windows Laptop with a bigger screen because I'm not sure how much longer I can tolerate this.

Thanks for all your replies/help though

---

### Post by silconsystem on 2013-07-20
Dont give up Linux just yet, maybe u should just try some other Linux distro's or maybe an older Ubuntu works for you.
I'm sure you have an usb stick or some empty disk lying around somewhere, just go here: [http://distrowatch.com/](http://distrowatch.com/) and see if theres anything to your liking.
I use Kubuntu on my faster PC, its a has a bit more eye-candy. Lubuntu is great for shear speed. Fedoras new distro is really amazing and beatifull too for a super stable Linux try Debian, etc...
There's so many flavours of Linux and once you learn one distro you'll find your way around all the others aswell.
The pro's from Linux are that its very customizable and very stable too, MS Windows has not changed all that much over the years and when it breaks, it breaks leaving you in the dark about whats really going on behind the screens.
I've rescued my Linux boxes from situations that I though (especially in the beginning) were death for my OS and files, wrong ! Always managed to get it going again, thanks to the console and to this amazing Linux community thats always ready to help you and have mostly years of experience.

I have not used MS Windows ever again since I changed to Linux and everything I used Windows for I could either run in Wine or replace by a another (free) program, that on top of that I could customize however I liked.
Not to mention the secure boot scheme Windows 8 uses to keep Linux away from machines that there OS is on. I cant support a company who is trying to monopolize their software. (and apple selling u a tweaked linux OS, like they re-invented the wheel for big bucks).


Once you start understanding how much control you have over your computer you wont go back to Bill 4 sure.
AlsoI understand that running Linux distros on a laptop can sometimes have some difficulties, the major distributions mostly have special .iso's for laptops and netbooks if you go on their websites.


Hope you dont give up too soon, good luck !! It can be very frustrating at times if you dont get results quickly but a bit of effort always pays off in the end...


Cheers,


Rob

---

### Post by elundmark on 2013-10-07
I wrote up a how-to for Times new Roman, and fixing fonts in general for browsers in Ubuntu, I hope it helps.
[http://ubuntuforums.org/showthread.php?t=2178674](http://ubuntuforums.org/showthread.php?t=2178674)

---

