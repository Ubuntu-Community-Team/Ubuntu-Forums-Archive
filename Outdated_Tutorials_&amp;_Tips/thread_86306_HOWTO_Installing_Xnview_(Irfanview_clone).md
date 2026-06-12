---
title: "HOWTO: Installing Xnview (Irfanview clone)"
date: 2005-11-04
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-11-04
If u are used to irfanview on windows, u shd install Xnview. it almost completely emulates irfanview save a few options.
herez how to install it:
```
wget -c http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz
tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz
cd XnView-1.70-x86-unknown-linux2.x-static-fc4
chmod +x install
sudo ./install
```
never mind the errors.
use alacarte or smeg to add a menu entry for xnview under graphics
try xnview by running from terminal:
```
xnview
```
the interface isnt pretty but it works like irfanview.

---

### Post by poptones on 2005-11-04
GQview is similar, and it's open source. It's the first thing I install after cryptsetup and build-essentials. I build the 2.1 version myself from source, but the version in synaptic is even more like irfan.

---

### Post by arnieboy on 2005-11-04
[QUOTE=poptones]GQview is similar, and it's open source. It's the first thing I install after cryptsetup and build-essentials. I build the 2.1 version myself from source, but the version in synaptic is even more like irfan.[/QUOTE]
gqview doesnt even have a tenth of the options of irfanview. xnview atleast attempts to come close.

---

### Post by poptones on 2005-11-04
slideshows, lossless rotation, simple interface and one click launch to gimp.

And... gqview is open source. 

Color adjustments and such might be needed in windows where there's nothing better unless you pay for it, but I don't see it here. To me irfanview means "lightweight image viewer" not "photo editor." Gqview fits that perfectly.

That's why restaraunts have menus....

---

### Post by arnieboy on 2005-11-04
[QUOTE=poptones]slideshows, lossless rotation, simple interface and one click launch to gimp.

And... gqview is open source. 

Color adjustments and such might be needed in windows where there's nothing better unless you pay for it, but I don't see it here. To me irfanview means "lightweight image viewer" not "photo editor." Gqview fits that perfectly.

That's why restaraunts have menus....[/QUOTE]
linux is all about choices.. open source or not being one of them... menus in a restaurant being another.. lets save this discussion for later.. i wud like to keep this thread for troubleshooting if any.

---

### Post by BLTicklemonster on 2005-11-05
Yeah, Xnview seems kinda familiar to Irfanview.

---

### Post by ounas on 2005-11-05
[QUOTE=arnieboy]If u are used to irfanview on windows, u shd install Xnview. it almost completely emulates irfanview save a few options.
herez how to install it:
```
wget -c http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz
tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz
cd XnView-1.70-x86-unknown-linux2.x-static-fc4
chmod +x install
sudo ./install
```
never mind the errors.
use alacarte or smeg to add a menu entry for xnview under graphics
try xnview by running from terminal:
```
xnview
```
the interface isnt pretty but it works like irfanview.[/QUOTE]

Thanks Arnieboy

-Ounas:smile:

---

### Post by lotusleaf on 2005-11-05
[QUOTE=arnieboy]the interface isnt pretty but it works like irfanview.[/QUOTE]

