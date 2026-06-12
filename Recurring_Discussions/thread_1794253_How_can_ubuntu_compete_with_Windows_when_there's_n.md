---
title: "How can ubuntu compete with Windows when there's no quality DVD software?"
date: 2011-06-30
forum: Recurring Discussions
---

### Post by nrundy on 2011-06-30
Apparently I can't purchase PowerDVD for linux because ubuntu has not paid off some hollywood DVD consortium. Totem is a piece of crap that no matter what I try will not play commercial DVDs. After I installed the libraries that are supposed to allow DVD play on ubuntu I'm able to get VLC to play DVDs. But VLC is kinda ridiculous. I can't even figure out how to rewind a movie. It has no rewind button, it doesn't display what chapter or title your watching. I can fast-forward, but there's no button to make it play normal speed once I've started fast-forwarding. It's an ergonomic-use nightmare.

I would prefer to pay for Ubuntu (say $30, like Mac OS costs) just so ubuntu can pay somebody off so that it can fully support DVD and other restricted  codecs. Then professional quality software like Cyberlink's PowerDVD could be made to work with Ubuntu. 

I mean, if I want to be able to sit down and watch a DVD (with rewind capability etc) or stream a movie, I can't do it with ubuntu. Yet this is a major function of compouter use. It's frustrating because operationally, ubuntu blows windows away. But functionally (with app choices) it's lacking bigtime.

Is the only solution to charge money for ubuntu so canonical can pay off the right people? If ubuntu had even a modicum of the app support Windows has, Windows would be a dying beast.

---

### Post by magmon on 2011-06-30
Lol, DVD players.

---

### Post by JRV on 2011-06-30
To ebable most video codecs run this command:
```
sudo apt-get install ubuntu-restricted-extras
```

ubuntu-restricted-extras also installs Java and Flash.

You also may want to:
```
sudo apt-get install vlc
```

The following script will install DVD playback.

Copy the script into a file in your home directory and name it "installDVD.sh".

Before you run it you must make it executable with the command:
```
chmod +x installDVD.sh
```
Then read the comments for proper syntax to execute the command.

```

#!/bin/bash
#
# Name installDVD.sh
#
# Script to install libdvdcss2 and w32/64/codecs to  
# allow for the playback of DVDs.
#

# Syntax: sudo ./installDVD.sh VERSION 32/64
#
# VERSION is the version name, all lower case (lucid, natty, etc.)
# 32/64 is 32 for a 32 bit system or 64 for a 64 bit system.
# If 32/64 is blank it defaults to 32 bit.

# This script must be run only once.

echo "deb http://archive.ubuntu.com/ubuntu "$1" universe multiverse" >>/etc/apt/sources.list
echo "deb-src http://archive.ubuntu.com/ubuntu "$1" universe multiverse" >>/etc/apt/sources.list

apt-get update

wget http://www.medibuntu.org/sources.list.d/$1.list --output-document=/etc/apt/sources.list.d/medibuntu.list

apt-get update
apt-get install medibuntu-keyring

apt-get update

if [ "$2" = "64" ]; then
    sudo apt-get install w64codecs libdvdcss2 hot-babe
else
    sudo apt-get install w32codecs libdvdcss2 hot-babe
fi

```

---

### Post by haqking on 2011-06-30
> **nrundy said:**
> Apparently I can't purchase PowerDVD for linux because ubuntu has not paid off some hollywood DVD consortium. Totem is a piece of crap that no matter what I try will not play commercial DVDs. After I installed the libraries that are supposed to allow DVD play on ubuntu I'm able to get VLC to play DVDs. But VLC is kinda ridiculous. I can't even figure out how to rewind a movie. It has no rewind button, it doesn't display what chapter or title your watching. I can fast-forward, but there's no button to make it play normal speed once I've started fast-forwarding. It's an ergonomic-use nightmare.

I would prefer to pay for Ubuntu (say $30, like Mac OS costs) just so ubuntu can pay somebody off so that it can fully support DVD and other restricted  codecs. Then professional quality software like Cyberlink's PowerDVD could be made to work with Ubuntu. 

I mean, if I want to be able to sit down and watch a DVD (with rewind capability etc) or stream a movie, I can't do it with ubuntu. Yet this is a major function of compouter use. It's frustrating because operationally, ubuntu blows windows away. But functionally (with app choices) it's lacking bigtime.

Is the only solution to charge money for ubuntu so canonical can pay off the right people? If ubuntu had even a modicum of the app support Windows has, Windows would be a dying beast.

vlc, totem, xine and mplayer all work fine for me.

and in VLC you just drag the slider backwards ?

---

### Post by nrundy on 2011-06-30
did all that. like i said, totem still wont work to play DVDs. Totem won't play most online video streams either,.

---

