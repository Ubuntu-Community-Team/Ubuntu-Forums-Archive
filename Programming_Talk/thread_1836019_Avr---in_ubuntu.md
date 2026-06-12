---
title: "Avr---in ubuntu"
date: 2011-08-30
forum: Programming Talk
---

### Post by arun_nr on 2011-08-30
im new to Ubuntu and im  using 11.04 version.and im working on avr microcontrollers,and installed avr dude avr gcc and avr lib c in it.can anyone tel how to do compiling and burning from terminal..
with regards 
arun

---

### Post by seawolf167 on 2011-08-30
You can read the gcc man page

```
man gcc
```

compiling a c/c++ program is essentially

```
gcc -o outfile infile
```

if you don't specify the "-o outfile" part, then part default it will be named "a.out" in the working directory

---

### Post by gshendrick on 2011-08-30
Hi arun,
avrdude will write to your chip if you have the right hardware connected to your computer. It's a very versatile tool and you can see what hardware it supports by viewing 
```
man avrdude
```I can probably help you a bit more if you could provide more details regarding your hardware. What programmer do you have ? Which chip do you have ?
Thanks,
Gary

---

### Post by arun_nr on 2011-08-30
yup im using an usbasp programmer for my avr atmega 16 board..

---

### Post by blitzit on 2011-08-30
You could use this *makefile*. It uses 3 commands:
[LIST=1]
[*]avr-gcc : to compile your code
[*]avr-objcopy : to build modules into a .hex
[*]avrdude : the downloader uploader device to burn the .hex into the flash
[/LIST]

Here are the contents of the file:
```
#BUILDS AND COMPILES .C FILE DEFINED AT THE COMMAND LINE TO PRODUCE .OUT AND .HEX FILE; SUBSEQUENTLY LOADS THE .HEX FILE INTO THE FLASH OF THE MICROCONTROLLER
#DEFINED WITHIN THIS MAKEFILE

$(FILE).hex : $(FILE).out
	avr-objcopy -j .data -j .text -O ihex $(FILE).out $(FILE).hex
	avrdude -c usbasp -p m8 -U flash:w:$(FILE).hex -U hfuse:r:hfuse.txt:h -U lfuse:r:lfuse.txt:h

$(FILE).out : $(FILE).c
	avr-gcc -mmcu=atmega8 -Os $(FILE).c -o $(FILE).out
```

Create a file and copy these contents into it. Save it as "makefile".

This file is targeted for an ATmega8. As I see from your reply you seem to be interested in burning your code on an ATmega16. For this you will have to modify "atmega8" in the code lines to "atmega16" for avr-gcc and "m8" to "m16" for avrdude.

To use this file directly, copy it into the directory of your project, and use this command:
```
make <FILENAME>
```
where <FILENAME> must be substituted with the name of your C code file. e.g., if it is nonsense.c, type ```
make nonsense
```

Also note, this makefile is helpful if you have a single .C file to compile. If there are multiple files to be compiled, modify the avr-gcc command. You could do with ```
man avr-gcc
``` in that case.

---

### Post by arun_nr on 2011-08-30
> **seawolf167 said:**
> You can read the gcc man page

```
man gcc
```

compiling a c/c++ program is essentially

```
gcc -o outfile infile
```

if you don't specify the "-o outfile" part, then part default it will be named "a.out" in the working directory
can u tel me how to compile from terminal..should i use avr gcc command from terminal or should i go to the directory i kept d makefile and source code and do make?

---

### Post by arun_nr on 2011-08-30
> **Vijay Rao said:**
> You could use this *makefile*. It uses 3 commands:
[LIST=1]
[*]avr-gcc : to compile your code
[*]avr-objcopy : to build modules into a .hex
[*]avrdude : the downloader uploader device to burn the .hex into the flash
[/LIST]

