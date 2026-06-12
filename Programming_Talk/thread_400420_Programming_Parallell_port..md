---
title: "Programming Parallell port."
date: 2007-04-03
forum: Programming Talk
---

### Post by ghandi69_ on 2007-04-03
Does anyone have any experience programming the parallel port in linux or ubuntu??  I've been looking on google and have found a few guides, although nothing linux specific or even better ubuntu specific.

I would like to be able to use the parallel port in a c++ program that monitors the voltage on certain pins, and then takes certain actions and writes to database files, all of which I could manage.. except for messing with the ports.

Also.. how precise is the parallel port, like if I wanted to measure time within a few millaseconds, is that possible??

Thanks for your help.

---

### Post by UK-sHaDoW on 2007-04-03
I don't think you measure voltage on a parallel port. Since it only works in digital(I think) either 0 or 1. You would probably need some Analog to digital chip or ADC for short

Persnally i would use python since there is probably a nice easy to use module to allow parallel port programming. Last time i tried USB programming in c, I had to write a driver. I don't know about parallel  ports though.

---

### Post by dwblas on 2007-04-03
I don't know if this is true for parallel ports, but generally anything over 3.5 volts is a "one" and anything less is a "zero".  As for the timing, you can get as precise as you want, but it depends on the programming language tools.  In Python for example, there is the datetime module which can calculate in microseconds.  I never synced it to an atomic clock though, so I don't know how accurate microsecond timing is.

---

### Post by UK-sHaDoW on 2007-04-03
Since this interests me i just tried pyparallel(parallel port module) and it keeps comming up with errors on mine. So you might acutally be better of with parapin and c.

---

### Post by wdk on 2007-04-03
You can easily access the ports in Linux (in c) using the <sys/io.h> library (<asm/io.h> on some older systems--libc5 I believe).

Basically, all you have to do is tell the system you would like to access the port using the ioperm or iopl command (depending on the address of your parallel port) and then read and write to it using the inb and outb family of commands.

My personal suggestion would be to connect 8 LED's and resistors as explained ["here"]("http://www.epanorama.net/circuits/parallel_output.html") (just watch your load, so you don't burn out the port) and write a small app to turn them on and off. From there, reading from and writing to any other sort of device through the port should be trivial.

The hex address of your parallel port(s) can be easily found using "cat /proc/ioports". Typically the address of the parport on the mainboard is 0x378, but you may want to consider using a PCI parallel card, just in case...

You can only use ioperm to access the first 0x3ff ports (see the man page), so to access anything above that (like a PCI parallel card) you will have to use iopl, which will give you access to all the ports and require you to run your program as root.

The inb and outb commands are actually part of a fairly large family of commands that should allow you to do pretty much anything with the parport. Again, see the man pages for more info.

If you connect some LED's to the parallel port, you can use the following code to flash them (randomly):

```

#include <stdio.h>
#include <stdlib.h>
#include <sys/io.h>

#define PORT 0x378 /* use your port address here */

int main(int argc, char *argv[])
{
	int r;
	double l;
	
	if (iopl(3)) /* you could also use ioperm(PORT, 1, 1) */
	{
		fprintf(stderr, "couldn't get ports,\ntry running as root\n");
		exit(1);
	}
	
	srand(time(NULL));
	while(1) /*use Ctrl+C to exit */
	{
		l = (double)rand()/(double)RAND_MAX*256;
		r = (int)l;
		outb(r, PORT);
		usleep(500000);
	}
	
	return 0;
}

```

I have used similar code for controlling stepper motors--you should be able to control pretty much anything that will take a digital signal. Reading digital signals is pretty much the same (just use inb), although I haven't done too much with it yet.

