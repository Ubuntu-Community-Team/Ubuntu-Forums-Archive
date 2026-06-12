---
title: "HowTo: Frets on Fire with Wii Guitar"
date: 2008-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by kiwi_bird on 2008-01-11
I have only tested this with Ubuntu, so good luck trying on any other distros.

You need: 

[LIST]
[*] Wiimote
[*] Guitar Hero III guitar
[*] some kind of blue-tooth adapter
[/LIST]

Now you have to install some packages first:
```

sudo apt-get install libbluetooth2 bluez-utils original-awk bison flex libbluetooth2-dev autoconf mouseemu libgtk2.0-dev 

```

With all that installed you can now install the actual Wiimote drivers:
```

sudo apt-get install libcwiid0 libcwiid0-dev lswm wmgui wminput

```

Now you could already use your Wiimote as a mouse! Just type:
```

sudo wminput 

```

Or to get it working with the IR sensor:
```

sudo wminput -c ir_ptr

```

Once that's setup we can go onto installing the script to get the guitar to work.
```

sudo gedit /etc/cwiid/wminput/gh3 

```

> 
Add:
# Wii Guitar profile for Frets on Fire
Classic.Down=KEY_ENTER #Strum
Classic.Dpad.X = ABS_X
Classic.Dpad.Y = ABS_Y
Classic.LStick.X = ABS_HAT0X
Classic.LStick.Y = ABS_HAT0Y
Classic.RStick.X = ABS_HAT1X
Classic.RStick.Y = ABS_HAT1Y
Classic.A = KEY_F1 #First Fret starting at top of wiiguitar
Classic.B = KEY_F2 #Second Fret
Classic.X = KEY_F3 #Third Fret
Classic.Y = KEY_F4 #Forth Fret
Classic.Minus = BTN_SELECT
Classic.Plus = BTN_START
Classic.Home = BTN_MODE
Classic.L = BTN_TL
Classic.R = BTN_TR
Classic.ZL = KEY_F5 #Fifth Fret
Classic.ZR = BTN_TR2

*Save.*



To let the guitar connect to your computer hold down the buttons 1 and 2 on your wiimote (which is attached to the guitar) and in the command line type
```
sudo wminput -c /etc/cwiid/wminput/gh3 
```

Now you just have to install Frets on Fire!
```
sudo apt-get install fretsonfire fretsonfire-game 
```

This didn't work on my laptop, so I had to download the file from the FOF website ([http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)), extract it and then just double click on "FretsOnFire".
Your now ready to rock! If you are wondering where all the songs are, they should be under "/FretsOnFire/data/songs". If not, well: "argh"....

---

### Post by gskarin on 2008-01-21
You are a god! Thank you so much!

:guitar:

---

### Post by onesojourner on 2008-02-01
nice write up. Now if only the guitar hero 3 controller was less than 80 bucks...

---

### Post by leonardoxiao on 2008-04-16
Now the gh3 guitar controller is less than 80 bucks. You probably can get it around $50-%60.
Time to get one?

---

### Post by maino82 on 2008-04-26
This is awesome, thanks!

Can anyone recommend a good, reasonably priced bluetooth adapter to use with this? I don't have one yet and am trying to figure out a decent one to get that will work well with Ubuntu without breaking the bank.

---

### Post by Schendje on 2008-04-27
Wow! It really worked! This is so cool! :lolflag:

Ubuntu couldn't find libcwiid0 and libcwiid0-dev though, I had to change them to libcwiid**1** and libcwiid**1**-dev. Maybe this is a Hardy thing? I don't know. I'm just happy it works. Thanks! :)

---

### Post by maino82 on 2008-04-28
Does anyone else have a problem with Frets on Fire hanging after you try this how-to when you load a song? It tells me "Tuning Guitar..." when I try and use the wii guitar controller and I have to do a ctrl-alt-backspace to get out of frets.

---

### Post by Azzco on 2008-05-24
> **maino82 said:**
> Does anyone else have a problem with Frets on Fire hanging after you try this how-to when you load a song? It tells me "Tuning Guitar..." when I try and use the wii guitar controller and I have to do a ctrl-alt-backspace to get out of frets.

It has nothing to do with this tutorial.
This tutorial makes the guitar fake some keys, like F1-5 and enter, the "Tuning Guitar..." part actually has nothing to do with the input device it's just a text instead of "Loading..."
RF-Mod has random phrases so it really can't be that. ;)

Anyways I was just wondering..```
sudo wminput -c /etc/cwiid/wminput/gh3
```
Do you really have to be root for that?
Could you just edit the post and remove sudo from that line please? And great thanks for sharing it would take me some time to dig up this info on my own. :)

