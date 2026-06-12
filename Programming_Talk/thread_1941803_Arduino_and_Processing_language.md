---
title: "Arduino and Processing language"
date: 2012-03-16
forum: Programming Talk
---

### Post by linuxonbute on 2012-03-16
I am trying to use my Uno as a simple oscilloscope but am having a problem with processing not receiving data from the arduino.
I decided to use some simpler code from Arduino Cookbook and have simplified that even more.
Both compile and the processing code displays a white box
but no rectangle is drawn and the line: println("Message received: " + value2);
does not show up in the processing IDE message window.
All I get is this:
> 
WARNING:  RXTX Version mismatch
    Jar version = RXTX-2.2pre1
    native lib Version = RXTX-2.2pre2
When I start processing up I get a message about Sun Java and I have Openjdk
I have tried to find out how I can install and use the Sun java jdk 
but I am completely lost with this as a lot of what I have depends on the Openjdk 
and I have not been able to find out how to actually install  the Sun Java sfuff anyway.
Having read various instructions I keep finding that what I have and where it is 
does not correspond with the instructions.
I am running ubuntu 10.10 

If I run the serial monitor in the arduino IDE I get characters displayed 
so I can see the arduino code is working.
To make it as simple as possible on the hardware side all I have is a 10k pot connected +5v > one end of pot,  arduino analog(0) > centre of pot,  Ground > other end of pot.

Anyone any ideas as to how solve this problem please?

arduino code
```

int intValue;
void setup()
{
  Serial.begin(9600);
}

void loop()
{
  Serial.print('H');
  intValue = analogRead(0);
  Serial.print(lowByte(intValue), BYTE);
  Serial.print(highByte(intValue), BYTE);
  delay(100);
}

```Processing code
```

import processing.serial.*;
Serial myPort;
short portIndex;

char HEADER = 'H';
float startx, starty, value1, value2;

void setup()
{
size(600, 600);

myPort = new Serial(this, "/dev/ttyACM0", 9600);

}
void draw()
{
 if (myPort.available() >= 3)
 {
   if(myPort.read() == HEADER )
   {
     value1 = myPort.read();
     value2 = myPort.read() * 256  + value1;
println("Message received: " + value2);
   }
}
background(255);
fill(0);
rect(startx, starty, value1, value2);
}

```

---

### Post by linuxonbute on 2012-03-17
I have now tried different code but it still doesn't do what I had hoped.

Arduino code:
```

int intValue;
void setup()
{
  Serial.begin(9600);
}

void loop()
{
  
  intValue = analogRead(0);
Serial.print(intValue, DEC);

}

``` And here is the Processing code:
```


import processing.serial.*;
Serial port; // Create object from Serial class
int val; // Data received from the serial port
int ypos = 0;
void setup() {
size(800, 400);
strokeWeight(2);
// IMPORTANT NOTE:
// The first serial port retrieved by Serial.list()
// should be your Arduino. If not, uncomment the next
// line by deleting the // before it. Run the sketch
// again to see a list of serial ports. Then, change
// the 0 in between [ and ] to the number of the port
// that your Arduino is connected to.
println(Serial.list());
String arduinoPort = Serial.list()[0];
port = new Serial(this, arduinoPort, 9600);
}
void draw() {
//  delay(10);
if (port.available() >0) {
val = port.read();
// If data is available,
// read it and store it in val
point(ypos, val );
ypos += 1;
println(val);

}
if(ypos >799)
{

  ypos=0;
  background(204);
}


}


```The message window in Processing prints out:

/dev/ttyACM0

which is correct
but then it just prints 52 48 52 48 over and over no matter how I adjust the potentiometer.

Any ideas anyone?

---

### Post by linuxonbute on 2012-03-18
Well with some help on the arduino.cc forum I have got this sorted.
In case anyone is interested here is the code which I am releasing under the GPL version 3.

arduino code

Code:
int val;
int dtime = 10;
void setup()
{
  Serial.begin(115200);
}

void loop()
{
  
  val = analogRead(0);
  Serial.println(val);
  delay(dtime);

}