According to a [post](http://newsgroup.xnview.com/viewtopic.php?t=3666) or two from the author of XnView on the [XnView forums](http://newsgroup.xnview.com/), he's considering making a QT version within the next year. XnView has some nice [features](http://perso.wanadoo.fr/pierre.g/xnview/enfeatures.html) in addition to supporting a lot of [formats](http://perso.wanadoo.fr/pierre.g/xnview/enformats.html).

---

### Post by gw90se on 2005-11-06
From an old Irfanview fan....

THANK YOU!!!!!!!

---

### Post by reet on 2005-11-08
I should add that for people that dual boot linux and windows, Xnview is also available for windows and works very well.

---

### Post by BLTicklemonster on 2005-11-08
I was going to make a launcher on my desktop; to launch it, do I put

/home/bill/xnview

and set it to launch from the terminal?

I got UnrealTournament to launch from the desktop finally, and I started thinking about getting that one on there, too.

---

### Post by arnieboy on 2005-11-08
[QUOTE=BLTicklemonster]I was going to make a launcher on my desktop; to launch it, do I put

/home/bill/xnview

and set it to launch from the terminal?

I got UnrealTournament to launch from the desktop finally, and I started thinking about getting that one on there, too.[/QUOTE]
no let the launcher just launch "xnview" (path not required). u dont need to launch it from terminal. it can get launched as such.

---

### Post by BLTicklemonster on 2006-01-29
Yep, works like you said. Thanks Arnieboy. I just tried it again, and tried enlarging an image, and it does well with making a 200x image a 1200x image and not pixellating, just like irfanview does. Thanks again, Arnieboy.

---

### Post by sailor2001 on 2006-08-12
> **arnieboy said:**
> If u are used to irfanview on windows, u shd install Xnview. it almost completely emulates irfanview save a few options.
herez how to install it:
```
wget -c http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz
tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz
cd XnView-1.70-x86-unknown-linux2.x-static-fc4
chmod +x install
sudo ./install
```
never mind the errors.
use alacarte or smeg to add a menu entry for xnview under graphics
try xnview by running from terminal:
```
xnview
```
the interface isnt pretty but it works like irfanview.

cd XnView-1.70-x86-unknown-linux2.x-static-fc4  this is as far as I can get in terminal and it freezes

---

### Post by jiminid on 2007-03-11
This is what I get when I paste the installation script into my terminal:

jim@jim-desktop:~$ wget -c [http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz](http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz)
--11:11:24--  [http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz](http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz)
           => `XnView-x86-unknown-linux2.x-static-fc4.tgz'
Resolving download.xnview.com... 213.186.33.5
Connecting to download.xnview.com|213.186.33.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 875 [text/html]

50% [=================>                   ] 875           --.--K/s

11:11:27 (37.93 MB/s) - `XnView-x86-unknown-linux2.x-static-fc4.tgz' saved [875/875]

jim@jim-desktop:~$ tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
jim@jim-desktop:~$ cd XnView-1.70-x86-unknown-linux2.x-static-fc4
bash: cd: XnView-1.70-x86-unknown-linux2.x-static-fc4: No such file or directoryjim@jim-desktop:~$ chmod +x install
chmod: cannot access `install': No such file or directory
jim@jim-desktop:~$ sudo ./install
sudo: ./install: command not found
jim@jim-desktop:~$

I would really appreciate any help or suggestions here as I am living currently in newbieville.

thanks

---

### Post by mshlin on 2007-03-12
Success! :) 

I could also not get to work using wget. So I went to XnView site [http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html]("http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html")

and downloaded the XnView v1.70 + NView/NConvert v4.51 tar gz version.

Then followed instructions in tutorial:

tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz
cd XnView-1.70-x86-unknown-linux2.x-static-fc4
chmod +x install
sudo ./install

never mind the errors.
use alacarte or smeg to add a menu entry for xnview under graphics
try xnview by running from terminal:

xnview



I noticed the file wget was fetching was a lot smaller than the 2.5mb file downloaded manually from site. I don't know much about wget so don't know why. 

Hope this helps.

arnieboy thanks for tip, neat program.

---

### Post by BLTicklemonster on 2007-03-12
bill@bill-desktop:~$ wget -c [http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz](http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz)
--06:20:20--  [http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz](http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz)
           => `XnView-x86-unknown-linux2.x-static-fc4.tgz'
Resolving download.xnview.com... 213.186.33.5
Connecting to download.xnview.com|213.186.33.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 875 [text/html]

100%[====================================>] 875           --.--K/s             

06:20:20 (83.45 MB/s) - `XnView-x86-unknown-linux2.x-static-fc4.tgz' saved [875/875]

bill@bill-desktop:~$ tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
bill@bill-desktop:~$ cd XnView-1.70-x86-unknown-linux2.x-static-fc4
bash: cd: XnView-1.70-x86-unknown-linux2.x-static-fc4: No such file or directory
bill@bill-desktop:~$ chmod +x install
chmod: cannot access `install': No such file or directory
bill@bill-desktop:~$ cd XnView-1.70-x86-unknown-linux2.x-static
bill@bill-desktop:~/XnView-1.70-x86-unknown-linux2.x-static$ chmod +x installbill@bill-desktop:~/XnView-1.70-x86-unknown-linux2.x-static$ sudo ./install
  OS  : Linux, version 2.6.17-11-generic
This script will install nview/nconvert/xnview in the /usr/local/bin directory

Done!
bill@bill-desktop:~$ xnview
xnview: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory


???? eh?  And mshlin, I got the same error doing it your way, too.

---

### Post by cb474 on 2007-03-14
> **jiminid said:**
> This is what I get when I paste the installation script into my terminal:

jim@jim-desktop:~$ wget -c [http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz](http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz)
--11:11:24--  [http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz](http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz)
           => `XnView-x86-unknown-linux2.x-static-fc4.tgz'
Resolving download.xnview.com... 213.186.33.5
Connecting to download.xnview.com|213.186.33.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 875 [text/html]

50% [=================>                   ] 875           --.--K/s

11:11:27 (37.93 MB/s) - `XnView-x86-unknown-linux2.x-static-fc4.tgz' saved [875/875]

jim@jim-desktop:~$ tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
jim@jim-desktop:~$ cd XnView-1.70-x86-unknown-linux2.x-static-fc4
bash: cd: XnView-1.70-x86-unknown-linux2.x-static-fc4: No such file or directoryjim@jim-desktop:~$ chmod +x install
chmod: cannot access `install': No such file or directory
jim@jim-desktop:~$ sudo ./install
sudo: ./install: command not found
jim@jim-desktop:~$

I got exactly the same response. What's right way to install this? Can it be done with the Synaptic Package Manager?

---

### Post by jiminid on 2007-03-25
> **mshlin said:**
> Success! :) 

I could also not get to work using wget. So I went to XnView site [http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html]("http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html")

and downloaded the XnView v1.70 + NView/NConvert v4.51 tar gz version.

Then followed instructions in tutorial:

tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz
cd XnView-1.70-x86-unknown-linux2.x-static-fc4
chmod +x install
sudo ./install

never mind the errors.
use alacarte or smeg to add a menu entry for xnview under graphics
try xnview by running from terminal:

xnview



I noticed the file wget was fetching was a lot smaller than the 2.5mb file downloaded manually from site. I don't know much about wget so don't know why. 

Hope this helps.

arnieboy thanks for tip, neat program.

This is what I get:
jim@jim-desktop:~$ tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
jim@jim-desktop:~$ tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
jim@jim-desktop:~$ cd XnView-1.70-x86-unknown-linux2.x-static-fc4
bash: cd: XnView-1.70-x86-unknown-linux2.x-static-fc4: No such file or directoryjim@jim-desktop:~$ chmod +x install
chmod: cannot access `install': No such file or directory
jim@jim-desktop:~$ sudo ./install
Password:
sudo: ./install: command not found
jim@jim-desktop:~$

Any ideas about why this is not working?

---

### Post by citizenr on 2007-03-26
wine i_view32.exe

so why bother with a clone?

---

### Post by BLTicklemonster on 2007-03-27
> **jiminid said:**
> This is what I get:
jim@jim-desktop:~$ tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
jim@jim-desktop:~$ tar xzf XnView-x86-unknown-linux2.x-static-fc4.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
jim@jim-desktop:~$ cd XnView-1.70-x86-unknown-linux2.x-static-fc4
bash: cd: XnView-1.70-x86-unknown-linux2.x-static-fc4: No such file or directoryjim@jim-desktop:~$ chmod +x install
chmod: cannot access `install': No such file or directory
jim@jim-desktop:~$ sudo ./install
Password:
sudo: ./install: command not found
jim@jim-desktop:~$

Any ideas about why this is not working?

jim@jim-desktop:~$ cd /XnView-1.70-x86-unknown-linux2.x-static-fc4
 notice the / in  /XnView 

Might also have to do this

mkdir: cannot create directory `/usr/lib/X11/app-defaults/XnView': No such file or directory
bill@bill-desktop:~/XnView-1.70-x86-unknown-linux2.x-static-fc4$ **sudo mkdir /usr/lib/X11/app-defaults**
bill@bill-desktop:~/XnView-1.70-x86-unknown-linux2.x-static-fc4$ **sudo mkdir /usr/lib/X11/app-defaults/XnView**
bill@bill-desktop:~/XnView-1.70-x86-unknown-linux2.x-static-fc4$ sudo ./install  OS  : Linux, version 2.6.20-13-386
This script will install nview/nconvert/xnview in the /usr/local/bin directory

Done!
bill@bill-desktop:~/XnView-1.70-x86-unknown-linux2.x-static-fc4$

---

### Post by BLTicklemonster on 2007-03-27
What a pity. I can't find an icon for my loader.

Oh, I know, use this:

[IMG]http://img482.imageshack.us/img482/6967/iviewjw2.png[/IMG]

---

### Post by BLTicklemonster on 2007-03-27
> **citizenr said:**
> wine i_view32.exe

so why bother with a clone?
xnview loads a lot quicker. And why have wine run something when there's no need to?

---

### Post by shadowboxer_k on 2007-03-28
can anyone please update the code?&#12288;i saw the changes bill made but i don't know how to do the input myself without screwing up. 

thank you!

---

### Post by BLTicklemonster on 2007-03-28
Sorry, that was all less than straight forward, try this:

in your terminal, type
```
sudo mkdir /usr/lib/X11/app-defaults
```
(you're making a directory -mkdir- and need to be root, hence the sudo command. enter your password)

then
```
sudo mkdir /usr/lib/X11/app-defaults/XnView
```

now 
```
cd /home/directory where you downloaded to/XnView-1.70-x86-unknown-linux2.x-static-fc4
```

and
```
sudo chmod +x install
```

and finally
```
sudo ./install
```

and that ought to get it going.

I messed around with an installer once and made it do what I wanted it to do by editing it. I wonder if one could add the mkdir lines to the installer themselves?

Something along these lines:

```
echo This script will install nview/nconvert/xnview in the /usr/local/bin directory

BASEDIR="/usr/local"

if [ ! -e $BASEDIR ]; then
	mkdir $BASEDIR
fi

if [ ! -e $BASEDIR ]; then
	exit 0
fi

if [ ! -e $BASEDIR/bin ]; then
	mkdir -p $BASEDIR/bin
	chmod 755 $BASEDIR/bin
fi

if [ ! -e $BASEDIR/lib ]; then
	mkdir $BASEDIR/lib
	chmod 755 $BASEDIR/lib
fi

[B][I][SIZE="4"]if [ ! -e $BASEDIR/X11 ]; then
	mkdir $BASEDIR/X11
	chmod 755 $BASEDIR/X11
fi

if [ ! -e $BASEDIR/app-defaults ]; then
	mkdir $BASEDIR/app-defaults
	chmod 755 $BASEDIR/app-defaults
fi

if [ ! -e $BASEDIR/XnView ]; then
	mkdir $BASEDIR/XnView
	chmod 755 $BASEDIR/XnView[/SIZE][/I][/B]
```

Stuff I would add is large and bold. Anybody here know if that would work to add the right directories? :) I have no idea, I just like playing with stuff.

---

### Post by shadowboxer_k on 2007-03-29
bill, thanks so much!

---

### Post by shadowboxer_k on 2007-03-29
oops, i seem to have messed things up again!

when i get to step #3, it gives me the following error:

> bash: cd: /home/kris/Desktop/XnView-1.70-x86-unknown-linux2.x-static-fc4: No such file or directory


can anyone please tell me what i am doing wrong?

i have the xnview rpm file downloaded on my desktop and i haven't unpacked it.

---

### Post by BLTicklemonster on 2007-03-29
Not 

cd: /home/kris/Desktop/XnView-1.70-x86-unknown-linux2.x-static-fc4

but 

cd /home/kris/Desktop/XnView-1.70-x86-unknown-linux2.x-static-fc4

leave out the :

:)