### Post by danbuter on 2011-06-30
You probably need libdvdcss2. Google on how to get it.

---

### Post by haqking on 2011-06-30
see here

[http://ubuntuforums.org/showthread.php?t=1790725](http://ubuntuforums.org/showthread.php?t=1790725)

---

### Post by nrundy on 2011-06-30
guys, let's pretend that I could get totem to play DVDs. It still doesn't fix the usability difference between Totem/vlc and PowerDVD. They just different quality of software, PowerDVD being a lot more usable and understandable how to use.

---

### Post by haqking on 2011-06-30
> **nrundy said:**
> guys, let's pretend that I could get totem to play DVDs. It still doesn't fix the usability difference between Totem/vlc and PowerDVD. They just different quality of software, PowerDVD being a lot more usable and understandable how to use.


Well i am sure the majority of Linux users out there enjoy DVD playback and in a multitude of different apps which they can choose at will without paying for them.

So it begs the question, why dont you just use windows then ? ;-)

and amost windows users i know use VLC in windows anyways ;-)

there are so many to choose from and ive never had any issues with any of them, so it is not a product or Linux issue per se, more of a machine configuration issue, codecs, hardware etc, all of which you could and more likely to in windows ?

---

### Post by nrundy on 2011-06-30
> **haqking said:**
> Well i am sure the majority of Linux users out there enjoy DVD playback and in a multitude of different apps which they can choose at will without paying for them.

So it begs the question, why dont you just use windows then ? ;-)

and amost windows users i know use VLC in windows anyways ;-)

I explained in my original post why i prefer not to use windows: because ubuntu is operationally superior.

---

### Post by oldsoundguy on 2011-06-30
Power DVD is a really horrible program for viewing DVD's on Windows .. Media Player Classic (which is FREE and comes with every codec known to man .. also FREE) is a MUCH better choice for Windows.

And what is it with people that have to have it all wrapped up in a neat one size fits all package in order to "think" (yea, THINK) that the program is NUMBAH UN!!

VLC is a monstrously good DVD program,  but you have to be able to walk and chew gum to install it. (yea, THINK)  I even have some Windows user friends that liked the VLC I use on Linux so much that they installed the Windows version on their boxes. (again FREE)

---

### Post by haqking on 2011-06-30
> **nrundy said:**
> I explained in my original post why i prefer not to use windows: because ubuntu is operationally superior.

do you not think it is your own configuration/machine etc that is the problem and not the software or the fact that "If ubuntu had even a modicum of the app support Windows has, Windows would be a dying beast." issue ?

I mean we all have things that dont work from time to time but we get them to eventually ? If you are in windows and PowerDVD didnt work how much real support do you think you will get (after a 1000 emails and phone calls ? to cyberlink who will blame MS and MS who will blame cyberlink

and i am still stuck on the fact you cant rewind in VLC ? it is a button you drag backwards (it rewinds) and playability and support is usually lack of codecs, which are all covered on this forum in various places

---

### Post by nrundy on 2011-06-30
> **oldsoundguy said:**
> Power DVD is a really horrible program for viewing DVD's on Windows .. Media Player Classic (which is FREE and comes with every codec known to man .. also FREE) is a MUCH better choice for Windows.

And what is it with people that have to have it all wrapped up in a neat one size fits all package in order to "think" (yea, THINK) that the program is NUMBAH UN!!

VLC is a monstrously good DVD program,  but you have to be able to walk and chew gum to install it. (yea, THINK)  I even have some Windows user friends that liked the VLC I use on Linux so much that they installed the Windows version on their boxes. (again FREE)

look,I like VLC. And I am not claiming PowerDVD is the greatest player ever. What im saying is that it is a LOT easier to get around a DVD while playing it when using PowerDVD than it is when using VLC. When talking about a specific purpose: playing DVD movies, PowerDVD has better controls and easier to understand navigation than VLC. For example, Far as i can tell there is no rewind button in VLC.

---

### Post by haqking on 2011-06-30
> **nrundy said:**
> look,I like VLC. And I am not claiming PowerDVD is the greatest player ever. What im saying is that it is a LOT easier to get around a DVD while playing it when using PowerDVD than it is when using VLC. When talking about a specific purpose: playing DVD movies, PowerDVD has better controls and easier to understand navigation than VLC. For example, Far as i can tell there is no rewind button in VLC.


I think it is late and i must be not reading things properly, NO there is no REWIND button, but there is a slider bar which you drag.....it does the same thing just not a button you click ?

if it is the lack of a button then that is a UI thing which videolan are responsible for

and on that note i am gonna go watch a DVD...in VLC....and pause, fast forward and rewind at will just cause i can ;-)

---

### Post by beew on 2011-06-30
> **oldsoundguy said:**
> 
  I even have some Windows user friends that liked the VLC I use on Linux so much that they installed the Windows version on their boxes. (again FREE)

