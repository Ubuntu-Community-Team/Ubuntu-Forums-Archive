---
title: "HOWTO: Rockin fonts in Gnome.."
date: 2005-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2005-04-01
Ok.. My biggest issue is fonts in Linux. However by gathering some tools and random bits from around the Internet I got the following :)..

[img]http://download.ubuntuforums.org/howtos/fonts/image1.png[/img]

[img]http://download.ubuntuforums.org/howtos/fonts/image2.png[/img]
On to the Installation..

 >  1. Enable Universe in your sources.list
2. Install the msttcorefonts package
3. cd /usr/share/fonts/truetype/msttcorefonts
sudo wget [http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz]("http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz")
    sudo tar xvzf miscfonts.tar.gz
    sudo rm -f miscfonts.tar.gz
4. Goto System > Preferences > Fonts 
Below are the screenshots of my settings.
[img]http://download.ubuntuforums.org/howtos/fonts/image3.png[/img]

Click the Details Button.
[img]http://download.ubuntuforums.org/howtos/fonts/image4.png[/img]

5. Open a terminal window and enter sudo nano /etc/fonts/local.conf

And enter the following right above </fontconfig>
 [QUOTE]   <match target="pattern">
            <test qual="any" name="family">
                    <string>Bitstream Vera Sans
            </test>
            <edit name="family" mode="assign">
                    <string>Verdana
            </edit>
    </match>
    <match target="pattern">
            <test qual="any" name="family">
                    <string>Helvetica
            </test>
            <edit name="family" mode="assign">
                    <string>Arial
            </edit>
    </match>
    <match target="pattern">
            <test qual="any" name="family">
                    <string>Palatino
            </test>
            <edit name="family" mode="assign">
                    <string>Georgia
            </edit>
    </match>
You can view my local.conf file here:
[http://download.ubuntuforums.org/howtos/fonts/local.conf]("http://download.ubuntuforums.org/howtos/fonts/local.conf")

6. Tweaking Open Office.

Fire up Open Office Word Processor. Goto Tools > Options then select "view" (see screenshot)
[img]http://download.ubuntuforums.org/howtos/fonts/ooview.png[/img]
Under "Screen font Aliasing" change that number to "12" and click ok.

You make need to log out of gnome or reboot to get your fonts to reset. :) I hope this works for you as it did me. 

Enjoy :)

---

### Post by gw90se on 2005-04-01
Thanks!! Worked great and looks better. I was going to dig into fonts for use with NVU.

I did use Synaptic to install msttcorefonts, so when I was doing the...
>  wget [http://download.ubuntuforums.org/ub...iscfonts.tar.gz](http://download.ubuntuforums.org/ub...iscfonts.tar.gz)
tar xvzf miscfonts.tar.gz
rm -f miscfonts.tar.gz 
I had to use sudo (just a note for some of us noobs.) :lol:

---

### Post by Buffalo Soldier on 2005-04-01
I'm surprised that some (if not many) people prefer setting **smoothing: none**. I guess that's what they're used to in Windows. Anyway, to each his own. And I'm happy you've manage something that works for you :) Power to Ubuntu. Power to the people.

p/s: Sorry about the shout out. Getting psyc about Ubuntu climbing #1 on [DistroWatch.com](http://distrowatch.com/)

---

### Post by mark on 2005-04-01
[QUOTE=Buffalo Soldier]I'm surprised that some (if not many) people prefer setting **smoothing: none**. I guess that's what they're used to in Windows. Anyway, to each his own. And I'm happy you've manage something that works for you :) Power to Ubuntu. Power to the people.

p/s: Sorry about the shout out. Getting psyc about Ubuntu climbing #1 on [DistroWatch.com](http://distrowatch.com/)[/QUOTE]
I've also been watching Ubuntu work it's way up the DistroWatch ladder (*yes*) - and I'm grateful for the font tips.  My eyesight ain't that good, so I tend to accept whatever's on offer ("eh, it must be fine for other folks...").  Thanks, u-g!

Mark

---

### Post by armar on 2005-04-02
Thanks for the post. I don't like the smoothing at all. IMO the smoothing is too soft/fuzzy for me. When I switch to XP(for windows only apps), the font's are nice and crisp. Great post!

---

### Post by doans on 2005-04-02
I had the smoothing on for awhile, but honestly I thought it looked horrible!  Is this just because I am used to no smoothing?  Is it really supposed to look better with smoothing on??  Just a question that has always bugged me with Linux.

---

### Post by basse1989 on 2005-04-02
The smoothing is a **FEATURE**.

---

### Post by occy8 on 2005-04-02
I selected in font rendering best contrast or best shapes instead of monochrome. The fonts look much sharper and have better contrast

---

### Post by seven on 2005-04-02
works great 10x :)
i prefer using Arial font for everything. i realy like it, much more than thoma