---

### Post by shadowboxer_k on 2007-03-30
thanks again for the patience. :)

---

### Post by BLTicklemonster on 2007-03-30
So you got it going? Have you noticed all the cool filters (effects) it has that irfanview doesn't? Impressive program!

---

### Post by SirShaggy on 2007-05-02
> **BLTicklemonster said:**
> What a pity. I can't find an icon for my loader.

Oh, I know, use this:

[IMG]http://img482.imageshack.us/img482/6967/iviewjw2.png[/IMG]


I downloaded the gif off Xnviews homepage, put it in my home folder and then:

sudo gedit /usr/share/applications/xnview.desktop

in the file that opened, I put this:

[Desktop Entry]
Name=Xnview
Comment=Graphics conversion
Exec=xnview
Icon=/home/shaggy/xnview.gif
Terminal=true
Type=Application
Categories=Application;Graphics;


"make sure to hit return to move the curser below the above text and then save the file.

It created a launcher in Application, Graphics for me with Xnviews own logo. I am happy enough with that and it seems to always work. Plus, it opens with the terminal so if I need help, it's already open.

SirShaggy

---

### Post by koolkatkiwi on 2007-10-03
Hi all. Thanks for all your advice (found this thread via search), and I will be trying to install Xnview soon. BTW, it's a fantastic program. I don't know about Irfanview - I used to use it a bit years ago, and it was fine. 

