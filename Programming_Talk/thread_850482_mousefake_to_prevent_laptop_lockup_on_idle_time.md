---
title: "mousefake to prevent laptop lockup on idle time"
date: 2008-07-05
forum: Programming Talk
---

### Post by KingTermite on 2008-07-05
Are you on a laptop like me and your computer hibernates fine when you tell it to, but when it goes to idle time, it locks up and forces a reboot? It's really annoying. I will hibernate it when I know I'm going away for a while, but it bites me when I want to go away for a while and I'm downloading a big file.

I thought I'd try to write a program to fake mouse movement to keep the computer alive. 

Enter "mousefake". It was based on the source [from this web page]("http://www.mail-archive.com/linux-input@vger.kernel.org/msg00063.html") which was in turn based on  [this article]("www.einfochips.com/download/dash_jan_tip.pdf").

I've cleaned it up a little (you can probably see two VERY DIFFERENT programming styles), added a few command line arguments and such. For it to run properly, you must have the uinput loadable module, loaded.
**sudo modprobe uinput**

Just compile the program mousefake.cpp and run it.
Compile: **g++ mousefake.cpp -o mousefake**

Run it with -h option to see arguments and instruction.
**mousefake -h**

mousefake.cpp
```

// mousefake.cpp - Application to send fake mouse events to keep computer from timing out
// author: kingtermite (e.g. Chris Chartier)
// date: 07/05/2008

//
// Mouse Faker application, to send mouse events to kernel in order to keep laptop
// from going idle as it locks up when it goes idle.
//
// This code based from the code found at this web page: 
// http://www.mail-archive.com/linux-input@vger.kernel.org/msg00063.html
// and was written by Nick Turner, Nuvation, inc., San Jose, CA, 408-228-5580 x258.
//
// Per the web page, it was derived from the information found in web article:
// www.einfochips.com/download/dash_jan_tip.pdf
//

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <errno.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <linux/input.h>
#include <linux/uinput.h>
#include <time.h>
#include <unistd.h>


// Mouse event interval is in seconds
#define MAX_MOUSEEVENT_INTERVAL 1800	// 30 min between mouse events
#define MIN_MOUSEEVENT_INTERVAL 30	    // 30 sec between mouse events
#define DEFAULT_MOUSEEVENT_INTERVAL 300	// 5 minutes between mouse events

// Program timeout arguments are in seconds too
#define INFINITE_MOUSEFAKE_TIMEOUT -1	// Program will not time out, user must break out from terminal
#define DEFAULT_MOUSEFAKE_TIMEOUT 7200	// 120 minutes until program terminates


struct uinput_user_dev   uinp;
struct input_event       event;

// Simple printhelp function. Called when the -h option is given to print
// help to the screen.
void printhelp()
{
    printf("\n\nmousefake will move your cursor at a predefined interval until a predefined timeout.\n");
    printf("You can set the interval between each mouse movement and you can set the interval\n");
    printf("until it timesout and exits. This program is a good tool to keep your computer from\n");
    printf("going idle if you have it doing something.\n\n");
    printf("Arguments:\n");
    printf("-t <num> => Sets the timeout (in seconds) until program exits.\n");
    printf("            if <num> is a negative number, program will not time out and must\n");
    printf("            exited by the user with ctrl-c or killing the process.\n\n");
    printf("-i <num> => Set interval between mouse movements (in seconds).\n");
    printf("            <num> must be a value between %d and %d.\n\n", MIN_MOUSEEVENT_INTERVAL,MAX_MOUSEEVENT_INTERVAL);
    printf("\n\nNote: For this program to work correctly, you must load the uinput module.\n");
    printf("With super user privleges, type the command 'modprobe uinput' to load the module.\n");
    printf("The command 'lsmod|grep uinput' can determine if the uinput module is loaded.\n\n\n");
}


// Main
int main(int argc, char *argv[]) 
{

            int ufile, retcode, i;
            int iOpt = 0;
            int iMouseInterval =  DEFAULT_MOUSEEVENT_INTERVAL;
            int iTimeout = DEFAULT_MOUSEFAKE_TIMEOUT;
            int iArg = 0;
            int iStart = 0;
            int iProgramStart = 0;


    // Arguments
    // -t <num> (num = seconds to timeout, negative means INFINITE (no timeout)
    // -i <num> (num = seconds between mouse movements, will not allow < MIN_INTERVAL or > MAX_INTERVAL)
    // -h (print help)
    while ( (iOpt = getopt(argc, argv, "hi:t:")) != -1)
    {

    switch(iOpt)
        {
            case 'i':
                iArg = atoi(optarg);
                //int iIntervalArg = atoi(optarg);
                if ( ( iArg >= MIN_MOUSEEVENT_INTERVAL)||
                     (iArg <= MAX_MOUSEEVENT_INTERVAL) )
                     {
                        // only set if argument is within parameters
                        iMouseInterval = iArg;
                     }
                printf("Interval is set to %d.\n", iMouseInterval);
                break;
            
            case 't':
                //int iTimeoutArg = atoi(optarg);
                iArg = atoi(optarg);
                if (iArg < 0)
                {
                    iTimeout = INFINITE_MOUSEFAKE_TIMEOUT;
                }
                else
                {
                    iTimeout = iArg;
                }
                
                if (iTimeout == 0)
                {
                    // They must have given a malformed argument that processed 
                    // to 0 in atoi.  Reset to the default value.
                    printf("Come again on that timeout value??\n");
                    printf("Setting timeout value to default of %d seconds\n", 
                    DEFAULT_MOUSEFAKE_TIMEOUT);
                    iTimeout = DEFAULT_MOUSEFAKE_TIMEOUT;
                }
                break;
                
            case 'h':
                printhelp();
                return 0; // exit program after printing help
                break;
                
            case ':':
                printf("Option did not have an associated value\n");
                break;
                
            case '?':
                printf("Unknown option: %c\n", optopt);
                break;
                        
        } // end switch
    } // end while


    // Time the program starts. Used to compare with for program timeout.
    iProgramStart = time(NULL);

    // Startup message
    printf("mousefake starting\n");
    printf("Interval between mouse movements = %d seconds.\n", iMouseInterval);
    printf("Program timeout = %d seconds.\n", iTimeout);

    // open uinput
    ufile = open("/dev/input/uinput", O_WRONLY | O_NDELAY );
    if (ufile == 0) 
        {
            printf("Could not open uinput.\n");
            return -1;
    	}

    memset(&uinp, 0, sizeof(uinp)); // Intialize the uInput device to NULL
    strncpy(uinp.name, "simulated mouse", 20);
    uinp.id.version = 4;
    uinp.id.bustype = BUS_USB;

    // Setup the uinput device
    ioctl(ufile, UI_SET_EVBIT, EV_KEY);
    ioctl(ufile, UI_SET_EVBIT, EV_REL);
    ioctl(ufile, UI_SET_RELBIT, REL_X);
    ioctl(ufile, UI_SET_RELBIT, REL_Y);

    for (i=0; i<256; i++) 
        {
            ioctl(ufile, UI_SET_KEYBIT, i);
    	}

    // Controlling mouse
    ioctl(ufile, UI_SET_KEYBIT, BTN_MOUSE);

    // create input device in input subsystem
    retcode = write(ufile, &uinp, sizeof(uinp));

    retcode = (ioctl(ufile, UI_DEV_CREATE));
    if (retcode) 
        {
            printf("Unable to create UINPUT device. Error=%d.\n", retcode);
            return -1;
    	}

           
    // Send mouse events !!!!
    int increment = 10;
	
            while (1) 
		        {
                    // Set start time for timer
                    iStart = time(NULL);
                    
		            increment *= -1; // Toggle between increment and -increment

                    // move pointer left by <increment> pixels
                    memset(&event, 0, sizeof(event));
                    gettimeofday(&event.time, NULL);
                    event.type = EV_REL;
                    event.code = REL_X;
                    event.value = increment;
                    write(ufile, &event, sizeof(event));
        
                    // move pointer up by <increment> pixels
                    memset(&event, 0, sizeof(event));
                    gettimeofday(&event.time, NULL);
                    event.type = EV_REL;
                    event.code = REL_Y;
                    event.value = increment;
                    write(ufile, &event, sizeof(event));
        
                    // accept/sync mouse movements
                    memset(&event, 0, sizeof(event));
                    gettimeofday(&event.time, NULL);
                    event.type = EV_SYN;
                    event.code = SYN_REPORT;
                    event.value = 0;
                    write(ufile, &event, sizeof(event));
    
                    do // Stay busy until next interval
                    {
                        // if timeout is infinite, don't check timeout
                        if (INFINITE_MOUSEFAKE_TIMEOUT != iTimeout)
                        {
                            // If we do have a finite timeout, check it while
                            // we're waiting for the next interval
                            if ((time(NULL) - iProgramStart) >  iTimeout)  
                            {
                                printf("Program timeout has been met. Exiting...\n\n");
                                return 0;
                            } 
                        }            
                    } while ( (time(NULL) - iStart) < iMouseInterval );
                    
                    
                } // end while

    // destroy the device
    ioctl(ufile, UI_DEV_DESTROY);
    close(ufile);

}

```