---

### Post by donar73 on 2005-04-02
[QUOTE=occy8]I selected in font rendering best contrast or best shapes instead of monochrome. The fonts look much sharper and have better contrast[/QUOTE]

Have you tried it with the Bytecode-Interpreter enabled instead of using the default Autohinting? (via "sudo dpkg-reconfigure fontconfig")

Btw, there is another nice (and a bit more detailed) HowTo here: [http://www.ubuntuforums.org/showthread.php?t=20976&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=20976&page=1&pp=10)

---

### Post by Nano on 2005-04-02
Let me show you how it fonts look in my laptop:
I think there's nothing like Tahoma for system font...

[http://iamfuckedup.com/tmp/Pantallazo.png](http://iamfuckedup.com/tmp/Pantallazo.png)

I just edited /etc/fonts/local.conf ;)

---

### Post by j_baer on 2005-04-02
Ubuntu-geek,

Nice how-to. I pretty much traveled the same road to get my fonts where I like them. The one thing I did notice is screen resolution seems to play a part of all of this. The fonts I choose on my 1280x1024 system are different than those on my 1024x768 system.

Thanks ...

---

### Post by Michael on 2005-04-02
Dunno, making my linux distro look more like windows makes me feel a bit dirty, but maybe it's just me :p

---

### Post by ubuntu-geek on 2005-04-02
The reason for this howto is because I personally find the "smooth" font feature hard on the eyes and dirty. If I can have clean fonts in linux and still be in linux then I am happy. :)

---

### Post by Buffalo Soldier on 2005-04-02
I think smoothing only works in high resolution. Running it in lower resolution could be the cause of the fonts looking blurry.

---

### Post by J. S. Jackson on 2005-04-02
[QUOTE=Michael]Dunno, making my linux distro look more like windows makes me feel a bit dirty, but maybe it's just me :p[/QUOTE]

I think it was generous of MS to (sort of) release these.  Some of these fonts have no peer.  They are widely regarded as simply the best fonts in the world for displaying text on a computer screen.

Don't feel badly just because MS paid for them, and owns them.  They are still a great work of art by the world's top type designers and hinting experts.

Using your reasoning, you should also feel dirty if you like a Beatles/Elvis song that Michael Jackson owns?   :mrgreen:

---

### Post by Psquared on 2005-04-02
Thanks for the "how-to." That and a little tweaking on my own has gotten rid of the faded look some of my fonts were showing. I don't know if that was "smoothing" or just the fonts I was using, but they do look better now.  =D>

---

### Post by paretooptimum on 2005-04-02
Isn't the most obvious question "What sort of monitor are you using? CRT or LCD?" Doesn't the answer (IMHO) depend on this?l

I'm running subpixel smoothing/full with the standard fonts and think it looks fine 

Remember: "de gustibus non disputandum est" (There is no disputing taste)

---

