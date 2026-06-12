---
title: "C: stream to printer"
date: 2010-06-05
forum: Programming Talk
---

### Post by MichaelBurns on 2010-06-05
I want to use **fprintf()** in a C program to send some text directly to a printer, but I can't figure out how to open a stream to a printer.

In other words, I'm trying to do something like this:
```

#include<stdio.h>
#define PRINTER_FILE "I have no clue."
int main(void){
  FILE *prntr_strm;
  prntr_strm=fopen(PRINTER_FILE,"w");
  fprintf(prntr_strm,"This message has been printed.\n");
  fclose(prntr_strm);
  return 0;
}

```
but I don't know what to put in place of **PRINTER_FILE** in the **fopen()** function.  Ultimately I want it to be generic (i.e. so that someone on a completely different computer could compile and run the code without having to edit it), but for now I don't even know what it should be specific to my computer.  Maybe I'm not even supposed to use a stream to do this.  I am just clueless at this point.  The one requirement that I have is that I want to stick with C rather than C++.

---

### Post by gmargo on 2010-06-05
You can use **popen(3)** to open a stream to the **lp(1)** command.  Then **fprintf(3)** as normal.  When you **pclose(3)** the pipe, the job will be sent to the print scheduler.

---

### Post by dwhitney67 on 2010-06-05
> **MichaelBurns said:**
> I want to use **fprintf()** in a C program to send some text directly to a printer, but I can't figure out how to open a stream to a printer.

Use the CUPS API.  Don't reinvent the wheel with sloppy popen() calls.

You can obtain the CUPS development package from the repository.

I've included a small test application that you can play with (refer to the attached tar-ball).  Please accept my apologies, but it is written in C++.  :P

---

