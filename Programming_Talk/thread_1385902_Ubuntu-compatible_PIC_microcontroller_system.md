---
title: "Ubuntu-compatible PIC microcontroller system"
date: 2010-01-20
forum: Programming Talk
---

### Post by seanlano on 2010-01-20
I am looking into learning how to use some sort of PIC microcontroller, and I know there are a variety of computer interfaces available for programming the PIC from a computer, but I don't know which of them are usable with Linux and Ubuntu. Is there any recommended brands or systems that are known for Linux compatibility? Also, there is often supplied software for assisting with writing programs to put onto the microcontroller, are there any equivalent programs for Ubuntu? 

To clarify, I am looking at something like the Atmel ATTiny series (or ATMega) or Microchip PIC12 series (or PIC16 or PIC18 ). I have no previous experience with any microcontroller, I am complete newbie. So I would appreciate any help anyone can offer with what pieces I need, and in particular what I should get so I can do everything from Ubuntu. Any relevant links would be greatly appreciated.

---

### Post by Queue29 on 2010-01-20
If you're okay with Atmel I'd go with an Arduino if you're on 32 bit Ubuntu. The community is very good for helping new comers and there are projects published regularly in magazines and on hackaday that you can make with them.

---

### Post by seanlano on 2010-01-20
Yeah, thanks. I'd just found an instructable that said something about Arduino, and I wondered "what's that?" so I looked into it a bit more. It looks great! That it pretty much exactly what I was looking for. It'll cost me about $35 for the Arduino Duemilanove, and from the looks of things that's all I need to connect to a computer and program the microcontroller and then run it and connect it to various peripherals. Fantastic!

---

### Post by OgreProgrammer on 2010-01-20
My arduino worked with 64 bit ubuntu with a bit of trickery regarding java. 

Next time I set up i will probably virtual box a 32bit environment for it.

---

### Post by kaivalagi on 2010-03-18
I know this thread has been silent for a while but I wondered if any of you guys use PIC microcontrollers at all? Do you have a preferred way to develop and code them. I am currently using MikroC in a Windows VM until I find a good Linux solution. I have had a quick look at SDCC for C based PIC development but the info available isn't great.

I would prefer to use a language such as C to develop for the PIC, I'd rather not have to get my head into assembly too much. I develop in C/C#/VB/Python for my profession so you can understand my eagerness to not use assembly unless absolutely necessary.

Cheers

---

### Post by cubeist on 2010-03-18
> **kaivalagi said:**
> I know this thread has been silent for a while but I wondered if any of you guys use PIC microcontrollers at all? Do you have a preferred way to develop and code them. I am currently using MikroC in a Windows VM until I find a good Linux solution. I have had a quick look at SDCC for C based PIC development but the info available isn't great.

I would prefer to use a language such as C to develop for the PIC, I'd rather not have to get my head into assembly too much. I develop in C/C#/VB/Python for my profession so you can understand my eagerness to not use assembly unless absolutely necessary.

Cheers

As mentioned, Arduino is the way to go.  The possibilities are nearly endless, the open-source support is good, and the community is growing faster than anything else out there.  Arduino code can be written in C, C++, and a few other languages. MikroC is expensive, and there is virtually no linux/unix support or users (that I know of).

---

### Post by kaivalagi on 2010-03-18
> **cubeist said:**
> As mentioned, Arduino is the way to go.  The possibilities are nearly endless, the open-source support is good, and the community is growing faster than anything else out there.  Arduino code can be written in C, C++, and a few other languages. MikroC is expensive, and there is virtually no linux/unix support or users (that I know of).

Too bad I already have a PICKIT2 programmer and several chips less than a week old...how much would it cost to get setup with Arduino development proper i.e. programmer/demo board/tools/chips? And what are the development tools in Linux like? Any favourites I could check out?

Could I use Eclipse with some sort of custom chip programmer plug-in? That would be something!

