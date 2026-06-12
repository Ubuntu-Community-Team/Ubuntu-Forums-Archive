---
title: "[SOLVED] reinstalling Ubuntu from USB"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by munchkin360 on 2008-10-26
I have mad another post with a problem I had with a pre-installed version of Ubuntu on a webbook with no CD drive. (basically I messed up Ubuntu).

Some very nice people helped me out by directing me to a help thingy that allowed me to put Ubuntu on a USB key.

I have it on the key now (I used UNetbootin) but I do not know how to reinstall Ubuntu on a machine with it already on (just not working) from a USB key.

I know very little about computers and even less about Linux or Ubuntu so I am after a idiots guid to how to reinstall it so I have a working machine again.

Any help would be most appreciated.

---

### Post by C.S.Cameron on 2008-10-26
Plug in your flash drive.
Reboot.
In BIOS set your flash drive as the first HDD.
Boot to the flash drive.
Run install.
That's it, install should work just like from the Live CD.

---

### Post by Amarsingh0793 on 2008-10-26
First try this,

1) Make sure your ubuntu usb stick is already in before you press on.
2) Wait for it to boot into the USB Stick. If it doesnt, then you might want to consider changing a few BIOS settings or just getting hold of a CD-ROM.

Anyway, to change the BIOS Settings, you have to press either F8 or Delete when it says something about that on screen. When you get into it, you need to change the boot order. I recommend:

1)CD/DVD
2)USB
3)Hard Drive (usually says SATA or something)

After doing this, exit the BIOS and save changes. Then it will restart and hopefully do what you need it to do :)

Hope this helps!

---

### Post by munchkin360 on 2008-10-26
Ok thanks for the info. I am sort of half way there.

I got it to boot from the USB key. It came up with...

This is the Ubuntu Live CD
Press F1 for help and advanced options
For the defult options press enter

I pressed enter. The Ubuntu screen with the orange bar came up and the bar was moving back and forth. It then played a small clip of music and then the screen went black and nothing else happened. i left it for a good 20 mins and nothing.

Any ideas why I could not progress further than this?

---

### Post by Amarsingh0793 on 2008-10-26
Hmmm. I think you should try installing by CD/DVD if possible. I've never installed ubuntu by a USB Stick before.

---

### Post by munchkin360 on 2008-10-26
I really wish that was on option. But the webbook has no CD drive and I do not have an external one.

I am starting to wonder if its a graphic problem. Humm I think I have just killed the machine.

Anyone got any bright ideas before my boyfriend chops my head off??

---

### Post by panhandle on 2008-10-26
What type of machine is this?

---

### Post by ashmew2 on 2008-10-26
> **Amarsingh0793 said:**
> Hmmm. I think you should try installing by CD/DVD if possible. I've never installed ubuntu by a USB Stick before.

I always do it using UnetBootin and it tends to go much faster from the USB than the CD/DVD!

> **munchkin360 said:**
> I really wish that was on option. But the webbook has no CD drive and I do not have an external one.

I am starting to wonder if its a graphic problem. Humm I think I have just killed the machine.

Anyone got any bright ideas before my boyfriend chops my head off??

Are you trying to install a different version ? I mean is it the same as the one that came pre-installed ? Because sometimes a version will work without problems but the others wouldnt..

We'll help you along the way ;)

---

### Post by ashmew2 on 2008-10-26
And Yes , Please do not be worried ,  YOU HAVE NOT messed it up beyond repair.. Its only a software issue and we'll fix it....somewhow :D

---

### Post by teaker1s on 2008-10-26
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")
describes how to install

---

### Post by ashmew2 on 2008-10-26
-*Please Ignore Post*-

---

### Post by ashmew2 on 2008-10-26
I forgot , When you boot up using the USB , and you see a black screen even after 20+ minutes , try pressing CTRL+ALT+F1 (try till F6 if doesnt work) and post back!

Oh and , Are you using Windows to post replies ?

---

### Post by munchkin360 on 2008-10-26
I was getting tired eyes looking at the little webbook screen trying to figure out what I had done so I plugged the webbook in to my normal deck top PC's monitor and to my shock, I had a picture on the external monitor!!

I clicked 'try Ubuntu' and hay presto the desk top loaded (only on the external monitor not on the webbook screen). So I am just installing Ubuntu in the hope that this works.

