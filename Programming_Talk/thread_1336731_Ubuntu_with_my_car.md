---
title: "Ubuntu with my car"
date: 2009-11-24
forum: Programming Talk
---

### Post by Jefferythewind on 2009-11-24
Hello everybody,
  I have a little topic for discussion.  I have a car, 1978 datsun 510 wagon.  I want to put a new stereo system and other things into it.  I was thinking about getting a little computer  in the car, preferably linux and ubuntu.  I was wondering if anyone out there has ever computerized a car before?
  There are a few little alerts in the car, like for seat belt and when the door is open.  I am also wondering if anyone knows any kind of integrated circuit that can handle these 12 volt signals from the different indication signals?  This integrated circuit would preferably be programmable through the computer to do different things for each signal.  Like for example, if your door is open, the computer could play over the speakers: "the left front door is ajar." 
  Anyway i was wondering if the people in the ubuntu community have any experience with something like that.

Thanks!

---

### Post by froggyswamp on 2009-11-25
That's a great idea I think.
I think you should go ahead and also add a video cam pointing to the road ahead with face recognition software, you see, since the car isn't exactly new your breaks might stop functioning and you might drive over some people and the software would automate the toll identification process by counting them and trying to do the identification of those people "on-the-fly", in real time (Linux supports realtime to a degree, make sure you use the latest kernel).

---

### Post by hoboy on 2009-11-25
Good question

---

### Post by cascade9 on 2009-11-26
I've built a computer for a car, but it didnt integrate any of the cars systems. Just an old p3 turned into a media player for the car.

---

### Post by gil_johnson on 2009-11-26
> **Jefferythewind said:**
> 
[...]
I was wondering if anyone out there has ever computerized a car before?
  [...]
  Anyway i was wondering if the people in the ubuntu community have any experience with something like that.

Thanks!

Jeffrey,

I considered it but didn't do it, so no experience, but I did a lot of looking. Try a search on "car computer" and you'll turn up a lot of possibilities, including "fully ruggedized" tiny computers. A search on "car computer mods" will turn up examples of people who've done it, and "how-to" pages.

The Ubuntu community may not be large enough to include many people with this interest, but can I expand the topic to "I put a computer in my..."? Are there any people who have put computers in unusual places?

Gil

---

### Post by Kalibur on 2009-11-26
I am seriously on the path to purchase and install an in car computer for media, internet and Navigation.  There is a few on the market(ebay) running windows CE/xp and some other OS.  

For linux you may want to checkout what the moblin project guys are up to and what they are chatting about.

I think the potential issues I will come across should I install Ubuntu on such a system is mainly touchscreen drivers and video drivers etc.  As for open door voice prompts and the like I think you need to install some sensors and write some software code to respond to your sensors, similar to home-brew infra red remotes (lirc).

---

### Post by Jefferythewind on 2009-11-28
Hey Everybody thanks for the help.  
  I will do some searches for those kind of things.  Basically for what i want to do with the stereo there is no problem with a regular computer or laptop.  That should also be easy enough to hook up to a camera for the hood (froggyswamp).  
  Yeah main question is looking for the hardware/software package that could integrate basic 12 volt signals into the software so i could program exactly how i want the car's electronics to respond.  Kalibur mentioned some sensors and programming language...  has anybody heard of anything in particular?
  I'll post with anything i find.

---

### Post by hockey97 on 2009-11-28
I had the same idea. But my idea was to make my own embedded radio/computer system. 

What would be neat if your can get wireless Internet connection. You can then play music off the Internet. I never attempted it but thought it would be a neat project. Like have the radio/computer device have a touch screen. I was thinking to also add pressure sensors to the car tires so the computer system would alert me  when the pressure is low or high. Just seems to take time and money to do such a thing. 

Well good luck with your idea.

---

### Post by Jefferythewind on 2009-11-29
Hi Hockey97 Thanks for the response,
  I don't think there is any real reason to need the stereo embedded in the computer system, since anything you play off the computer automatically can come out of the car stereo.  You can just have the output from the soundcard as an input in the back of you stereo.  The touch screen is a cool idea too but also don't know how immediately feasible.  I love the idea about the pressure sensors in the tires.  
  It would take time an money to do this project.  But what i need first is a good plan.  Basically what we need to know is how to get the computer to recognize these different signals.  Is there some kind of hardware/software combo that would have these capabilities?