Here are the contents of the file:
```
#BUILDS AND COMPILES .C FILE DEFINED AT THE COMMAND LINE TO PRODUCE .OUT AND .HEX FILE; SUBSEQUENTLY LOADS THE .HEX FILE INTO THE FLASH OF THE MICROCONTROLLER
#DEFINED WITHIN THIS MAKEFILE

$(FILE).hex : $(FILE).out
	avr-objcopy -j .data -j .text -O ihex $(FILE).out $(FILE).hex
	avrdude -c usbasp -p m8 -U flash:w:$(FILE).hex -U hfuse:r:hfuse.txt:h -U lfuse:r:lfuse.txt:h

$(FILE).out : $(FILE).c
	avr-gcc -mmcu=atmega8 -Os $(FILE).c -o $(FILE).out
```

Create a file and copy these contents into it. Save it as "makefile".

This file is targeted for an ATmega8. As I see from your reply you seem to be interested in burning your code on an ATmega16. For this you will have to modify "atmega8" in the code lines to "atmega16" for avr-gcc and "m8" to "m16" for avrdude.

To use this file directly, copy it into the directory of your project, and use this command:
```
make <FILENAME>
```
where <FILENAME> must be substituted with the name of your C code file. e.g., if it is nonsense.c, type ```
make nonsense
```

Also note, this makefile is helpful if you have a single .C file to compile. If there are multiple files to be compiled, modify the avr-gcc command. You could do with ```
man avr-gcc
``` in that case.
wen i try 2 compile from terminal it shows no target.is it the problem of my usbasp hardware?

---

### Post by blitzit on 2011-08-30
Please post the actual output here; i.e. the output as you get on the terminal.

The target can imply for the makefile as well as for avrdude which searches for the target board when you call it. From an intuitive guess, I suppose it is avrdude which is generating that error. Try adding sudo to the avrdude command in the makefile like this:
```
sudo avrdude ... 
```
and retry.

---

### Post by arun_nr on 2011-08-30
iam getting dis error anybody knows how to keep  headerfiles in ubuntu.i installed ubuntu inside windows. Compiling C: main.c
avr-gcc -c -mmcu=atmega16 -I. -gstabs -DF_CPU=16000000UL -Os -funsigned-char -funsigned-bitfields -fpack-struct -fshort-enums -Wall -Wstrict-prototypes -Wa,-adhlns=./main.lst  -std=gnu99 -Wundef -MMD -MP -MF .dep/main.o.d main.c -o main.o 
main.c:2:18: error: delay.h: No such file or directory
main.c: In function ‘main’:
main.c:12: warning: implicit declaration of function ‘delayms’
make: *** [main.o] Error 1
:guitar:

---

### Post by blitzit on 2011-08-30
The library header file you are looking for is <util/delay.h> not <delay.h>. Refer the library documentation for avr-gcc.

