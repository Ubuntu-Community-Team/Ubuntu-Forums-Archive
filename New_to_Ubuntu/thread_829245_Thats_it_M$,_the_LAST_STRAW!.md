---
title: "Thats it M$, the LAST STRAW!"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Valk01 on 2008-06-14
Alright. this morning, my desktops xp install took a massive dump and for me, its the LAST BLOODY TIME. i format my pcs a few times a year to keep them clean and zippy. last time i did it, the desktop wouldnt let me install any version of firefox and support the mousewheel.. 

maybe a dumb reason to format an os, but it just would not work, no matter what fix i tried.. and belive me, i spent a good week trying to get the thing to work, the browser settings, drivers and global settings.. 

i actully did it twice that weekend, cause the second time, my sound would not work at all.. drivers installed ok, but still no sound device. onboard or add on. format again lol...

....

desktop has been good lately, but died when one of my sticks of ram went, sent them in for rma and got a replacment, then it runs for weeks and weeks playing games and doing the anime thing only to bsod on my this morning... bam, out of nowhere.. 

so now, its telling me, wsock32 not found... cants tart firefox and a few other apps. ie starts, wont go anywhere.. no outside access at all, yet somehow peer guardian manages to update itself.. 

blarg. 



so.... /rant.. 

im gonna give linux a shot again. I have messed with it on and off a few times with different disto's debian, yoper, ubuntu ect but never really delve into learning more intricate things with the command line.

I can make it work just fine on the desktop.. no problem there, but i need help getting it to work on my tablet pc laptop.

I have a tc4200, there was a pretty good guide out there for making various functions work under linux, but that site seems to have expired or died off or some such thing. 
mine has a wacom digitizer and the swivel hinge for changing modes. there are obviously the soft buttons and vaious other buttons. 
im all that interested in those, but i wanna know if there are alternatives to xp tablets input panel for linux. 

I know people swear by M$ onenote, but i could care less for it. i use journal most of the time since its lighter and plays nicer with the 345675787 other programs i run on the thing at once. 

otherwise, drawing is important, and some light handwriting recognition would be handy. i dont ink that much since im pretty damn fast on this little keyboard now. its actully one of the better ones on a 12" notebook. 
obviously ill need h264 and xvid support, and if i can get it, a very minimalistic shell. limited desktop space after all. 

ahh. i know it seems like i want i want i want.. ive actully done a fair bit of reading about this and people have met with varied success. a place to start is all i really need..

last time i tried it. ubuntu started but no wacom.. tried kubuntu, started and supports wacom but dosent support my intel graphics? 
blarg. semi linux noob here so be gentle.

---

### Post by cariboo on 2008-06-14
Have a look at Linux Mint, it pretty lightweight, its based on Ubuntu and if you don't have any really weird hardware it'll set everything up automagically.

Jim

---

### Post by Valk01 on 2008-06-14
there is a few questionable items that i had a hard time finding aside from the hp website heh. 
cmedia audio, TI card reader ect. ill give that a look, thanks man =) 
I just find it really weird how ubuntu didnt support my gma 900 onboard graphics. took my 7900gt np, and my old pos ati, but not that lol. 

which driver does the gma base on? since i could run the config at startup to load a bunch of shiz but couldnt find it on there. tried 810i, which got me the furthest, showed the start up screen, but died before getting to a desktop.

---

### Post by kerry_s on 2008-06-14
sounds like your running stuff ms don't agree with.
just changing to linux might not solve your problems, it's worth it, though, you might be just changing the problems on 1 os to , problems on a different os.

reading through your rant, it sounds like your problems are from hardware issues, keep in mind most hardware is built for ms, so you may have a equal amount of problems in linux.

