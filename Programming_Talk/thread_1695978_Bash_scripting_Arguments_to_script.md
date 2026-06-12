---
title: "Bash scripting: Arguments to script"
date: 2011-02-26
forum: Programming Talk
---

### Post by evillan on 2011-02-26
I'm a noob a bash scripting and want to write a script where the number of arguments (i.e. $ script.sh arg1 arg2 arg 3... etc.) varies. 

Is there any easy way to do this?

The arguments will later be used in the script and should have individual names (but that shouldn't be a problem, i.e. @1, @2, @3 etc.).

Furthermore is there a simple way to count the number of arguments? I could of course make a for loop or something, but it would be great if there was an actual function.

Thank you!

---

### Post by cgroza on 2011-02-26
The command line arguments are accessed via the variables $1, $2, $3 etc.
$0 is the name of the script.

---

### Post by Joeb454 on 2011-02-26
To count the number of arguments passed to a script, you use **$#**, so if I wanted to ensure there were 2 arguments, I would do something like ```
if [ $# == 2 ]; then
    #do stuff here
fi
```
The script itself isn't included in this count.

---

### Post by LarryJor on 2011-02-26
I'm not sure where you plan to go with this - it would be difficult to set up a program that can read in a different number of arguments and still sort out what they are at run time.  I THINK the concept you are asking about can be covered with the responses given, if a little more interpretation is provided.  According to "Linux Shell Scripting with Bash", by Ken O. Burtch, you would use something like this:

#!/bin/bash
#
#
if [ #$ -eq 0 ] ; then
   printf "%s\n" "Type --help for help."
fi

# processing the arguments

while [ $# -gt 0 ] ; do
    case "$1" in
    -h | --help)  # show help
        printf "%s\n" "Use MYPRGRM [-h][--help] -c companyid"
        exit 0
        ;;
     -c ) shift
        if [ #$ -eq 0 ] ; then
         printf "MYPRGM:$LINENO:  %s\n" "Company for -c is missing" >&2
         exit 192
        fi
        COMPANY="$1"
        ;;
     -* ) printf "MYPRGM:$LINENO: %s\n" "Switch $1 not supported" >&2
         exit 192
        ;;
      * ) printf "MYPRGM:$LINENO: %s\n" "Extra argument or missing switch" >&2
         exit 192
        ;;
    esac
    shift
done
if [ -z "$COMPANY" ] ; then
     printf "%s\n" "Company name missing" >&2
     exit 192
fi
#  Whatever you wanted to do here....
exit 0



     This is loosely based on a demo script on pages 147-148 of aforementioned book.  Note that the 'shift' command moves to the next argument on the command line to continue processing, and some error messaging is provided.  Does this help?
      There is a better way, using the 'getopts' command, but it doesn't allow for quite the variation in the number of arguments....  Generally, you would want to know what command line arguments you are going to use, and then you can set up the program to find whether each argument is present.

---

### Post by evillan on 2011-02-27
Thanks for the answers. I don't think bash scripting has the function I'm looking for.

I want to make a script that takes x arguments (data files) and plots them in the same graph using gnuplot. Since the number of data files per system varies, the script would have to be able to take different arguments. 

Anyways, I'll figure something else out.

---

### Post by Jose Catre-Vandis on 2011-02-27
> **evillan said:**
> Thanks for the answers. I don't think bash scripting has the function I'm looking for.

I want to make a script that takes x arguments (data files) and plots them in the same graph using gnuplot. Since the number of data files per system varies, the script would have to be able to take different arguments. 

Anyways, I'll figure something else out.

Should be that difficult with bash; in English:

Script goes off and find all the data files you want/need and counts them, a loop will then generate variables for the correct number of files based on that count, then then next loop will action each file in turn?

---

### Post by evillan on 2011-02-27
> **Jose Catre-Vandis said:**
> Should be that difficult with bash; in English:

Script goes off and find all the data files you want/need and counts them, a loop will then generate variables for the correct number of files based on that count, then then next loop will action each file in turn?

Yes, something like that. The files are typically in different folders and need to be input manually - the file names are randomly generated. 

Could you outline the code for such a program?

I'm currently trying to combine python, bash scripting and gnuplot...  very confusing when you're new to all the programs.

---

### Post by Jose Catre-Vandis on 2011-02-27
Your going to need some commonality in the filename / filetype in order to automagically use them in a script. If they are completely randomly named and located, you raise the bar significantly on the complexity of the script, and you may have to feed it arguements of some kind to help it along. Can you not manipulate the data file filenames and location in some way?

I am no bash guru, hence why I wrote in plain English, but I am guessing you would use "find" and some "awk" for the first part, then create some kind of array with the output from "find", then a for each loop to action the contents of the array.

---

### Post by evillan on 2011-02-27
> **Jose Catre-Vandis said:**
> Your going to need some commonality in the filename / filetype in order to automagically use them in a script. If they are completely randomly named and located, you raise the bar significantly on the complexity of the script, and you may have to feed it arguements of some kind to help it along. Can you not manipulate the data file filenames and location in some way?

I am no bash guru, hence why I wrote in plain English, but I am guessing you would use "find" and some "awk" for the first part, then create some kind of array with the output from "find", then a for each loop to action the contents of the array.

The files are the same filetype, yes. 

I think I've found a way to do this with python/subprocess, so its working for now.

Thank you for your help!

---