Actually VLC works better in Linux than it is in Windows in my experience.

---

### Post by tgm4883 on 2011-06-30
So buy the Fluendo DVD player through the Ubuntu Software Center for $24.95 and be done with it?

:EDIT:

Link for those who don't want to purchase though the Software Center

[http://www.fluendo.com/shop/product/fluendo-dvd-player/](http://www.fluendo.com/shop/product/fluendo-dvd-player/)

---

### Post by beew on 2011-06-30
> **nrundy said:**
>  Totem won't play most online video streams either,.

I agree, that's why I don't use Totem for streaming most online videos. Install the gecko-mediaplayer, works as good as if not better than anything you can find in Windows for online streaming (like divx)

Totem however is excellent in streaming quicktime stuffs like apple trailers (gecko-mediaplayer is a bit flaky for quicktime). The quality and speed is much better than quicktime player for Windows.

EDITED:

If you want rewind button and other bells and whistles (which I don't really care as long as I get good quality playback and I suspect I am not alone) try XBMC.

---

### Post by snowpine on 2011-06-30
Also keep in mind the Hollywood movie you're watching on that DVD was probably made using Linux. Those supercomputers at Pixar, Weta, etc. aren't running Windows! :)

---

### Post by cariboo on 2011-06-30
That really doesn't solve the op's problem, DVD play in Ubuntu works quite well, I don't know why the op is insisting on buying a commercial DVD playback program when the codec's are installable by running the install script in /usr/share/doc/libdvdread4:

```
sudo install-css.sh
```

---

### Post by nerdy_kid on 2011-06-30
Search for Fluendo DVD Player in the software center if you want to buy a dvd player.  I use totem, and it works fine for me.  VLC also works for me (you do know you can customize the toolbar?) as does KDE's DragonPlayer.  Also SMPlayer is good.

---

### Post by Tibuda on 2011-06-30
> **snowpine said:**
> Also keep in mind the Hollywood movie you're watching on that DVD was probably made using Linux. Those supercomputers at Pixar, Weta, etc. aren't running Windows! :)
and it matters because... no, it does not matter.


> **cariboo907 said:**
> That really doesn't solve the op's problem, DVD play in Ubuntu works quite well, I don't know why the op is insisting on buying a commercial DVD playback program when the codec's are installable by running the install script in /usr/share/doc/libdvdread4:

```
sudo install-css.sh
```

That doesn't solve the op's problem either. He is not complaining about the codecs, but about teh players interface.

---

### Post by beew on 2011-06-30
> **Tibuda said:**
> and it matters because... no, it does not matter.




That doesn't solve the op's problem either. He is not complaining about the codecs, but about teh players interface.

I am not sure most people care about interface a great deal as long as the player does its job. Moreover that is rather subjective, I hate apps that have a lot of buttons that I don't use anyway. If OP wants something really baroque he can always try XBMC.

---

### Post by james_xxx on 2011-06-30
nrundy,

I believe the best advice for you is to learn to google, and learn to read documentation.

When you step into the world of FOSS, you do your own research first, THEN seek help in forums like this one for the problems you could find no solution to, not the other way around.

There is a LOT of documentation explaining how to install support for DVD playback/DVD menus. It is not included by default, because it involves the use of patent-encumbered libraries. However, installing these libraries is trivially easy.

Also, there are almost more media players that can be used in GNU/Linux than I can count, many of which I would take over Power DVD any day.

You might want to pay a visit to this site, as it is one place where you can find the DVD software you are looking for:

[Medibuntu]("http://medibuntu.org")

Good luck!

P.S. There are some media players I could recommend (all of them front-ends for mplayer)... my favorite is SMPlayer, or if you prefer a GTK-based media player designed for use with Gnome, there is gnome-mplayer. Both of these can be installed from the repositories. You might also want to consider UMPlayer, which you can find here: [UMPlayer]("http://www.umplayer.com/")

---

### Post by dmizer on 2011-07-01
How about using mouse gestures?

[http://wiki.videolan.org/Mouse_Gestures](http://wiki.videolan.org/Mouse_Gestures)

Edit:
If you don't like gestures, click "view" -> "interface" and add buttons for fast forward and rewind (and/or anything else you might like to have).

---

### Post by nrundy on 2011-07-01
> **haqking said:**
> I think it is late and i must be not reading things properly, NO there is no REWIND button, but there is a slider bar which you drag.....it does the same thing just not a button you click ?

if it is the lack of a button then that is a UI thing which videolan are responsible for

and on that note i am gonna go watch a DVD...in VLC....and pause, fast forward and rewind at will just cause i can ;-)