Processing code

Code:
import processing.serial.*;
Serial myport; // Create object from Serial class
int val; // Data received from the serial port
int ypos = 0;
int xpos;

void setup() {
size(1200, 512);
strokeWeight(2);
line(0,255,1200, 255); // horizontal line half way up 
String arduinoPort = Serial.list()[0];
myport = new Serial(this, arduinoPort, 115200);
myport.bufferUntil('\n');
}
void draw() 
{
}

void serialEvent(Serial myport)
{
String inString = myport.readStringUntil( '\n' );

if(inString != null )
  {
  inString = trim(inString);
  xpos = int(inString)/2;
  point(ypos, 512 - xpos );
  ypos += 1;
  println(xpos);

  if(ypos >1199)  // One less than displayed window width.
  {
     ypos=0;
     background(204);
     line(0,255,1200, 255);
  }

}

}


Now to see if I can develop it further.                             [IMG]http://arduino.cc/forum/Themes/arduinoWide/images/buttons/doc_edit.png[/IMG]

---

### Post by Landreas on 2012-12-20
linuxonbute, I just need to thank you for this. I've spent so many hours trying to make Arduino, Processing and Ubuntu play nice, but after an accidental reinstall of Ubuntu (don't play with tasksel), everything just worked right out of the box with your code. The arduinoPort array of your code which previously wouldn't contain any elements, now contains the port of my Arduino. 

For those curious, this is what I did (32-bit system):
1. Installed Arduino IDE (v. 1.0.1) from the Software Center
2. Downloaded processing (v. 2.0b7) from their official site and extracted it within my home folder
3. Connected my Arduino R3 and ran the IDE
4. Gave the IDE the permissions it needed
5. Logged out and in again
6. Started the Arduino IDE
7. Copied linuxonbute's code and transferred it to the Arduino (if a message pops up saying your Arduino can't be detected, ignore it and press OK)
8. Went to Processing's folder and ran the file «processing».
9. Copied the rest of the code, clicked run, and the rest was bliss. If you have a potmeter or something hooked up to A0, you should see a graph being drawn in the processing window as you turn the knob.

As for my java version:
```
landreas@Mox:~$ java -version
java version "1.7.0_09"
OpenJDK Runtime Environment (IcedTea7 2.3.3) (7u9-2.3.3-0ubuntu1~12.10.1)
OpenJDK Client VM (build 23.2-b09, mixed mode, sharing)

```

---

### Post by linuxonbute on 2012-12-20
Here is an update to the processing code.
I just started working on this again a couple of days ago.
It splits the screen into an upper and a lower section.
It is still only 1 input so it draws the line across the top section then continues on the lower section.
It then goes back to the top section and continues, wiping out the previous line ahead of the new one.
I am going to work on increasing the speed at which the arduino code works next if I can/
```

import processing.serial.*;
Serial myport; // Create object from Serial class
int val; // Data received from the serial port
int ypos = 0;
int xpos;
int divider = 4;
int topend = 512;
int[] lastpos = new int[2005];
PFont font;
int offset=0;


void setup() {
size(1260, 512);
strokeWeight(1);
line(0,255,1200, 255);

font = loadFont("AndaleMono-28.vlw");
textFont(font);
pagesetup();
String arduinoPort = Serial.list()[0];
myport = new Serial(this, arduinoPort, 115200);
myport.bufferUntil('\n');
}
void draw() 
{
}

void pagesetup()
{
background(225);
line(0,255,1200, 255);
fill(255);
rect( 1000,0, 1000,512);
fill(0);
text(" Norm's scope", 1000, 30, 1000, 100);
line(1000,127,1010,127);
text(" 2.5 volts", 1005, 110, 1005,110);
line(1000,383,1010,383);
text(" 2.5 volts", 1005, 365, 1005,373);
}

void serialEvent(Serial myport)
{
String inString = myport.readStringUntil( '\n' );

if(inString != null )
{
inString = trim(inString);
xpos = int(inString)/divider;
if (lastpos[offset] != 257)
{
stroke(255);
point(ypos, topend - lastpos[offset+1]);
}
stroke(0);
point(ypos, topend - xpos );
lastpos[offset]= xpos;
ypos += 1;

if(ypos >999 && topend==512)
{
ypos=0;
topend= 256;
//offset=1000;
}

if(ypos >999 && topend==256)
{
ypos=0;
topend= 512;
//offset=0;
}
offset++;
if(offset>2000)
{
  offset=0;
}
}

}

```