Also, please do not flood the forums with multiple threads for the same queries. Infact, it would be better if multiple queries could be integrated into a single thread. It only adds to the redundancy in the site : [http://ubuntuforums.org/showthread.php?t=1836083&highlight=avr](http://ubuntuforums.org/showthread.php?t=1836083&highlight=avr), [http://ubuntuforums.org/showthread.php?t=1836082&highlight=avr](http://ubuntuforums.org/showthread.php?t=1836082&highlight=avr)

Also the function you are looking for is _delay_ms();

---

### Post by gshendrick on 2011-08-30
It looks like there is an issue with your includes. I'm guessing that the compiler doesn't see delay.h or the prototypes declared within and that it balks at that issue, then balks again at the later reference to delayms because it failed the first time.

---

### Post by gshendrick on 2011-08-30
Vijay is 100% right on this, but I just want to expand on his message regarding delay.h by pointing you toward the library reference. [Click Here]("http://www.nongnu.org/avr-libc/user-manual/group__util__delay.html") to view the avr-libc reference for util/delay.h

---

### Post by arun_nr on 2011-08-30
hei thnk u guys dis was my code actually..
#include<avr/io.h> 
#include"delay.h" 
 
int main(void) 
{ 
  while(1) 
      
        { 
        PORTD=0x00; 
        delayms(300); 
               PORTD=0X01; 
        } 
         
         
 }

---

### Post by uRock on 2011-08-30
Triplicate threads merged. Please only create one thread for a topic.

---

### Post by arun_nr on 2011-08-30
thnk u..
but i hav a doubt
if u install ubuntu inside windows where would d headerfiles lie?
in windows i used cmd to program avr..and i hav 2 go to the folder having source code using "cd".is it same for ubuntu 11.04 also

---

### Post by blitzit on 2011-08-31
```
#include<avr/io.h> 
#include<util/delay.h> 

int main(void) 
{ 
    DDRD = 0x01;
    while(1) 
    { 
        PORTD = 0x00;
        _delay_ms(300);
        PORTD = 0x01;
        _delay_ms(300);
    }

    return 0;
}
```

Please observe the added / modified lines. They are important modifications without which your code would not have worked as desired.

---

### Post by blitzit on 2011-08-31
> **arun_nr said:**
> thnk u..
but i hav a doubt
if u install ubuntu inside windows where would d headerfiles lie?
in windows i used cmd to program avr..and i hav 2 go to the folder having source code using "cd".is it same for ubuntu 11.04 also

If you install ubuntu inside windows, ubuntu creates a folder for itself inside anyone of the FAT/NTFS drives that you assign to it. After that there is no difference in what you would experience in the way an ubuntu inside windows would function to that of a normal ubuntu installation, except for a few booting methods which is inconsequential for you. All in all, the libraries are in proper places and you shouldn't have to worry about them as long as you are using #include<library_filename> instead of #include"library_filename".

---

### Post by arun_nr on 2011-09-03
actually i get an error like this on terminal . avrgcc no input files ....i hav installed all avr things in ubuntu 11.04.still cant sort out the thing?

---

### Post by blitzit on 2011-09-03
arun: Please understand that without detailed information on the input and/or output we can't keep guessing what might have gone wrong. Please put up the command you gave as input and the output you got exactly as you got it at the terminal.

---

### Post by arun_nr on 2011-09-03
vijay.the problem is dat,i used the makefile given by u. and was able to do compilation for it but usbasp is not working,or it doesnt detect my programmer .i checkd wid my friend's lap who uses 10.04 and it worked in his.when we give lsusb it shows different things for both systems.

---

### Post by blitzit on 2011-09-04
Once again, from an intuitive understanding of what might be happening (please copy-paste the output as you get on the screen and put it inside ```
 
``` tags), I think it is a USB Port access permission, which is not granted by default.

As a solution, try sudo-ing the avrdude command. That is, your makefile should now look something like this:

> #BUILDS AND COMPILES .C FILE DEFINED AT THE COMMAND LINE TO PRODUCE .OUT AND .HEX FILE; SUBSEQUENTLY LOADS THE .HEX FILE INTO THE FLASH OF THE MICROCONTROLLER
#DEFINED WITHIN THIS MAKEFILE

$(FILE).hex : $(FILE).out
	avr-objcopy -j .data -j .text -O ihex $(FILE).out $(FILE).hex
	sudo avrdude -c usbasp -p m8 -U flash:w:$(FILE).hex -U hfuse:r:hfuse.txt:h -U lfuse:r:lfuse.txt:h

$(FILE).out : $(FILE).c
	avr-gcc -mmcu=atmega8 -Os $(FILE).c -o $(FILE).out

You will be asked for your password if and when avrdude is called.

If the password is not asked, that means there is an error either in avr-gcc / avr-objcopy. On the other hand, if the password prompt does come up, avr-gcc and avr-objcopy seem to be doing fine. We'll then have to check responses for you avrdude separately.

Also, please note that this makefile is very basic and does not update the Modified Time of the .c file. So you will need to Save the .c file everytime you run the make file, if eveything works.

---

### Post by arun_nr on 2011-09-04
"avrdude:error:could not find "usbasp"with vid=0x16c0 pid=0x5dc"dis is d error i get.

---

### Post by blitzit on 2011-09-04
Does that error still come on sudo-ing avrdude?

---

### Post by arun_nr on 2011-09-05
yes vijay i am unable to detect usbasp in linux.and hav d error i mentioned before.

---

### Post by arun_nr on 2011-09-05
but my frnd who uses 10.04 detects it successfully.

---

### Post by blitzit on 2011-09-07
Plug in the USBasp programmer into a USB port on your computer. Do you get the same result as the one shown below?

```
vijay@307-21:~$ lsusb | grep USBasp
Bus 004 Device 003: ID 16c0:05dc VOTI USBasp AVR Programmer

```

In my computer, when I do not sudo avrdude the programmer seems to be absent (as is the case with you), as shown below.
```
vijay@307-21:~$ avrdude -c usbasp -p m8
avrdude: Warning: cannot query manufacturer for device: error sending control message: Operation not permitted
avrdude: error: could not find USB device "USBasp" with vid=0x16c0 pid=0x5dc

```

However, on sudoing avrdude I can get through to the programmer, as shown below (I haven't connected a target board, so that is the error coming up). This should work for you as well if your answer for my question was a 'yes'.
```
vijay@307-21:~$ sudo avrdude -c usbasp -p m8

avrdude: error: programm enable: target doesn't answer. 1 
avrdude: initialization failed, rc=-1
         Double check connections and try again, or use -F to override
         this check.


avrdude done.  Thank you.

vijay@307-21:~$ 
```

---

### Post by arun_nr on 2011-09-07
wen i do lsusb:the output is
arun@ubuntu:~$ lsusb
Bus 002 Device 008: ID 054c:04be Sony Corp. 
Bus 002 Device 007: ID 16c0:05dc VOTI shared ID for use with libusb 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 0c45:6409 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by arun_nr on 2011-09-07
thank u vijay u solved d puzzle cheers 2 u :).thanks a lot d same output gets for me wen i do " sudo".

---

### Post by blitzit on 2011-09-07
Ah! There it is! :)

