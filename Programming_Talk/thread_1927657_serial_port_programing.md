---
title: "serial port programing"
date: 2012-02-18
forum: Programming Talk
---

### Post by conradin on 2012-02-18
Hi all,
I'm trying to do something like this:
[http://www.codeproject.com/Articles/4981/I-O-Ports-Uncensored-1-Controlling-LEDs-Light-Emit](http://www.codeproject.com/Articles/4981/I-O-Ports-Uncensored-1-Controlling-LEDs-Light-Emit)

alas, those are windows resources. Is there any site akin to this for Linux?
I was discussing this subject with an old dude, but hes sick and may die. But he said that termios is to send data, and ioctl is to enable and disable specific ports. Is there a list of all address spaces for all major hardware out there some place? Right now Im interested in enable / disable on specific serial ports, but that may change to PCI slots, or something else too.

---

### Post by drdos2006 on 2012-02-18
that is not a serial port, it is a parallel port, different beast altogether.

regards

---

### Post by alexfish on 2012-02-22
Don't know if on right track with what your after doing

possibly python may be the answer

if serial pyserial should on the system ,  reality, you need to have something which can transmit and receive data , so it is physical device with wires

python-parallel , can be installed , it should be in the repos , the parallel port is a physical device on the motherboard , so you don't need a device to respond at the other end . IE lighting up Leds

[http://pyserial.sourceforge.net/pyparallel.html](http://pyserial.sourceforge.net/pyparallel.html)

also be aware of permissions when using the parallel port

one obvious advantage of python , it easy to build a gui IE: pygtk wxwidgets, python quickly

Good Luck

---

### Post by alegomaster on 2012-02-22
I wonder what you are doing. Are you doing the project with a serial port instead of a parallel port? Also do you know how to program in any language. I remembered that I had to do some serial port programming (in C)last year and I may be able to provide the source code.

---

### Post by lisati on 2012-02-22
> **drdos2006 said:**
> that is not a serial port, it is a parallel port, different beast altogether.

regards
In general that's true, but I have seen a parallel printer port used as if it were a serial port: I once had a scanner worked that way.

---

### Post by conradin on 2012-02-23
> **alegomaster said:**
> I wonder what you are doing. Are you doing the project with a serial port instead of a parallel port? Also do you know how to program in any language. I remembered that I had to do some serial port programming (in C)last year and I may be able to provide the source code.

Im going to be undertaking this in C (im new an newbish to Python).
I'd love some source code! I thing the context of setting pins on and off is the same idea. The port addresses are probably different, but I still think it can be done with IOCTL. 

There are some more hackerish tricks Ive picked up on in the last few days, but I haven't really found a single concrete source that is a tutorial for hardware, and software in Linux

---

### Post by alexfish on 2012-02-23
Have you looked at parapin

[http://parapin.sourceforge.net/](http://parapin.sourceforge.net/)

alexfish

---

### Post by drdos2006 on 2012-02-23
Here is the important part of the code you are trying to reproduce ffrom the web site you mentioned.


#define printer_port 0x378 // Port Address
#define data printer_port+0 // Data Port of the parallel cable
void main (void)
{
  _out(printer_data, 255); // For all lights on
  _out(printer_data, 0); // For all lights off
}

/*/ Some more code ***********/*/
	strcpy(printer_port_str,     "LPT1")	;
	printer_port = fopen(printer_port_str, "w+")	;
	fprintf(printer_port, 255)       	;
/*/ for all lights on /*/

	fprintf(printer_poprt, 0 );
/*/ for all lights off /*/

	fprintf(printer_port, "a"); 
/*/ for something in between all on and all off /*/

/*/ Some more code ***********/*/
/*/------------------------------------------------------------- /*/
void    check_if_finished()
{
	c = bioskey(1)	;

	if (c != 0)
	{
		c = bioskey(0)	;
	if ((c == 'x') || (c == 'X'))
	{
	exit_menu()	;
	printf("Please wait.. Updating data.. \n")	;
	}
	}
}
/*/------------------------------------------------------------- /*/

regards

---

### Post by alegomaster on 2012-02-23
> **conradin said:**
> Im going to be undertaking this in C (im new an newbish to Python).
I'd love some source code! I thing the context of setting pins on and off is the same idea. The port addresses are probably different, but I still think it can be done with IOCTL. 

There are some more hackerish tricks Ive picked up on in the last few days, but I haven't really found a single concrete source that is a tutorial for hardware, and software in Linux

Are you programming in  a Serial Port or parallel port? You need to answer this question for me to help.

---

### Post by escentrix on 2012-02-23
If you're going to be programming in C for serial ports, might I suggest you look at Arduinos as well. Fun to play with, very well documented and full of addons. Just a thought!

---

### Post by alexfish on 2012-02-24
> **drdos2006 said:**
> Here is the important part of the code you are trying to reproduce from the web site you mentioned.


#define printer_port 0x378 // Port Address
#define data printer_port+0 // Data Port of the parallel cable
void main (void)
{
  _out(printer_data, 255); // For all lights on
  _out(printer_data, 0); // For all lights off
}

/*/ Some more code ***********/*/
    strcpy(printer_port_str,     "LPT1")    ;
    printer_port = fopen(printer_port_str, "w+")    ;
    fprintf(printer_port, 255)           ;
/*/ for all lights on /*/

    fprintf(printer_poprt, 0 );
/*/ for all lights off /*/

    fprintf(printer_port, "a"); 
/*/ for something in between all on and all off /*/

/*/ Some more code ***********/*/
/*/------------------------------------------------------------- /*/
void    check_if_finished()
{
    c = bioskey(1)    ;

    if (c != 0)
    {
        c = bioskey(0)    ;
    if ((c == 'x') || (c == 'X'))
    {
    exit_menu()    ;
    printf("Please wait.. Updating data.. \n")    ;
    }
    }
}
/*/------------------------------------------------------------- /*/

regards

that is on surface  , of what parapin does , the problem with Linux well not so much a to Linux
it needs to know who or what needs access to the system , 

imagine been in a dark room with one switch to put the light on , the only way in or out is on other side  of the room, but you don't know that there is a pit across the full width of the room and you don,t know that the switch is on the other side of the pit , parapin bridges the gap and also switches the light on.

can have a look at the read me ;

part of the read me. 
> Parapin has two ``personalities'': it can either be used as a
   user-space C library, or linked as part of a Linux kernel module. The
   user and kernel personalities were both written with efficiency in
   mind, so that Parapin can be used in time-sensitive applications.
   Using Parapin should be very nearly as fast as writing directly to the
   parallel port registers manually.
   
   The kernel module personality of parapin is not directly accesible
   by programs running in userspace.  However, a device driver called
   "parapindriver" is also included that allows userspace programs to
   control the parallel port through standard device system calls such as
   open(), close(), and ioctl().  

---