But Xnview has one great feature that none of my other pricey Windows programs had - the Create Filmstrip feature. It's priceless when you want to combine different views of an item, for instance to sell on Trademe (our local Ebay clone). You pay for each photo on the auction over the first one which is free - so if you can combine them, it's great.

This would also be good for listings on Ebay - I don't know how their pricing structure for photos works, though.

---

### Post by jkarma on 2007-11-06
cd /home/joshua/Desktop/XnView-1.70-x86-unknown-linux2.x-static-fc4

its saying no such directory exists. I cannot complete the install. I'm an AVID Irfan user on Windows and this is a must for a linux switch.

---

### Post by Jerry N on 2007-11-14
The current Linux version of Xnview is ugly and works poorly.  However, Version 1.9 for Windows installs and works great under Wine.  Irfanview is also supposed to work with Wine but when I tried it the thumbnails were washed out almost completely and the performance was poor.  I am going to stick with Wine and Xnview for Windows until the next Xnview for Linux is released.

Jerry

---

### Post by Giradman on 2007-11-22
Sorry for reactivating an 'old' thread on Irfanview, but I'm new to Ubuntu but an old Windows user, and I've been using Irfanview for years for simple image manipulation - mainly to 'crop & resize' images for web submission - I know I can do this in GIMP (but not very conveniently); so, since the last posts, are there any 'new' options that are comparable to Irfanview (which seems to still be only useable w/ WINE) - thanks for any comments - :)