### Post by soltanis on 2010-06-05
[http://www.cups.org/doc-1.1/spm.html](http://www.cups.org/doc-1.1/spm.html)

As it is the Common Unix Printing System, it is common to Unixes (including OS X, apparently/thankfully). Won't be Windows portable though.

---

### Post by nvteighen on 2010-06-06
> **dwhitney67 said:**
> Use the CUPS API.  Don't reinvent the wheel with sloppy popen() calls.

You can obtain the CUPS development package from the repository.

I've included a small test application that you can play with (refer to the attached tar-ball).  Please accept my apologies, but it is written in C++.  :P

Actually, using popen() to call lp will end calling up the CUPS server anyway :P In other words: an unneeded additional layer.

---

### Post by dwhitney67 on 2010-06-06
> **nvteighen said:**
> Actually, using popen() to call lp will end calling up the CUPS server anyway :P In other words: an unneeded additional layer.

You probably meant to state that 'lp' is the unneeded additional layer?

In layman's terms...

Application -> popen() -> lp -> CUPS -> printer

or

Application -> CUPS -> printer


For trivial applications, perhaps using the 'lp' option might be easiest; but for complex applications, which may need to provide insight (to the user) as to which printers are available on the system, which types of media and which print options each supports, well then CUPS is appropriate to use.

---

### Post by nvteighen on 2010-06-06
> **dwhitney67 said:**
> You probably meant to state that 'lp' is the unneeded additional layer?

That was exactly what I meant.

> 
For trivial applications, perhaps using the 'lp' option might be easiest; but for complex applications, which may need to provide insight (to the user) as to which printers are available on the system, which types of media and which print options each supports, well then CUPS is appropriate to use.

IMO, lp (or lpr, which allows other options) has its place on shell scripts or stuff where no direct interface to the CUPS API is available. I always favor library-based solutions over pipe-based ones (when both are possible) as the former makes your program "inherit" the functionality, while the other adds a runtime dependency... in other words, using popen() doesn't make your program print something on its own, but just calls something else.

---

### Post by MichaelBurns on 2010-06-10
I appologize for the lateness of this reply; learning the CUPS API is going to take me a while.  I will admit that I continued to search for a simpler, more straightforward, solution, but I finally realized that CUPS seems to be "the" printing solution.  (I.e. good luck finding a "good" printing solution that doesn't in some way rely on CUPS.)

It seems strange to me that such an elaborate construction is required for something so mundane as printing.  For example, what is wrong with including a **stdprinter** in the list of standard streams (**stdin**, **stdout**, **stderr**, **stdprinter**)?  I guess the issue is that printers are not "standard enough" while computer screens are, for some reason?  How strange.  (Thank god I don't need a CUMS API to print to the screen.)  I don't like this CUPS situation, but I don't know of a better way, so here I am.

Anyway, on a positive note, this is a great opportunity to force myself to use an API (for the first time that I am aware of).

I have been able to compile my first (trivial) programs yesterday "using" the CUPS API.  Incidently, for anyone else in my situation, this may save you some frustrations:
```

ubuntu@ubuntu:~$ gcc -Wall -pedantic -o my_program.x `cups-config --cflags` my_program.c `cups-config --libs`

```
I'm currently trying to figure out how I can test my programs, and I have no printer, so I would like to "print to file" (as can be done from, say, Firefox, printing a webpage to a ps file).  So, I am trying to figure out how to use the CUPS API to print some text to a ps file.  **cupsGetDests()** returns **0**, which I interpret to mean that "print to file" is not seen as a printer in CUPS, even though it seems to be listed as a printer in the **File > Print** menu (of, say, Firefox).

Also, there is a feature (of CUPS?) that particularly bothers me.  Somehow, root access is required for printing.  Can someone help me to understand why this is the case?  Is there a way to remove this restriction?

---

### Post by Bachstelze on 2010-06-10
> **MichaelBurns said:**
> 
It seems strange to me that such an elaborate construction is required for something so mundane as printing.  For example, what is wrong with including a **stdprinter** in the list of standard streams (**stdin**, **stdout**, **stderr**, **stdprinter**)? I guess the issue is that printers are not "standard enough" while computer screens are, for some reason?  How strange.

What about computers that just don't have a printer? Also, stdout does not in any way mean "screen", it means "the output device of the terminal the current shell runs on". It might or might not be a screen, but there will always be one. This is not true of printers.

---

### Post by MichaelBurns on 2010-06-10
OK.  Any suggestion how I can write a program in C that utilizes the CUPS API to print text to a .ps file?

---

### Post by dwhitney67 on 2010-06-10
> **MichaelBurns said:**
> OK.  Any suggestion how I can write a program in C that utilizes the CUPS API to print text to a .ps file?

CUPS is for printing to a printer, not a file.

If all you want to do is generate a PostScript file, then perhaps you could take a shot at using pslib.  Read here for info on this library: [http://pslib.sourceforge.net/](http://pslib.sourceforge.net/)

To install it under Ubuntu, I believe the correct meta-package is "pslib-dev".

---

### Post by MichaelBurns on 2010-06-12
I think we're missing the point, so I will paraphrase my situation:
I want to learn a simple and portable printing solution.  Apparently, CUPS is the solution, so I have installed the library (libcups2-dev, with eight dependencies) and I use the CUPS API in my code.  However, I need a way to verify that my code is doing what I intend.  Right now, CUPS is aware of 0 printers on my computer, so the code does nothing interesting.  I don't care about printing to file, per se, and I would simply write my own postscript code if that were an issue.  I just don't know how to test my CUPS API code.

I have recently run into another problem:
My compiler is not recognizing some parts of the CUPS API, using
```

gcc -Wall -pedantic -o "%e" `cups-config --cflags` "%f" `cups-config --libs`

```
in Geany (and, of course, including cups/cups.h).  For example, it recognizes:
```

cups_dest_t, cupsGetDests(), cupsGetOption(), cupsFreeDests()

```
but not:
```

cupsCreateJob(), CUPS_HTTP_DEFAULT, cupsStartDocument(), CUPS_FORMAT_TEXT, cupsWriteRequestData(), cupsFinishDocument(), 

```
Also, for instance:
```

ubuntu@ubuntu:~$ grep -c cupsGetDests /usr/include/cups/cups.h
2

```
whereas:
```

ubuntu@ubuntu:~$ grep -c cupsCreateJob /usr/include/cups/cups.h
0

```
So, I wonder why the [documentation](http://www.cups.org/documentation.php/doc-1.4/api-cups.html) instructs the usage of these undefined functions.

---

### Post by dwhitney67 on 2010-06-12
So post the code you are trying to use.  I don't care about Geany (it's not even worth discussing!).

All you need to link with is "-lcups"; period.

I wrote the following code, in C++; translate as approriate to C, which should be a "bunny":
```

PrintUtility::PrintUtility(const std::string& printerName)
   : myPrinterName(printName),
     myOrientation(PORTRAIT),
     myMediaType("letter"),
     myNumCopies(1),
     myCollateChoice(false),
     myDuplexChoice(false),
     myTumbleChoice(false),
     myColorChoice(false),
     myCPI(10),
     myLPI(6),
     myQuality(NORMAL)
{
   cups_dest_t* dests;
   const int    numDests = cupsGetDests(&dests);

   if (myPrinterName.empty() )
   {
      myDestination = cupsGetDest(NULL, NULL, numDests, dests);

      if (myDestination && myDestination->instance == NULL)
      {
         myPrinterName = myDestination->name;
      }
   }
   else
   {
      myDestination = cupsGetDest(myPrinterName.c_str(), NULL, numDests, dests);
   }
}

...

int
PrintUtility::print(FILE* fd, const char* filename)
{
   int jobId = 0;

   if (fd && myDestination)
   {
      collectOptions();

      jobId = cupsCreateJob(CUPS_HTTP_DEFAULT, myDestination->name, filename,
                            myNumOptions, myOptions);

      if (jobId > 0)
      {
         const char* format = (std::string(filename).find(".ps") != std::string::npos ?
                               CUPS_FORMAT_POSTSCRIPT : CUPS_FORMAT_TEXT);

         char   buffer[4096] = {0};
         size_t bytes = 0;

         snprintf(buffer, sizeof(buffer) - 1, "%s", filename);

         cupsStartDocument(CUPS_HTTP_DEFAULT, myDestination->name, jobId, buffer, format, true);

         while ((bytes = fread(buffer, 1, sizeof(buffer), fd)) > 0)
         {
            cupsWriteRequestData(CUPS_HTTP_DEFAULT, buffer, bytes);
         }

         cupsFinishDocument(CUPS_HTTP_DEFAULT, myDestination->name);
      }

      releaseOptions();
   }

   return jobId;
}

```

In summary:
```

..
cupsCreateJob(...)
...
cupsStartDocument(...);
cupsWriteDocument(...);
cupsFinishDocument(...);
...

```
The first step, "cupsCreateJob", is to verify that you do indeed have the names printer available on your system.  In your case, since you do not have a printer, it will return NULL.

I'm not quite sure how you plan to test your code *without* a printer?

---

### Post by nvteighen on 2010-06-13
> **MichaelBurns said:**
> OK.  Any suggestion how I can write a program in C that utilizes the CUPS API to print text to a .ps file?

Use the CUPS PDF printer...

Install it using:
```

sudo apt-get install cups-pdf

```

It works as a printer, so if that works, CUPS is working... :P It's rather useless for OpenOffice.org, which has its own native PDF exporter, but it works for everything else... like your program, for example. Usually the CUPS PDF printer is conveniently called "PDF" and outputs the file to ~/PDF

---

### Post by MichaelBurns on 2010-06-13
> **nvteighen said:**
> Use the CUPS PDF printer...

Install it using:
```

sudo apt-get install cups-pdf

```Yes!  This is the sort of thing that I'm looking for.  CUPS now finds a printer named "PDF" and the cupsGetOption() function also returns "PDF".  Thank you!

However, I still have the other problem.  Do you have any idea why some of the CUPS API is recognized while some of it is not?

---

### Post by nvteighen on 2010-06-14
> **MichaelBurns said:**
> 
However, I still have the other problem.  Do you have any idea why some of the CUPS API is recognized while some of it is not?

What do you mean by that?

---

### Post by MichaelBurns on 2010-06-15
When I include the header file and build with the library, the compiler (gcc) still doesn't recognize cupsCreateJob(), CUPS_HTTP_DEFAULT, cupsStartDocument(), CUPS_FORMAT_TEXT, cupsWriteRequestData(), cupsFinishDocument().

---

### Post by dwhitney67 on 2010-06-15
> **MichaelBurns said:**
> When I include the header file and build with the library, the compiler (gcc) still doesn't recognize cupsCreateJob(), CUPS_HTTP_DEFAULT, cupsStartDocument(), CUPS_FORMAT_TEXT, cupsWriteRequestData(), cupsFinishDocument().

Can you please be more specific?  On my first post to this thread, I provided a complete example of how to to use the CUPS API... including the Makefile necessary to build the project.

Is there something else that you are doing?  Could you please post the **exact** error messages you get when you are trying to build your project, including the actuall gcc statement your using?

---

### Post by MichaelBurns on 2010-06-16
```

ubuntu@ubuntu:~$ gcc -Wall -pedantic my_prog.c -lcups
my_prog.c: In function ‘main’:
my_prog.c:16: warning: implicit declaration of function ‘cupsCreateJob’
my_prog.c:16: error: ‘CUPS_HTTP_DEFAULT’ undeclared (first use in this function)
my_prog.c:16: error: (Each undeclared identifier is reported only once
my_prog.c:16: error: for each function it appears in.)
my_prog.c:21: warning: implicit declaration of function ‘cupsStartDocument’
my_prog.c:22: error: ‘CUPS_FORMAT_TEXT’ undeclared (first use in this function)
my_prog.c:25: warning: implicit declaration of function ‘cupsWriteRequestData’
my_prog.c:27: warning: implicit declaration of function ‘cupsFinishDocument’

```

---

### Post by dwhitney67 on 2010-06-16
Those are compiler errors.  Did you include <cups/cups.h> in your source code?

If so, then verify that you have the cups.h file in /usr/include/cups.  If not, then install the cup development package.

---

### Post by uOpt on 2010-06-16
There is nothing wrong with just doing a popen(lprcmd);, except the delayed error handling which IMHO is acceptable, and the cost of the fork() which shouldn't be an issue in most cases.

First of all, it is portable to where there is no cups. You don't need to install development libraries.

The luser can control which printer will be in use with a simple environment variable $PRINTER, or you add a control for a printer name that you put into the commandline.

Advanced printer options can be set by using cupscontrol to define aliases for printers.

Unless you have a real need for extensive interactive control of options I wouldn't bother with cups. The lpr solution is portable, and you can quickly morph it into feeding something else, e.g. on Windoze.

---

### Post by dwhitney67 on 2010-06-16
> **uOpt said:**
> 
First of all, it is portable to where there is no cups. You don't need to install development libraries.

Without CUPS, lp (or lpr) could not work... that is, under Linux.

I cannot think of any Linux distro that does not use CUPS.  One does not need the development library unless they are compiling/linking an application.  During runtime, as just mentioned, the Linux distros provide the CUPS library.  Check for yourself; it should be at /usr/lib/libcups.so (shared-object library) or /usr/lib/libcups.a (static library).

---

### Post by uOpt on 2010-06-16
> **dwhitney67 said:**
> Without CUPS, lp (or lpr) could not work... that is, under Linux.

I cannot think of any Linux distro that does not use CUPS.  One does not need the development library unless they are compiling/linking an application.  During runtime, as just mentioned, the Linux distros provide the CUPS library.  Check for yourself; it should be at /usr/lib/libcups.so (shared-object library) or /usr/lib/libcups.a (static library).

And who says this program will only ever run on Linux?

Portable programming isn't very hard these days, except if you make it hard by pulling in random subsystems that are specific to the environment and that you didn't need in the first place.

---

### Post by dwhitney67 on 2010-06-16
> **uOpt said:**
> And who says this program will only ever run on Linux?

Portable programming isn't very hard these days, except if you make it hard by pulling in random subsystems that are specific to the environment and that you didn't need in the first place.
Your argument is very shallow.  Going with the popen() approach is no more portable.

As discussed earlier, lp uses CUPS.  Why not just use CUPS directly, thus avoiding another layer, which could possibly be different from one system to another (eg. Linux and Mac)?

As for CUPS, it is available for 32-bit Windoze, and who knows, perhaps in the near future a 64-bit solution will be available too.


P.S.  I will not discuss my opinion any further; frankly I do not get the impression the OP is developing s/w for multiple platforms; for Christ's sake... he couldn't even compile under Linux!

---

### Post by uOpt on 2010-06-16
> **dwhitney67 said:**
> Your argument is very shallow.  Going with the popen() approach is no more portable.

As discussed earlier, lp uses CUPS.  Why not just use CUPS directly, thus avoiding another layer, which could possibly be different from one system to another (eg. Linux and Mac)?

As for CUPS, it is available for 32-bit Windoze, and who knows, perhaps in the near future a 64-bit solution will be available too.

popen will instantly work on Linuxes that have lpd installed (as opposed to cups), the BSD and Solaris when they chose not to install CUPs (common), and I don't think MacOS X ships with cups, does it?

And popen() also allows you to play tricks like this:
```

popen("ssh mysmarthost lpr", "w");

```

Where "mysmarthost" is a machine that has a printer installed and/or reachable. Your current computer might not have any printer installed, and no printer software, not be on the same LAN (no printer discovery), behind or in front of a firewall etc etc etc

You people give really lousy advice. There is no reason whaysoever to bother with the CUPS C api unless you have the specific need to present printer options interactively to the user (as opposed to just using cupscontrol).

---

### Post by tjandracom on 2010-11-07
> Originally Posted by MichaelBurns  
When I include the header file and build with the library, the compiler (gcc) still doesn't recognize cupsCreateJob(), CUPS_HTTP_DEFAULT, cupsStartDocument(), CUPS_FORMAT_TEXT, cupsWriteRequestData(), cupsFinishDocument().

that functions only available on libcupsys version 1.4, and that included in the Ubuntu Karmic and above. if you're using Ubuntu before Karmic, (i.e Hardy using libcusys version 1.3.7) then those mentioned function does not exists.

---

