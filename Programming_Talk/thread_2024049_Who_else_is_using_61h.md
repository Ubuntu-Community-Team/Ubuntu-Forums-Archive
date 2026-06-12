---
title: "Who else is using 61h"
date: 2012-07-13
forum: Programming Talk
---

### Post by nidzo732 on 2012-07-13
I'm writing a program that controls the pc speaker (the beeping one). It controls the hardware directly with the PIT 2 timer and address 61h. But as soon as i set the first two bits of 61h to 1, someone (something) sets them back to zero and the sound is only heard for about half a millisecond. 
I tried running the program on TinyCore linux and it works perfectly, so I'm guessing that there is another program (kernel module perhaps) that also controls the speaker and that it's included in Ubuntu but not in TinyCore to preserve size.
Does anyone know which other programs use 61h.

Note: I've tried rmmoding the pcspkr and snd_pcsp modules, but they weren't loaded anyway

---

### Post by Paddy Landau on 2012-07-13
You may have to undo blacklisting the PC speaker.

[LIST]
[*]Edit [FONT=Lucida Console]/etc/modprobe.d/blacklist.conf[/FONT]
[*]Comment out the line [FONT=Lucida Console]blacklist pcspkr[/FONT].
[*]Test; you may need to also comment out [FONT=Lucida Console]blacklist snd_pcsp[/FONT].
[/LIST]
If that doesn't work, reinstate those lines.

---

### Post by nidzo732 on 2012-07-13
You don't understand, I don't want it to be loaded, I'm writing a program that controls the speaker directly, not via the kernel driver. But even with these two modules blacklisted, something else is controlling the speaker and I need to know what that is.

Here is the code for my program

```

ioperm(0x61, 0x20,1); //request permisions to accsess the memory
ioperm(0x42, 0x02,1); //locations used to controll the speaker

int frequency = 4000;
int countdown = 1193180 / frequency;       //calculate the countdown value for the timer

int lowerbyte = countdown & 0xff;	   //the countdown value is sent in two bytes
int higherbyte = (countdown >> 8) & 0xff;  //so we split the coundtown to higerbyte and lowerbyte
	
outb(0xb6, 0x43);	//notify the timer that we are sending a new countdown value		   
outb(lowerbyte, 0x42);	//send the lowerbyte
outb(higherbyte, 0x42);	//send the higherbyte

int value = inb(0x61);  //
value = value | 3;	//set the first two bits of 61h to 1 in order to turn on the speaker
outb(value, 0x61);   	//
	
sleep(1); 		//wait while the speaker plays
	
value = inb(0x61);	//
value = value & 0xfc;	//turn off the speaker by setting the first two bits of 61h to zero
outb(value, 0x61);	//

```

But as soon outb(value, 0x61) sets the two bits of 61h to 1, something turns it off, I thought it was the pcspkr module, but as we've seen it's blacklisted. What else could be doing this?

---

### Post by Paddy Landau on 2012-07-13
> **nidzo732 said:**
> You don't understand…
Sorry, nidzo, I don't know. Let's hope someone with more information could tell you.

Would it be worth looking at the source code for the [beep]("apt:beep") program? It is available on the standard repositories.

---

### Post by nidzo732 on 2012-07-13
Thanks anyway, I'll see if I can get anything out of the beep program.

---

