---
title: "[c]problem with small program that should shutdown computer"
date: 2008-09-23
forum: Programming Talk
---

### Post by cmay on 2008-09-23
hi.
i am trying to as learning experience to write some small program on windows xp like wc grep shutdown ls and so on and i have a problem with this program. it does not as the first thing i want it to do and it should do according to my notes i took sometime ago reboot and shutdown.

when i test it it does log me out of the system however. but i want it to do power off and reboot. also when i test the --help and --version option it fails and gives the pop up box with send application error message to microsoft box.it compiles and runs with out any problem.  
can any one see what the problem is. thanks in advance.
 
[PHP]/* author cmay 2008

 * license GPL

 * usage: shuts down the computer :)

 * 

 */

#include <stdio.h>

#include <stdlib.h>

#include <windows.h>

#include <string.h>



char *progname;

float version = 0.1;

void help();



int main(int argc, char **argv)

{

    progname=argv[0];

    /* we need a set of golden rules for how many argcs passed */

   if(argc != 2)

   {

      printf("USAGE: %s [-s] [-r] \n",progname);

      exit(0);

      }

      

      /* THE WIN32 API CALLS TO SHUTDOWN AND REBOOT*/

    if(strcmp(argv[1],"-s")==0)       

       ExitWindows(EWX_SHUTDOWN,0);

    

    /* the shutdown or reboot options as win32 api allows*/

    if(strcmp(argv[1],"-r")==0)

       ExitWindows(EWX_REBOOT,O); 

    

    /* display our version scheme */

    if(strcmp(argv[1],"--version")==0)

       printf("%1.2f\n",version);

       

    /* display our help-man-page-like thinghy*/

    if(strcmp(argv[1],"--help")==0)

             help();

    /* OR ELSE USER FAILED TO PASS THE RIGHT PARAMTERES SHAME ON HIM/HER/IT/THAT*/

    else printf("%s invalid or incorrect options \n",progname);

    

          system("PAUSE");	

  

  return 0;

}



void help()

{

     printf("%s USAGE: [-s][-r]\n");

     printf(" [--help] this help\n");

     printf(" [--version] version\n");

     printf(" the time option known from UNIX systems are omitted\n");

     printf(" license GPL \n");

     printf(" author cmay 2008\n");

}[/PHP]

---

### Post by Zugzwang on 2008-09-24
Answer: Read the manual about the ExitWindows and ExitWindowsEx functions [here]("http://msdn.microsoft.com/en-us/library/aa376883(VS.85).aspx"). You'll see that "ExitWindows" doesn't do what you expect.

Anyway, this is *definitely* the wrong forum for that!

---

### Post by cmay on 2008-09-24
> Anyway, this is *definitely* the wrong forum for that! 
then i strongly suggest you report me.

---

### Post by Kadrus on 2008-09-24
> Anyway, this is *definitely* the wrong forum for that!
[I]This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any programming language is allowed. [/I]
Anything programming related is allowed,and we have seen over the past weeks a lot of post regarding Python exectuable for windows with no complaints,so anything goes.

---

### Post by lisati on 2008-09-24
A couple of observations: 
[LIST=1]
[*]Would adding a "return 0" to the help function make a difference?
[*]the "invalid option" error message will come up if the option isn't "--help"
[/LIST]

---

