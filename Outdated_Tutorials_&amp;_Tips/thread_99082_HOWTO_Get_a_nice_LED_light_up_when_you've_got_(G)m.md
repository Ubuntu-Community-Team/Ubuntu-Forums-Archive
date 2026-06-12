---
title: "HOWTO: Get a nice LED light up when you've got (G)mail"
date: 2005-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by shandar on 2005-12-04
Well, probably there are a thousand ways to do this both easier and prettier but this is how I did it real quick :-)
 
 **What is needed?**
 One parallel (printer) cable
 One or more LEDs of any color. You can connect up to 8 LEDs AFAIK.
 One 330 Ohm (Red - Red - Brown) or higher resistor per LED
 
 **Building the hardware**
 Well, not very much hardware, but anyway :)
1. Attach the resistor to the shortest leg of the led somehow (I did it by twisting them together. Not recommended, if you have the time and patience solder them together).
2 Insert the LED part of the assembly into pin 2 and the resistor part into pin 18. If you have more LEDs you want to connect simply keep inserting them into pin 3 and pin 19 etc.
 Done! Simple, isn't it? Yet it looks quite pretty when it's done :-)
**[COLOR=Red]WARNING: Make sure that you don't bypass the resistor, thus short circuiting the parallel port! On some motherboards this can fry everything from the parallel port controller to the entire motherboard![/COLOR]**
 
 **Getting the software**
 1. Download the attached file and extract it in your home dir. It's a compiled version of the lptout.c program listed here: [http://www.epanorama.net/circuits/parallel_output.html#linuxprogramming]("http://www.epanorama.net/circuits/parallel_output.html#linuxprogramming") 
 In other words, I didn't code it, all kudos for this app goes to Tomi Engdahl.
2. To make this app work it must be run as root but it's quite annoying having to run "sudo lpt 0" and enter your password each time you want to turn of the lights, isn't it? To make the app run with root privileges do the following in your home dir:
 ```
sudo chown root lpt
sudo chmod +s lpt
``` 3. Try it out! This should light up the LED connected to pin 2:
 ```
~/lpt 1
``` and this turns on all LEDs connected to the parallel port:
 ```
~/lpt 255
``` 
If nothing happens make sure that you've connected the LEDs the right way. Try to move them around and connect the resistor part to pin 2 and the LED part to pin 18.
 