### Post by ziekfiguur on 2012-07-13
The beep program uses the ioctl function, so it's a little less direct than what you're trying to do.
Here is a little program i made that's based on the beep program. It reads tekst and converts it to morse code using the pc speaker.
Like the beep program the pcspkr kernel module needs to be loaded for this to work.
```
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>
#include <unistd.h>
#include <getopt.h>
#include <fcntl.h>
#include <signal.h>
#include <errno.h>
#include <string.h>
#include <sys/kd.h>
#include <sys/ioctl.h>

#ifndef CLOCK_TICK_RATE
#define CLOCK_TICK_RATE 1193181
#endif

#define VERSION_STRING "morse-0.9"
char *copyright =
"Copyright (C) Hans Alves, 2010-11.\n"
"Use and Distribution subject to GPL.\n"
"For information: http://www.gnu.org/copyleft/.";

#define DEFAULT_FREQ       440.0
#define DEFAULT_LENGTH     60

/* Morse-code rules:
1. A dash is equal to three dots.
2. The space between two parts of one letter is equal to one dot.
3. The space between two letters is equal to three dots.
4. The space between two words is equal to seven dots.
*/
int console_fd = -1;

typedef struct
{
    float freq;
    int   length;
    int   tone;
    char ** files;
    FILE * currfile;
} options;


void handle_signal(int signum)
{
    if(console_fd < 0)
        exit(signum);
    else
    {
        // first stop the sound
        ioctl(console_fd, KIOCSOUND, 0);
        close(console_fd);
        exit(signum);
    }
}

void usage(char * progname)
{
    fprintf(stderr, "Usage:\n%s [-f freq] [-l length] [file1] [file2] ...\n\n",
                    progname);
    fprintf(stderr, "  Freq can be a floating point number and indicates the "
                        "frequency of the beeps\n   in Hz.\n"
                    "  Length can be an integer and indicates the length of "
                        "the beeps in ms.\n"
                    "  When no files are given input will be read from "
                        "stdin.\n");
    fprintf(stderr, "\n%s\n", copyright);
    exit(1);
}

/* Parse the command line.
 * Valid parameters:
 *  "-f <frequency in Hz>"
 *  "-l <tone length in ms>"
 *  "-h/--help"
 *  "-v/-V/--version"
 */
void parse_cl_parms(int argc, char **argv, options * opt)
{
    int c;
    struct option opt_list[4] = {{"help",    0, NULL, 'h'},
                                 {"version", 0, NULL, 'V'},
                                 {NULL,      0, NULL, 0}};

    while ((c = getopt_long(argc, argv, "f:l:hVv", opt_list, NULL)) != -1)
    {
        int arglength = -1;
        float argfreq = -1;
        switch (c)
        {
            case 'f':  // freq
                if(!sscanf(optarg, "%f", &argfreq)
                    || (argfreq >= 20000)
                    || (argfreq <= 0))
                    usage(argv[0]);
                else
                    opt->freq = argfreq;
                break;
            case 'l' : // length
                if(!sscanf(optarg, "%d", &arglength)
                    || (arglength <= 0))
                    usage(argv[0]);
                else
                    opt->length = arglength;
                break;
            case 'v' :
            case 'V' : // also --version
                fprintf(stdout, "%s\n\n%s\n", VERSION_STRING, copyright);
                exit(0);
                break;
            case 'h' : //also --help
            default :
              usage(argv[0]);
        }
    }
    opt->files = argv + optind;
}

void beep(int tone, int length)
{
    if (tone)
    {
        ioctl(console_fd, KIOCSOUND, tone);
        usleep(length * 1000);
        ioctl(console_fd, KIOCSOUND, 0);
    }
    else
        usleep(length * 1000);
}

void beep_code(int tone, int length, char * code)
{
    char * ptr;
    if (!code)
        return;
    //fprintf(stderr, "beeping %s\n", code);
    for (ptr = code; *ptr; ++ptr)
    {
        if (*ptr == '.') beep(tone, length);
        if (*ptr == '-') beep(tone, 3 * length);
        beep(0, length);
        //2. The space between two parts of one letter is equal to one dot.
    }
    beep(0, 2 * length);
    // 3. The space between two letters is equal to three dots.
    //    (2 + the time after the last part of the last letter)
}

char * non_ascii(options * opt, int input)
{
    int input2;
    if (input <= 128)
        return NULL;

    input <<= 8;
    if ((input2 = fgetc(opt->currfile)) == EOF)
        return NULL;
    input += input2;

    switch (input)
    {
        case 0xc3a4:
        case 0xc3a6:
        case 0xc485: return ".-.-";
        case 0xc3a8:
        case 0xc582: return ".-..-";
        case 0xc3b1:
        case 0xc584: return "--.--";
        case 0xc3a0:
        case 0xc3a5: return ".--.-";
        case 0xc3a9:
        case 0xc491:
        case 0xc499: return "..-..";
        case 0xc3b6:
        case 0xc3b8:
        case 0xc3b3: return "---.";
        case 0xc3a7:
        case 0xc489:
        case 0xc487: return "-.-..";
        case 0xc49d: return "--.-.";
        case 0xc59d: return "...-.";
        case 0xc5a1:
        case 0xc4a5: return "----";
        case 0xc3be: return ".--..";
        case 0xc3b0: return "..--.";
        case 0xc4b5: return ".---.";
        case 0xc3bc:
        case 0xc5ad: return "..--";
        case 0xc59b: return "...-...";
        case 0xc5ba: return "--..-.";
        case 0xc5bc: return "--..-";
        default:
            return NULL;
    }
}

void morse(options * opt)
{
    int input;
    int lastspace = 0;
    char * code = NULL;
    char * codes[] = {NULL,     NULL,     NULL,     NULL,    NULL,      NULL,    NULL,    NULL,     NULL,    NULL,     NULL,     NULL,     NULL,     NULL,     NULL,     NULL,
                      NULL,     NULL,     NULL,     NULL,    NULL,      NULL,    NULL,    NULL,     NULL,    NULL,     NULL,     NULL,     NULL,     NULL,     NULL,     NULL,
                      NULL,     "-.-.--", ".-..-.", NULL,    "...-..-", NULL,    ".-...", ".----.", "-.--.", "-.--.-", NULL,     ".-.-.",  "--..--", "-....-", ".-.-.-", "-..-.",
                      "-----",  ".----",  "..---",  "...--", "....-",   ".....", "-....", "--...",  "---..", "----.",  "---...", "-.-.-.", NULL,     "-...-",  NULL,     "..--..",
                      ".--.-.", ".-",     "-...",   "-.-.",  "-..",     ".",     "..-.",  "--.",    "....",  "..",     ".---",   "-.-",    ".-..",   "--",     "-.",     "---",
                      ".--.",   "--.-",   ".-.",    "...",   "-",       "..-",   "...-",  ".--",    "-..-",  "-.--",   "--..",   NULL,     "-..-.",  NULL,     NULL,     "..--.-",
                      ".----.", ".-",     "-...",   "-.-.",  "-..",     ".",     "..-.",  "--.",    "....",  "..",     ".---",   "-.-",    ".-..",   "--",     "-.",     "---",
                      ".--.",   "--.-",   ".-.",    "...",   "-",       "..-",   "...-",  ".--",    "-..-",  "-.--",   "--..",   NULL,     NULL,     NULL,     NULL,     NULL};


    while ((input = fgetc(opt->currfile)) != EOF)
    {
        if (!isprint(input))
        {
            //beep(console_fd, 0, 2 * length);
            //fprintf(stderr, "non printable: %d, %c\n", input, input);
            code = non_ascii(opt, input);
        }
        else
        {
            if (input == ' '
                || input == '\t'
                || input == '\n')
            {
                if (lastspace)
                    continue;
                lastspace = 1;
                beep(0, 4 * opt->length);
                // 4. The space between two words is equal to seven dots.
                //    (4 + 3 after the last letter)
                code = NULL;
            }
            else
                code = codes[input];
        }
        beep_code(opt->tone, opt->length, code);
        if (code)
            lastspace = 0;
    }
}

int main(int argc, char ** argv)
{
    options opt;
    char ** file;
    opt.length = DEFAULT_LENGTH; // pulse duration in miliseconds
    opt.freq = DEFAULT_FREQ;  // frequency in Hz
    opt.files = NULL;
    opt.currfile = stdin;
    signal(SIGINT, handle_signal);
    parse_cl_parms(argc, argv, &opt);

    opt.tone = (int) (CLOCK_TICK_RATE / opt.freq);

    if((console_fd = open("/dev/tty0", O_WRONLY)) == -1)
        console_fd = open("/dev/vc/0", O_WRONLY);

    if (!*opt.files)
    {
        fprintf(stderr, "Reading from stdin.\n");
        morse(&opt); // stdin is default
    }
    else
        for (file = opt.files; *file; ++file)
        {
            fprintf(stderr, "Beeping file: %s\n", *file);
            opt.currfile = fopen(*file, "r");
            if (!opt.currfile)
            {
                fprintf(stderr, "%s\n", strerror(errno));
                continue;
            }
            morse(&opt);
            fclose(opt.currfile);
        }

    return 0;
}
```