I am assuming I have a graphics problem. Maybe I have damaged the drivers and need to re-install them?? (I don't even know what graphics card I have got) Any one know how to do that? Its the Elonex webbook you get free from Carphone Warehouse. (I picked it up on ebay cheap, but not cheap enough to kill it in 24 hours LOL).

I know so little about computers, to the point when I got the desktop (windows xp) the only question I had for the guy in the shop was "how can I make the desktop pink?" He then told me girls and computers next mix well. I quite agree with him now!!

So do I need to reinstall graphics driver thingy or something as I am getting a picture on the external monitor but not the webbook screen? All I get on the webbook screen is the inital text 'press tab to enter POST screen or DEL to enter setup' and the orange Ubuntu scrolling bar that says its loading. After that it goes black but the extrenal screen keeps going.

You guys are super. I really appreciate all the help.

---

### Post by munchkin360 on 2008-10-26
Just to confirm it IS (I think) a graphic problem.

Ubuntu has installed perfectly and is all working on the external plugged in monitor but NOT on the elonex screen.

So my next question is... How can I fix this??

Many thanks for putting up with me.

---

### Post by ashmew2 on 2008-10-26
Nice job..
So you can log on and do stuff normally on your Desktop's monitor ? 

Try pressing CTRL+ALT+F1 when the screen goes blank (On the Cheap (lol) Notebook). If you see somewhere you can type , we are lucky.


Btw , how much time do we have for fixing up things ?

---

### Post by munchkin360 on 2008-10-26
OOO yes I now have a typing screen on both the webbook screen and on the monitor. How exciting it says...

alex-laptop login:

Sorry got excited. Yes everything is visable on the external monitor, the proper desktop.

How much time do I have to fix things?? As much as needed, I'm quite excited now and chuffed that I got this far :) (with the help of you lot)

---

### Post by teaker1s on 2008-10-26
possibly it's the wrong resolution rate previously you could issue command 
```
sudo dpkg-reconfigure xserver-xorg
``` if this doesn't work for you (later xorg-can't tell as using debian at the moment)

then have a look here [https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by ashmew2 on 2008-10-26
> **munchkin360 said:**
> OOO yes I now have a typing screen on both the webbook screen and on the monitor. How exciting it says...

alex-laptop login:

Sorry got excited. Yes everything is visable on the external monitor, the proper desktop.

How much time do I have to fix things?? As much as needed, I'm quite excited now and chuffed that I got this far :) (with the help of you lot)


Yeah I was as excited as you are now the first time I installed an operating system!
> **teaker1s said:**
> possibly it's the wrong resolution rate previously you could issue command 
```
sudo dpkg-reconfigure xserver-xorg
``` if this doesn't work for you (later xorg-can't tell as using debian at the moment)

then have a look here [https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

+1

---

### Post by munchkin360 on 2008-10-26
The code did not work for some reason, going to have a look at the link you provided. :)

---

### Post by ashmew2 on 2008-10-26
What did it say when you put the code in ? Did you forget a space somewhere or added an extra space somewhere ? Do check..

---

### Post by teaker1s on 2008-10-26
the code only works on older version of xserver, I would suggest that your xorg.conf monitor section may need manually editing.
 Hopefully the link will help you-as for double posting:-sunday lunch with wine and didn't realize:popcorn:

---

### Post by munchkin360 on 2008-10-26
It came up with a big box asking me if I wanted it to auto dectect my screen and keyboard settings. I said yes to both and then it restarted the computer, still a black screen on the webbook and a good screen on the external monitor.

Going through the link you gave but need to find out things like horizontal sync frequency and range of the webbook screen which are not in the user book, typical!

---

### Post by munchkin360 on 2008-10-26
I got to the screen following the link and found the Section Monitor bit and all it says is...

Identifier      "configured monitor"

In the link it says to imput the values manually trouble is I don't know what the values are. It does not say in the 4 page instruction book for the webbook and a google came up with nothing either! So now I am stuck again. Going to go and cry now sob sod :(

---

### Post by jerome1232 on 2008-10-26
Yeah and actually to reset xorg it's
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

But I think we should edit xorg.conf and start at some safe settings like 640x480@50hz and work from there.

correct me if my syntax is wrong but I think putting something like this in /etc/X11/xorg.conf under the 'screen' section would work.


```
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@50"
    EndSubSection
```

To edit xorg from the commandline:

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by talbain on 2008-10-26
> **munchkin360 said:**
> I was getting tired eyes looking at the little webbook screen trying to figure out what I had done so I plugged the webbook in to my normal deck top PC's monitor and to my shock, I had a picture on the external monitor!!

I clicked 'try Ubuntu' and hay presto the desk top loaded (only on the external monitor not on the webbook screen). So I am just installing Ubuntu in the hope that this works.

I am assuming I have a graphics problem. Maybe I have damaged the drivers and need to re-install them?? (I don't even know what graphics card I have got) Any one know how to do that? Its the Elonex webbook you get free from Carphone Warehouse. (I picked it up on ebay cheap, but not cheap enough to kill it in 24 hours LOL).

I know so little about computers, to the point when I got the desktop (windows xp) the only question I had for the guy in the shop was "how can I make the desktop pink?" He then told me girls and computers next mix well. I quite agree with him now!!

So do I need to reinstall graphics driver thingy or something as I am getting a picture on the external monitor but not the webbook screen? All I get on the webbook screen is the inital text 'press tab to enter POST screen or DEL to enter setup' and the orange Ubuntu scrolling bar that says its loading. After that it goes black but the extrenal screen keeps going.

You guys are super. I really appreciate all the help.

I gotta tell you, you may think you dont know much about computers but if thats the case, you are very brave and/or very resourceful, i was surprised reading your posts, you made a bootable ubuntu usb stick? tried and connected an external monitor? you are reinstalling ubuntu?
may sound like simple things for an aficionado but for a girl that doesnt know much about computers, wow, you rock
i cant even start to imagine my wife doing any of those or most of my girl-friends or even male former customers

i like you :)

