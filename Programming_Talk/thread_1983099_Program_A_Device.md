---
title: "Program A Device"
date: 2012-05-19
forum: Programming Talk
---

### Post by Xender1 on 2012-05-19
I really have no idea where to put this question - so I will put it on my favorite programming forum to start before I can narrow in on specifics. 

I am a very experienced programmer with 3 years of Computer Science wrapping up at a university. I have done lots of programming with servers, scripts, puzzle solvers, simple algorithms, etc with knowledge/experience of languages (from most to least) in C,C++,Java,Perl,Python.

I really want to program a device this summer - write code on my computer - upload it to a machine that is connecting to my computer - unplug turn on and tada its doing what I wrote. But I have no idea what device is actually called or how to get it. Essentially at the lowest level I want to have a light flash every few seconds, or have a gear turn a wheel or something. What sort of device would this be? Anyone have any ideas on this? Thank you very much!

[edit] spelling

---

### Post by Bachstelze on 2012-05-19
You can use something like [this](https://www.digilentinc.com/Products/Detail.cfm?NavPath=2,400,790&Prod=BASYS2), but it is programmed in a hardware description language like VHDL or Verilog, not in a general-purpose language like C or C++. I know only VHDL personally, but I've found it quite simple to learn, so you shouldn't have any problems. I have learned VHDL using [this book](http://www.amazon.com/dp/0470052635/).

I used it in a digital design class last year, it's generally a lot of fun. Even using only the 8 switches and LEDS, the 4 push-buttons and the 7-segment displays, you can do some cool things like a clock or a bin/octal/hex/decimal converter.

---

### Post by LemursDontExist on 2012-05-20
I think maybe you want an [Arduino]("http://www.arduino.cc/")?

You can upload a program to one and hook it up to control lightbulbs, servo-motors, or anything else that takes an electronic input.

---

### Post by Bachstelze on 2012-05-20
I never got the point of Arduinos, at least the way most people use them. No, you do not need a complete uC, a Java API and whatnot just to control a bunch of LEDs.

When I'll need a uC, I'll get an Arduino (or more probably use the Elan or the Geode that I have sitting around). Until then I stick to FPGAs.

---

### Post by xb12x on 2012-05-20
> **Xender1 said:**
> I really want to program a device this summer - write code on my computer - upload it to a machine that is connecting to my computer - unplug turn on and tada its doing what I wrote. But I have no idea what device is actually called or how to get it.

You might want to think about doing some Android development. 

The Android SDK is freely available for your PC, running on either Windows or Linux or OSX. 

To get started an actual Android device is not necessary as Android emulators are also freely available. Or buy an inexpensive Android device just for development.

You can develop in Java or 'Python for Android'.

[https://developer.android.com/index.html](https://developer.android.com/index.html)
[http://www.linuxjournal.com/article/10940?page=0,1](http://www.linuxjournal.com/article/10940?page=0,1)

Plus the experience might actually be helpful when you're looking for work.

---

### Post by Bachstelze on 2012-05-20
We will need to wait for Xender1 to come tell us what he had in mind, but I'm pretty sure it's not Android. Developing for Android is no different than developing from any other computer platform, I think he wants something a bit more low-level. Shiny stuff tends to get boring, and getting dirty is a lot of fun.

---

### Post by kalaharix on 2012-05-21
hi,

In the past I have had great fun with PICAXE ([www.picaxe.com](www.picaxe.com)). Single chip microcontroller with onboard BASIC. Bundled into starter kits as well. Strong in education here in UK and therefore very fairly priced. Most of what I did was from Windoze but they do have a Linux development IDE as well.

---

### Post by ofnuts on 2012-05-21
> **Xender1 said:**
> I really have no idea where to put this question - so I will put it on my favorite programming forum to start before I can narrow in on specifics. 

I am a very experienced programmer with 3 years of Computer Science wrapping up at a university. I have done lots of programming with servers, scripts, puzzle solvers, simple algorithms, etc with knowledge/experience of languages (from most to least) in C,C++,Java,Perl,Python.

I really want to program a device this summer - write code on my computer - upload it to a machine that is connecting to my computer - unplug turn on and tada its doing what I wrote. But I have no idea what device is actually called or how to get it. Essentially at the lowest level I want to have a light flash every few seconds, or have a gear turn a wheel or something. What sort of device would this be? Anyone have any ideas on this? Thank you very much!

[edit] spelling
See this: [http://www.arduino.cc/](http://www.arduino.cc/)

My son used one for one of his highschool project ([sumo robot]("http://en.wikipedia.org/wiki/Robot-sumo") control). Comes with some analog (D/A converter) and some digital interfaces, and a USB port (code load, and debug output). Code is written in some C derivative. Programming toolkit/IDE for Windows and Linux. You can focus on the coding, and on the external electronics (sensors, relays...)

---

### Post by alexfish on 2012-05-21
Get an arm device ensure has gpio pins on board , put a Linux os on it , add downloader - uploader  for software etc.

Communication - connections :: Internet / usb / Ethernet

forgot to add >>> QEMU on Ubuntu  for testing

---

### Post by roelforg on 2012-05-21
I've got lego mindstorms nxt + accu + hitechnic proto board.
I've build a lot with the thing... Ahhh the memories.
I tend to write a prog on a pc that controls the nxt via usb or bt.
But i've mucked with nxc as well and it's very good as well (i just prefer the multithreading, big screen and debugger on my pc).
I use the proto to interface with regular electronics.
It's a bit expensive but worth every cent!

And you don't have to worry about breakage as much as people say, my 1st gen nxt has been droppen from 2m+, water spilled on and it still works just fine (after 7 years of abuse it still works).

---

### Post by Xender1 on 2012-05-21
Wow! Thank you all so much for the responses they have all been so helpful!

@xb12x - thank you for mentioning that there are emulators for android development. This has been something of interest to me but the lack of a smart phone has held me back. I will definitely check this out. But I was looking for something more low level like Bachstelze said.

I have looked at both the Digilent robotics board and also the Arduino board - both seem to do the tasks that I am interested in (especially the Arduino board because of the sensory pickup).

My question is what is the difference between these two products? Is it just merely two companies with similar ideas essentially because I see both use their own languages to code in but other than that both products seem to be quite similar. 

Picaxe also seems to do what I want too - with the input and output devices except uses Basic and has lots of tutorials. 

Alexfish - I am pretty lost as to what you are saying - but looking up QEMU it seems to be very cool. Essentially I can upload an OS to the micro controller? What you are saying seems very cool and I would love if you can share a link or some more information about getting started.

roelfrog - Lego mindstorms was essentially what sparked this whole thought. I wanted to create something but I didnt want to have the high level lego software doing all the basic ground work and taking some of the fun away (at least for me). It is interesting that there are lots of other companies supplying sensors for Lego products.

I have lots of research to do still thanks to all of the information you guys/gals have given me on all these different products that can do what I intend. I guess to clarify a little more I will share a simple concept that shows how I want to play with this thing: Have a light go on/off depending on if a sound was heard (or if using a camera depending on if movement was detected) - A mini car that I place in my room that drives around and creates a map which I can upload to my computer and essentially see what it thinks my room looks like (marking O's for where it can go and X where it got blocked). Another more out there idea is hook up wireless to one of these things and have it send a message to my computer/email saying 'hello' every few seconds (if that's even possible?).

Again, I appreciate all of your responses they have been so helpful and I am definitely getting more excited about this project because there are so many options available to explore.

---

### Post by trent.josephsen on 2012-05-21
The Spartan-3E board and the Arduino are really very, very different.

An Arduino is a greatly reduced general-purpose computer with a handful of I/O ports. You can easily connect it to different things to make it light lights, turn wheels, whatever, but the discipline of programming it is no different from programming an ordinary PC. (The main difference being that ordinary PCs don't have general purpose I/O pins on the front.)

An FPGA is a blank slate. It has a number of pins that can be inputs or outputs; you get to determine which ones you want to use; and you decide the logic that goes on in the middle. When I say "logic", I'm talking about actual digital logic gates -- ANDs and ORs and NANDs and so forth. You do so with a hardware description language; Bachstelze already mentioned the two big ones (Verilog and VHDL).

Generally speaking, FPGAs are more versatile than microprocessors. You can create pretty much anything with an FPGA and a sufficiently fast oscillator. You can even synthesize a processor on an FPGA if you want (and have a sufficiently large FPGA).

CS folks tend to be pretty useless when it comes to firmware, so I encourage you to buck the trend and learn some VHDL. It can't hurt you and it looks great on a resume.

---

### Post by Bachstelze on 2012-05-21
A microcontroller is basicaly a one-size-fits-all approach. Roughly, it's a large FPGA that someone has already programmed for you and that you can't change. It's programmed in such a way as to make it work well enough for most purposes, but this means that 1) there's a lof of overhead; and 2) if it doesn't work for you, you are out of luck.

Lousy analogy: a microcontroller is a standard Ubuntu install in which you would be forbidden to install or remove packages. If it does what you want, cool, but there will be a lot of overhead because there is also a lot of things you don't need. If it doesn't do what you want, you are just out of luck. A FPGA is a LFS, you can make it do what you want, and only that, but it's a little more complicated to the neophyte.

*EDIT:* Also, the programming is done at a lower level on a FPGA than on a microcontroller. A particular model of µC is the same for everyone, but of course not everyone has the same needs, so you need to program it in order to make it do what you want (if it can). With a FPGA you basically design your own µC that perfectly fits your application, which will invariably be smaller and faster than a general-purpose µC.

---

### Post by alexfish on 2012-05-21
@ Xender1

Can have a look at these links + also look up beagle board

[http://www.cnx-software.com/2011/10/18/raspberry-pi-emulator-in-ubuntu-with-qemu/](http://www.cnx-software.com/2011/10/18/raspberry-pi-emulator-in-ubuntu-with-qemu/)

[http://www.aurel32.net/info/debian_arm_qemu.php](http://www.aurel32.net/info/debian_arm_qemu.php)

[http://mbed.org/](http://mbed.org/)

there are many more links, try googling ARM projects , ARM robotics , etc , etc

But read all of what is been posted , note the Arduino route , don't know if already mentioned ,  Arduino IDE should be in the repo's , you could go that route, then experiment with images on qemu .

have fun

alexfish

---

### Post by Bachstelze on 2012-05-21
> **Xender1 said:**
> 
I have lots of research to do still thanks to all of the information you guys/gals have given me on all these different products that can do what I intend. I guess to clarify a little more I will share a simple concept that shows how I want to play with this thing: Have a light go on/off depending on if a sound was heard (or if using a camera depending on if movement was detected) - A mini car that I place in my room that drives around and creates a map which I can upload to my computer and essentially see what it thinks my room looks like (marking O's for where it can go and X where it got blocked). Another more out there idea is hook up wireless to one of these things and have it send a message to my computer/email saying 'hello' every few seconds (if that's even possible?).


If you really want to do that kind of things over the course of a couple weeks, you probably want a µC. The design process on a FPGA and on a µC are totally different, because on a FPGA you design a digital circuit, whereas on a µC you just write a program. You know how to write a program, but based on what you say, I will hazard a guess that you are not familiar with digital design, so you will basically have to learn it all before you can do anything that's not trivial, let alone something really elaborate like a wifi communication device.

Personally, I think that knowing how things are done in industry, even if for a while you will only do simple things like timers or arithmetic converters, is a much more valuable skill than doing "cool" things that won't really teach you anything. And of course, once you have mastered digital design, the sky's the limit. You can do things impossible on a µC (simple example, adding very large integers really fast).

---

### Post by roelforg on 2012-05-21
@xender

I didn't like that either,
but lego put the lowlevel docs online (if you pm me your email, i'll send you a copy of the pdf files).
I control mine by giving commands through the usb.
I use nxtpp with a few patches and my own driver for the hitechnic proto board (that too has it's lowlevel docs online. Heck, they're included with it in printed form!)
Nxc'll give you the finegrained control you want while running nativly on the nxt without new firmware (mine runs off the mill lego fw, v1.0.5 iirc).
I don't like the standard lego ide (it keeps crashing, even on windows) just like you, but nxc is very good and gives you very fine grained control.
It's just that i prefer to have my pc control it directly.
That way i can log every action to see where a bug is or hook up a debugger if needed.
Put 2-3 days in it and you'll be baffled with how much you can control it.
Give it a shot, you can do a lot with it!

(i even build 3d-printer that has sub-millimeter accuracy and it works! Well... It would if i could get a working extruder, but everything else (sans a few touch buttons hooked to the protoboard) is lego. If that isn't finegrained enough, then i don't know what else. (you can get <1 degree accuracy from the servos if you know how to work the power correctly))

---

### Post by Xender1 on 2012-05-21
> **trent.josephsen said:**
> CS folks tend to be pretty useless when it comes to firmware, so I encourage you to buck the trend and learn some VHDL. It can't hurt you and it looks great on a resume.

Totally agree. I have taken a Computer Organization course which went slightly into digital circuits (mux/and/or gates) and it definitely a challenge for me because of little prior knowledge. Another example is many of my friends are EE and when looking at their homeworks of drawings of circuits I pretty much don't know whats going on. 

I am currently taking a peak at Verilog and VHDL. Verilog seems a little more syntax friendly to what I am used to working with.

I will post again here once I do some more research and look at the pricing of different products. Again I appreciate all the help.

Currently I am leaning towards using a µC but the more reading I do from alexfish's links the more that entices me. FPGA's sadly scare me right now and I am not sure if I should start at that level and work up - or work at a slightly higher level and work down.

[edit] I think roelforg is giving me a great starting point especially for the concepts I am hoping to design. Also as I sent in a message announcing a concern: diving into the micro controllers and FPGA's seems like a very steep jump from being a good programmer to knowing how circuits work.

---

### Post by Bachstelze on 2012-05-21
> **Xender1 said:**
> 
Currently I am leaning towards using a µC but the more reading I do from alexfish's links the more that entices me. FPGA's sadly scare me right now and I am not sure if I should start at that level and work up - or work at a slightly higher level and work down.


It's not really a matter of starting somewhere and then walking up or down. The question is what you want to do. If you have a very precise idea of something you want to build and don't really care how it's done, most likely there is a µC with which you can do that with much less effort than with a FPGA. But it will be very much ad-hoc and largely a dirty hack.

If, like me, you want to learn how to properly design digital devices, you learn the process of digital design and a board like the one I linked above will let you experiment with it. And then, if you really like it, you can move to more complex devices. It's like programming: at first you do "hello world" and computing the nth term of the Fibonacci sequence, then you gradually move up.

---

### Post by roelforg on 2012-05-21
> **Bachstelze said:**
> It's not really a matter of starting somewhere and then walking up or down. The question is what you want to do. If you have a very precise idea of something you want to build and don't really care how it's done, most likely there is a µC with which you can do that with much less effort than with a FPGA. But it will be very much ad-hoc and largely a dirty hack.

If, like me, you want to learn how to properly design digital devices, you learn the process of digital design and a board like the one I linked above will let you experiment with it. And then, if you really like it, you can move to more complex devices. It's like programming: at first you do "hello world" and computing the nth term of the Fibonacci sequence, then you gradually move up.


I did some mucking with pic chips as well,
it's very funny when the smoke escapes after accidentally putting the chip in upside down.
But i went back to my nxt because you don't have to worry as much about the hw aspect,
while stuff like protoboards give you the same abilities as the other systems.

---

### Post by alexfish on 2012-05-21
> **Xender1 said:**
> Totally agree. I have taken a Computer Organization course which went slightly into digital circuits (mux/and/or gates) and it definitely a challenge for me because of little prior knowledge. Another example is many of my friends are EE and when looking at their homeworks of drawings of circuits I pretty much don't know whats going on. 

I am currently taking a peak at Verilog and VHDL. Verilog seems a little more syntax friendly to what I am used to working with.

I will post again here once I do some more research and look at the pricing of different products. Again I appreciate all the help.

Currently I am leaning towards using a µC but the more reading I do from alexfish's links the more that entices me. FPGA's sadly scare me right now and I am not sure if I should start at that level and work up - or work at a slightly higher level and work down.

[edit] I think roelforg is giving me a great starting point especially for the concepts I am hoping to design. Also as I sent in a message announcing a concern: diving into the micro controllers and FPGA's seems like a very steep jump from being a good programmer to knowing how circuits work.

That just reminded me of something
[http://www3.informatik.uni-erlangen.de/Research/FAUmachine/](http://www3.informatik.uni-erlangen.de/Research/FAUmachine/)

this could also be in the repo's

ADDED::
if user have installed FAU and stuck on how to get started, IE , the screen says "No operating system found"
can look here
[http://www.linux-mag.com/id/8719/](http://www.linux-mag.com/id/8719/)

---

### Post by roelforg on 2012-05-22
> **alexfish said:**
> That just reminded me of something
[http://www3.informatik.uni-erlangen.de/Research/FAUmachine/](http://www3.informatik.uni-erlangen.de/Research/FAUmachine/)

this could also be in the repo's

I think he didn't mean full on osdev...

---

### Post by alexfish on 2012-05-22
> **roelforg said:**
> I think he didn't mean full on osdev...

Just a link , RE : to highlight "- VHDL interpreter for automating experiments and tests"

if the OP is Thinking using this sort of Knowledge in terms of Employment,
then one has better Prospects at this Level ,than the low level IT , as in web or servers , or making an LED blink..

---

### Post by roelforg on 2012-05-22
> **alexfish said:**
> Just a link , RE : to highlight "- VHDL interpreter for automating experiments and tests"

if the OP is Thinking using this sort of Knowledge in terms of Employment,
then one has better Prospects at this Level ,than the low level IT , as in web or servers , or making an LED blink..

He did say he wanted to program a real device, though...

---

### Post by alexfish on 2012-05-22
> **roelforg said:**
> He did say he wanted to program a real device, though...

Yep , cost wise , start with a device you can afford , + learn the Virtual Machines as in Devices or CPU or Logic chips , researching in this area cost only the price of a down load.
Making an LED blink on a $2 device is no different than making it blink on a $100 device.

For me there is no difference in VM  . as in  looking at the device on screen or than looking at the device in real life , in some cases can be lot safer.

it is reasonable to assume that by researching VM and the devices , one can make or decide choices...... From the Knowledge gained.

---

### Post by roelforg on 2012-05-22
> **alexfish said:**
> Yep , cost wise , start with a device you can afford , + learn the Virtual Machines as in Devices or CPU or Logic chips , researching in this area cost only the price of a down load.
Making an LED blink on a $2 device is no different than making it blink on a $100 device.
 
For me there is no difference in VM . as in looking at the device on screen or than looking at the device in real life , in some cases can be lot safer.
 
it is reasonable to assume that by researching VM and the devices , one can make or decide choices...... From the Knowledge gained.
 
It's funny because he already has the hw...
(in a pm he sent me for those low-level docs i mentioned a few posts back, he told me he outgrew NXT-G, i did that a long time ago as well but never found good info, so told him about a few (not very widely known but very (if not more) capable) alternatives like nxc and direct usb control (nxtpp works great for me, btw) that i found to work very well. Haven't heard back yet)

---

### Post by alexfish on 2012-05-22
> **roelforg said:**
> It's funny because he already has the hw...
(in a pm he sent me for those low-level docs i mentioned a few posts back, he told me he outgrew NXT-G, i did that a long time ago as well but never found good info, so told him about a few (not very widely known but very (if not more) capable) alternatives like nxc and direct usb control (nxtpp works great for me, btw) that i found to work very well. Haven't heard back yet)

Hope you get some feed back , but here is my perspective of the arm route + linux

The OP is looking to control the device ,the first mentioned , second looking to extend , by way of retrieval of info from the device , 

in all instances the arm route + Linux can full-fill that and more ,

Say for instance , this device I am using now , is how I am viewing this thread and posting , yet in the next hour I want to mow the lawn , so I plug it into the mower , 
and off goes the mower , then mower dully returns back once the program has completed the task . This is often the Nature of Invention and Inventive people

Don't think these devices are new , I have still an epoc , runs at a stunning speed of 18mhz, bah, how times are changing.

---

### Post by Xender1 on 2012-05-22
Not sure if it is just because of well designed website - but in all honesty after looking at all these options - it appears to me the Arduino boards are actually what I am looking for. I feel like an Arduino board with any of the sensors from here [http://www.parallax.com/](http://www.parallax.com/)  will essentially be able to do what I want. Just wondering if anyone on here has had experience using an Arduino board + sensors - I would love to hear what you thought about it.

Granted the amount of information in this thread is enormous, and since its all new to me, it is taking some time to sift through each of the possible option. I again would like to thank everyone for all this information. 

I have not made any purchases yet because I want to make sure that whatever I end up getting is something I can play around with doing different things - but it seems to me still that Arduino might be a simple solution and good starting place for this adventure.

---

### Post by ofnuts on 2012-05-22
> **Xender1 said:**
>  Just wondering if anyone on here has had experience using an Arduino board + sensors - I would love to hear what you thought about it.I have no direct experience, but I've seen my son design and code up something (control for a simple Sumo robot: 2 motors, two binary light sensors (ring bounds detection), one ultrasonic distance sensor (enemy detection) with whatever programming & electronics experience you achieve in the last year of secondary education in France. Of course I showed him how to recode all that properly but his code worked. 4 teams in his class built such robots as last year projects so my son isn't exceptional (alas! :-))  I didn't see much additional electronics, the sensors where wired directly into the Arduino inputs. Got me thinking that my dream universal camera controller could very well be built around this stuff...

---