---

### Post by tgalati4 on 2012-12-20
I would like to see some screenshots.  I just got a sparkfun.com kit and I'm going through the exercises.  What is the upper frequency bound?

---

### Post by linuxonbute on 2012-12-21
Good question!

I have not got to the stage where I can say for sure. However the microcontroller chip is not a fast one and I suspect it will only do audio frequency or maybe a little more.

---

### Post by Landreas on 2012-12-22
Can't answer you about that, tgalati4. 

linuxonbute: I've kept my self occupied all day reading about serial communication and I may have a solution as to how you can get faster transfer speeds. Serial.print() sends the data as ASCII encoded characters, while Serial.write() sends the data as bytes. Which means the string "1234\n" takes 5 bytes versus the 2 bytes of the int. Transferring with write() will therefore be more efficient.

Serial.write() can only send one byte at a time, though, so you'll need to break the int up, send it's bytes individually, recieve the bytes with processing and reconstruct the int. myport.read() in processing reads one byte on every call, so we'll call that twice when enough bytes are available. In other words, some code:

Arduino code
```


void setup(){
  Serial.begin(115200);
}

void loop(){
  int number = 12856;

  /*Since the int holds two bytes in Arduino and
  write() can only send one byte at a time, we'll 
  break the int into separate bytes: 
  */ 
  Serial.write(number / 256);
  Serial.write(number % 256);  
  
  while(1); //Excecution stops here

}
```

Processing code
```

import processing.serial.*;
Serial myport;

void setup(){
  String arduinoPort = Serial.list()[0];
  myport = new Serial(this, arduinoPort, 115200);
  myport.bufferUntil('\n');
}

void draw(){
  //Let's check if we've gotten our two bytes
  while (myport.available() >= 2) { 
    int inInt = myport.read() * 256 + myport.read(); 
    //read() reads one byte at a time and puts them together.
    println("Here's your int: " + inInt);
  }
}
```

[IMG]http://i.imgur.com/2i1GB.png[/IMG]

This should give you the value in processing's terminal. In my case 12856. I should however warn you that I'm pretty novice, and there may be way better ways of doing this. I haven't figured out how to transfer doubles the same way, and I was also unable to invoke serialEvent() - that's why the receiving bit is placed to loop infinitely in draw(). Perhaps serialEvent is waiting for '\n'?

---

### Post by Landreas on 2012-12-22
Processing is a ton of fun!

linuxonbute, wiping out the lines ahead was no bad idea at all. Looked way smoother.

Here are some screenshots for you, tgalati4:

Simple voltmeter, graph
[IMG]http://i.imgur.com/mc6oI.png[/IMG]

Processing code for the graph version
```
import processing.serial.*;
Serial myport;
final int WIDTH = 480;
final int HEIGHT = 480;
/*If we're going to draw a graph, we'll need both current
and the previous Y coordinate. The previous one must be
initialized to something: */
int xpos = 0;
int ypos, yposLast = HEIGHT/2;
PFont font;

void setup(){
  String arduinoPort = Serial.list()[0];
  myport = new Serial(this, arduinoPort, 115200);
  myport.bufferUntil('\n');
  font = loadFont("Sawasdee-28.vlw");
  textFont(font);
  pagesetup();
}

void pagesetup(){  
  size(WIDTH,HEIGHT);
  background(51);
  text("0V", width - 40, height - 10);
  text("5V", width - 40, 30);
  stroke(254, 87, 0);
}

void draw(){
  while (myport.available() >= 3) {
    //The arduino now sends a control byte before each int, 11111111.
    if(myport.read() == 0xFF){
      ypos = myport.read() * 256 + myport.read();
      ypos = (int)map(ypos, 0, 1023, 0, 480);
      
      //Let's draw the current bit of the graph
      line(xpos - 1, yposLast, xpos, height - ypos);
      
      yposLast = height - ypos;
      xpos += 1;
      if(xpos > width){
        xpos = 0;
        background(51);
        text("0V", width - 40, height - 10);
        text("5V", width - 40, 25);
      }
        
    }
  }
  
}
```