Edit:
I also just noticed that this thread was started on my birthday :O
(Didn't want to add to my postcount for something as small as this :P)

---

### Post by yztlyrn on 2008-06-06
The wiimote works as a mouse, but when I apply the gh3 config file nothing happens.  The command line reports the following 2 errors.

Wiimote write error
Extension initialization error

Please help.

---

### Post by Darkade on 2008-06-06
It kindda worked for me. It's just that mouseemu "kidnaps" my keyboard. by that I mean that when I install mouseemu my keyboard doesn't work properly:
>The caps/numlock/scrolllock lights won't work
>sometimes my mouse won't work either

do you know a workaround for this? is there a way to prevent it from automatically start?
thanks:lolflag:

---

### Post by LitusMayol on 2008-06-18
Oh my god!

Really nice and so helpfull! Thanks dude!

---

### Post by ilowman on 2008-06-19
I just saw this great post yesterday and managed to set everything up first time so thanks! 
I did find that the version of fretsonfire from the website ran lot smoother than the one using apt.
I've changed the config file a bit so that you can strum up or down and also use the d pad on the Wii to navigate the menus in the game and go back by pressing the + button.

> 
# Wii Guitar profile for Frets on Fire
Classic.Down=KEY_ENTER #Strum
Classic.Up=KEY_ENTER
Classic.Dpad.X = ABS_X
Classic.Dpad.Y = ABS_Y
Classic.LStick.X = ABS_HAT0X
Classic.LStick.Y = ABS_HAT0Y
Classic.RStick.X = ABS_HAT1X
Classic.RStick.Y = ABS_HAT1Y
Classic.A = KEY_F1 #First Fret starting at top of wiiguitar
Classic.B = KEY_F2 #Second Fret
Classic.X = KEY_F3 #Third Fret
Classic.Y = KEY_F4 #Forth Fret
Classic.Minus = BTN_SELECT
Classic.Plus = KEY_ESC
Classic.Home = BTN_MODE
Classic.L = BTN_TL
Classic.R = BTN_TR
Classic.ZL = KEY_F5 #Fifth Fret
Classic.ZR = BTN_TR2
Wiimote.Left= KEY_LEFT
Wiimote.Up= KEY_LEFT
Wiimote.Down= KEY_DOWN
Wiimote.Right= KEY_DOWN



---

### Post by webbut on 2008-07-17
im new to Ubuntu and Linux. Im running Ubuntu 7.04 i was trying this how to and i ran into some trouble 1 sudo apt-get install libcwiid0 libcwiid0-dev lswm wmgui wminput 
returns an error saying that it cannont find the libwii0 so tried a few more times and skipped it. i got the wiimote working as a mouse both tilt and IR but when i did sudo gedit /etc/cwiid/wminput/gh3 and placed the commands in the empty file and tried to save it i got another error message saying that it could not save the file because cwiid/wminput/gh3 did not exist

---

### Post by pmsumner on 2009-02-06
Thank you for this guide, it pretty much worked straight away on Intrepid, couple of things didn't (the apt-get libwiithingie returned a "not found" error), but thank you!

---

### Post by meirm on 2009-03-12
Hi there,
all works ok on intrepid using the wiimote and nunchuck, but it fails to detect my wii guitar from Nyko.
I went back to the store and it works ok on Wii.
using wmgui, it says that there is no extention and therefore I do not see any feedback from the guitar.
I would love to make it work with FoF.

A diffence I found with the how-to is that on intrepid I have libbluetooth3 instead of libbluetooth2
and libcwiid1 libcwiid1-dev instead of libcwiid0 libcwiid0-dev

---

### Post by tonyr1988 on 2009-04-16
> **meirm said:**
> Hi there,
all works ok on intrepid using the wiimote and nunchuck, but it fails to detect my wii guitar from Nyko.
I went back to the store and it works ok on Wii.
using wmgui, it says that there is no extention and therefore I do not see any feedback from the guitar.
I would love to make it work with FoF.

A diffence I found with the how-to is that on intrepid I have libbluetooth3 instead of libbluetooth2
and libcwiid1 libcwiid1-dev instead of libcwiid0 libcwiid0-dev

I'm using Jaunty RC, and I'm getting the same problem. Everything with my Wiimote and bluetooth work (wmgui works flawlessly), but the guitar does nothing. In wmgui, it shows "No extension" when the guitar is plugged in, and clicking the guitar buttons does nothing.

I used libbluetooth3 instead of libbluetooth2 and libcwiid1* instead of libcwiid0*.

Any ideas? I'd love to get this working...

P.S. I'm using the guitar hero guitar that came with the GH:WT game for Wii.

---

### Post by NullHead on 2009-04-17
> **tonyr1988 said:**
> I'm using Jaunty RC, and I'm getting the same problem. Everything with my Wiimote and bluetooth work (wmgui works flawlessly), but the guitar does nothing. In wmgui, it shows "No extension" when the guitar is plugged in, and clicking the guitar buttons does nothing.

I used libbluetooth3 instead of libbluetooth2 and libcwiid1* instead of libcwiid0*.

Any ideas? I'd love to get this working...

P.S. I'm using the guitar hero guitar that came with the GH:WT game for Wii.

I found that the GH:WT guitar doesn't work. You need to use an older guitar. 

I just use my Aerosmith guitar.

---

### Post by tonyr1988 on 2009-04-17
> **NullHead said:**
> I found that the GH:WT guitar doesn't work. You need to use an older guitar. 

I just use my Aerosmith guitar.

Yeah, that kinda sucks that GH:WT guitars aren't supported (and I don't have any other Wii guitars).

