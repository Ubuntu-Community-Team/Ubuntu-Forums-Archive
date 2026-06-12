---
title: "HOWTO:Beep-Media-Player Docklet"
date: 2005-12-01
forum: Outdated Tutorials &amp; Tips
---

### Post by cdhotfire on 2005-12-01
----------------------------------------------
New Version, with different icon.
----------------------------------------------

[img]http://img306.imageshack.us/img306/1556/screen6ud.png[/img]

This is how to get a dockable bmp.:)

Start off by downloading this:
[http://www.drunkenpirate.5gigs.com/uploads/bmp-docklet_1.3-1_i386.deb.tar.bz2](http://www.drunkenpirate.5gigs.com/uploads/bmp-docklet_1.3-1_i386.deb.tar.bz2)

To install:
1. Put tar.bz2 package in home folder
2. Extract it, in home folder, Right Click->Extract Here
2. Open up Terminal, Applications -> Accessories -> Terminal
3. Type in:
    $sudo dpkg -i bmp-docklet_1.3-1_i386.deb
4. If everything goes well, then its installed.

If bmp running:
1. Restart
2. Go to Right Click -> Preferences
3. Plugins -> General
4. Mark Docklet Plugin
5. Your set to go

If not currently running just do 2-5, and its up it will be all good. :)

------------------------------------------------------
If you want a different icon
------------------------------------------------------
Download this:
[http://www.drunkenpirate.5gigs.com/uploads/bmp-docklet-1.3-icon.tar.bz2](http://www.drunkenpirate.5gigs.com/uploads/bmp-docklet-1.3-icon.tar.bz2)

Get you icon, open up Gimp and reduce it to 24x24 using Cubic interpolation, which is best.  Then save it as an xpm, naming it bmp_player.xpm. *Do not save as xpm and then reduce size, it will lower the quality very much*.
Then place the icon in the "bmp-docklet-1.3/src/" folder, and replace the old one.

Then you can compile it yourself:
1. Extract Here
2. Open Terminal
3. "cd bmp-docklet-1.3"
4. "./configure"
5.  apt-get any dependencies you dont have
6. "make"
7. "sudo make install"
Now its installed, and your good to go.

*OR*

You can make a .deb which is better, IMO.

First
```

$ sudo apt-get install build-essential dh-make fakeroot

```

Second, unpack the source and cd to folder
```

$ cd bmp-docklet-1.3

```

Third, run dh-make
```

$ dh_make

```
What one usually compiles are single binarys, so press "s" then "enter" when it asks you.

Fourth
```

$ fakeroot debian/rules binary

```

If it encounters any errors during the configuration, it should tell you what to install. 

After its done it should make a "deb" on .. so do
```

$ sudo dpkg -i ../bmp-docklet_1.3-1_i386.deb.deb

```
To install.

Okay thats about it.

Thanks to Drunken Pirate, for his hosting site. :)

---

### Post by ruffneck on 2005-12-01
thanks man. But what do we do with the downloaded file? apt-get install it ?

---

### Post by cdhotfire on 2005-12-01
[quote=ruffneck]thanks man. But what do we do with the downloaded file? apt-get install it ?[/quote]

Ooops.:(

Ill edit

---

### Post by bionnaki on 2005-12-02
does this still have the bug where if you have visualizations going *and* change the size of the playlist...and then try to dock bmp, it'll crash?

I have beep-media-player-docklet_1.3-1_i386 installed & this bug is still present....is it present in your 1.2?

---

### Post by cdhotfire on 2005-12-02
[quote=bionnaki]does this still have the bug where if you have visualizations going *and* change the size of the playlist...and then try to dock bmp, it'll crash?

I have beep-media-player-docklet_1.3-1_i386 installed & this bug is still present....is it present in your 1.2?[/quote]

My visualizations appear in a different window, so when I dock bmp it only docks bmp not the visualizations, but no it does not crash.;)

---

### Post by bored2k on 2005-12-02
[bmp-docklet-1.3_1.3-1_i386]("http://rapidshare.de/files/8487497/bmp-docklet-1.3_1.3-1_i386.deb.html")

---

### Post by cdhotfire on 2005-12-02
[quote=bored2k][bmp-docklet-1.3_1.3-1_i386]("http://rapidshare.de/files/8487497/bmp-docklet-1.3_1.3-1_i386.deb.html")[/quote]