Note: There may surely have been easier ways to accomplish was I was trying to do...but this was a fun exercise to learn a bit of programming in Linux. If you know of other ways that could have accomplished the same goal, please post them.

---

### Post by -grubby on 2008-07-05
Nice, but can't you just disable your comptuer from auto-hibernating?

---

### Post by henchman on 2008-07-05
i thought writing a program which disables auto-hibernating for the time would be easier, but OPs approach is much more interesting :)

*will study your code* :)

---

### Post by KingTermite on 2008-07-05
> **nathangrubb said:**
> Nice, but can't you just disable your comptuer from auto-hibernating?

Unless there is another way to do it, no. I set "never" for the Put computer to sleep when idle for time, and it would not hibernate, but it would lock up at that point.

---

### Post by slavik on 2008-07-05
> **KingTermite said:**
> Unless there is another way to do it, no. I set "never" for the Put computer to sleep when idle for time, and it would not hibernate, but it would lock up at that point.
there is an applet which can prevent hibernation ...

---

### Post by odyniec on 2008-07-05
I haven't tested your code, but it appears you have a busy waiting loop in there:
```
                    do // Stay busy until next interval
                    {

                        [...]

                    } while ( (time(NULL) - iStart) < iMouseInterval );
```
This will cost a lot of CPU time, and should generally be avoided (see the [Wikipedia article on busy waiting]("http://en.wikipedia.org/wiki/Busy_waiting") for a comprehensive explanation). You should use timers/signals instead, for example getitimer().