Simple voltmeter, bars
[IMG]http://i.imgur.com/VWa4H.png[/IMG]

Processing code for the bar version
```
import processing.serial.*;
Serial myport;
int xpos = 0;
int ypos;
final int WIDTH = 480;
final int HEIGHT = 480;
PFont font;

void setup(){
  String arduinoPort = Serial.list()[0];
  myport = new Serial(this, arduinoPort, 115200);
  myport.bufferUntil('\n');
  font = loadFont("Sawasdee-28.vlw");
  textFont(font);
  pagesetup();
}

void pagesetup(){  
  size(WIDTH,HEIGHT);
  background(51);
  text("0V", width - 40, height - 10);
  text("5V", width - 40, 30);
  stroke(254, 87, 0);
}

void draw(){
  while (myport.available() >= 3) {
    //The arduino now sends a control byte before each int, 11111111.
    if(myport.read() == 0xFF){
      ypos = myport.read() * 256 + myport.read();
      ypos = (int)map(ypos, 0, 1023, 0, 480);
      
      //Let's draw the current bar
      line(xpos,height,xpos, height - ypos);
      
      xpos += 1;
      if(xpos > width){
        xpos = 0;
        background(51);
        text("0V", width - 40, height - 10);
        text("5V", width - 40, 25);
      }
        
    }
  }
  
}
```

---

### Post by linuxonbute on 2012-12-22
The code running on the Arduino can be speeded up by altering the values in some of the registers of the atmmega328 to reduce the time taken for the analogread:

```

byte byteValue;
int dtime = 500;
void setup()
{
  bitClear(ADCSRA,ADPS0);
  bitClear(ADCSRA,ADPS1);
  bitSet(ADCSRA,ADPS2);
  Serial.begin(115200);
}

```

