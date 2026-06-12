---
title: "help serial port programming"
date: 2009-12-01
forum: Programming Talk
---

### Post by athrun01 on 2009-12-01
I have code c program communnication with rs232 to CO2 sensor but it use for pic microcontroller. I want to convert code use on ubuntu. How to convert code
this code for pic microncontroller
```
//*** definition of the interface***
#use
rs232(baud=2400,XMIT=PIN_C6,rcv=PIN_C7,STREAM=CO,bits=7,parity=E,errors)
//***prepare request to the status flags***
#byte TXSTA = 0x98                      //from datasheet
#bit TRMT = TXSTA.1
#define wait_for_RS232() while(TRMT == 0)
void main(void) { // main function
boolean d = 1;
boolean e = 1;
char c1;
int i;
while (TRUE) {
    i = 0;
    e = 1;
    d = 1;
    delay_ms(100);
    fprintf(CO,":A00300050001A6\r\n"); //send request
    wait_for_RS232();                                 //wait for all data tob e sent
    if (kbhit(CO))
        {
          //***wait for the start of the strings to be received***
          while (e)
                 {
                  if(fgetc(CO) == ':') e=0;
                 delay_us(2);
                  }
           while (d)                     //running loop until LF
  {
           c1=fgetc(CO);                 //get characters from the interface
           str[i++]=c1;                 //store characters in the string
           if(c1 == 10) d = 0;         // 10 is the ASCII character for LF
         }
         auswerten();                  // Modulation
       }
  }
}
void auswerten()
{
  long co2long, co2r;
  int hilf;
   costring[0]='0';             //simulates hexadecimal number
   costring[1]='x';
   for(hilf=7;hilf<11;hilf++) //saves relevant values for the CO2 value
     {
     costring[hilf-5]=str[hilf];
     }
   costring[6]=0;               //end sign in the string gets set
   co2long = atol(costring); //changes string to long
   co2r=0.0000024169*(co2long*co2long*co2long); // callibration
   co2r=co2r+(0.001064478*(co2long*co2long));
   co2r=co2r+(1.5139504215*(co2long));
   i=0;                        //rest of the variable
   for(hilf=0;hilf<20;hilf++) str[hilf]=0;
}
```

data sheet 
[http://www.mediafire.com/?zjnwu4rogvx](http://www.mediafire.com/?zjnwu4rogvx)

---

### Post by Zugzwang on 2009-12-01
Ok, so first of all choose a suitable programming language. You probably either want to do it in C or some higher level language, like Python. Technically, the correct choice of language heavily depends on what you actually know and into what kind of application you actually want to integrate your code into. Does a terminal application suffice? Or does it have to be GUI. If unknown, start with a plain terminal application.

After choosing the language, start by finding some tutorial on serial communication for the language you have chosen. Probably for Python and/or C, you will find more than one. Then have a look at the code that you have and try to figure out what it means. Search for the equivalent commands in C or Python and translate as well as you can. For example, this "#use rs2322" pragma will probably need to be converted to some "open port" command which you will find in the tutorial.

As it furthermore looks like that the communication with the device is run in plain-text, you might want to search for a linux program with which you can try out the connection first. I'm not sure how such a program is called. Something like this perhaps?: [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-use-serial-port-like-hyper-terminal-in-windos-538080/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-use-serial-port-like-hyper-terminal-in-windos-538080/)

---

### Post by athrun01 on 2009-12-01
Thanks for suggestion. I use c language. but i'm try convert code but it not work.
i don' understand what is **stream **? because code for microcontroller it check stream.
my code use for ubuntu
```

#include <stdio.h>
#include <fcntl.h> #include <termios.h> 
#include <stdlib.h> 
#include <strings.h> 
#include <unistd.h>
#include <error.h>
#define boolean int
#define true 1
#define false 0
char c1;
int i,n;
char str[30];
char stdinstring[30];
void auswerten();

void main(){

FILE *fd;
struct termios options;
int n,r,w;
char buff[255];
boolean d;
d=true;
boolean e;
e=true; 

/* Open Port */
fd = open("/dev/ttyAM1", O_RDWR | O_NOCTTY | O_NDELAY);
if(fd == -1){
printf("ERROR Open Serial Port!");
}else
printf("Port Open");
fcntl(fd, F_SETFL, 0);

/* Serial Configuration */
tcgetattr(fd, &options); // Get Current Config

cfsetispeed(&options, B2400); // Set Baud Rate to 2400
cfsetospeed(&options, B2400);

options.c_cflag &= ~CSIZE; // data 7 bits
options.c_cflag |= CS7;

options.c_cflag |= PARENB; // even parity bits
options.c_cflag &= ~PARODD;

options.c_cflag &= ~CSTOPB; // stop bit 1
options.c_oflag |= OPOST;
options.c_iflag |= (INPCK | ISTRIP);
options.c_cc[VMIN] = 0;
options.c_cc[VTIME] = 10;
/* Save The Configure */
tcsetattr(fd, TCSANOW, &options);

while(1){
  i = 0;
  e = 1;
  d = 1;  
w=write(fd,":A00300050001A6\r\n",16); //send request                            
  
        //***wait for the start of the strings to be received***

        while(e){
                if(fgetc(stdin) == ':') e=0;
                }
         while (d)                     //running loop until LF
  {
           c1=fgetc(stdin);                 //get characters from the interface
           str[i++]=c1;                 //store characters in the string
           if(c1 == 10) d = 0;         // 10 is the ASCII character for LF
         }
         auswerten();                  // Modulation
  }
close(fd);
}

void auswerten()
{
  long co2long, co2r;
  int hilf;
   stdinstring[0]='0';             //simulates hexadecimal number
   stdinstring[1]='x';
   for(hilf=7;hilf<11;hilf++) //saves relevant values for the CO2 value
     {
     stdinstring[hilf-5]=str[hilf];
     }
   stdinstring[6]=0;               //end sign in the string gets set
   co2long = atol(stdinstring); //changes string to long
   co2r=0.0000024169*(co2long*co2long*co2long); // callibration
   co2r=co2r+(0.001064478*(co2long*co2long));
   co2r=co2r+(1.5139504215*(co2long));
   printf(co2r);        // show data;
   i=0;                        //rest of the variable
   for(hilf=0;hilf<20;hilf++) str[hilf]=0;    
}


```please help

---

### Post by Zugzwang on 2009-12-01
> **athrun01 said:**
> i don' understand what is **stream **? because code for microcontroller it check stream.


I don't know. The programmer's manual for your PIC should have a description of what this means.

Oh, and one thing: Please format your source code before posting it here. For example, you can install the tool "astyle" ("sudo apt-get install astyle") and run "astyle <yourcode.c>" in order to get it nicely formatted. This simplifies reading a lot!

---