---

### Post by munchkin360 on 2008-10-26
Thanks :) I am feeling quite proud of myself (well more excited, its all good fun :) )

Right when I type sudo dpkg-reconfigure -phigh xserver-xorg

I get this come up...

xserver-xorg postinst warning: overwriting possibly customised configuration file; backup in /etc/X11/xorg.config .20081026051559

That look sort of right??

going to try to edit xorg from the commandline now...

---

### Post by munchkin360 on 2008-10-26
> **jerome1232 said:**
> Yeah and actually to reset xorg it's
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

But I think we should edit xorg.conf and start at some safe settings like 640x480@50hz and work from there.

correct me if my syntax is wrong but I think putting something like this in /etc/X11/xorg.conf under the 'screen' section would work.


```
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@50"
    EndSubSection
```

To edit xorg from the commandline:

```
sudo nano /etc/X11/xorg.conf
```

Confused as to where I type this...

My screen I get up with all the weird configuration stuff in only says

Section "Monitor"
        Identifier     "Configured Monitor"
EndSection

Where abouts do I type the bits in? Under the 'Identifier' line?

Sorry I am being so slow at getting all this!

---

### Post by ashmew2 on 2008-10-26
**munchkin360** We all are really PROUD to have you as a member..

Hats Off..:guitar:


Add all of this : (After the EndSection of "Monitor" Section)

> Section "Screen"
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@50"
    EndSubSection
EndSection

---

### Post by teaker1s on 2008-10-26
[found what you need http://webbookblog.com/?p=171]("http://webbookblog.com/?p=171")

[xorg.conf download]("http://webbookblog.com/wp-content/uploads/2008/09/xorg.conf")

[http://webbookblog.com/]("http://webbookblog.com/") this chap supports and worked with carphone warehouse to create the ubuntu install(offers live support)



 [http://www.hants.lug.org.uk]("http://www.hants.lug.org.uk") group has Alan Bell
if you get really stuck Alan Bell was involved with ubuntu for carphone warehouse 
[http://www.theopenlearningcentre.com/index.php/about/the-team]("http://www.theopenlearningcentre.com/index.php/about/the-team")

---

### Post by munchkin360 on 2008-10-26
Humm it be doing funny things...

Ha ha ha...

I have a screen on the webbook again YAY your all stars :)

But its not over yet (go grab a coffee)...

Firstly the graphics are quite poor. Not sharp like they use to be. So thats problem one, which I am assuming is going to be the easier of the two.

Problem 2 is I have an error message come up...

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with imcompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/Keyboard/kbd

I (think) I know what caused it, I acciently changed the keyboard settings and cannot figure out how to change it back.

Oh and when ever I start it up it says...

Ubuntu is running in low graphics mode and gives me three options...

Configure which brings up a list of makes of graphice card thingys (i think)
Shut down
Continue

When I click continue it loads up fine (like I said above I get the desktop on the webbook now) but its poor graphics.

Cheers again everyone. My aim in life now is to learn about Linux and Ubuntu because when it works its ace :)

HOLD ON problem number 3 is happening. It says the display number I picked is busy and asks a yes no question (which I clicked too fast and missed most of) anyway I hit yes and it says...

The specified display number was busy, so the server was started on display :1.

Then I hit the OK button and it loads the log in screen and then the desktop

---

### Post by munchkin360 on 2008-10-26
Oh no now when I turn it on it goes to a black screen and says

alex-laptop login:

Where has the pretty login screen gone??

Someone tie me up!! I have not touched anything else promise

---

### Post by teaker1s on 2008-10-26
okay you want to copy the contents of the xorg.conf file I pointed to for download to your xorg.conf

```
sudo gedit /etc/X11/xorg.conf 
``` copy paste and save-should sort your web book out as it was set up for it.
xkb error can normally be cleared by System>preferences>keyboard creat another keyboard map same as your normal one-then delete old keyboard map.

it's caused by corrupted xkb data

---

### Post by munchkin360 on 2008-10-26
Oh wow I love you all and owe you huge pints.

Its worked YAY I have a working webbook :) :) :) :)

How can I think you? Is this site like a lot of forums? Funded by donations? Can I donate?

I do really appreciate it and would like thank everyone and the forum.

---

### Post by teaker1s on 2008-10-26
you can donate to ubuntu if you would like:KS

While I like a beer (guiness/stella) but guess your not near Somerset or for this week Barnet:lolflag:

You will find these forums people help people because it's like a big family- as people gain experience they help others. 
You'll find these forums safe,friendly and the best:guitar:

---

### Post by munchkin360 on 2008-10-26
Somerset... Nearly. I'm Dorset :)

I will donate :) When I figure out how LOL

Thanks again everyone

---

### Post by teaker1s on 2008-10-26
:popcorn: Have some virtual popcorn

---

### Post by ashmew2 on 2008-10-27
The bottom line is :

Girls and Computers mix well after all :lolflag:

---

### Post by talbain on 2008-10-27
> **ashmew2 said:**
> the bottom line is :

Girls and computers mix well after all :lolflag:

+1 :)

---