How does this work? The parallel port works by outputting each bit of a byte to the pins 2 to 9 where each bit of the byte is equivalent to a pin on the parallel port. The first bit is pin 2, second bit pin 3 and so on.
For example: if you output decimal 1 to the parallel port pin 2 goes high since it's the equivalent of binary 00000001. (Google for binary numbers if you don't get a word about what I'm talking about right now). If you want to make the second led connected light up you want to output 00000010 which is decimal 2, third LED: 00000100 decimal 4.
If you want to many LEDs to light up at the same time you simply output 3, which will light up the first and second LED (00000011).
 To light up all leds you output 255 which is 11111111 binary, every pin goes high.
 *I know this is what people usually call a worthless explanation but it's almost four in the morning here and I'm getting kinda tired. Will fix it tomorrow.*
 
 You're set. To make the LEDs light up when a new mail arrive you need to configure your email application to execute the command
 ```
~/lpt 255
``` when a new mail arrives. I use checkgmail (HOWTO found here: [http://www.ubuntuforums.org/showthread.php?t=74539]("http://www.ubuntuforums.org/showthread.php?t=74539") ). To configure it rightclick on the Gmail icon in your notification area and select Preferences. In the bottom right corner is a text field to input a command that will be executed when a new mail arrives.
 
I've also created a launcher on my desktop that runs ```
~/lpt 0
``` to make the lights turn off when I've read the mail and I made a nice box for them out of paper. Photos tomorrow :-)

 To read a better explanation and learn a lot more about the parallel port check this site: [http://www.epanorama.net/circuits/parallel_output.html]("http://www.epanorama.net/circuits/parallel_output.html")

---

### Post by One Quick Question on 2005-12-09
Whoa...  I'm deffinitely going to build something awesome with this!
Combined with KDE's knotify, Kopete LEDs!

---

### Post by benplaut on 2005-12-09
that can be really usefull, for other things, too!

i need to get one of those printer cables!

---

### Post by Rob2687 on 2005-12-09
Fun stuff... We played around with parallel port stuff a lot in high school engineering classes.

---

### Post by Iandefor on 2005-12-10
I'm going to have fun with this...

---

### Post by shandar on 2005-12-10
Wow, it took five days to get this posted :P But yeah, it's a really neat and useful trick. I also built a soundcard / DA converter that connects to the parallel port. It works fairly well (just haven't figured out how the change frequency when using it as a soundcard :D ). But as a D/A Converter it works great. I'm thinking of using it combined with the LEDs to make them fade in and out when I get mail.

---

### Post by garba on 2005-12-10
eheh! well done shandar! calling all of this stuff geeky is un understatement! :D :D :KS

---

### Post by henriquemaia on 2005-12-10
This looks like one of the funniest to follow (& accomplish) howtos! Thanks a lot for this.

---

### Post by christooss on 2005-12-10
You couldmake a script which would

1. on first led
2. on second led off first led
3. off second led on third

Night rider stile :)

---

### Post by shandar on 2005-12-10
christoos, that is really easy to do if you get the source. edit two lines et voila!

and garba, this isn't very geeky compared to a lot of other stuff I've made, this is really simple to do. and it's actually useful too...

---

### Post by shandar on 2006-02-26
It's been a while now. Has anyone tried this tutorial? If so, what have you done? Photos perhaps? :)

---

### Post by renzokuken on 2006-02-26
photos would be amazing, might even give it a go myself then

---

### Post by jerome bettis on 2006-02-27
this is pretty cool, unfortunately my laptop doesn't have a parallel port.  do they make usb > parallel cables lol?  i wonder if this thing is possible using usb instead.

edit, they do make usb > parallel cables!  sweet

---

### Post by christooss on 2006-02-27
> I've also created a launcher on my desktop that runs
Code:

~/lpt 0

to make the lights turn off when I've read the mail and I made a nice box for them out of paper. Photos tomorrow

You have option in checkgmail What to do when no mail So you could put his in there :)

---

### Post by robert_pectol on 2006-02-27
About 2 years ago, I set out to find a peice of C code to do some simple parallel port manipulation.  I bet it's similar if not the same bit of code listed in the first post.  Anyhow, I needed our remote server to be able to interact with the outside world, and using the parallel port was obviously the easiest method.

We had a situation in which the router that provides Internet connectivity for our remote server, would sporatically "lock up" for no apparent reason and data would cease to flow until the unit was reset.  It happened frequently enough to start being a real pain in the neck!  Always having to place a phone call and them having track someone down to reset the router was not a workable solution so I set out to make something that would allow the server to automatically reset the router when it detected that it's Internet connection was down.  With the little parallel port controller code, a simple shell script, and a cron job, the software portion was solved!  All I had to do was construct a simple circuit which utilized a resistor, a transistor, and a micro-relay to interrupt the DC power line which fed the router.  It all fit in the "D" shell connector so it was all nicely (and safely) packed away and out of sight.  With some, "tweaking" of the Internet connectivity detector script, we had a solution that fixed our connectivity problems from that point on.  It's been nearly 2 years now and I'm glad to say, it's still working like a charm!  We still rely on it.  I've since, modified my original script to also provide logging as well as to send me e-mail alerts whenever it has to reset the router.  I get 1 or 2 e-mails per month, from the server.  I haven't had to call and request a router reboot even once since I implimented it!

Using that little parallel port controller program and some simple scripts, the possibilities are endless/limited only by your imagination!  Anyone else have a story to tell?  If so, I'd like to hear it.  It's things like this that make Linux fun!  :)

---

### Post by KillerBOB on 2006-03-20
Hello!
I just recently found this How-To, and I was very excited to try this out, to say the least! This is exactly the type of geeky thing that I tend to find both cool and interesting! Anyway I used an old printer-cable as suggested in your how-to, and used my solder-iron to make it more durable. 

The notifier-software that I found the best (for my uses) was ([Mail Notification 2.0]("http://www.nongnu.org/mailnotify")), compiled from source because the one in the repositories does'nt come with SSL-support. Another advantage with Mail Notification 2.0 is that it allows both to execute a script/binary when receiving AND when message is marked as read! So, it's no longer necessary to manually switch off the LEDs.

I put three LED's in the front of my computer case, they fitted very good in the air-intake :cool: . (Hopefully not obstructing too much of the incoming air)

I had only three leds at home, otherwise I would have used eight, since it looks really cool! I will attach a (poorly shot:evil: ) picture for you to see.

I also made two (very amateur-like) bash-scripts to get some effects out of the led's, which makes it look even better! If I have time I will make a short movie showing the effects.

Thank you for this how-to and if you have more projects you would like to share, I'm all up for it hehe

BTW, how do I attach a picture to my post? EDIT: I found out how to do it

EDIT: Now I have attached a small .3gp video showing the LED's blinking! (I think you need the Quicktime codec to view this.)

---

### Post by majikstreet on 2006-03-20
I've always wanted to do something like this.. but probably not going to be for new email though.. this reminded me of a howto I saw about smoothwall for status leds.. [http://martybugs.net/smoothwall/leds.cgi](http://martybugs.net/smoothwall/leds.cgi)
it actually can be used with any linux I believe and it is from a PS/2 port.. (good for me because my printer uses paralell...) I actually did what it said to an old keyboard.. I think I'm gonna play around with it lol.


edit: well, just my luck.. the old keyboard that I disassembled had an older "standard" connector.. NOT ps/2!

---

### Post by Randomskk on 2006-03-21
I guess I may as well add what I've done here..
After seeing this guide and reading something in a book I decided I must do this, so I gathered together a parallel cable, 8 3mm red LEDs and some 330 resistors and a breadboard from school, and got to work..
click the image for a video (it's in .3gp I'm afraid, but most players seem to handle it (like VLC)):
[[IMG]http://randomskk.net/RANDOM/LED.jpg[/img]](http://randomskk.net/RANDOM/led.3gp)

---

### Post by Randomskk on 2006-03-25
Well, I've worked on my original design..
I'll be making a PCB for this at a later date, so for now it's still breadboarded. This version uses an LPT (DB25) connecter you can solder to to make my life easier, four red 5mm LEDs and four green 5mm LEDs, eight 330 ohm resistors.
The four green LEDs are a CPU indicator - the more lit up, the more CPU usage, like so:
0% to 25% --> one LED
26% to 50% -> two LEDs
51% to 75% -> three LEDs
76% to 100% > four LEDs

The red LEDs, on the left (outputs 1 and 2) alternate when there is new email, and the reds on the right alternate when there is a new RSS feed (both these notifications use KDE's Notification thing, I use KMail and Akregator)

Click the image for a film that shows the CPU meter in action (I type "yes" into a console to bring up CPU) and the alternating lights (I manually turned on the program that does it).

[[IMG]http://randomskk.net/RANDOM/parallel/Image004.jpg[/IMG]](http://randomskk.net/RANDOM/parallel/Video001.3gp)

nb: if anyone wants the bash scripts used to do this (and the Python script someone in the programming forum gave me for CPU) just ask / PM me and I'll send them to you)

---

### Post by christooss on 2006-03-26
Randomsk: What about same thing with four or more LEDs that shows how much Hard disk is full

---

### Post by Randomskk on 2006-03-26
I'm sure this would be possible - a call to df, just get the usage % for the root file system (or for more prehaps, if you want) - and then use the same script as CPU but the input percentage is the HDD usage.

However, I can't say I'm anyway near good enough to implement such a thing.. and I can't really see the point of always having a HDD monitor. Mine doesn't fill up that quick :/

---

### Post by jason.b.c on 2006-05-14
**Randomskk** could you provide some more links to things like this..?? :-k   Serial port and parallel port stuff..  :D 

I'm not sure where to look on the internet for this kinda stuff..!:confused: 

Thanks..

---

### Post by Randomskk on 2006-05-14
Have you seen my how-to here?
[http://ubuntuforums.org/showthread.php?t=158265](http://ubuntuforums.org/showthread.php?t=158265)

---

### Post by mentok on 2006-05-14
[http://www.epanorama.net/circuits/parallel_output.html](http://www.epanorama.net/circuits/parallel_output.html)

[http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html](http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html)

[http://parapin.sourceforge.net/doc/parapin.html](http://parapin.sourceforge.net/doc/parapin.html)

---

### Post by skippy81 on 2006-05-15
While the project doesnt seem to be the most practical thing Ive ever heard of, it is undoubtedly very cool and it looks like great fun :p 

I'm thinking, how hard would it be to repace the led with a relay (i think thats what you call it) and use it to switch the lights on and off?  :D

Also, do you know if similar interfacing tricks can be done via USB? if I could have USB controlled interior lighting that would be awesome.  :)

---

### Post by Randomskk on 2006-05-15
Skippy, it would be easy to replace the LED with a relay, or a transistor depending on your need.

Doing this via USB would be very difficult, as that would require a USB driver chip in your circuit.

Parallel is much, much easier for integrating your own circuits with a computer.

---

### Post by ewtesterman@cox.net on 2006-05-15
[QUOTE=skippy81]I'm thinking, how hard would it be to repace the led with a relay (i think thats what you call it) and use it to switch the lights on and off?  :D[/QUOTE]

I have used the parallel ports and serial ports for controlling relay logic circuits. This allows you to control high voltage 110 standard house lights, coffee pot, etc. I have used this primarily in building automated machines like conveyors running on 480 3 phase anyway the point is that you just have to get a coil of 5 volt dc to activate your relay. If you all like this stuff they make external I/O carriages that you can control, then you can have 100s of pins and with the use of relay or PLC you can have an unimaginable amount of control. I come from the other side of the house I can control machines I need to learn to build web interfaces and network information between the machines That would make a powerful combination. :twisted:

---

### Post by skippy81 on 2006-05-16
Thanks guys, controlling my house with my PC would be awesome :D  Maybe one day linux can do the cooking and cleaning for me also....

---

### Post by Randomskk on 2006-05-16
[QUOTE=ewtesterman@cox.net]I have used the parallel ports and serial ports for controlling relay logic circuits. This allows you to control high voltage 110 standard house lights, coffee pot, etc. I have used this primarily in building automated machines like conveyors running on 480 3 phase anyway the point is that you just have to get a coil of 5 volt dc to activate your relay. If you all like this stuff they make external I/O carriages that you can control, then you can have 100s of pins and with the use of relay or PLC you can have an unimaginable amount of control. I come from the other side of the house I can control machines I need to learn to build web interfaces and network information between the machines That would make a powerful combination. :twisted:[/QUOTE]

I guess that for the serial port you need some kind of driver chip to get any meaningful output? Serial only has one actual data out pin, AFAIK.

What kind of chips give you the multiple outputs? Sounds like fun.


Finally, as far as making web interfaces goes - this is really easy, if the stuff is already computer controlled! You edit scripts to take input when run as a CGI script on, say, apache and then you're away!
Google up CGI scripts and apt-get Apache to see what I mean, but you can have command line scripts run from the web server. Also, for simpler programming you can have PHP on the web server that just runs some simple scripts.

---

### Post by jason.b.c on 2006-08-18
> **shandar said:**
> Well, probably there are a thousand ways to do this both easier and prettier but this is how I did it real quick :-)
 
 
 
 **Getting the software**
 1. Download the attached file and extract it in your home dir. It's a compiled version of the lptout.c program listed here: [http://www.epanorama.net/circuits/parallel_output.html#linuxprogramming]("http://www.epanorama.net/circuits/parallel_output.html#linuxprogramming") 
 In other words, I didn't code it, all kudos for this app goes to Tomi Engdahl.



Yea uh...???   , I would really hope that somebody noticed this ..

**Where's the [SIZE="3"]compiled file[/SIZE]** of **lptout.c**....????

When you click on that download link he provided and start scrolling down to where the program (lptout.c) is located it's actually just a link to another page and lptout.c is in the wrong section of that page ( under webserver listing )...

> Make sure you can access your Linux computer with your web browser (running on the same or other computer) when Apache is running on the Linux computer.

2. Compile the lptout.c source code to lptout binary program, copy the pgoram to /usr/sbin/ directory and set rights so that it is always executed as root. You can do this by logging on as root and executing the following commands: 
[And here's the actual (supposed) download page.]("http://www.epanorama.net/circuits/weblpt/lptout.c")

I don't get it , Did anyone actually build this thing..??   I want to..! \\:D/

---

### Post by Randomskk on 2006-08-18
I did, heh.
I took it to the next step, as well:
[first try]
[http://ubuntuforums.org/showthread.php?t=158265](http://ubuntuforums.org/showthread.php?t=158265)
This one used a dirty collection of BASH scripts, plus that original lptout.c code, to generate a four-LED CPU monitor and used the other four LEDs as alerts for RSS/email

[second try]
[http://ubuntuforums.org/showthread.php?t=228894](http://ubuntuforums.org/showthread.php?t=228894)
I then rewrote the entire thing in one C++ file, which I've got compiled for both 32- and 64-bit machines, or you can download the source.

Really though if all you want is plain lptout, do this:
sudo apt-get install build-essential
gcc -o lptout lptout.c

Then you'll get a file "lptout", use it like:
sudo lptout 255
to light up all ports.


PM me or reply here if you have questions!

---

### Post by dragonlor20 on 2006-08-18
Photos anyone?

---

### Post by Randomskk on 2006-08-18
See my "Second Try" link in the post above, I've got three or four pictures in that post.

---

### Post by artr2334 on 2007-03-09
Please help me to compile that script.
Here is what my compiler returns:
```
root@artrr:/home/artr/Desktop# gcc -o lptout lptout.c
[B]lptout.c: In function 'main':
lptout.c:25: error: 'argc' undeclared (first use in this function)
lptout.c:25: error: (Each undeclared identifier is reported only once
lptout.c:25: error: for each function it appears in.)
lptout.c:27: error: 'argv' undeclared (first use in this function)[/B]
root@artrr:/home/artr/Desktop#
```

---

### Post by sarang on 2009-05-21
Just a warning: if you are driving more than a few LED's, don't drive them directly with the parallel port. Use a buffer in between  or use the parallel port to drive a transistor base and let the transistor drive the LED. The easiest way however would be to use a buffer, like the 7407 or 7417 chips.

---