---

### Post by Zugzwang on 2009-11-29
> **Jefferythewind said:**
> Is there some kind of hardware/software combo that would have these capabilities?

It appears as you actually want something like a USB interface board connected to your PC. Google for it for details. Or browse here for a start: [http://en.wikipedia.org/wiki/Arduino](http://en.wikipedia.org/wiki/Arduino)

By the way: How many +12V signals are you actually wanting to read? And how fast are they? Here's some idea for a quick'n'dirty solution: Take some cheap USB-joystick and remove all cable connections to the buttons. Then take some 12V relay (yes, the mechanical ones) and connect the old button cables to the secondary side. Use the +12V signal to drive the coil in the relay (make sure that such a load is OK). Now you can connect the "joystick" to your computer and you will see that every time some of these signals is given, the computer will "think" that some joystick button has been pressed. This way, the standard Linux joystick driver will allow you to read your signals. Of course, this doesn't work for "fast" signals.

---

### Post by Jefferythewind on 2009-12-02
Zugzwang, That is a great idea, i will get one of my friends who knows more about electricity to help me with that, that seems like a simple and easy way to get the 12V inputs into linux language.

---

### Post by gil_johnson on 2009-12-02
> **Jefferythewind said:**
> Zugzwang, That is a great idea, i will get one of my friends who knows more about electricity to help me with that, that seems like a simple and easy way to get the 12V inputs into linux language.

jeffrey,
Please keep posting about your progress - I'd like to hear it.
Gil

---

### Post by Jefferythewind on 2009-12-03
Wow, i've been checking out that Arduino on wikipedia and youtube, it looks pretty good.  It looks like almost exactly what I have been looking for.  I think not only will i be able to make cool alert sonds but much more, hopefully i will get this thing going.  I was wondering if anyone knows about any other kinds of boards like this?

Also, i only saw the software download for windows and OSX, i hope they have something for linux

---

### Post by Jefferythewind on 2009-12-05
Well I have ordered this Freeduino kit:

[http://www.nkcelectronics.com/freeduino-arduino-diecimila-compatible-board-complete-kit.html]("http://www.nkcelectronics.com/freeduino-arduino-diecimila-compatible-board-complete-kit.html")

  I am still waiting to get it.  It has the ATmega328P microcontroller, and can be programmed with the arduino IDE which has a linux version already installed on my system.  I have a small sony hand-held digital recorder with a speaker output that i am going to wire to my car speakers.  I just have to wire up and program the Freeduino to manipulate the digital recorder.  
  The program will be able to select which track to play, and play that track.  I am going to make custom alert messages on my computer and then save them onto the device.
  It is all open-source and its going to be sweet!

---

### Post by Jefferythewind on 2009-12-09
I just finished assembling the Freeduino.  The the IDE seems to bo communicating correctly with the chip.  The next step in assembling the prototype board and mounting the voice recorder.

---

### Post by eewoz on 2009-12-10
> **Jefferythewind said:**
> Hello everybody,
  I have a little topic for discussion.  I have a car, 1978 datsun 510 wagon.  I want to put a new stereo system and other things into it.  I was thinking about getting a little computer  in the car, preferably linux and ubuntu.  I was wondering if anyone out there has ever computerized a car before?
  There are a few little alerts in the car, like for seat belt and when the door is open.  I am also wondering if anyone knows any kind of integrated circuit that can handle these 12 volt signals from the different indication signals?  This integrated circuit would preferably be programmable through the computer to do different things for each signal.  Like for example, if your door is open, the computer could play over the speakers: "the left front door is ajar." 
  Anyway i was wondering if the people in the ubuntu community have any experience with something like that.

Thanks!
I was going to suggest that you interface with the ODB connector on the car that service technicians use to get trouble codes out of the car's computer.  Information from all of the car's sensors may be available there.  But I think your 1978 Datsun came out before the ODB system.  You will probably want to buy some sort of digital I/O board that interfaces with the serial or USB port.  [http://www.bb-elec.com/product.asp?sku=UD128A8D&pathid=298&altsku=daq](http://www.bb-elec.com/product.asp?sku=UD128A8D&pathid=298&altsku=daq) shows a card that interfaces with the USB port.  It has many features that you probably do not need but it does have 8 digital channels that can be configured as inputs.  The voltage levels that the inputs on the card work with are not 12 Volt so some level shifting would be required.  Someone probably makes a digital I/O card that works with 12 Volt signals and interfaces with the serial or USB computer ports.  It may take some looking but hardware like that is available.

Have fun!

---

### Post by phrostbyte on 2009-12-10
I think Moblin would make a good UI for a CarPC, but it needs GPS support.

---

### Post by Jefferythewind on 2009-12-11
I just finished soldering wires to all the buttons that I need on the digital voice recorder, and I connected these wires to 5 of the pins on the Freeduino.  After some trial and error I figured out how I can trigger the buttons from the Freeduino.  Now I can set my car's alert connections, like those for the seatbelt, door, headlights, etc as inputs on the freeduino chip, and do some simple programming, and I should be in business.  
  (See Picture)

---

### Post by Mickeysofine1972 on 2009-12-11
Beagle Boards are awesome

[http://beagleboard.org/](http://beagleboard.org/)

[http://www.youtube.com/watch?v=FuVwh_VrIxk](http://www.youtube.com/watch?v=FuVwh_VrIxk)

Mike

---

### Post by Zugzwang on 2009-12-11
> **Jefferythewind said:**
> I just finished soldering wires to all the buttons that I need on the digital voice recorder, and I connected these wires to 5 of the pins on the Freeduino.  After some trial and error I figured out how I can trigger the buttons from the Freeduino.  Now I can set my car's alert connections, like those for the seatbelt, door, headlights, etc as inputs on the freeduino chip, and do some simple programming, and I should be in business.  
  (See Picture)

Looks like a cool project. :-) So in the US, you don't need the approval from some technical inspection organization before you may put that into your car?

---

### Post by Jefferythewind on 2009-12-12
I don Think So.

---

### Post by elj4176 on 2009-12-12
I have built a carpc and it's runs ubuntu with a 7" touchscreen in the dash, verizon cell modem and usb GPS receiver. It's an Atom system and sits in trunk.

You may want to look at the mp3car forums for some good info. There is a linux sub-forum. I also run nghost as the frontend and it does have a car interfaces section for the obd. The version I have doesn't have anything in there yet but I also do not have a connection to the obd.
The devs of the project are working on a newer version with the clutter UI.

---

### Post by Mister.Vash on 2009-12-12
Ran across the following a while ago, might provide some ideas for new features you want to add to yours.

[http://www.geekmyride.org/wiki/index.php/Jon%27s_RX-8](http://www.geekmyride.org/wiki/index.php/Jon%27s_RX-8)

---

### Post by Jefferythewind on 2009-12-15
elj4167 - Do you have any pics of your system?  It sounds pretty good, and is something that I would like to do in the future if i get some more money.

Mister.vash - That looks pretty cool too, with the obd and everything, My car unfortunately does not have one, so that is kind of what I am building although the circuit i designed with the arduino basically just triggers spoken messages when something happens, it doesn't record anything to memory yet.  I am planning on getting a new stereo system, with all the music coming from a portable storage device, and then hopefully a computer, UBUNTU!

---

### Post by Kalibur on 2009-12-15
> **elj4176 said:**
> I have built a carpc and it's runs ubuntu with a 7" touchscreen in the dash, verizon cell modem and usb GPS receiver. It's an Atom system and sits in trunk.

You may want to look at the mp3car forums for some good info. There is a linux sub-forum. I also run nghost as the frontend and it does have a car interfaces section for the obd. The version I have doesn't have anything in there yet but I also do not have a connection to the obd.
The devs of the project are working on a newer version with the clutter UI.

Hi Elj

Am about to go live with putting a pc in my car.  I have noticed that the hardware is easy to get hold of including pc that are small enough to fit in the place ur stereo normally seats.  However a descent linux basic gps navigation application is what is making me hold on to my money a little longer.  If somehow we get some ported versions of andriod os software that would be cool.  So what navigation software and other software would you recommend for ubuntu car pc.

Am going with ubuntu netbook remix with Moovida(elisa) media center as they have excellent touchscreen support.

---

### Post by elj4176 on 2009-12-18
I do not have any pics but I can take a few. The case is just a standard mini-atx so nothing special there. mp3car store has a lot of pre-built carpcs too but i built my own with the intel/atom board.

For GPS - I have tried a few so far and go back and forth between roadnav and navit. I'm also experimenting with googleearth a bit. Roadnav is the easiest to setup and use but navit is actively being developed and has more features - but it is more difficult to setup.

My biggest issue so far has been my powersupply. It is dead at the moment so I'll be upgrading to something a bit more robust soon. The other problem I ran into was the powersupply was waiting 60 seconds after shutdown and turning the pc back on and draining my battery. I finally got that worked out and everything was working well. 
The amp turn-on thump was an issue but we wired a toggle to the power distro block in the trunk and I just wait until the pc is booted and flip the toggle to turn on the 4 amps, pre-amp and XO.

---

### Post by UbuKunubi on 2009-12-21
For a cheap GPS I'd recommend visiting [http://www.telit.com/en/products/gsm-gprs.php?p=7&p_ac=show](http://www.telit.com/en/products/gsm-gprs.php?p=7&p_ac=show)

As you will notice the module is also gprs, so you can receive alerts (alarm) while away from your car. They communicate via rs232 and i2c, so are friendly with either the serial or parallel port.

Is my projects I use these modules with the development board because they are rather cheap and useful - an extra bonus is that the module also has external i/o ports/pins which can be used to expand the number of i/o's available for your project.

It might also be a viable consideration to use an array of buttons around your head-unit display if a touch-screen is too expensive or the drivers are troublesome.

As far as your connecting the cars systems to your pc, I'd recommend the extensive use of opto-isolators to protect your computers parallel port, reducing power usage, and extending the working life/speed of the interface.

The parallel port is often my prefered weapon of choice in all external signalling because coding with python is very easy. While there are a limited number of normal input/output pins, it is very easy to either multiplex the pins(assuming your using a laptop for your project?).

Here is a working example that makes use of skype to send alarm messages to the skype phones when a switch pulls pin11 to 0volt :
```

# -*- coding: utf-8 -*-
#!/usr/bin/env python
  
import Image
import os,sys
import parallel
import time
import Skype4Py

def do(dothis):
    cmd = "xdotool "+dothis
    #print cmd
    print
    f=os.popen(cmd)
    f.close()
    cmd=""
    dothis=""

def OnMessageStatus(Message, Status):
    if Status == 'RECEIVED':
        print(Message.FromDisplayName + ': ' + Message.Body);

def OnAttach(status):
    print 'API attachment status: ' + skype.Convert.AttachmentStatusToText(status)
    if status == Skype4Py.apiAttachAvailable:
       skype.Attach();
 
    if status == Skype4Py.apiAttachSuccess:
       print('******************************************************************************');

skype = Skype4Py.Skype();
skype.OnAttachmentStatus = OnAttach;
skype.OnMessageStatus = OnMessageStatus;
print('******************************************************************************');
print 'Connecting to Skype..'
skype.Attach();
print
print "-------------------------------------------"
print "Parallel port program starting"
print
print "Attempting to read status of PIN 11 "
p = parallel.Parallel()

while 1:
    nds = p.getInBusy()
    if not nds:
        print "Motion Detected at",
        ndsticked =time.asctime()
        print ndsticked
        skypmsg="Motion Detected at "+ndsticked
        skype.SendMessage("XXXSUERNAMEGOESHEREXXX", skypmsg);
        print "Alert Via Skype Now sent"
       
        
    time.sleep(1)
    


```
Hope this helps,
Ubu

---

### Post by Calmor on 2009-12-21
I had a PC in my car a few years back when I was still driving 12 hours every other weekend.  There are a few good forums on the web for in-car PCs, including everything from custom electronics to custom software to custom plastic/fiberglass/carbon fiber how-tos.

My PC was a Via M1000 mini-ITX system, 80GB laptop drive, 7" Liliput touchscreen, with GPS and WiFi via USB, powered by a DC-DC power supply (now readily available online).  This was back in my Windows days, so I ran Windows XP with MediaCar.  I also had some software for OBD-II integration, but it was meant for a larger screen and rather hard to use with the tiny touchscreen.  (I used the MediaCar frontend, if anyone is interested).  Everything mounted where the old radio went, and the touchscreen was 'glassed into the dash plate to look as stock as it could.  The GPS mouse sat where one of the dash speakers originally went.

All was wired to a set of amps through the onboard stereo out, and sounded *very* good actually.  I did have to fight with a minimal amount of alternator whine, but filtered most of that out with hardware.

As far as integration with the car itself, I didn't do any of that (other than that OBD-II solution), though.

Linux in the car would be great, but would present different challenges than Windows.  Windows had good GPS and hardware support, but I think the more custom hardware integration would be more difficult than in Linux.  There are also distros (can't remember the name now) that just "are" the front-end - it's not something on top of Gnome, it runs right on the X server and minimizes overhead.  Sounds awesome!

Good luck with your project!

---

### Post by Maheriano on 2009-12-21
I have a computer running all the media in my car:
- GPS
- thousands of mp3s
- videos/movies
- Wi-Fi
- dash cam

Unfortunately I'm running Windows XP as a back end because there's more front ends available for it right now. The only one I know of that runs on Linux right now is [nGhost]("http://sourceforge.net/projects/nghost/"). And to run all your car's electronics you'll need an onboard diagnostics (OBD) scanner. The problem is your car's way too old and likely doesn't have any type of OBD support built in.

---

### Post by Jefferythewind on 2009-12-22
Wow, this thread is getting pretty sweet.  I appreciate all the info about car electronics.  I guess my end goal is to get ubuntu into my car.

Ubukunubi - That is pretty cool about sending alerts to your phone.  I am still trying to understand exactly what you did.  Is your computer on even when your car is off?

---

### Post by UbuKunubi on 2009-12-23
> **Jefferythewind said:**
> Wow, this thread is getting pretty sweet.  I appreciate all the info about car electronics.  I guess my end goal is to get ubuntu into my car.

Ubukunubi - That is pretty cool about sending alerts to your phone.  I am still trying to understand exactly what you did.  Is your computer on even when your car is off?

No, I had the GSM module connected to its own li-ion battery and charger. The module has on board python support (3 Mb code space), and using it's own ports was able to monitor the door switches, bonnet switch, etc... and then send a normal GSM SMS.

The python code in my post for using skype was modified for sending me notifications for when transfering music and other files was completed, and its not a lot of work to use the skype chat as a terminal direct into the onbaord Ubuntu.

Ubu.

---

### Post by g7kse on 2009-12-29
I too have built a system based on a mini-itx form factor. There are a few hardware considerations to think about first as a car isn't the best place for electronics on any sort and they have to be treated nicely.

Hardware websites (both UK but I'm sure similar ones are in other countries) that I've used are linitx.com and mini-itx.com. They do loads of small form factor m'boards, psu's drives and enclosures. Some are ruggedised mechanically and electrically as well. Touchscreens are plenty, remember though you get what you pay for and some don't work as well in sunlight.

Software. Like it or not but the windows stuff seems to be a bit better developed. there are even commercial products like centrafuse that do a very good job. It shouldn't be too hard to tweak ubuntu to make a distro or 'shell' (Is that the right word?) that does the whole touchscreen thing.

Hope this helps

---

### Post by UbuKunubi on 2009-12-29
This is a worthy read:
[http://tnoergaard.wordpress.com/2009/05/09/ubuntu-touch-screen-setup-and-calibration/](http://tnoergaard.wordpress.com/2009/05/09/ubuntu-touch-screen-setup-and-calibration/)

---

### Post by Jefferythewind on 2010-02-05
Thanks guys for all the help, unfortunately I am still a long way from really digitizing my ride, but You have given me some great ideas

---

### Post by Kalibur on 2010-02-06
I am still into making my car a mobile infotiament centre but I have have to cut done how much am willing to spend because of the lack of a decent turn by turn navigation application.  I will start by testing my ibm t42 laptop with a car charger till the till I find it worthy I will not be buying a touchscreen monitor or itx chasis etc.  Am trying to match my google g1 smart phone to keep it simply.

---

### Post by Maheriano on 2010-02-09
> **Kalibur said:**
> I am still into making my car a mobile infotiament centre but I have have to cut done how much am willing to spend because of the lack of a decent turn by turn navigation application.  I will start by testing my ibm t42 laptop with a car charger till the till I find it worthy I will not be buying a touchscreen monitor or itx chasis etc.  Am trying to match my google g1 smart phone to keep it simply.

Navit


[IMG]http://linux.softpedia.com/screenshots/Navit_3.png[/IMG]

---

### Post by Jefferythewind on 2010-02-09
Awesome.

---

### Post by CerealKiller93 on 2010-02-20
I really don't feel like reading all four pages of this, so i will go ahead and say what i know on the subject.

First of all, i know this has been stated, but yes it can and has been done.



I'm currently building a system for this, and since i'm cheap, i'm going with two computers. I have this old Touch screen netbook that i plan on stripping down and building a custom enclosure for it to mount in my center console/dash area. The netbook only has an 800Mhz Crusoe processor in it, and it runs alright with "Damn Small Linux" but it just doesn't have the computing power i'm looking for. I have a full-tower Ubuntu 8.10 box running an Athlon XP 2800+ that i plan on using for a server in the trunk. My plan is to use the netbook for remote desktop, which will give basically turn it into a small screen for me. I don't want to spend 200+ on a small touchscreen. So far i have $0.00 in my setup. I'm no where near done with it, but i do have both computers set up and operational. The biggest problem i have is building the custom case for the netbook. I like an OEM look, so whatever i do is going to involve alot of custom stuff. The car is a 1987 BMW 325e [my baby, my project, my true love (ok, my fiance is my true love but you get the idea)]. Only other thing i got to work out is setting up the remote desktop and all the networking crap between the two computers, but i'm sure i'll have no problem with it, and i haven't even tried to start on that part yet. I should also point out that their will also be a third computer involved, although this one is for the engine. I plan on installing Megasquirt soon, if you don't know what that is, think of it as the Linux version of fuel injection. It can be bought as a unassembled kit, or an assembled kit. It can do pretty much anything and allows you to tune the car to your liking, with your parts, how ever you want to do it. I will be able to tune it, on the fly, with the car-puter. Buddy of mine has done all this, and has been running his system for a while. Although he actually has a real screen rather then a netbook. 

Now, on to the links for ya!

Heres a website with alot of useful information on it, and they also sell some things to integrate with other systems, you can even have the computer control things like Power windows, Power Locks, etc. My buddy is actually working on having his system control his HVAC Controls.
           ---- [www.dashpc.com]("http://www.dashpc.com")

Heres my buddy's setup:
[http://www.r3vlimited.com/board/showpost.php?p=1009659&postcount=29](http://www.r3vlimited.com/board/showpost.php?p=1009659&postcount=29)
[http://www.r3vlimited.com/board/showpost.php?p=1009662&postcount=30](http://www.r3vlimited.com/board/showpost.php?p=1009662&postcount=30)
[http://www.r3vlimited.com/board/showpost.php?p=1009665&postcount=31](http://www.r3vlimited.com/board/showpost.php?p=1009665&postcount=31)
[http://www.r3vlimited.com/board/showpost.php?p=1009669&postcount=32](http://www.r3vlimited.com/board/showpost.php?p=1009669&postcount=32)


Here's the full thread that those posts came from, Its not completely computer focused though, its based on screens in E30 Chassis BMW (84-91 BMW 3-series)
[http://www.r3vlimited.com/board/showthread.php?t=69368](http://www.r3vlimited.com/board/showthread.php?t=69368)

Megasquirt:
[http://www.diyautotune.com](http://www.diyautotune.com)  <where to buy, lots of other place too just google it>
[http://www.megasquirt.info/](http://www.megasquirt.info/)   <the Mega Manual>

Hope i've been some help!

---

### Post by Jefferythewind on 2010-02-21
@CerealKiller93

Yes you have been a good help, you have been really informative.  That also brings up another problem I have been thinking about.  My car is a 1978 datsun 510 wagon, it has a carburetor, not fuel injection, but I wonder if I could install a custom fuel injection system.  That would be perfect to be able to tune the fuel/air ratio on the fly.  I will check out the link you posted about megasquirt to see if that is possible, but I don't think it is.  

Good luck with your project.

---

### Post by Maheriano on 2010-02-22
> **CerealKiller93 said:**
> I really don't feel like reading all four pages of this, so i will go ahead and say what i know on the subject.

First of all, i know this has been stated, but yes it can and has been done.



I'm currently building a system for this, and since i'm cheap, i'm going with two computers. I have this old Touch screen netbook that i plan on stripping down and building a custom enclosure for it to mount in my center console/dash area. The netbook only has an 800Mhz Crusoe processor in it, and it runs alright with "Damn Small Linux" but it just doesn't have the computing power i'm looking for. I have a full-tower Ubuntu 8.10 box running an Athlon XP 2800+ that i plan on using for a server in the trunk. My plan is to use the netbook for remote desktop, which will give basically turn it into a small screen for me. I don't want to spend 200+ on a small touchscreen. So far i have $0.00 in my setup. I'm no where near done with it, but i do have both computers set up and operational. The biggest problem i have is building the custom case for the netbook. I like an OEM look, so whatever i do is going to involve alot of custom stuff. The car is a 1987 BMW 325e [my baby, my project, my true love (ok, my fiance is my true love but you get the idea)]. Only other thing i got to work out is setting up the remote desktop and all the networking crap between the two computers, but i'm sure i'll have no problem with it, and i haven't even tried to start on that part yet. I should also point out that their will also be a third computer involved, although this one is for the engine. I plan on installing Megasquirt soon, if you don't know what that is, think of it as the Linux version of fuel injection. It can be bought as a unassembled kit, or an assembled kit. It can do pretty much anything and allows you to tune the car to your liking, with your parts, how ever you want to do it. I will be able to tune it, on the fly, with the car-puter. Buddy of mine has done all this, and has been running his system for a while. Although he actually has a real screen rather then a netbook. 

Now, on to the links for ya!

Heres a website with alot of useful information on it, and they also sell some things to integrate with other systems, you can even have the computer control things like Power windows, Power Locks, etc. My buddy is actually working on having his system control his HVAC Controls.
           ---- [www.dashpc.com]("http://www.dashpc.com")

Heres my buddy's setup:
[http://www.r3vlimited.com/board/showpost.php?p=1009659&postcount=29](http://www.r3vlimited.com/board/showpost.php?p=1009659&postcount=29)
[http://www.r3vlimited.com/board/showpost.php?p=1009662&postcount=30](http://www.r3vlimited.com/board/showpost.php?p=1009662&postcount=30)
[http://www.r3vlimited.com/board/showpost.php?p=1009665&postcount=31](http://www.r3vlimited.com/board/showpost.php?p=1009665&postcount=31)
[http://www.r3vlimited.com/board/showpost.php?p=1009669&postcount=32](http://www.r3vlimited.com/board/showpost.php?p=1009669&postcount=32)


Here's the full thread that those posts came from, Its not completely computer focused though, its based on screens in E30 Chassis BMW (84-91 BMW 3-series)
[http://www.r3vlimited.com/board/showthread.php?t=69368](http://www.r3vlimited.com/board/showthread.php?t=69368)

Megasquirt:
[http://www.diyautotune.com](http://www.diyautotune.com)  <where to buy, lots of other place too just google it>
[http://www.megasquirt.info/](http://www.megasquirt.info/)   <the Mega Manual>

Hope i've been some help!

Your friend is going in the wrong direction. Point him to:
[http://guino.home.insightbb.com/roadrunner.html](http://guino.home.insightbb.com/roadrunner.html)
[http://www.mp3car.com](http://www.mp3car.com)
[http://www.inavcorp.com/](http://www.inavcorp.com/)
[http://www.fusioncontrolcentre.com/FusionStore/catalog/index.php](http://www.fusioncontrolcentre.com/FusionStore/catalog/index.php)

---

### Post by WarrenSH on 2011-06-04
WOW 

Great topic any updates from the OP?

Has anyone ells done this? Whats the status of Linux in a car?

---

### Post by s3a on 2011-06-04
For making the computer speak, use espeak. For the rest, I don't know.

---

### Post by uRock on 2011-06-05
Necromancy

Thread Closed

---