:cool: thanks.

---

### Post by christooss on 2005-12-02
Maybe you can all try [BMPX]("http://beep-media-player.org/index.php/BMPx_Homepage") :) It has "dockable" inscluded.

Its in serios development but you have many nice futures included. I find multiple plalist most useful.

Sorry if this is offtopic

---

### Post by cdhotfire on 2005-12-02
[quote=christooss]Maybe you can all try [BMPX]("http://beep-media-player.org/index.php/BMPx_Homepage") :) It has "dockable" inscluded.

Its in serios development but you have many nice futures included. I find multiple plalist most useful.

Sorry if this is offtopic[/quote]

My post has been hijacked.:???:

But, ya thats a better choice.:rolleyes:

Has a nice internet radio finder.:cool:

---

### Post by bionnaki on 2005-12-03
[QUOTE=cdhotfire]My visualizations appear in a different window, so when I dock bmp it only docks bmp not the visualizations, but no it does not crash.;)[/QUOTE]

how do you do this?

---

### Post by cdhotfire on 2005-12-03
[quote=bionnaki]how do you do this?[/quote]

Maybe it depens on the one your using, I was using the blur scope one, it came with bmp.;)

---

### Post by bionnaki on 2005-12-03
oh...well. I dont plan on using that.

just thought I'd let you guys know of the bug that exists if you use the visualizations in the main player + the docklet + changing the size of the playlist.

---

### Post by cutOff on 2005-12-03
[QUOTE=christooss]Maybe you can all try [BMPX]("http://beep-media-player.org/index.php/BMPx_Homepage") :) It has "dockable" inscluded.

Its in serios development but you have many nice futures included. I find multiple plalist most useful.

Sorry if this is offtopic[/QUOTE]
Thanks for that info. I'll give it a try.

---

### Post by cdhotfire on 2005-12-03
Btw, anyone who wants to try bmpx, I dont really recommend it yet, as it is very buggy now.:rolleyes:

---

### Post by christooss on 2005-12-03
With 0.12.9 version application crash hasn't happened.

But like I sad application is in development. But if you are a reasearcher you will love bmpx :)

---