try different linux versions, they all have different ways of doing things.
so get yourself a stack of cdr's/cdrw's, head over here->
[http://distrowatch.com/](http://distrowatch.com/)

work your way down the top 100 list on the right. make sure you burn as a image at 4x for the best results.

---

### Post by Valk01 on 2008-06-14
well, my motherboard is definitly in need of replacment, but it will work perfectly for a while then just take a dump with no explanation heh. 

im not really running anything ms hates. both are pretty average setups and aged by todays standards but meh. 

this time ill actully force myself to just run linux for a while. i dont game very much at all anymore. basicly, i use both pcs to surf, collect anime, chat and general doc stuff. 

the tablet pc is more important though, since its my primary. i use it 99% of the time.

iw ish that tc4200 gentoo site was still up. really sucks it died =(

---

### Post by arpanaut on 2008-06-14
[http://ubuntuforums.org/showthread.php?t=765915&highlight=tc4200](http://ubuntuforums.org/showthread.php?t=765915&highlight=tc4200)

anda:[http://ubuntuforums.org/showthread.php?t=780464&highlight=tc4200](http://ubuntuforums.org/showthread.php?t=780464&highlight=tc4200)

Maybe get you going?

---

### Post by ibuclaw on 2008-06-14
I agree with kerry_s, it definately sounds like a hardware problem.

Although, there are some really cool distributions out there.
But it really does depend on taste more than anything.

The best at the moment, really, is [Ubuntu 8.04]("http://www.ubuntu.com/") and [Mandriva One Spring 2008]("http://www.mandriva.com/").

Although, recommended derivatives of Ubuntu would definitely be [Linux Mint]("http://www.linuxmint.com/") or [Kiwi Linux]("http://kiwilinux.org/kiwi/en/").

Regards
Iain

---

### Post by Dougie187 on 2008-06-14
I actually have a toshiba tablet r10 pc. and my wacom has been working since dapper without any trouble. Granted in Fiesty Fawn (when it started) I had to add some stuff into xorg.conf but its not that difficult. I think there is also a package called wacom-tools to help with the use of wacom tablets.

They stopped adding it by default into the configuration, but its not hard to get it in. 

I will look around and see if I can help getting mine set up first. I kinda stopped using mine a while ago, but there are quite a few programs to use it with. Gournal, Xournal, and there are more. I know there are threads devoted to tablet software here on the forums, just dig around a little and you should find thing.

EDIT: After you install the wacom-tools package, they have a howto.html file that gets installed to /usr/share/doc/wacom-tools if you open that up it has a lot of useful information on what to add to your xorg.conf file to make your tablet work. Also, you can type 
```
man wacom
```
for help with it.

---

### Post by Valk01 on 2008-06-14
awsome, thanks for the links and the suggestions. ive downloaded a few versions of ubuntu/kubuntu and im gonna try out the linux mint as suggested. looks nice. 

i know there are probably some hardware issues with that desktop atm. frankly im suprised the mobo still works for the abuse i put on it with the watercooling heh. im starting to actully have a hate for crucial ram. since ive rma'd two sets and i just keep buyin em cause they are like $20 lol. 

i have 6 gigs of crucial ram, 4 of which are replacments... funny. 

ah well. the tablet is flawless. in fact, it has been the most trouble free pc ive ever owned. I had to make my own install disc from one i downloaded *with my legit sticker underneth of course* but i really like xp tablet edition. I hear vista business is way better, but i doubt my little dothan can take that. 

linux has always been interesting to me, just never diciplined myself to go for it at length =)

---

### Post by agurk on 2008-06-14
> **Valk01 said:**
> which driver does the gma base on? since i could run the config at startup to load a bunch of shiz but couldnt find it on there. tried 810i, which got me the furthest, showed the start up screen, but died before getting to a desktop.

I have a GMA950 which used the 'i810' driver up to a few weeks ago, when I switched to 'intel' instead. Might be worth a try.

**Edit:** You might want to check out netbook-remix: [http://www.markshuttleworth.com/archives/151](http://www.markshuttleworth.com/archives/151)

---

### Post by Dougie187 on 2008-06-14
Alright,
I just got my tablet working. I did it in ubuntu 8.04 just so you know.

Basically, you have to install wacom-tools first so you open a terminal and type:
```
sudo apt-get install wacom-tools
```

After you get this installed, you have to edit your xorg.conf file.
but first you want to back up your xorg.conf file. Still in a teminal type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If you have any issues, just type:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
this will revert all your changes incase you mistype something. 

Now to edit the file, push ALT+F2 and type
```
gksudo gedit /etc/X11/xorg.conf
```

Then you need to add the following right after the last InputDevice section.

```

Section "InputDevice"
        Driver        "wacom"
        Identifier    "stylus"
        Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
        Option        "Type"          "stylus"
        Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver        "wacom"
        Identifier    "eraser"
        Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
        Option        "Type"          "eraser"
        Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver        "wacom"
        Identifier    "cursor"
        Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
        Option        "Type"          "cursor"
        Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

```

And you need to add the following lines in the Section "ServerLayout" section.
```

        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"

```

After you finish this, hit CTRL+ALT+Backspace to restart your xserver. Now, you should be able to use your tablet. If you have any issues with logging in, or your Xserver fails hit CTRL+ALT+F1 and login to the terminal, then revert your xorg.conf file back to the original and try again. Also, you can read the howto I mentioned earlier for more information.

Let me know if this helps.

---

### Post by Valk01 on 2008-06-14
awwwwsome. that will be pretty easy then heh. done this before trying to get multiple monitors to work so should be good. 

next question would be, is there an event logger that you can use to track the various buttons on the laptop? like, can you figure out what events occur from the soft buttons and give them scripts to run?

probably a dumb noob question but im curious.

---

### Post by Dougie187 on 2008-06-14
yes there is. if you open a terminal and type xev it will give you a little window. if you push a button then it will tell you what keycode is assigned to that button, and you can use it to do assign a task.

---

### Post by Valk01 on 2008-06-14
great. that will help a lot in getting the little buttons working. followed that guide for running live cd off usb and right now im in 804 via usb. its very zippy i have to admit, WAYYYY better than the 606 live option.
so far, everything works from what ican tell, although i havent messed around with wacom too much. 

gonna go buy a another 4gb drive and mess around with some installs.

---

### Post by Dougie187 on 2008-06-14
Well good luck with everything. let us know if you have any issues. im sure people will be willing to help.

---

### Post by Fenris_rising on 2008-06-14
welcome to the family. my advice make notes and lots of them everytime you do something new or install/fix something. patiance is also a virtue at times there may be trouble ahead but whilst theres the ubuntuforum you'll not lack for help and advice.......theres a song there im sure :lolflag:

---

### Post by Valk01 on 2008-06-14
alright. so that works so far. got the wacom to work easily enough. now to figure out the pressure sensitivity and find a working handwriting input tool. works great as a mouse ^^

still running the live cd off usb, so not sure how much i can edit but its working well. 
running the linux mint but i will probably go to ubuntu instead since this looks a little TOO basic.

---

### Post by Valk01 on 2008-06-14
ok. now that i got it installed to my other flash drive, im having the problem with x just hanging at a orange screen. the sudo rm /tmp/.X0-lock doesnt seem to work though. says no such file or directory. =(

---

### Post by st33med on 2008-06-14
> **agurk said:**
> I have a GMA950 which used the 'i810' driver up to a few weeks ago, when I switched to 'intel' instead. Might be worth a try.

**Edit:** You might want to check out netbook-remix: [http://www.markshuttleworth.com/archives/151](http://www.markshuttleworth.com/archives/151)

Ubuntu uses the Intel driver by default...

(honk)

---

### Post by Valk01 on 2008-06-21
Alright, well shifting gears a little, i decided to stop trying this on my laptop for the time being due to software support and my limited experience heh. 

ive moved to wanting this on the desktop though, to make dealing with my tb's of various storage easier and general use since i dont really game anymore. 

gonna dual boot, but i cant get the live distro to work with my video card?
specs.

Core2 Duo 2180@4ghz
2x1gb Ballistix 6400 2x1gb Tracer 6400
Nvidia 650i ultra *xfx*
Nvidia 7900GT *evga*

everything seems to work EXCEPT the nvidia for some reason. i popped in my old ati 2mb rage and it started right up, hell, found the native resolution of my lcd tv even. but my 7900 just gives me a bunch of asci random crap and wont even display a command line. 
is there  a way around this? if i install the os on the ati card, can i fix this problem realitivly easily?

Laptop all worked too. after doing the wacom stuff it worked almost completly, minus the soft buttons and the rotate. couldnt even get an event from that. 
pen pressure didnt work either but im sure there is a setting somewhere i can fix that with. 
I wanna try it more, but no open canvas and photoshop is kinda pushing me away. i know ic an wine it, but the lappy is just a single core dothan and i dunno what the performence loss will be like considering both programs lag bad in high res anywhere with penabled heh. 

anyway, thank you for all the help you guys have given me so far, and a pre thanks for the future issues im bound to have =).

---

