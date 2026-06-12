---
title: "Connecting temperature module to serial port"
date: 2007-10-18
forum: Programming Talk
---

### Post by Swab on 2007-10-18
So, this is perhaps the wrong place to be asking, but someone might be able to help. 

I bought a temperature module from Maplin, it has a "13-bit BCD Serial output" which I want to connect to my PC via the serial port.  I naively thought there would just be an  rx terminal on the module which I could connect to the tx on my serial interface.  However there are 2 serial output terminals on the temperature module.

Pin 9: Serial data output terminal
Pin 10: Load pulse serial output terminal

I am not sure what a load pulse serial output is!

The scan attached  shows the purpose of each terminal.  I can see that D1 - D13 would represent the 13 bits, presumably D1 being used for signing, and then 4 bits each for each BCD number.  But still not really sure what is going on.

So basically, does anyone know how to connect this to my serial port? 

[IMG]http://www.freeandopenisland.org/images/serial.png[/IMG]

---

### Post by xtacocorex on 2007-10-18
Does the temperature module have the 9-pin d-sub connector on it? If not, you'll probably have to find a 9-pin solder cup serial connector and attach it yourself.
 
This is a link to how to program apps to use the serial port.
[COLOR=#000000][http://tldp.org/HOWTO/Serial-Programming-HOWTO/index.html](http://tldp.org/HOWTO/Serial-Programming-HOWTO/index.html)[/COLOR]
 
[COLOR=#000000]Other than that, I don't know. Hope this helps some.[/COLOR]
 
[COLOR=#000000]You have a link to specs about the actual temp module?  That might help some.[/COLOR]

---

### Post by Swab on 2007-10-18
Thanks for the reply, much appreciated.

No the module does not have the db connector, only terminals to solder on to.  What I do not know is what to solder where :) 

Don't really have much other information other than the images I posted.  Pin 1 is ground, Pin 16 is +1.5V, the rest of the pins other than 9 and 10 do not seem to be relevant to serial comms.  

Here is the module on Maplin's website: [http://www.maplin.co.uk/Search.aspx?criteria=FE33L&DOY=18m10](http://www.maplin.co.uk/Search.aspx?criteria=FE33L&DOY=18m10)

---

### Post by Swab on 2007-10-18
OK, I think that "load pulse" has something to do with flow control, so I am *guessing* this has to be connected to RTS pin on the db connector.    Guess I'll just give it a go!

---

### Post by xtacocorex on 2007-10-18
After looking at the serial port pin out, I figured that load pulse would be RTS and the data pulse would go in the RX port.  Good luck with the stuff.

---