### Post by ubuntu-geek on 2005-04-02
I have:
[http://www.viewsonic.com/products/desktopdisplays/lcddisplays/xseries/vx910/index.htm](http://www.viewsonic.com/products/desktopdisplays/lcddisplays/xseries/vx910/index.htm)
and
[http://www.necdisplay.com/products/ProductDetail.cfm?Product=305&ClassificationFamily=2&Classification=1](http://www.necdisplay.com/products/ProductDetail.cfm?Product=305&ClassificationFamily=2&Classification=1)

Both are running at 1280x1024.. I perfer my fonts look like the ones in the howto.. Like I mentioned I do not like the "Smooth" look.

---

### Post by unkwn on 2005-04-03
looks like shit with "Font Rendering" set to "monochrome"; anyone who doesn't like jaggies on their type should set it to "Best Shapes".

---

### Post by Buffalo Soldier on 2005-04-03
[QUOTE=doans]I had the smoothing on for awhile, but honestly I thought it looked horrible!  Is this just because I am used to no smoothing?  Is it really supposed to look better with smoothing on??  Just a question that has always bugged me with Linux.[/QUOTE]
I'm guessing it's down to individual preferences. As they said "beauty is in the eye of the beholder". Or it could be the case that different settings for different hardware. Here's how I set up my fonts with smoothing.

---

### Post by CowPie on 2005-04-08
How do we install the misc. fonts like tahoma?

---

### Post by super on 2005-04-08
this may sound like a stupid question but how do you change the fonts/themes in xmms, mplayer, etc... I don't mean the skins. I'm talking about the the fonts/themes on the menus of these programs. Like when you left-click on xmms.

---

### Post by angrykeyboarder on 2005-04-08
[QUOTE=Buffalo Soldier]I'm surprised that some (if not many) people prefer setting **smoothing: none**. I guess that's what they're used to in Windows. Anyway, to each his own.[/QUOTE]
Uhhh you must not have been on a Windows box in years. Font smoothing became a permanant fixture on Windows as of Windows 98 (and later).....

[http://www.microsoft.com/typography/SmoothFonts.mspx]("http://www.microsoft.com/typography/SmoothFonts.mspx")

---

### Post by Julius on 2005-04-09
In windows you have two ways of antialiasing:
- regular antialiasing (that disables AA for fonts under a certain size)
- cleartype

I guess cleartype is similar to hinting, but I'm not sure, since I never used cleartype on my computer, just for some minutes. Fonts look cool with cleartype, more spaced or something.

This HOWTO shows that there are many ways to have windows-like fonts :P I just disable antialiasing for small sizes in my .fonts.conf and voila.. just the same as windows (with tahoma 8, of course).

And yes, I agree tahome 8 is one of the best fonts out there :P I'm used to it and looks very professional.

---

### Post by CowPie on 2005-04-10
I have a question, how to get the menu to be tahoma?  It stays bitstream even when  I changed all hte fonts in the Fonts panel to tahoma.

EDIT:  OK i =figured it out, I installed that kde-gtk-engine (sp) package and it made the file .gtkrc-2.0-mine, so I moved it and all was well.

---

### Post by kuleali on 2005-04-12
Thank's. Nice fonts

---

### Post by Paool on 2005-04-21
sorry, where i can download miscfonts.tar.gz? because link doesn't work...

---

### Post by nickless on 2005-04-21
[http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz](http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz) seems to be down :)

---

### Post by plb on 2005-04-21
Save this in a file called ~/.fonts.conf and see if it improves anything for you guys....BTW I have a LCD monitor thus subpixel is uncommented...adjust accordingly  :) 

*****************snip****************

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts.conf file to configure system font access --><fontconfig>
<!--  Enable sub-pixel rendering -->
         <match target="font">
                 <test qual="all" name="rgba">
                         <const>unknown</const>
                 </test>
                 <edit name="rgba" mode="assign"><const>rgb</const></edit>
         </match>

<!-- Autohint fonts -->
         <match target="font">
                 <edit name="autohint" mode="assign"><bool>true</bool> </edit>
         </match>
<!-- Antialias --> <match target="font" >
  <test compare="more" name="size" qual="any" >
   <double>8</double>
  </test>
  <test compare="less" name="size" qual="any" >
   <double>15</double>
  </test>
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
</fontconfig>

***********snip*****************

Enjoy  O:)

