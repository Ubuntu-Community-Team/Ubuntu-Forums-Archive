---
title: "Connecting PICDEM board through serial to USB cable to my Ubuntu Linux laptop"
date: 2017-12-28
forum: New to Ubuntu
---

### Post by vivitern on 2017-12-28
I have PICDEM board with PIC18F87J11 and PIC18F8722 microcontrollers(datasheet:[http://www.kynix.com/uploadfiles/pdf65976/PIC18F8722-E2fPT_787736.pdf](http://www.kynix.com/uploadfiles/pdf65976/PIC18F8722-E2fPT_787736.pdf)), connecting the board through serial to USB cable to my Ubuntu Linux laptop. The code in the microcontroller is supposed to transmit any character typed on the keyboard back to the console. This works alright with Windows 7 computers and putty. With Ubuntu - there is connection established in screen or putty, but the output is invisible - only the cursor continuously moves upon each keypress (which is the same behavior with Window 7).


Doing hexdump reveals the following:


skolodya@ubuntu:$ sudo hexdump -c /dev/ttyUSB0                                 
[sudo] password for xieerqi: 
0000000  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b
*
0001900  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \b  \n  \n
0001910  \n  \n  \n  \n  \n  \n  \n  \n  \n  \n  \n  \n  \n  \n  \n  \n
cat /dev/ttyUSB0 reveals that characters are there, except show up in the caret notation, ^H , ^E , like that.


The code on the microcontroller itself doesn't reveal any hints of issue. The char array rxBuffer receives its characters from RCREG1 like so rxBuffer[rxCount] = RCREG1 .


Additional Info(as requested):


Currently the code is spitting out "HelloWorld string" (TXREG1 = txStr[txCount]).


Output of hexdump -C  /dev/tty | head -n 10


skolodya@ubuntu:$ hexdump -C /dev/ttyUSB0 | head -n 10                         
00000000  0f 01 17 0f 09 0c 0a 08  15 0c 0c 0f 01 17 0f 09  |................|
00000010  0c 0a 08 15 0c 0c 0f 01  17 0f 09 0c 0a 0f 01 17  |................|
00000020  0f 09 0c 0a 08 15 0c 0c  0f 01 17 0f 09 0c 0a 08  |................|
00000030  15 0c 0c 0f 01 17 0f 09  0c 0a 0f 01 17 0f 09 0c  |................|
00000040  0a 08 15 0c 0c 0f 01 17  0f 09 0c 0a 08 15 0c 0c  |................|
00000050  0f 01 17 0f 09 0c 0a 0f  01 17 0f 09 0c 0a 08 15  |................|
00000060  0c 0c 0f 01 17 0f 09 0c  0a 08 15 0c 0c 0f 01 17  |................|
00000070  0f 09 0c 0a 0f 01 17 0f  09 0c 0a 08 15 0c 0c 0f  |................|
00000080  01 17 0f 09 0c 0a 08 15  0c 0c 0f 01 17 0f 09 0c  |................|
00000090  0a 0f 01 17 0f 09 0c 0a  08 15 0c 0c 0f 01 17 0f  |................|
The output of stty -aF /dev/ttyUSB0


skolodya@ubuntu:$ stty -aF /dev/ttyUSB0                                        
speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^H; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 100; time = 2;
-parenb -parodd cs8 -hupcl -cstopb cread clocal -crtscts
-ignbrk brkint ignpar -parmrk -inpck -istrip -inlcr -igncr -icrnl ixon -ixoff
-iuclc -ixany -imaxbel -iutf8
-opost -olcuc -ocrnl -onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
-isig -icanon iexten -echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke
Update: Trying out different computer with Ubuntu 14.04 32 bit didn't work either , same result


Update 4/20:


I've placed very simple code into the main :


 while (1) {


        while (!PIR1bits.RC1IF);  //Wait for a byte
        sprintf(txStr,"%X",RCREG1);
        LCDWriteLine(txStr,0);
        continue;
It's supposed to show the hex value of RCREG1 on LCD screen. For a letter typed on keyboard windows produces 61 as expected, but on Linux I get E1. Oddly enough, the last 4 bits are correct regardless of what I type. But for top 4 i get values usually from D to F. So for hex value 62 , I get E2.

---

