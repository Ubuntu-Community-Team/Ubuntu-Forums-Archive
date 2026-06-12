---
title: "How does a computer flip it's switches?"
date: 2011-07-01
forum: Programming Talk
---

### Post by ki4jgt on 2011-07-01
I've asked several people this question (teachers, professors, programmers, and a couple of hackers) no one seems to have an answer. They all take me to binary charts and show me the number sequence (which I already know) My question is: How does a computer flip the switches inside of it to store, process, and evaluate those number sequences? (Example number sequence: 01001101 how does the computer flip those switches? I know it's a magnetic hard <not really switches> drive, but I'm asking in general.) On a more local level, A light bulb can not flip it's own switch. A human must flip the switch and allow the electrons to flow. When the computer receives the command poweroff/reboot, how does it flip it's own switch to poweroff? So how does the computer do it? How does it use electrons to influence hardware?

---

### Post by r-senior on 2011-07-01
I see at least three questions in there:

a. How does a computer use and manipulate switches to process binary data?

It's been a long time since I did electronics and my knowledge of how microelectronic technology has lapsed but the basic idea is one of flip-flops and latches:

[http://en.wikipedia.org/wiki/Flip-flop_%28electronics%29](http://en.wikipedia.org/wiki/Flip-flop_%28electronics%29)

Essentially these are overdriven amplifiers that flip on or off but retain their state due to the way the timing of the circuit is arranged. Modern circuits use different technology but the basic idea is the same.

b. How does a computer set "switches" on a storage device, e.g a hard disk

Hard disks are a form of magnetic storage. A circuit can magnetize tiny parts of the medium so that ons and offs can be retained even when the power goes off:

[http://en.wikipedia.org/wiki/Magnetic_storage](http://en.wikipedia.org/wiki/Magnetic_storage)

c. How does a computer switch itself off?

When you are thinking of the light bulb example, you are thinking of a single circuit. Appliances that can switch themselves on and off or go into standby have a low-power controlling circuit that controls another circuit using a relay of some sort:

[http://en.wikipedia.org/wiki/Relay](http://en.wikipedia.org/wiki/Relay)

If you think of a TV in standby, the remote control interacts with a low-power circuit that uses a relay to control the main circuit. So when you press the on button, the TV comes on.

With a computer switching itself off, the final act of the relay could be to power down the low-power "standby" circuit. Or it could leave it on - some motherboards have a wake-on-lan feature for example. In this case the low power circuit is always on.

I'm sure someone with more current knowledge (if you'll pardon the pun) could explain what actually happens with computers shutting down but that's the basis of it.

---

### Post by Tony Flury on 2011-07-01
Wow - deep question - probably.

the thing to remember is that in a computer the switches are not mechanical things - the switches are implement as transistors. A transistor can be made to act as a switch - and more importantly more tnan one transistors together can be made to act as a logic gate - And/Or/Not etc.

Also you can build transistor based switches to switch the power to the main circuits (essentially powering off your computer). Pressing the power button again, triggers a small signal to these power transistors, causing a ripple of various items powering up.

String some And/Or/NOT gates together and you can build an Adder - i.e. literally a device that takes in two digital inputs and generates an output which is the sum of those inputs. From these you can build any mathematical operation you wish.

Comibine some transistors in another way and you get a device called a bistable. These can be used as the basis of a memory device - so long as you keep power to them they can be used to "remember" the last input - and can be read as many times as you want without degrading the memory (until you turn off the power).

Hard drives are subtly different again - they store the 1s and 0s as a pattern of magnetic fields on a ceramic disk - and those patterns can be read back as often as you want - and you don't need to keep any power to the disk to keep that memory alive.

---

### Post by amauk on 2011-07-01
Transistors
The "switch" that allows modern electronics to operate

One electrical input, going to one of two possible outputs depending on the value of the input
Voltage below a certain threshold, Output 1
Voltage above a certain threshold, Output 2

See here
[http://en.wikipedia.org/wiki/Transistor](http://en.wikipedia.org/wiki/Transistor)

You can imagine that when a bunch of transistors and other components (resistors, capacitors, diodes, etc.) are arranged in certain ways, you can get some quite interesting results with one device's output feeding into the input of the next, and so on down the line

This circuit logic can be utilised to create "logic gates"
For a known input, some known process occurs and you get a pre-determined output

See here
[http://en.wikipedia.org/wiki/Logic_gate](http://en.wikipedia.org/wiki/Logic_gate)

As for how a computer turns itself off, there will be a certain set of conditions that when filtered down through all the circuit logic results in the mains power circuit being broken

---

### Post by jhonan on 2011-07-01
I find it's much easier to visualise this from the viewpoint of the old 8-bit processors.

So imagine the computer wants to store a character or a number in memory. And it'll need to do this a lot. In fact, the main thing the CPU does is read stuff from the memory, process it, and write it back out again. And the memory one place where these tiny little switches are turned off or on.

In 8-bit land, if I told the CPU to store the number 187 somewhere in memory, it would find a free location (a part of the memory chip not being used by anything else), and converts 187 to binary (10111011 in this case) ready to be stored.

At that point, it uses electrical signals to turn a row of 8 microscopic transistors to either on (representing 1) or off (representing 0) - If you could look at that part of the memory with a voltage detector, you'd see a row of 8 transistors that look like this;

on, off, on, on, on, off, on, on

Which in binary means;

10111011

which in decimal means

187

When you tell the CPU at a later time to read the contents of that memory location, it scans the state of each of the transistors, and returns the binary number. In modern chips there are millions and millions of these, and instead of being ordered into groups of 8 (8-bit) they're arranged in groups of 64 (64-bits)

---

### Post by boast on 2011-07-01
the system clock starts the process and controls the process. 


as for memory, I will use dynamic ram as an example since its simple:

[img]http://www.cse.scu.edu/~tschwarz/coen180/LN/Images/dramcell.bmp[/img]

based on the address that is sent to the memory, the memory controller figures out what memory chip and what word line (a word like can be 16-32-64 bits wide) to select. As you see above, this turns on the transistor by the gate being pulled high, so the logic value stored in capacitor "C1" (there is not a physical capacitor, but imagine it as one) comes out the column "bit line." If you want to store a value, when the transistor T1 is enabled, the bit line will actually contain the logic you want to store instead receiving the logic stored, and then C1 will be "overwritten" with the logic in the bit line.

Memory use sense amplifiers to quickly determine the logic stored, since going from 0V to say 5V is a lot of power usage and too slow for memory (since its very small, the power lines are small, so bigger resistance and slower). So it uses a sense amplifier along with reduced swing voltage, so if a 1.3V line drops to like 1.1V it knows there is a logical 0- not waiting until the voltage completely reaches 0.

---

### Post by ac7nj on 2011-07-01
> **ki4jgt said:**
> I've asked several people this question (teachers, professors, programmers, and a couple of hackers) no one seems to have an answer. They all take me to binary charts and show me the number sequence (which I already know) My question is: How does a computer flip the switches inside of it to store, process, and evaluate those number sequences? (Example number sequence: 01001101 how does the computer flip those switches? I know it's a magnetic hard <not really switches> drive, but I'm asking in general.) On a more local level, A light bulb can not flip it's own switch. A human must flip the switch and allow the electrons to flow. When the computer receives the command poweroff/reboot, how does it flip it's own switch to poweroff? So how does the computer do it? How does it use electrons to influence hardware?
This has been an interesting thread because all of the post are part of the the answer.

a transistor has 3 wires 2 of the wires are input and output, the third wire controls the flow of electricity form the input to the output. The third wire accomplishes this by either putting voltage on the third wire or removing the voltage. There are 2 types of transistors, 1 is the on type and the other the off type. (PNP or NPN) so we now have a switch that is controlled by electricity. If we arrange these transistors so that they remain on or off in other words toggling we can create a logic condition. This is kind of like the light switch on a lamp and plugging or unplugging the lamp from the wall, it will come on or stay off based on the last condition of the switch (logic switch simplified)

1 logic switch by it's self is not very exciting it can't do much, but what if we had several of them lets say 8 now how many different configurations can we have 00000000 or 10101010? I used 0's and 1's intentionally. So next OK we can create all these different configurations, what is the point? The point is we have ASCII standard as a logic table this defines all of the possibilities as things like the letter "A" or the number "4" etc. Because the configurations are binary numbers we can do another cool thing with them math adding or subtracting etc.

---

### Post by scu-ba-de-buntu on 2011-07-01
NOTE: I got board while writing this. i am posting it any way since it is sort of helpful. 

first, why is everyone assuming it is a transistor based architecture?


You would think your question would be a straightforward thing to answer, but it really isn't.

There are MANY levels to how a computer "works". These can range from hardware implementation, to a interpretation of what the hardware means, basic logic format, to how the logic moves through the system, arrangement of memory locations, to low level protocols, to any range of protecols that may be build on others.  

I find that the method of working with (physically) the data is irrelevant until a general decision on how logic should operate has been made. 1 doesn't have to be a high-bit it could be a low-bit and could be decided to be interpreted leading edge or trailing edge. It is all how the engineers agree the "system" will "work." The system may have different word sizes, etc.

My first recommendation is to look at [http://www.fastchip.net/howcomputerswork/p1.html](http://www.fastchip.net/howcomputerswork/p1.html) . It is a very good primer on the subject of logic used in a computer. Then check out some books on the topic and take some college course in electrical engineering, computer architecture and computer operating systems (development of, no how to use or something).

Here is an example:
From electronics, you may remember that some memory devices can output data FirstInFirstOut (FIFO). Lets say that that memory device has a X amount of data burnt onto it. This data, the binary, has been laid out explicitly for the system it will run on. This means that lets say it is a type of 3bit system.

This system does not have any buffer, understanding of timing, etc.

```

000 might mean if a button is pressed (wire has a value 1, we shall define that as true) then LOGIC bit =1
001 means increment system / do nothing
010 means logic bit = inverse logic bit
011 if logic bit = 1, light turns on, if not it turns off
101 set bit to 0
100
110 start reading memory off normal (Harddrive?) memory at address 0  instead
111 branch (skip some i don't know,5 addresses [5*3 bits]) if logic bit true
etc

```

lets say the system has a 2 buttons, every time you push 1, it affects how 01 is interpreted, button 2  steps through the logic on button up. They system will work as long as there is power. Must be unpluged to reset, eg on halt.n  Logic bit is not in a safe state since we don't know how it is implemented - it may or may not hold information after power goes out.

"BIOS" for this system may include something that gets the system to a safe state by setting logicbit to 0 and making sure that the user is not pushing the button by flashing the light if he/she is. This code could be dumped into the processor. The system could be made that if at the end of the 20 cycles, the system starts pulling from some other memory. 


i wrote it into this text box, so it WILL have errors
```

001  .. give system a sec
101  .. try setting to 0
000  .. check button for stick , eg. errors
111  ..  branch if true
011  .. turn off the light if on
110  .. false good, so end bios / firmware pullup a
001  .. do nothings, filler since a branch would skip this
001
001
000  .. check button again
011  .. start that binking warning (on)
010  .. logic for blink
011  .. binking warning (off)
010  .. logic for blink
011  .. binking warning (on)
000  .. check button again
111
110
001  .. do nothings, filler since a branch would skip this
001
001
001
011  .. start that binking warning (on)
010  .. logic for blink
011  .. binking warning (off)
001
111
110 .. good stopped pressing button, start machine up
001
001
001
001
011  .. start that binking warning (on)
010  .. logic for blink
011  .. binking warning (off)
011  .. start that binking warning (on)
010  .. logic for blink
011  .. binking warning (off)
011  .. start that binking warning (on)
010  .. logic for blink
011  .. binking warning (off)
011  .. start that binking warning (on)
010  .. logic for blink
011  .. binking warning (off)
100  .. failed  to boot, halt


```


if you are looking to learn more about the physics of lumped mass devices, those that you don't 'need' to worry about maxwell;s equations, then lopok at that - physics (& chemistry).  

I could be wrong, and this is only one system i made up as i wrote the response cheers


Edit: 

PS, the program would therefore be:
001101000111011110001001001000011010011010011000111110001001001001011010011001111110001001001001011010011011010011011010011011010011100


which requires 135bits of memory or 135/3=45 "3bit bytes" (if the system specification defined it as such - since a LONG time ago this would NEVER be the case other than 8bit to a byte, but again, that is just a specification) If you wanted you could store this on a modern piece of hardware and maybe pull two optcodes per 8bit-byte and drop the last for nothing other than requiring some pattern for data integrity varification -ei. every other is a 1 or all 1s or whatever....

---