---

### Post by nidzo732 on 2012-07-13
Thanks for the help, but it looks like I still haven't explained myself completely. I'm doing a school project and the goal of that project is making a program that controls the hardware _directly_ not through drivers, something like a userspace driver. I want to control the speaker completely from scratch, without any help of a kernel driver like pcspkr. 

Imagine that you don't have pcspkr or anything like it, this program should still work. The problem that I face is that some other program is writing to the address 0x61, that program and my program are conflicting. 

As I said, my program runs fine on TinyCore, which has a greatly reduced set of programs and drivers, among those that are removed is probably the one that's conflicting with my program. I need to know what else is writing to 0x61 so I can kill it.

---

### Post by xb12x on 2012-07-13
> **nidzo732 said:**
> But as soon outb(value, 0x61) sets the two bits of 61h to 1, something turns it off, I thought it was the pcspkr module, but as we've seen it's blacklisted. What else could be doing this?

First thing: check what the other bits of [61h] are. That might give you a clue where to look. A quick Google found:

```
061H Port B Output (acts as a one byte device control register):

               PB7 0 enable keyboard read
                   1 clear keyboard and enable sense of SW1
               PB6 0 hold keyboard clock low, no shift reg. shifts
                   1 enable keyboard clock signal
               PB5 0 enable i/o check
                   1 disable i/o check
               PB4 0 enable r/w memory parity check
                   1 disable r/w parity check
               PB3 0 turn off LED
                   1 turn on LED (old cassettee motor off)
               PB2 0 read spare key
                   1 read r/w memory size (from Port C)
               PB1 0 turn off speaker
                   1 enable speaker data
               PB0 0 turn off timer 2
                   1 turn on timer 2, gate speaker with square wave
```