---

### Post by florentx on 2007-12-21
> **Giradman said:**
> Sorry for reactivating an 'old' thread on Irfanview, but I'm new to Ubuntu but an old Windows user, and I've been using Irfanview for years for simple image manipulation - mainly to 'crop & resize' images for web submission - I know I can do this in GIMP (but not very conveniently); so, since the last posts, are there any 'new' options that are comparable to Irfanview (which seems to still be only useable w/ WINE) - thanks for any comments - :)

You can have a look at Gthumb for simple photo manipulation . Find different actions in menu to crop/resize/fix red eyes, and many more ...

-- 
Florent

---

### Post by adam0509 on 2007-12-22
French page about it :

[http://doc.ubuntu-fr.org/xnview](http://doc.ubuntu-fr.org/xnview)

---

### Post by neostead on 2008-03-03
i have insalled xnview, it;s excelent application, i use it under windows, but on my Ubuntu images are NOT proprly dispalyed :/

take a look at screenshoot

[http://v.rootnode.net/~bagheera/xnview.png](http://v.rootnode.net/~bagheera/xnview.png)

what could be wrong and how to fix it?

---

### Post by jonnylentilbean on 2008-08-14
xnview ripped irfan off, but that's another story.

why not just install irfanview in ubuntu through wine? it's as simple as it gets, and it's irfanview, not a clone. not a copycat.

---

### Post by idodialog on 2008-09-04
Long time I-view user on windows but I'm afraid time has moved on - and as good as it was there are now better  - and sadly I don't see them in Ubuntu. There are some drawbacks using apps in wine - but having said that I-view works fine - but why not drink champagne?

[[COLOR="Red"]PhotoFiltre[/COLOR] ]("http://photofiltre.free.fr/")is great - like a simple and mini Photoshop (not open source but free for home users) - all the tools work fine under wine - highly recommended. (PhotoFiltre Studio is shareware - [PhotoFiltre 6.2]("http://photofiltre.free.fr/") is free 

If you wan an image sorting/editing/slideshowing/ and god knows what else - I-view on steroids but just as simple and way better than Xn-view (tho similar) try the free (but not open source)[ [COLOR="Red"]FastStone Image Viewer[/COLOR]]("http://faststone.org/FSViewerDetail.htm"). I did need to play with it a bit to realize its vast strengths but it's a real keeper and again, everything seems to work under Wine (tho I haven't tried everything) 

Happy image editing

---

### Post by yug23 on 2008-11-01
I had some errors installing XnView from the tar.gz file on their site under Intrepid so I downloaded the .rpm and did:

```
sudo alien XnView-static-fc4.i386.rpm
```

and then:

```
sudo dpkg -i xnview_1.70-2_i386.deb
```

I agree the interface is incredibly ugly but it's the fastest way I've found to preview .psd files under ubuntu- if the ugliness gets to me too much I may have a go with the Windows version under Wine.

---

### Post by airplus on 2010-04-02
> **ounas said:**
> Thanks Arnieboy

-Ounas:smile:

Thanks, this really helped! :D

---

### Post by airplus on 2010-04-02
> **BLTicklemonster said:**
> Sorry, that was all less than straight forward, try this:

in your terminal, type
```
sudo mkdir /usr/lib/X11/app-defaults
```(you're making a directory -mkdir- and need to be root, hence the sudo command. enter your password)

then
```
sudo mkdir /usr/lib/X11/app-defaults/XnView
```now 
```
cd /home/directory where you downloaded to/XnView-1.70-x86-unknown-linux2.x-static-fc4
```and
```
sudo chmod +x install
```and finally
```
sudo ./install
```and that ought to get it going.

I messed around with an installer once and made it do what I wanted it to do by editing it. I wonder if one could add the mkdir lines to the installer themselves?

Something along these lines:

```
echo This script will install nview/nconvert/xnview in the /usr/local/bin directory

BASEDIR="/usr/local"

if [ ! -e $BASEDIR ]; then
    mkdir $BASEDIR
fi

if [ ! -e $BASEDIR ]; then
    exit 0
fi

if [ ! -e $BASEDIR/bin ]; then
    mkdir -p $BASEDIR/bin
    chmod 755 $BASEDIR/bin
fi

if [ ! -e $BASEDIR/lib ]; then
    mkdir $BASEDIR/lib
    chmod 755 $BASEDIR/lib
fi

[B][I][SIZE=4]if [ ! -e $BASEDIR/X11 ]; then
    mkdir $BASEDIR/X11
    chmod 755 $BASEDIR/X11
fi

if [ ! -e $BASEDIR/app-defaults ]; then
    mkdir $BASEDIR/app-defaults
    chmod 755 $BASEDIR/app-defaults
fi

if [ ! -e $BASEDIR/XnView ]; then
    mkdir $BASEDIR/XnView
    chmod 755 $BASEDIR/XnView[/SIZE][/I][/B]
```Stuff I would add is large and bold. Anybody here know if that would work to add the right directories? :) I have no idea, I just like playing with stuff.


Thanks very much! I did everything except the script. Now I can browse my hot pics collection :p

---