also maybe ( I haven't tried this bit yet )
the code in the loop could be altered.
The analogRead value would return 0 - 1023 so dividing it by 4 should reduce it to a value suitable for a byte.
The delay can also be shortened, maybe to microseconds
i.e delayMicroseconds(dtime)

```

void loop()
{
  
  byteValue = analogRead(0)/4;
  Serial.write(byteValue);
 delayMicroseconds(dtime);

}
```

I think the processing code I wrote can be altered so it reads the individual bytes in.

---

### Post by tgalati4 on 2012-12-22
That's definitely cool.  It's amazing what these little controllers can do.  I've resorted to using a digital camera to take pictures of my Tektronix O-Scopes of interesting waveforms, but this opens up a new way to capture data.

---

### Post by Landreas on 2012-12-23
> **linuxonbute said:**
> 
The analogRead value would return 0 - 1023 so dividing it by 4 should reduce it to a value suitable for a byte.
The delay can also be shortened, maybe to microseconds
i.e delayMicroseconds(dtime)

```

void loop()
{ 
  byteValue = analogRead(0)/4;
  Serial.write(byteValue);
 delayMicroseconds(dtime);

}
```

I think the processing code I wrote can be altered so it reads the individual bytes in.

Hey, that worked like a charm! Just got to remap the values to 1020 before dividing and writing them, since 1023 / 4 = 255.75. Having two inputs wasn't any worse than writing and reading twice in a row.

[IMG]http://i.imgur.com/ggU1j.png[/IMG]
The resolution is about 0.02 volts, more than enough for me.

For scaling the x axis, updating dtime from processing might work?

---

### Post by Landreas on 2012-12-23
> **tgalati4 said:**
> That's definitely cool.  It's amazing what these little controllers can do.  I've resorted to using a digital camera to take pictures of my Tektronix O-Scopes of interesting waveforms, but this opens up a new way to capture data.The Arduino platform definitely opens up new doors, especially with processing. Processing even lets you export your project as a standalone executable file :)

Some examples, if you haven't already taken a look: [http://processing.org/learning/](http://processing.org/learning/)

---

### Post by linuxonbute on 2012-12-23
I have a 2 pole 6 way rotary switch which could be used with the arduino to switch the input range. I am thinking that an analog input on the arduino could be used to read it's position and whenever it changed it could signal the processing program to signal the change. 
The problem is how to distinguish between a normal reading and that signal unless normal readings were restricted to for example 0 to 249 and values above that were to show the range. 
I have a piece of code which allows up to 10 switches to be wired up to be read by just 1 analog pin. This could be used to sense the position of 1 pole and the other pole could be to select a point on the input resistor chain which would scale the input voltage to the arduino pin used for voltage measurement.

It would need to be altered to send the figures we would want but that's trivial and the wiring in the image below would be a little different but again that's trivial.

[IMG]http://nelliott.co.uk/linux/resistor-ladder.png[/IMG]

```

void setup()
/* This outputs to the serial monitor for demo purposes */
{
Serial.begin(9600); // activate the serial output connection

}
int divider=100; //for 10 buttons
//int divider=125; //for 8 buttons
//int divider=200; //for 5 buttons
//int divider=250; //for 4 buttons
//int divider=333; //for 3 buttons
// setup some variables

float sensor = 0;
int button=0;

void loop()

{

sensor = analogRead(0);// change 0 to 1, 2, 3, etc
//depending on which analogue pin you wish to use.

button=int(sensor/divider);
Serial.print("Button: ");
Serial.print(button);
Serial.println(" pressed");
Serial.println("_ _ _ _ _ _ _ _ _ _ _ _ _ _ ");
delay (2000); // wait 2 seconds, otherwise the serial monitor box will
be too difficult to read

}

```

---

### Post by Landreas on 2012-12-23
I like your idea with the resistor chain, and reserving the top 6 values would definitely work. Being a bit of a novice, I don't have a clear image of your wiring setup, though. But I bet you'll make it work ;)

---

### Post by linuxonbute on 2013-01-04
I have been looking at this again and thought about doing the bit about speeding up the ADC but then writing the value to 8 digital pins as a direct access to a port instead of using the Serial.write. 

To get the results into the computer I am thinking of buying a USB <-> parallel lead. I remember about 25 years ago a way of using the parallel port to control external kit. I think this might be a way of getting more throughput. 