A slider does not do the same thing. A rewind button usually has multiple speeds as well. I can tap rewind button and go back like 15 seconds then hit Play to return to normal speed with other DVD players. Using the slider in VLC is not as precise. using the slider, When I try to go back 15 seconds cause I missed something that was said, I end up going back 3 minutes.

---

### Post by nrundy on 2011-07-01
> **tgm4883 said:**
> So buy the Fluendo DVD player through the Ubuntu Software Center for $24.95 and be done with it?

:EDIT:

Link for those who don't want to purchase though the Software Center

[http://www.fluendo.com/shop/product/fluendo-dvd-player/](http://www.fluendo.com/shop/product/fluendo-dvd-player/)

Thanks! I'm going to check this out.

---

### Post by SeijiSensei on 2011-07-01
sudo apt-get install smplayer

It has a variety of options for navigation; basically it's just sending keystroke sequences to mplayer.  There are buttons for +/- 30 seconds, but right-clicking on the video will give you more fine-grained options.  You can also jump to a particular timestamp.

---

### Post by haqking on 2011-07-01
ha ha this thread has really taken a spiral downwards...LOL ;-)

Well i hope you get your DVD playback issues sorted and find a suitable UI for your tastes, apparenlty PowerDVD was available for linux at one point, not sure what happened to it ?

whatever we use there will always be some issues somewhere with someone about something, that is part of what drives development ;-)

Personally i like VLC, it does everything i need it to and works fine on my hardware.

Best of luck finding your answers ;-)

---

### Post by nerdy_kid on 2011-07-02
also, you might like xine -- it has a more powerdvdish interface.

---

### Post by wolfen69 on 2011-07-02
When I used to use windows, I used vlc for dvd's, just like I do in linux. When I watch a movie, I hit play and watch it. I don't need pointless controls that powerdvd has. I think most people will survive without powerdvd. ;)

---

### Post by khelben1979 on 2011-07-02
> **nrundy said:**
> Totem is a piece of crap that no matter what I try will not play commercial DVDs.

I can play DVD:s with Totem and it works fine. If you call Totem "crappy software", you should consider doing some deeper research in the world of open source software instead of just compare it off to some badly written commercial software like PowerDVD.

In my opinion, software that works and that is free, if it lacks features, add them yourself and stop complaining, that's mostly how things works over here in the open source land.

Besides, if Totem does not work, you got a lot of alternatives and they are open source too, or go for the Fluendo software which have been suggested in this thread.

---

### Post by oldsoundguy on 2011-07-02
Touched on .. let us elaborate a tad.

FREE software in the FOSS area is getting better day by day.  There are gangs of DVD playing software programs.  NONE of them cost a dime, but do cost your time.
THE super advantage of running Linux of any kind is that no matter what third party or add on program you install, it will not grab your operating system in a strangle hold.  It can be removed with a couple of clicks in Synaptic and it is gone without doing any harm to the OS.  Then load something else in there and give IT a try.  And if that  is not to your liking .. pull the plug on it and try another.  

Makes life grand as you now can customize your experience!!

---

### Post by cgroza on 2011-07-02
> **khelben1979 said:**
> 
in my opinion, software that works and that is free, if it lacks features, add them yourself and stop complaining, that's mostly how things works over here in the open source land.

+1

---

### Post by Rasa1111 on 2011-07-02
Don't know what the problem is.

I can insert any DVD and it will open right up in whatever I choose.
VLC, UMPlayer, Mplayer, etc etc. No problems. 

To get it to work properly you need one single command. 

When I wanted to know how to do it, I asked the almighty google..
Google answered my question, and I can now play any DVD you can throw at me.

Again,
What's the problem? 

Other than being unsure of what your going on about?

Really, it's very simple. 

usually I would post up the link that would help you out..
But I think it would do you some good to find the very simple solution on your own. 

Good luck.

---

### Post by WinterMadness on 2011-07-02
> **nrundy said:**
> did all that. like i said, totem still wont work to play DVDs. Totem won't play most online video streams either,.

tbh i always hated totem. just use vlc.

if you think the layout is confusing you can gto vlc's website and download a skin to make it look like windows media player

---

### Post by GWBouge on 2011-07-03
> **nrundy said:**
> A slider does not do the same thing. A rewind button usually has multiple speeds as well. I can tap rewind button and go back like 15 seconds then hit Play to return to normal speed with other DVD players. Using the slider in VLC is not as precise. using the slider, When I try to go back 15 seconds cause I missed something that was said, I end up going back 3 minutes.

Crtl + Left/Right: Jump 1 minute
Alt + Left/Right: Jump 10 seconds

And someone mentioned mouse gestures, too ...
Right-Click + Drag Left/Right: Jump 10 seconds

And you can goto View -> Customize Interface and drag the Step Forward/Backward buttons for a 10 seconds jump.

---

