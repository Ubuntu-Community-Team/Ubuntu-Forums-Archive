---
title: "Make WINE Apps Look Better"
date: 2006-03-11
forum: Outdated Tutorials &amp; Tips
---

### Post by quandar on 2006-03-11
**[SIZE="3"]How to Make WINE Apps Look Better[/SIZE]**
*[SIZE="1"]By Dan "quandar" Rise[/SIZE]*

[IMG]http://gui.deletefactory.net/ubuntu/wine1.png[/IMG]

**_Introduction_:**
Well, we all know if you leave WINE at its general configuration it is quite ugly, and if you use the .msstyle option in *winecfg* it makes everything slow, and its buggy at best. This guide is not set out to perfectly replicate your GTK theme, but hopefully make it blend.
First this guide will assume you have a fully functioning WINE setup. If you have that then lets get on with it, pick these apps (that we will use WINE to run) up.

**_Apps You Will Need_:**
[LIST]
[*][Jasmin 3D Color Changer 4]("http://jote.pai.net.pl/jn/3dcc/files/3dcc4-en.zip")
[*][DisplaySet]("http://wittswallpapers.com/Oldies/displayset.zip")
[/LIST]

**_Install Your Apps_:**
This step is fairly simple enough, unzip both of those ZIPs to folders and run the Setup.exe on both of them. Basicaly press agree, next, next, you know, Windows style *wink*.

**_DisplaySet / Fonts_:**
Open Nautilus, and press CTRL+L and type ~/.wine and go from your root windows folder (on mine it is "drive_c") and Program Files > DisplaySet, and open DisplaySet.exe. And switch all your font settings to your fonts in you System > Preferences > Font menu.

[IMG]http://gui.deletefactory.net/ubuntu/wine2.png[/IMG]

**_3DCC / Colours_:**
Navigate to ~/.wine//home/quandar/.wine/drive_c/Program Files/JaSMiN Co/3D Color Changer 4 and open Js3Dcc.exe with WINE. Okay, as a base for making a similar theme download a 3DCC pack from [this site]("http://www.customize.org/list/3dcc/0/30/downloads-desc"). Basically after this point install it in 3DCC and modify your colours accordingly using the RGB section under the example window for a perfect match. Keep in mind don't use the capture eyedropper feature, it generally is buggy going again anything outside the WINE window.

[IMG]http://gui.deletefactory.net/ubuntu/wine3.png[/IMG]

---

### Post by NobodySpecial on 2006-04-15
I finally got around to trying this out and it does make things look much nicer.  Great work and thanks for posting!  :)

---

### Post by mc_bizon on 2006-04-15
I have IE6 from [ies4linux]("http://www.tatanka.com.br/ies4linux/") and it looks like it looked before. other apps are ok

---

### Post by echo on 2006-08-03
Attached is a 3DC file that matches the Dapper default  "Human" theme.

Enjoy :)

Also, a screenshot of utorrent running under wine with this theme :)

---

### Post by robinl on 2006-08-04
Hey thanks alot now my wine apps look so much better...

---

### Post by Kebabji on 2006-08-07
yeah, although it makes wine apps a lot better looking, it drags down speed tremendously for some reason

---

### Post by mgmiller on 2006-08-07
What a great tip!  My wine apps no longer have "scratchy" looking fonts.  I just changed them to Tahoma and Tohoma bold and they look great.  It worked for me in an appointment book program I use called ChronlistNT and also for Quicken Premier 2005.

Thank you.

---

### Post by jdhawk on 2006-08-17
Sweet Jesus thank you. Running Firefox under wine for Flash9 was killing me with the default theme.

---

### Post by johnbl on 2006-08-17
wine '/john/.wine/drive_c/myob15/Myob.exe'

Love wine, can't get anything to run from a ' click the image and it goes / runs ' link. Know it should. But have tried all I can think of. Somethings wrong with above command clearly.. Any ideas???

John

---

### Post by 23meg on 2006-08-17
This was really helpful, thanks a lot. It's not perfect but most controls blend a lot better.

---

### Post by quandar on 2006-08-20
> **johnbl said:**
> wine '/john/.wine/drive_c/myob15/Myob.exe'

Love wine, can't get anything to run from a ' click the image and it goes / runs ' link. Know it should. But have tried all I can think of. Somethings wrong with above command clearly.. Any ideas???

John

Perhaps that should be:
```
wine ~/.wine/drive_c/myob15/Myob.exe
```

---

### Post by bodhi.zazen on 2006-10-11
This information has been added to the Ubuntu Wine wiki:

[How to wine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by gbesso on 2006-12-27
> **johnbl said:**
> wine '/john/.wine/drive_c/myob15/Myob.exe'

Love wine, can't get anything to run from a ' click the image and it goes / runs ' link. Know it should. But have tried all I can think of. Somethings wrong with above command clearly.. Any ideas???

John

Try wine /home/john/.wine/drive_c/myob15/Myob.exe

---

### Post by DerArzt on 2007-02-14
ROCK ON thanks a bunch

---

### Post by boujemong on 2007-03-19
you could also try this website:

[http://editplus.info/wiki/Running_on_Linux](http://editplus.info/wiki/Running_on_Linux)

about halfway down is a section called Windows Theme, and shows you how to install the media center style royal theme.

---

### Post by cRoMo on 2007-04-05
How did you manage to set up the Window Text font? I managed to set up everything but this one and that's the thing that particularly makes the interface ugly.
EDIT: Actually, I do have Tahoma set up as Window Text, but I wonder how did you set it to be antialiased?

---

### Post by demonbane on 2007-04-20
> **mc_bizon said:**
> I have IE6 from [ies4linux]("http://www.tatanka.com.br/ies4linux/") and it looks like it looked before. other apps are ok

ies4linux creates a custom folder structure specifically for IE. So if you run Wine apps from the default location it won't actually affect IE. You'll need to run Wine with the WINEPREFIX environment variable set to wherever your IE install is. If you look at the ie6 (or ie5, etc) file that ies4linux creates for you (usually in /usr/local/bin) you can get the appropriate settings from in there.

---

### Post by Enverex on 2007-05-26
> **mc_bizon said:**
> I have IE6 from [ies4linux]("http://www.tatanka.com.br/ies4linux/") and it looks like it looked before. other apps are ok

IEs4Linux is separate to Wine, things done inside IEs4Linux or Wine are independent.

---

### Post by Dax0r on 2007-05-28
Anyone has experienced slowness with this tips?

---

### Post by darundal on 2007-05-28
Demonbane, any idea what the command would look like? I have tried WINEPREFIX="/home/ME/.ies4linux/ie6", then it brings up a prompt with >, and I tried running winecfg there but it didn't work. Thanks.

---

### Post by veebis on 2007-08-11
Excellent tip... Thanks!
-Vb  :)

---

### Post by Knorr on 2007-10-18
Can't seem to get the toolbar look anything like the Human theme. Besides the colour.

Used the human.3cd file included in this thread.

How do I get the 3D look and different buttons?

Screenshot attached.

 - Knorr

---

### Post by dhyoga on 2007-11-06
Great, my portable thunderbird & portable firefox looks better with wine :) Thank You.

---

### Post by hihihi on 2008-05-31
some years later and this tips are veryveryvery valuable, thanks very much, i am one minute away from leaving windows for good, this makes it more pleasant, nice colors=good mood

---

### Post by antonferdinand on 2008-09-17
> **gbesso said:**
> Try wine /home/john/.wine/drive_c/myob15/Myob.exe

i try wine /home/user/.wine/drive_c/myob/Myobp.exe
can run,, but when i try to open the sample data
i got the error msg :

> 
MYOB Premier must terminate.

Terminate Code: 1244

Important Details : Error 9998 i IMRProcessEvents
(1143:2003:3).

---

### Post by KillerKiwi on 2008-09-17
see this python script [http://ubuntuforums.org/showthread.php?t=55286&page=4](http://ubuntuforums.org/showthread.php?t=55286&page=4)

---

### Post by Endolith on 2008-09-30
> **KillerKiwi said:**
> see this python script [http://ubuntuforums.org/showthread.php?t=55286&page=4](http://ubuntuforums.org/showthread.php?t=55286&page=4)

I posted it on Launchpad.  Not sure if I'm doing it right, but it's there.  :)

[https://code.launchpad.net/~endolith/+junk/wine-color-scraper]("https://code.launchpad.net/%7Eendolith/+junk/wine-color-scraper")

---

### Post by jvlake on 2008-10-25
Regarding the MYOB error ImrProcessEvents crash, I found my version stoped crashing if I didn't access as a multi user, the error was choking on some netbeui/tcp/ip thing where as single user does not use the networking features.. hope this helps someone, I understand the forum posts are quite old now. Mine is MYOB premier 10...

---

### Post by ltwinner on 2009-08-10
> **cRoMo said:**
> How did you manage to set up the Window Text font? I managed to set up everything but this one and that's the thing that particularly makes the interface ugly.
EDIT: Actually, I do have Tahoma set up as Window Text, but I wonder how did you set it to be antialiased?

I have the same issue, I can change every font except for the Window Text font and that is by far the most problematic. So how can it be changed as I dont see any options for it in DisplaySet?

---

### Post by Endolith on 2009-08-10
You can set some fonts in winecfg under Desktop Integration.  Does that do what you want?

---

### Post by jackharvest on 2010-05-02
THANK YOU for this tutorial. 4 years later, and Wine looks 300 times better now. :D

---

### Post by mrkazoodle on 2010-06-28
The Jasmin 3D Color Changer link didn't work for me, but I found it here:
[http://fileforum.betanews.com/detail/3D-Color-Changer/1072531930/1]("http://fileforum.betanews.com/detail/3D-Color-Changer/1072531930/1")

I attached it as wel.

**EDIT:**
I didn't find 3D Color Changer as useful as the script mentioned earlier, which automatically makes wine use the current theme colors.
You can find the last version here: [http://gist.github.com/74192]("http://gist.github.com/74192")
(and some instructions [_here_]("http://www.webupd8.org/2010/06/make-wine-applications-look-like-your.html"), if you'd need them)

I did use displayset to make wine use sans (déjavu).

I also used the winefontssmoothing script I found [_here_]("http://www.omgubuntu.co.uk/2009/09/font-clear-wine-nice-linux.html") to make wine use smooth fonts.

And finally I adjusted the number of dots per inch (this made word look so much better): 
[LIST=1]
[*]Open the file ~/.wine/system.reg (with gedit)
[*]Search for [System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]
[*]And change the value of "LogPixels"=dword:00000060 to 00000072
[/LIST]
(00000060 is the default value)

---