I have also been on the adruino.cc forum asking for advice about using an ADC with a Raspberry Pi  which has tons of GPIO pins to make a decent oscilloscope and they gave me this link: [http://www.instructables.com/id/Girino-Fast-Arduino-Oscilloscope/#step1](http://www.instructables.com/id/Girino-Fast-Arduino-Oscilloscope/#step1)  which really shows what can be done with the ATMega328p chip in the arduino as well. A great source of information.

---

### Post by linuxonbute on 2013-01-12
Another way to make an oscilloscope would be Interfacing via USB with a USB<->Parallel cable
Years ago I remember trying to do stuff with the parallel printer port and I have a USB to parallel cable so I might try that more out of curiosity than anything. So hardware and software needed. I have no idea at present how fast this could be so no idea what frequency it could go up to.
If it will work at a decent frequency it could be a reasonably cheap way of making a scope.
I have a 15" LCD monitor with DVI input so even if I bought a RasPi just to use it for that it wouldn't work out to be costly.
Below are details I have collected so far relating to using the lead and as long as i run my bit of code as root it seems to access the port without any problems.
Using the parallel port as a data access system.
taken from [http://tldp.org/HOWTO/IO-Port-Programming-6.html#ss6.1](http://tldp.org/HOWTO/IO-Port-Programming-6.html#ss6.1)
with some bits added myself.
====================================================================================
OR to turn bit on. AND to turn it off	
Bit	 0	 1	 2	 3	 4	 5	 6	 7
OR	 1	 2	 4	 8	 16	 32	 64	128
AND	254	253	251	247	239	223	191	127

====================================================================================
The port BASE+0 (Data port) controls the data signals of the port (D0 to D7 for bits 0 to 7, respectively; states: 0 = low (0 V), 1 = high (5 V)). A write to this port latches the data on the pins. A read returns the data last written in standard or extended write mode, or the data in the pins from another device in extended read mode.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The port BASE+1 (Status port) is read-only, and returns the state of the following input signals:
Bits 0 and 1 are reserved.
Bit 2 IRQ status (not a pin, I don't know how this works)
Bit 3 ERROR (1=high)
Bit 4 SLCT (1=high)
Bit 5 PE (1=high)
Bit 6 ACK (1=high)
Bit 7 -BUSY (0=high)
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The port BASE+2 (Control port) is write-only (a read returns the data last written), and controls the following status signals:
Bit 0 -STROBE (0=high)
Bit 1 -AUTO_FD_XT (0=high)
Bit 2 INIT (1=high)
Bit 3 -SLCT_IN (0=high)
Bit 4 enables the parallel port IRQ (which occurs on the low-to-high transition of ACK) when set to 1.
Bit 5 controls the extended mode direction (0 = write, 1 = read), and is completely write-only (a read returns nothing useful for this bit).
Bits 6 and 7 are reserved.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Pinout (a 25-pin female D-shell connector on the port) (i=input, o=output):
1io -STROBE, 2io D0, 3io D1, 4io D2, 5io D3, 6io D4, 7io D5, 8io D6,	9io D7, 
10i ACK,	 11i -BUSY,	 12i PE, 13i SLCT, 14o -AUTO_FD_XT,	15i ERROR, 16o INIT, 17o -SLCT_IN, 18-25 Ground
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The IBM specifications say that pins 1, 14, 16, and 17 (the control outputs) have open collector drivers pulled to 5 V through 4.7 kiloohm resistors (sink 20 mA, source 0.55 mA, high-level output 5.0 V minus pullup). 
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The rest of the pins sink 24 mA, source 15 mA, and their high-level output is min. 2.4 V. The low state for both is max. 0.5 V. Non-IBM parallel ports probably deviate from this standard. For more information on this, see [http://www.hut.fi/Misc/Electronics/circ](http://www.hut.fi/Misc/Electronics/circ) ... power.html.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Finally, a warning: Be careful with grounding. I've broken several parallel ports by connecting to them while the computer is turned on. It might be a good thing to use a parallel port not integrated on the motherboard for things like this. (You can usually get a second parallel port for your machine with a cheap standard `multi-I/O' card; just disable the ports that you don't need, and set the parallel port I/O address on the card to a free address. You don't need to care about the parallel port IRQ if you don't use it.)
=====================================================================================
This program shows a way to use it.
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/io.h>
#include <sys/types.h>
#include <fcntl.h>

#define BASEPORT 0x378 /* lp1 */

int main() {
   char c;
   int n, tem;
   
   printf("Hit any key to stop\n");
   
   //set permissions to access port
   if (ioperm(BASEPORT, 3, 1)) {perror("ioperm"); exit(1);}
   
   tem = fcntl(0, F_GETFL, 0);
   fcntl (0, F_SETFL, (tem | O_NDELAY));
   
   //main loop where actual blinking is done
   while (1) {
      //if some key is pressed, break out from loop
      n = read(0, &c, 1);
      if (n > 0) break;
      
      //write 'on' bit on all data pins and wait 1/4 second
      outb(255, BASEPORT);
      usleep(250000);
      
      //write 'off' bit on all data pins and wait 1/4 second
      outb(0, BASEPORT);
      usleep(250000);
   }
   
   fcntl(0, F_SETFL, tem);
   outb(0, BASEPORT);
   
   //take away permissions to access port
   if (ioperm(BASEPORT, 3, 0)) {perror("ioperm"); exit(1);}
   
   exit(0);
}

```

---