I'm actually using WiiRemoteJ now. It's just a Java library, so you have to write your own "apps", but the API is extremely straightforward and feature-rich. It supports GH:WT guitars (even the touch pad buttons!), drums, etc.

---

### Post by piratekingdan on 2009-04-28
Is it possible to post more details, or upload exactly which files you're using?

I only have a Nyko and GH:WT guitar, as well as a drum set, and as of right now none of them work.

Please post your results.

Currently running Ubuntu Studio: Jaunty.

---

### Post by marshmallow1304 on 2009-07-07
I followed this guide.  Every time I press a button on the guitar controller, I get a black screen and get kicked back out to the login screen.  (Edit: It seems that it restarts gmd (same as "/etc/init.d/gdm restart"))  It happens even when I'm not in the game.  The Wiimote by itself works fine.  It also doesn't happen when I connect with wmgui.

GH3 Controller
Jaunty 64-bit

---

### Post by tonyr1988 on 2009-07-07
> **marshmallow1304 said:**
> I followed this guide.  Every time I press a button on the guitar controller, I get a black screen and get kicked back out to the login screen.  It happens even when I'm not in the game.  The Wiimote by itself works fine.  It also doesn't happen when I connect with wmgui.

GH3 Controller
Jaunty 64-bit

That's a crazy bug -- it completely kills X? Like I said, I'm using the WiiRemoteJ library now, and it's working beautifully with my GHWT guitar, but I'm sure I can make some tweaks to get it to work with the GH3 guitar. I'm not sure it will work on a 64-bit machine, but I'll look into it.

Are you just wanting to use this with Frets on Fire? Are you using FoFiX (or similar), or just vanilla FoF?

I'll try to get back with you in a few days and we can start experimenting with different things to get this working for you -- feel free to send me annoying PMs to remind me if I haven't contacted you by this weekend. :)

---

### Post by marshmallow1304 on 2009-07-08
> **tonyr1988 said:**
> 
Are you just wanting to use this with Frets on Fire? Are you using FoFiX (or similar), or just vanilla FoF?


I was trying to use it with FoFiX.
I used the second version of /etc/cwiid/wminput/gh3 on this thread.

I tried it again with the GH3 guitar with the same result.
I tried it with the GHWT guitar.  The buttons on the guitar didn't cause the crash, but the buttons on the actual Wiimote did.  The guitar buttons didn't seem to do anything at all.  wmgui shows no extension.
I have yet to test the GHWT drums.


Edit:  I fixed the issue by removing the following two lines
```
Classic.Dpad.X = ABS_X
Classic.Dpad.Y = ABS_Y
```
See post 6 on [this thread]("http://ubuntuforums.org/showthread.php?t=1219645") for more info.

---

### Post by piratox on 2009-10-02
[LEFT]The guitar from GHWT can be used on linux. Just build the latest revision of cwiid :). This topic [http://www.mattcutts.com/blog/linux-wii-balanceboard/](http://www.mattcutts.com/blog/linux-wii-balanceboard/) explain how.[]("http://www.mattcutts.com/blog/linux-wii-balanceboard/")[/LEFT]

---

### Post by reswob on 2010-01-01
Argh, follow all instructions here and the guitar from GHWT still won't work.  Checking for the latest cwiid gets me this:

sudo apt-get install wminput wmgui lswm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wminput is already the newest version.
wmgui is already the newest version.
lswm is already the newest version.

The Wiimote seems to connect just fine.  When I run wmgui and connect the wiimote, I can click all the buttons and all the correct labels get highlighted.  When I run wminput, I get:

sudo wminput -c /etc/cwiid/wminput/gh3
Put Wiimote in discoverable mode now (press 1+2)...
Ready.

But when I start FOF, none of the buttons on the guitar work.

Any ideas, other suggestions, pointers to other how tos?

Also, someone metioned they were using a different library, WiiRemoteJ.  How do I install that and use it?

Thanks.

---

### Post by sidrit on 2010-02-09
> **piratox said:**
> [LEFT]The guitar from GHWT can be used on linux. Just build the latest revision of cwiid :). This topic [http://www.mattcutts.com/blog/linux-wii-balanceboard/](http://www.mattcutts.com/blog/linux-wii-balanceboard/) explain how.[]("http://www.mattcutts.com/blog/linux-wii-balanceboard/")[/LEFT]

hey there man.
can you please give some extra info if possible?
as far as the script used to set it up.
i installed cwiid from github just fine and the controller connects as a mouse per default.
when given the GH3 config file though it's simply dead.

any help would be appreciated.

---

### Post by sidrit on 2010-02-10
ooooooookay.
finally got it sorted.

downloaded the source of cwiid 0.6.
patched the hci_red function.
patched and removed the decode function and add the headers for the ghwt and compiled. now it works.

here's a write-up about it 
[http://sidrit.wordpress.com/2010/02/10/frets-on-fire-with-guitar-hero-world-tour-ghwt-on-ubuntu/](http://sidrit.wordpress.com/2010/02/10/frets-on-fire-with-guitar-hero-world-tour-ghwt-on-ubuntu/)

---

