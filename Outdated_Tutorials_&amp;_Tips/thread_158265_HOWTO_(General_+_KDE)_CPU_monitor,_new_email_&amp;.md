---
title: "HOWTO: (General + KDE): CPU monitor, new email &amp; new RSS alerts using LEDs"
date: 2006-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Randomskk on 2006-04-10
I'll start by quickly saying that this was all inspired by [this](http://ubuntuforums.org/showthread.php?t=99082) thread. It got me started on ideas :D

Before I get started, this produces something like:
[URL=http://randomskk.net/uploads/oldpar/Video001.3gp]
[IMG]http://randomskk.net/uploads/oldpar/Image004.jpg[/IMG][/URL]
That your computer can fully control. (click it for a video)


Anyway, this How-To is for making 8 LEDs that are connected to your computer via the parallel cable, and are controlled to show a CPU monitor, and give an alert on a new email or RSS feed.
This How-To is General+KDE because while almost all of it is general, to actually get the alerts to trigger I can only speak for KDE programs - although I'm sure GNOME programs can be configured to the same effect.

**The first thing you'll need is hardware:**

To make this without a breadboard or PCB:
8 LEDs of whatever size/colour you want
8 330ohm resistors (or larger, colour bands orange orange brown)
9 short wires
Parallel cable
(optional) DB-25 connector to parallel cable for easy soldering

To make a breadboard version:
8 LEDs of whatever size/colour you want
8 330ohm resistors (a bit bigger would be OK as well) - these are colour bands orange, orange, brown.
9 small (2") wires to go from DB25 socket to breadboard
1 standard breadboard
(Optional) 1 DB25 connector, this lets you plug a parallel cable in one side and solder to the other

To make a PCB version:
8 LEDs of whatever size or colour
8 330ohm resistors (this is orange, orange, brown and slightly large would be OK)
parallel cable
PCB mountable DB-25 connector
and of course, PCB development stuff


Once you have the hardware, it needs to be connected like so:
[IMG]http://www.epanorama.net/circuits/lptleds.gif[/IMG]
Note that you only need to connect to one of the ground ports, so just connecting to 18 would do.

If you're not using a breadboard or PCB, this will be fairly easy to simply solder some wires to the LEDs, resistors to them, and then the resistors to pin 18. Some more cable might help you here.

If you're using a breadboard, you should be able to make this fairly easily, connect pin 18 to a long rail, then pins 2 through to pin 9 to the 
cathode of an LED (long leg), put the anode (short leg) into the nearby line, then a resistor from that to the negative rail.

If you're making a PCB, I'm sure you can make your own artwork as you want it, and I don't have PCB devel kit anyway so can't help I'm afraid :(

If you do not get a DB-25 connector (like [this](http://www.maplin.co.uk/Module.aspx?ModuleNo=1113&criteria=D-Sub%20Connectors&doy=11m4)) then you'll need to cut off one end of the parallel cable, cut off some shielding and expose the wires inside, then use a multimeter or similar to find out what wires go to what ports. The DB-25 connector really makes this project a LOT easier, so I really recommend getting one if you can.

After you have your 8 LEDs connected to your computer via a parallel port, you need software.

**Software**

[lptout](http://www.epanorama.net/circuits/lptout.c) - a C program written by Tomi Engdahl, it's a really simple program that just takes a value and sends it to the pins. Accepts decimal values (ie, from 0 to 255) and needs root permissions to run properly (sudo chown root lptout; sudo chmod +s lptout) and must be compiled (gcc lptout.c -o lptout)

pin, part of the [parashell](http://parashell.sourceforge.net/) suite. Download the .tar.gz, tar xvf it, then make and sudo make install to install. Once installed, you can call "pin" at the command line and it will tell you what pins are lit up.

BASH, and the scripts I've put [here](http://randomskk.net/uploads/oldpar/parallel.tar.gz). Extract these to a directory, I use parallel, and then open each and change every occurrence of "/home/adam/parallel" to "/path/to/your/parallel" and then chmod +x each file. Once you've done this, and lptout is in the same directory, you should be able to run flash.sh and have a little pattern flash by.

You'll see a usage.sh and cpu.sh, both of these require a program in python someone gave to me on the Ubuntu forums [here](http://ubuntuforums.org/showpost.php?p=853257&postcount=4), and I modified it slightly so that it works for me (version you need is [here](http://randomskk.net/uploads/cpu.py)) and save my version to the same parallel folder.
(you'll also need to chmod this +x)

Once you're all done, setup your programs (I use email and RSS, but you could use whatever) to start the newmail.sh or newrss.sh programs when they get new email, and if they support it to run nomail.sh or norss.sh when there is nothing new. If they don't support it, I bound windows+D to run the lightsout.sh program, which just run both the nomail/norss.sh files.
To do this in KDE, assuming KMail for email and aKregator for RSS, go to Settings / Configure Notifications, choose the option you want (for example, "New mail has arrived") and click the advanced button. Then, tell it to execute a program, type in the path to newmail.sh, click OK and you're set - the program will alternate the lights when it gets new email.

Note that the BASH scripts do have a few bugs:
1) when you get new email or new RSS, the CPU monitor pretty much locks itself until you turn the alerts back off
2) sometimes the alternating doesn't work nicely when two new RSS/emails are gotton before you turn them off, if the second instance of the program starts at a bad time both LEDs could just turn solid.
Both of these bugs could be worked out, but they're nothing too bad really.

If you have any problems, feel free to ask me.

As an aside - it is possible to have switches built into this, but they need a separate 5v power supply to be reliable, and add complexity to the circuit that isn't really needed. For more info on that, look [here](http://www.epanorama.net/circuits/parallel_output.html#input)

---

### Post by Randomskk on 2006-04-11
Ok, for connecting switches as inputs, the hardware side of things:
Pins 10, 11, 12, 13 and 15 are inputs, run a wire from one of them through a switch and then to ground (use pin 19, for example).

Then you press the switch to drop the voltage on the pin and effectively send it high.

As far as programs to control this, [http://www.epanorama.net/circuits/parallel_output.html#input](http://www.epanorama.net/circuits/parallel_output.html#input)

---

### Post by uantuzri on 2006-04-19
It took me some time but I have it working. It's really nice. Now i'm trying to give it some other functions, such as the temperature in my box, since I can't use gdesklets (hello compiz, goodbye gdesklets), but I don't know how to begin. Any ideas?

---

### Post by Randomskk on 2006-05-14
If you want the four LEDs to show hard disk usage, the following command will output a % of a partition, so just point it to whatever partition you want monitoring:

df /dev/{partition} | egrep -o "..%" | egrep -o ".." | grep -v "se"

Example for /dev/hda1:
df /dev/hda1 | egrep -o "..%" | egrep -o ".." | grep -v "se"


Saving this to a script, chmod +x the script and modify usage.sh to query your script will have it show the disk usage.

---

### Post by William the Conquerer on 2006-06-16
so does anyone know the possibilities of using this idea to send signals to groups of LEDS (through the parallel port) to correspond to music playing on that computer??... (like disco lights or have the lights "dance" to the music..)  any ideas, I would love to do this, but I doubt it could be anywhere near easy =(

---

### Post by Randomskk on 2006-06-16
A plugin for xmms could conceivably do this, but I'm afraid I'd have no idea how.

---

### Post by Randomskk on 2006-07-16
I'm now re-writing this project in C++, will update this thread with more info when I finish.
The new version will have a GUI and should be a good deal better and easier to use =D

---