The site I mentioned above is a great resource for some of the more technical aspects of dealing with the parport (signal voltages, amps, etc.) and goes into detail about parport programming on several platforms (including web control with php). The author also gives specific details for linux, which you may find helpful. Here it is again: [http://www.epanorama.net/circuits/parallel_output.html]("http://www.epanorama.net/circuits/parallel_output.html")

Happy Hacking!

Also, some sources indicate that programs containing inb and outb need to be compiled with optimization turned on (gcc -O). I have not found this to be necessary on my system (Ubuntu Edgy, gcc 4.1.2), but it's something you may want to try if the program behaves strangely.

---

### Post by ghandi69_ on 2007-04-04
Thanks guys.. this is actual going to be for work I'm hoping.  Basically.. my company designs automatic transfer switches, that are designed to switch from a utility power source to a back up power source in case of failure.  He have some beta units we are trying to test.  To comply to regulations.. they have to mike the transition in under 100 millaseconds.  As is, we have the equpment(mainly.. PLC controllers).. to measure and display the time.. but we have no way of storing the information if we are not there to actually watch it.  The dangerous part.. is we will be dealing with rather large voltages, but I basically just need to measure the time it takes from one pin on the port to "have voltage" to when it "doesn't have voltage".. or basically.. a 1 to a zero.  We plan on running these units through several thousand cycles.. my plan.. is to measure the amount of time on each transfer.. and then store that time in a text file... I believe you guys have gotten me off to a great start.. and I would welcome any more ideas you might have.. (if it turns out great.. I 'll be sure to give the forum credit to my boss as well ; )

---

### Post by dwblas on 2007-04-04
This is a link to something similiar with the serial port.  One thing to note is that you have to have a software flip-flop/toggle.  Otherwise the computer will read one signal many times.
[http://python-forum.org/py/viewtopic.php?p=12843&highlight=serial#12843](http://python-forum.org/py/viewtopic.php?p=12843&highlight=serial#12843)

---

### Post by supirman on 2007-04-04
> **ghandi69_ said:**
> The dangerous part.. is we will be dealing with rather large voltages

Just making sure... you do realize that you can't feed more than 5 volts into a parallel port, right?

---

### Post by wdk on 2007-04-04
You'll probably want to design a test oscillator circuit with a reliable, known period and use that to test the limits of your program/hardware. I threw one together with a period of about .14 s and by reading the port every 100 microseconds, I get 18-19 readings for each state (on and off), which seems like it should give you plenty of room for your millisecond measurements. 

I guess the key to your problem would be getting the timing right. If you know the transition will not take place in a shorter time than some lower limit (say 50 ms), you could scan the port every 10 ms (for example) and output the time if the reading has changed from the last scan. I don't think hardware timing should be an issue for the limits you gave (I could be wrong), but you still may want to use a dedicated machine for doing the measurements.

Also, you will need to add 1 to your parport address to read from the status port (read only), and remember that certain pins are hardware inverted.

Try this code with an oscillating circuit: it will output the value on the status port approximately every 100 microseconds (redirect the output to a file if you want to actually study the values it outputs, instead of watching them fly by :) )

```

#include <stdlib.h>
#include <stdio.h>
#include <sys/io.h>

#define PORT 0x378 /* use your port here */

int main(void)
{
	int inputs, i;

	i = 0;

	if(iopl(3)) /* for ports higher than 0x3ff */
	{
		printf("use root\n");
		exit(1);
	}

	while(1) /* Ctrl+C to exit */
	{
		inputs = inb(PORT+1); /* +1 accesses the status register */
		printf("%i: inputs = %i\n", (i++)*100, inputs); /* output approximate microseconds passed and port value */
		usleep(100);
	}

	return 0;
}

```

Good luck and happy hacking!

---

### Post by wdk on 2007-04-04
> **supirman said:**
> Just making sure... you do realize that you can't feed more than 5 volts into a parallel port, right?

Definitely don't forget that, unless you're looking for an excuse to buy lots of new computer equipment :mrgreen:

---

### Post by ghandi69_ on 2007-04-04
> **wdk said:**
> Definitely don't forget that, unless you're looking for an excuse to buy lots of new computer equipment :mrgreen:

Right Right guys.. I was planning on grabbing a transformer or using some relays to pass something else before getting to the parallel port.

I have been doing a little more reading... and I have gotten some very good information from you guys.. but apparently you can also program some things for a USB port??  Since not all computers have a parallel port, I think knowledge of the USB might be even more useful if possible.. what do you guys think?

---

### Post by dwblas on 2007-04-04
There are existing apps like pyserial and pyparallel you can use to access the ports.  I don't know if there is anything similar for usb.  If not, you should ask yourself if you want to develop and debug a new usb-port-read app, or use an existing/tested serial or parallel port app.

---

### Post by wdk on 2007-04-04
> **dwblas said:**
> ...you should ask yourself if you want to develop and debug a new usb-port-read app, or use an existing/tested serial or parallel port app.

dwblas made a really good point. I think the usb idea is great, especially for future compatibility and possibly increased functionality. However, most of the usb code I've seen is rather complex and focuses on communication with the device (on the device end, the circuitry is generally also much more complex, for the same reason), but if all you need to do is essentially count the bits coming in, you may be able to simplify the code (and the circuitry) quite a bit.

My personal recommendation would be to create a working, usable prototype on the parallel port, which will allow you to work out any interfacing problems (and other bugs), while keeping the programming relatively simple. That way, your company gets something they can actually use (in a relatively short amount of time), and you get more time to research and implement a usb interface. If you program the prototype right, you should be able to make the usb interface a drop-in replacement for the parport, with minimal changes to the code.

Good Luck!

---

### Post by fakie_flip on 2007-05-10
I see that your program uses usleep, but I don't have usleep in Ubuntu. Can someone help me to compile it or get it some how? Here is what I have tried.

chris@ubuntu:~/Desktop$ apt-cache search usleep
chris@ubuntu:~/Desktop$ gcc usleep.c -o usleep
usleep.c: In function &#8216;usleep&#8217;:
usleep.c:11: error: &#8216;NULL&#8217; undeclared (first use in this function)
usleep.c:11: error: (Each undeclared identifier is reported only once
usleep.c:11: error: for each function it appears in.)
chris@ubuntu:~/Desktop$ cat usleep.c 

#include <sys/types.h>
#include <sys/time.h>


void usleep(x) {
        struct timeval  time;

        time.tv_sec= x/1000000;
        time.tv_usec=x%1000000;
        select(0, NULL, NULL, NULL, &time);
        }

chris@ubuntu:~/Desktop$

---

### Post by amo-ej1 on 2007-05-10
but you do have usleep in ubuntu, see man 3 usleep

```

USLEEP(3)                  Linux Programmer’s Manual                 USLEEP(3)

NAME
       usleep - suspend execution for microsecond intervals

SYNOPSIS
       /* BSD version */
       #include <unistd.h>



```

---

### Post by fakie_flip on 2007-05-11
No, I don't. I'll prove it to you.

chris@ubuntu:~$ man 3 usleep
No manual entry for usleep in section 3
chris@ubuntu:~$

---

### Post by fakie_flip on 2007-05-11
That computer that does not have usleep is running Feisty Fawn. I ssh into another computer running Dapper D, and I got the same message. It does not have usleep either.

---

### Post by supirman on 2007-05-11
usleep is in libc, so I'm sure you have it.  The man page isn't on my system for some reason, hence you may not think you have the actual usleep function.  

**Edit**:  Check to make sure libc-dev is installed on your system.

You simply need to include the unistd.h header as was mentioned before:
```

#include <unistd.h>   // for usleep
#include <stdio.h>     // for printf

int main(void)
{

    printf("begin\n");

    usleep(2000);

    printf("end\n");

    return 0;
}


```

---