---

### Post by KingTermite on 2008-07-05
> **odyniec said:**
> I haven't tested your code, but it appears you have a busy waiting loop in there:
```
                    do // Stay busy until next interval
                    {

                        [...]

                    } while ( (time(NULL) - iStart) < iMouseInterval );
```
This will cost a lot of CPU time, and should generally be avoided (see the [Wikipedia article on busy waiting]("http://en.wikipedia.org/wiki/Busy_waiting") for a comprehensive explanation). You should use timers/signals instead, for example getitimer().

This is true, but that was a choice. I know it is bad, but as the only purpose was to keep the computer from going idle because little else is going on, I didn't bother to get fancier.

I tried using sleep() functions, but it didn't seem to get rescheduled for cpu time for some reason.

---

### Post by CptPicard on 2008-07-05
> **KingTermite said:**
> This is true, but that was a choice. I know it is bad, but as the only purpose was to keep the computer from going idle because little else is going on, I didn't bother to get fancier.

Considering it's a laptop, it's even worse... it's going to kill your battery life.

> I tried using sleep() functions, but it didn't seem to get rescheduled for cpu time for some reason.

:confused:  rather strange... it should most definitely work.

---

### Post by KingTermite on 2008-07-06
> **CptPicard said:**
> Considering it's a laptop, it's even worse... it's going to kill your battery life.



:confused:  rather strange... it should most definitely work.

It won't hurt battery at all....the point is only to do it when plugged in. I'd never do it on battery.

And I agree on the sleep(), no idea what was goofing it up.

---