Bus 002 Device 007: ID 16c0:05dc VOTI shared ID for use with libusb

Do you have libusb installed? If not do this:
```
sudo apt-get install libusb-1.0-0
```

---

### Post by arun_nr on 2011-09-07
yup its  already installed der.libusb

---

### Post by blitzit on 2011-09-07
Right and now that it's working for you, please mark this thread [SOLVED].

If you want, you could look up a little more and remove the need to keep sudo-ing avrdude everytime. It is a permissions issue. However, it is just for your security so that you know when USB data is going in and coming out.

Cheers :)

---

### Post by arun_nr on 2011-09-07
thnks a lot

---

### Post by arun_nr on 2011-09-07
heiii vijay can u summarize in short wat was d problem::with not detecting usbasp intially ;)

---

### Post by blitzit on 2011-09-07
As far as I can understand, it should have been detecting throughout, just that somehow you felt it wasn't coming up.

Also, I think there is a difference because of the versions in the drivers for the different kernels - USBasp showed up with two different descriptions against the same VID,PID.

Earlier, avrdude would work without having to call it through sudo. Later versions, (my personal experience since 10.04) have started needing a sudo for avrdude; perhaps an added security measure.

---

### Post by arun_nr on 2011-09-07
heii vijay can u decode dis command .i mean the"-c" and "-p m8" part of "sudo avrdude - usbasp -p m8".i mean the purpose or wat is d intention of giving so.:)

---

### Post by blitzit on 2011-09-08
These options are for the programmer (-c) and the part no (-p). You should read about them in the avrdude documentation : [http://www.nongnu.org/avrdude/user-manual/avrdude.html](http://www.nongnu.org/avrdude/user-manual/avrdude.html).

---

### Post by arun_nr on 2011-09-09
hii vijay:
im getting dis error wen i connect to d target.i guess dis is a hardware connection problem.
i did'nt connect d oscillator for atmega 8.but was able 2 do so by parallel port programming.
same error as u got while sudoing w/0 target.
avrdude: error: programm enable: target doesn't answer. 1 
avrdude: initialization failed, rc=-1
         Double check connections and try again, or use -F to override
         this check.


avrdude done.  Thank you.

---