---

### Post by tlepes on 2005-04-21
**MISSING FILES!!!**

```
tlepes@alembic:/usr/share/fonts/truetype/msttcorefonts $ sudo wget http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz
--08:59:22--  http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz
           => `miscfonts.tar.gz'
Resolving download.ubuntuforums.org... 66.246.118.208
Connecting to download.ubuntuforums.org[66.246.118.208]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:59:22 ERROR 404: Not Found.
```

Likewise...
[QUOTE=ubntu_geek]You can view my local.conf file here:
[http://download.ubuntuforums.org/ho...onts/local.conf](http://download.ubuntuforums.org/ho...onts/local.conf)[/QUOTE]
...is a no-go.

---

### Post by RastaMahata on 2005-04-21
[QUOTE=tlepes]**MISSING FILES!!!**

```
tlepes@alembic:/usr/share/fonts/truetype/msttcorefonts $ sudo wget http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz
--08:59:22--  http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz
           => `miscfonts.tar.gz'
Resolving download.ubuntuforums.org... 66.246.118.208
Connecting to download.ubuntuforums.org[66.246.118.208]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:59:22 ERROR 404: Not Found.
```

Likewise...

...is a no-go.[/QUOTE]
 fix please :(

---

### Post by plb on 2005-04-22
you can download corefonts from sourceforge guys =)

[http://corefonts.sourceforge.net/](http://corefonts.sourceforge.net/)

just follow the instructions on how to install them if you don't know how  :wink:

---

### Post by das on 2005-04-24
Hello
Did eveything like discribed, but wasn't able to select tahoma. The font wasn't recognized by my system. I can find it in the msttcorefonts-folder but I can't chose it in the font preferences.

Can anybody help me to solve this problem?

---

### Post by Poul on 2005-05-24
I don't get the whole deal with changing fonts to look like in windows. For me default fonts are great: casual , antialiased , smooth- what else can i wanrt . I think that they look much better.

---

### Post by humina on 2005-05-27
I agree.  I don't want to get Microsoft fonts on my computer.  What I would like to know is how I can get ariel fonts to display in firefox.  When viewing pages in firefox with ariel, they don't show up as anything different.  Usually when a font is defined in a webpage, there are a list of fonts to be used.  If a webpage has Ariel set as a font, that font is skipped.  Is there some way to bind ariel to a specific font in my /etc/fonts/local.conf ?  Thanks

---

### Post by pdk001 on 2005-05-27
yea im same with you, i dont want to get M$ anythings either even though im using M$ sometime

---

### Post by Curlydave on 2005-06-15
Great tutorial! IT fixed my fonts!!! Score.

edit: except in Firefox. Any fixes? Thanks! I set them to Tahoma.

---

### Post by moment on 2005-06-15
My Python programs (for example bittornado) don't seem to follow the global fonts of my Gnome. They are still the same fonts as they were before. I presume there must be config file somewhere that sets them. Any idea?

---

### Post by mulperi on 2005-06-16
As you said, this rocks!

Note: I remember adding a <string>Verdana**[COLOR=DarkRed]</string>[/COLOR]**  on each font in /etc/fonts/local.conf to get this to work as expected. Dunno if this is needed..

Does anyone have a clue how to change the big ugly default "menu font" in many programs (xmms, xine...) to tahoma 8?

Mulperi

---

### Post by yucao89 on 2005-08-17
Can you do that in KDE? Cause some of the information in this howto is mostly adapted to GNOME.

---

### Post by ubuntufans on 2005-11-17
Can this be done on breezy? i tried it doesnt work

---