### Post by Cosu on 2005-12-07
Can anyone help me with the desklet package for beep media player? The links posted above seem not to work anymore :(
TIA

---

### Post by Greeface on 2005-12-12
Yeah, for me it crashes when I use visualizations also :(

---

### Post by bionnaki on 2005-12-12
see, I knew I wasnt crazy :p

---

### Post by Nano on 2005-12-12
Indeed, bmpx is becoming a serious choice. Although it's still in heavy development, I'm trying to use it as much as I can since the concept I believe is really good.
The music library really rocks.

---

### Post by ashrack on 2006-03-02
anyway to have a different color BMP docklet? Since the current orange is just disquisting. I was thinging something more the line of BLUE..

---

### Post by christooss on 2006-03-03
Change BMP icon to BLUE

---

### Post by graabein on 2006-03-03
Excuse me for asking but what is a docklet? The box thingies they have in Window Maker? Or something more general like an icon in the notification area? Can someone please post a screenshot of the bmp docklet in action?

---

### Post by ashrack on 2006-03-03
[QUOTE=christooss]Change BMP icon to BLUE[/QUOTE]
Where, I could't find it anywhere??

---

### Post by christooss on 2006-03-03
[[img]http://www2.shrani.si/pics/screenshdlfmhr_thumb.png[/img]](http://www2.shrani.si/pics/screenshdlfmhr.png)

Ashrack: probably in /usr/share/bmp

---

### Post by cdhotfire on 2006-03-03
To change icon, you will have to re-compile it.
[http://mark.xnull.de/bmp-docklet/bmp-docklet-1.3.tar.bz2](http://mark.xnull.de/bmp-docklet/bmp-docklet-1.3.tar.bz2)

Thats the source, extract and go to bmp-docklet-1.3/src/, and there should be a icon called bmp_player.xpm, just put in a diff icon and name it bmp_player.xpm, but make sure the icon is in xpm format (use gimp) and just in case same size, 48x48.

Good Luck.

If you'd like you can give me icon and ill recompile for you. :D

---

### Post by ashrack on 2006-03-05
[QUOTE=cdhotfire]To change icon, you will have to re-compile it.
[http://mark.xnull.de/bmp-docklet/bmp-docklet-1.3.tar.bz2](http://mark.xnull.de/bmp-docklet/bmp-docklet-1.3.tar.bz2)

Thats the source, extract and go to bmp-docklet-1.3/src/, and there should be a icon called bmp_player.xpm, just put in a diff icon and name it bmp_player.xpm, but make sure the icon is in xpm format (use gimp) and just in case same size, 48x48.

Good Luck.

If you'd like you can give me icon and ill recompile for you. :D[/QUOTE]
sweet.will go compiling now.....

---

### Post by ashrack on 2006-03-07
it wont work.
I resized the ICON to 48x48 and saved is as XPM. But then 'make' errors out.
Heres a brief output of make
```
docklet.c: In function 'docklet_plugin_init':
docklet.c:134: error: 'bmp_player_icon' undeclared (first use in this function)
docklet.c:134: error: (Each undeclared identifier is reported only once
docklet.c:134: error: for each function it appears in.)
make[2]: *** [docklet.lo] Error 1
make[2]: Leaving directory `/home/tom/src/bmp-docklet-1.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/src/bmp-docklet-1.3'
make: *** [all] Error 2
tom@wraith:~/src/bmp-docklet-1.3$

```
ps. I even tried opening the original XPM icon and then just resaving it, but it will still crap out.
ps2.needless to say but with the ugly original icon MAKE finishes

---

### Post by cdhotfire on 2006-03-07
Okay, after 10 mins, I finally got it. You can change the icon if you dont like the one I put in.  Everything makes fine here. :)

[http://rapidshare.de/files/14918747/bmp-dockle-1.3-icon.tar.bz2.html](http://rapidshare.de/files/14918747/bmp-dockle-1.3-icon.tar.bz2.html)

You can get it there.

If you'd like to make a .deb, follow these steps, onless you already know.
[quote=cdhotfire]
First
Code:

$ sudo apt-get install build-essential dh-make fakeroot


Second, unpack the source and cd to folder
Code:

$ cd folder


Third, run dh-make
Code:

$ dh_make

What one usually compiles are single binarys, so press "s" then "enter" when it asks you.

Fourth
Code:

$ fakeroot debian/rules binary


If it encounters any errors during the configuration, it should tell you what to install.

After its done it should make a "deb" on .. so do
Code:

$ sudo dpkg -i ../package.deb

To install.

Good luck.
[/quote]

---

### Post by ashrack on 2006-03-08
CDHOTFIRE
Now that approach is definetly different. I will try it when I get home.

I do compiling like this:
```

./configure
make  --> here it errors out with BMP DOCKLET
sudo checkinstall --pakdir=../

```
Is your approach better and/or why?

---

### Post by cdhotfire on 2006-03-08
No, I do the same, make gives me no errors, Ill have to check when I get back.  But it works fine for me, maybe post the ./configuration here, so I can compare it to mine.

Edit: That aprproach builds a deb, but it goes throught the ./configure, make, process. So if make gives out an error then it wont work.  Like I said dl the new one I edited, in the previous post, and try to make.  I did try to make it again and it came out all good. But if you cannot get it to work, let me know, send me you xpm, and I will make a deb for you. :)

---

### Post by cdhotfire on 2006-03-08
Okay, after a bit of more work, I have found for perfect panel intergration.  The old one was a bit blurry.

[http://rapidshare.de/files/15027505/bmp-docklet-1.3-icon.tar.bz2.html](http://rapidshare.de/files/15027505/bmp-docklet-1.3-icon.tar.bz2.html)

Download there.

The icon is in the "src" folder, change it if you dont like it. But this time make the image 24x24 then convert to xpm, if you conver to xpm then reduce size it will lose alot of quality.

This will give best outcome if your is at 24 pixel height.
If you want a .deb(recommended) follow the steps posted previously.
Screenshot:
[img]http://img306.imageshack.us/img306/1556/screen6ud.png[/img]

Edit: Updated first post.

---

### Post by hamil on 2006-05-07
Sorry to bump this thread...

I have built a deb of BMPx 0.14.4
But, there is something that I miss...
How do I make it to automatically add a starter to: Applications --> Sound & Video??? Without any user interference??

Thank you for any guidance, or help in the right direction!

EDIT:
Sorry.... It was there... Just had to update.. :(
Thanx anyway!

---