Edit: I see what you mean about support etc: [http://www.arduino.cc/playground/Code/Eclipse](http://www.arduino.cc/playground/Code/Eclipse)

Edit2: Only thing putting me off is the cost of the Arduino chips and the size of them too. Now I can appreciate these chips may be packed with features and be nice and easy to develop against but some tasks really only require a 6/8 pin chip. I'm thinking of simple LED lighting/motor control etc where only couple of pins need to output.

I was planning to use an 8 pin chip (PICF10206 for example) for the project I am working on, it will be used for fading and varying LED lighting for day and night in an aquarium.  Worst case I'd need to use a 14 pin (PIC16F505 for example)...I haven't got to the point of knowing just yet but I have both chips. If the project is a success I may end up selling pre-programmed DIY kits or build ones so cost and size is important.

I really was hoping someone would be able to highlight a fairly straight forward approach to developing using SDCC???

---

### Post by cubeist on 2010-03-18
you want small! [http://www.arduino.cc/en/Main/ArduinoBoardMini](http://www.arduino.cc/en/Main/ArduinoBoardMini)

I haven't used that one myself, but it packs 14 pins and it's tiny. It's known as the postage stamp arduino.

Cost, yes a bit higher, but each board has more potential.  For now, your best option is probably to stick with windows to program the stuff you have.  Or, hopefully someone else will post with some info on a linux environment to work with what you have... I just don't know of anything.

For me, once I saw the video of the six rotor, self balancing, auto-flying gps helicopter, I knew I would never use anything other than arduino for my diy projects again!

---

### Post by roccivic on 2010-03-18
I got a PicKit2 a few years ago. And since I could not be bothered to figure out "pk2cmd" (unix command line interface to pickit2) I just went ahead and virtualized Windogs using vmware server.

Here's what it looks like on my machine: [http://www.placella.com/foto/Screenshot.png](http://www.placella.com/foto/Screenshot.png)

By the way, me and other geeks are around at [http://www.dutchforce.com/](http://www.dutchforce.com/), which is probably one of the best electronics forums. ;)

Peace, Rouslan

---

### Post by kaivalagi on 2010-03-18
> **cubeist said:**
> you want small! [http://www.arduino.cc/en/Main/ArduinoBoardMini](http://www.arduino.cc/en/Main/ArduinoBoardMini)

I haven't used that one myself, but it packs 14 pins and it's tiny. It's known as the postage stamp arduino.

Cost, yes a bit higher, but each board has more potential.  For now, your best option is probably to stick with windows to program the stuff you have.  Or, hopefully someone else will post with some info on a linux environment to work with what you have... I just don't know of anything.

For me, once I saw the video of the six rotor, self balancing, auto-flying gps helicopter, I knew I would never use anything other than arduino for my diy projects again!

Right now I don't need the features as the chip I will program will go into a sealed unit and stay there, I won't reuse it. That being said next bigger project I undertake I might switch to an Arduino if I can find a good/cheap programmer...it really depends on my PIC programming experience though

> **roccivic said:**
> I got a PicKit2 a few years ago. And since I could not be bothered to figure out "pk2cmd" (unix command line interface to pickit2) I just went ahead and virtualized Windogs using vmware server.

Here's what it looks like on my machine: [http://www.placella.com/foto/Screenshot.png](http://www.placella.com/foto/Screenshot.png)

By the way, me and other geeks are around at [http://www.dutchforce.com/](http://www.dutchforce.com/), which is probably one of the best electronics forums. ;)

Peace, Rouslan

Cool, I'll check the site out.

Yeah, VirtualBox'ed Windows is working for me so far, USB programmer works fine and I must admit I like MikroC a lot so far. Maybe I can get it running in Wine...

The key thing here is that I want to code in C not assembler...once a have a hex file then I could use pk2cmd...but what do I do to get that hex file from C code. SDCC looks like the ONLY half decent solution for that and the online resources are not good.

I'll pick some discrete components up tomorrow so I can start testing stuff out properly. I may well try using SDCC this weekend to compile with...or maybe there's an eclipse plugin for SDCC? I'll obviously have to do a little more digging...

Anything I find I'll post back in case it's of any help to others...

Thanks guys

---

### Post by roccivic on 2010-03-19
Correct me if I'm wrong (I code for PICs in ASM), but I was under the impression that GCC was capable of compiling C code for PICs...

---

### Post by kaivalagi on 2010-03-19
> **roccivic said:**
> Correct me if I'm wrong (I code for PICs in ASM), but I was under the impression that GCC was capable of compiling C code for PICs...

SDCC creates a build chain to use with GCC, so yes GCC can compile C for PIC with the extra libraries it will need. SDCC site: [http://sdcc.sourceforge.net/index.php#News](http://sdcc.sourceforge.net/index.php#News)

No nice GUI/debugger and documentation is poor from what I have seen

I would sooner use C via GCC than any non open source solution, but I will fallback to MikroC if I have to (i.e. if SDCC is a royal pai in the butt). I already have the majority of the coding done via MikroC but nothing has been tested with the PIC I/O so I could have screwed that up...

Code so far (still very much a work in progress):
```
const unsigned short WHITE_DUTY_MAX = 128;
const unsigned short BLUE_DUTY_MAX = 64;
const unsigned long SAMPLE_INTERVAL_MS = 10000;
const unsigned long PWM_FREQ = 5000;
const unsigned long WHITE_FADE_DURATION_SECONDS = 30;
const unsigned long BLUE_FADE_DURATION_SECONDS = 2;
                           
unsigned short i;
unsigned short white_duty;
unsigned short blue_duty;
unsigned short RA0_current;
unsigned short RA0_high_count;

unsigned get_delay_ms(unsigned long seconds, unsigned short duty_ratio) {
    return (seconds*1000)/(int)duty_ratio;
}

void fadein_white(unsigned long seconds, unsigned short duty_ratio) {
  unsigned long fade_delay_ms;
  fade_delay_ms = get_delay_ms(seconds, duty_ratio);
  for(i=white_duty;i<duty_ratio;i++)
  {
    PWM1_Set_Duty(i);
    white_duty = i;
    if (blue_duty > 0) {
        PWM2_Set_Duty(blue_duty - 1);
        blue_duty = blue_duty - 1;
    }
    Vdelay_ms(fade_delay_ms);
  }

  if (blue_duty > 0) {
    for(i=blue_duty;i>0;i--) {
      PWM2_Set_Duty(i);
      blue_duty = i;
    }
    Vdelay_ms(fade_delay_ms/2);
  }
}

void fadein_blue(unsigned long seconds, unsigned short duty_ratio) {
  unsigned long fade_delay_ms;
  fade_delay_ms = get_delay_ms(seconds, duty_ratio);
  for(i=blue_duty;i<duty_ratio;i++)
  {
    PWM2_Set_Duty(i);
    blue_duty = i;
    if (white_duty > 0) {
        PWM1_Set_Duty(white_duty - 1);
        white_duty = white_duty - 1;
    }
    Vdelay_ms(fade_delay_ms);
  }

  if (white_duty > 0) {
    for(i=white_duty;i>0;i--) {
      PWM1_Set_Duty(i);
      white_duty = i;
    }
    Vdelay_ms(fade_delay_ms/2);
  }
}

void init() {
  ANSEL  = 0;                         // Configure AN pins as digital
  ANSELH = 0;
  C1ON_bit = 0;                       // Disable comparators
  C2ON_bit = 0;

//  PORTA = 255;
  TRISA = 0x80 ;                      // configure PORTA RA0 pin as input i.e. 1000000b
  PWM1_Init(PWM_FREQ);                    // Initialize PWM1 module at 5KHz
  PWM2_Init(PWM_FREQ);                    // Initialize PWM2 module at 5KHz
  
  white_duty = 0;
  blue_duty = 0;
  RA0_current = 0;
  RA0_high_count = 0;
}

void main() {

  init();

  while (1) { // Endless loop

    // if the high count is greater than 6/8 then we go with light, if less than 3/8 then we go with dark
    if (white_duty < WHITE_DUTY_MAX && RA0_high_count > 6) {
      RA0_current = 1;
      fadein_white(WHITE_FADE_DURATION_SECONDS, WHITE_DUTY_MAX);
    } else {
      if (blue_duty < BLUE_DUTY_MAX && RA0_high_count < 3) {
        RA0_current = 0;
        fadein_blue(BLUE_FADE_DURATION_SECONDS, BLUE_DUTY_MAX);
      }
    }
    Delay_ms(SAMPLE_INTERVAL_MS);
    
    // check state of LDR/On/Off input, high = light, low = dark, over 8 samples
    RA0_high_count = 0;
    for(i=0;i<8;i++) {
      if (RA0_bit == 1) {
        RA0_high_count++;
      }
      Delay_ms(SAMPLE_INTERVAL_MS);
    }
    
  }
}

```

---

### Post by Andre-D on 2010-03-28
I followed these instructions in order to make Pickit 2 work smoothly with "pikdev"

[http://tuxtronics.com/node/3#comment-1](http://tuxtronics.com/node/3#comment-1)

however, for some reason, I get the error (described in the comment)
- If anyone here can see why, please help.

Thanks.

---

### Post by cubeist on 2010-03-28
Those instructions are a little wonky. There should be no zero in front of a chmod number!  You need to go through the files you installed and double check the permissions.

I'm not sure if you know what permission numbers mean, so here is a brief primer:

There are three user types on a unix system -- user,group, and other; and each user has three possible permission states -- read, write, and execute.

So when you ls -l some files you will see something like:
drwxrw_r_x
the d is for a directory, and then the three users are represented, in this case user can read, write, and execute, group can read and write, and other can read and execute.

The octal numbers are a shorthand, assigned as:
read=4
write=2
execute=1

so chmod as 644 means user can read(4)and write(2), and group and other can only read.

Hope this helps some!

---

### Post by Andre-D on 2010-03-28
good point, I did;

$ chmod 755 pk2cmd
$ chmod 644 PK2DeviceFile.dat
$ sudo cp pk2cmd /usr/local/bin/
$ sudo cp PK2DeviceFile.dat /usr/share/pk2/

but it did not help ..

---

### Post by cubeist on 2010-03-28
Try downloading the source files and building it yourself, this way you don't have to worry about file permissions.

Just download the source files, unpack, then type "make linux"
you shouldn't get any errors...I tried, works aok for me... then type sudo make install.

---

### Post by Andre-D on 2010-03-28
thanks , do you have any idea why I get this: ?

andre@Loke-2:~/Downloads/pk2cmdv1.20LinuxMacSource$ make linux
make TARGET=linux
make[1]: Entering directory `/home/andre/Downloads/pk2cmdv1.20LinuxMacSource'
g++ -Wall -D_GNU_SOURCE -O2 -I/usr/local/include -DLINUX -DUSE_DETACH -DCLAIM_USB -o cmd_app.o  -c cmd_app.cpp
make[1]: g++: Command not found
make[1]: *** [cmd_app.o] Error 127
make[1]: Leaving directory `/home/andre/Downloads/pk2cmdv1.20LinuxMacSource'
make: *** [linux] Error 2

g++ ?

---

### Post by cubeist on 2010-03-28
```
sudo apt-get install build-essentials
```

you need the basic compiling tools to build software from source...  g++ is just a program that interprets raw code and turns it into usable software.

---

### Post by Andre-D on 2010-03-28
"E: Couldn't find package build-essentials"

cannot believe that's caused by 10.04 - and I did not find similar name in synaptic..

---

### Post by cubeist on 2010-03-28
> **cubeist said:**
> ```
sudo apt-get install build-essentials
```


Sorry, it is:
```
sudo apt-get install build-essential
```

I use tab-completion so I rarely get the names exactly right :-k

---

### Post by Andre-D on 2010-03-29
anyway make and make install went well, but I had the same problem until I deleted the folders/files I made before.

now it works just great. (thanks)

Do you recommend pikdev of piklab or any other tool ?
BTW: I've always programmed assembly only, and never touched higher lever language for PIC, but the current project is so simple, I could try to try some sort of basic or other, simple syntax, do you have any suggestions ?

---

### Post by jlewis05 on 2010-05-10
There's also JAL ([http://jal.sourceforge.net/](http://jal.sourceforge.net/)) though it is aimed at being Pascal-like.  Haven't done any real programming with it, only played with the compiler, but it seems very straightforward.  Don't know what GUIs you might be able to use with it, though.

---

### Post by Andre-D on 2010-05-11
thanks, will try..

---

### Post by jlewis05 on 2010-05-11
Sorry, forgot JALv2 as well ([http://www.casadeyork.com/jalv2/](http://www.casadeyork.com/jalv2/)).

---