Second thing: If you are _always_ seeing the bits being changed immediately after you write them, then I would suspect either your write is causing an interrupt and the interrupt's routine is the culprit, or something is polling [61h]. With those two possibilities in mind, a software debugger could help you track down the culprit.

And finally, why not just go with TinyCore since you know it works?

---

### Post by nidzo732 on 2012-07-13
The lines
```

int value = inb(0x61);  
value = value | 3;
outb(value, 0x61);

```

make sure that only the first two bits are changed since number 3 takes only the two first bits (00000011), the | operator just passes the rest of the byte, indeed 0x61 is used to control lots of stuff so i try to make sure I don't touch anything else. 

> 
Second thing: If you are _always_ seeing the bits being changed immediately after you write them, then I would suspect either your write is causing an interrupt and the interrupt's routine is the culprit, or something is polling [61h]. With those two possibilities in mind, a software debugger could help you track down the culprit.


Well, my primary suspect is some other driver in the kernel. How could i use debugger to track it down? Looks like I'll have to search trough the kernel source to find anything writing to that address.

---

### Post by xb12x on 2012-07-13
> **nidzo732 said:**
> The lines
```

int value = inb(0x61);  
value = value | 3;
outb(value, 0x61);

```

make sure that only the first two bits are changed since number 3 takes only the two first bits (00000011), the | operator just passes the rest of the byte, indeed 0x61 is used to control lots of stuff so i try to make sure I don't touch anything else.

Yes, but how do you know something is not sneaking in, between your read and write, something interrupt driven or polling, in microsecond/millisecond time-frames? See port 61h, bits [7-4]. 

> **nidzo732 said:**
> 
Well, my primary suspect is some other driver in the kernel. How could i use debugger to track it down? Looks like I'll have to search trough the kernel source to find anything writing to that address.

With a software debugger you could trap on writes to port 61h. Then compare the address of the culprit to the symbol table(s), etc. I admit it's not easy, but it's probably much quicker than looking through source code.

Another thing you could try is selectively disabling a specific interrupt then retrying your code. Since this is legacy PC stuff start with the legacy PC interrupts. And be prepared that disabling certain interrupts _will_ hang your system. If you find that disabling a certain interrupt helps, then that is a major clue.

One other suggestion: The fact that your code works with TinyCore might indicate that the answer lies with an app that is being loaded at startup/login on your Ubuntu installation.

However, if I had this task I would use a software debugger (a symbolic debugger) and trap on port 61h. I think that would be the quickest method by far.

---

### Post by nidzo732 on 2012-07-13
I'll se what I can do tomorrow. I made a program that prints the value of 0x61 repeadetly, it always stays 28 (signed int) and your description of it shows that it contains values that shouldn't be changed frequently.

---

### Post by xb12x on 2012-07-13
You might want to step back for a moment and think about what you're trying to do. 

You're trying to run _user_ code that _directly_ accesses hardware while on a modern 'Protected' Operating System. So even if you narrow down the cause of the other accesses to port 61h, that doesn't mean you can actually stop them without causing "side" effects, such as hanging or crashing the O.S.

When all is said and done, the correct way to access hardware when running a modern O.S. is to call IOCTL's (drivers). 

Another option is to use DOS or equivalent, something that is not a 'Protected' O.S.

---

### Post by nidzo732 on 2012-07-14
I won't touch programs that use bits 2-7, just the stuff that uses bits 0 and 1. Maybe it would be better to write a kernel module and temporarily disable interrupts while the 0x61 is changed to make sure the other bits are left undamaged.

Pseudocode:
```

disable interrupts;
set int n to value of 0x61;
change first 2 bits of n to 1'
set value of 0x61 to n;
restore interrupts;

```

But I still need to find what is using the bits 1 and 0. I'll try to compare the loaded modules on TinyCore and Ubuntu.

The whole point of this work is not relying on someone else's code, switching to a real mode operating system would just take too much time.

---

### Post by trent.josephsen on 2012-07-14
Yet another way in which academic exercises utterly fail to prepare students for real-world problems.

---

### Post by nidzo732 on 2012-07-16
Got it, it was the snd_hda_intel module, blacklisting it fixes the problem, although i've got no sound through the normal spekers :D.

---

