---
title: "fopen issues in C"
date: 2013-02-02
forum: Programming Talk
---

### Post by usernamer on 2013-02-02
I'm trying to work out how to use the fopen command in C, but I'm having some issues.
I've written the following short program (and various similar ones for trying to open different files).


#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    FILE *fp;
    fp = fopen( "~/../../usr/bin/vim", "r" );        //Open

    if( fp == NULL ) {                                              //Debugging
    perror( "\nDidn't work!\n" );
    printf( "errno = %d.\n", errno );
    exit(1);
    }

    getchar();                    //Close
    fclose(fp);

    return 0;
}


The output I always get is:
: No such file or directory
errno = 2.
(the errno 2 thing basically re-iterates that the file/directory is wrong)...


If I type into the terminal the directory I put into there '~/../../usr/bin/vim', it opens vim up fine, no issues...
I'm not sure what I'm doing wrong. How could I use fopen to open vim (or some other file) on my computer? Any help here would be great.

Cheers

---

### Post by MG&amp;TL on 2013-02-02
"~" is a shortcut your shell uses to get your home directory. You can't use it in your code paths, as it tries to open the directory "~". Since you just want to open /usr/bin/vim, use that path instead.

---

### Post by usernamer on 2013-02-02
> **MG&TL said:**
> "~" is a shortcut your shell uses to get your home directory. You can't use it in your code paths, as it tries to open the directory "~". Since you just want to open /usr/bin/vim, use that path instead.

Cheers, no error code turns up now, but vim doesn't open when I run the program...

---

### Post by r-senior on 2013-02-02
The "fopen" function opens a file so that you can read its contents. If you want to run the /usr/bin/vim program, you need the "system" function.

---

### Post by usernamer on 2013-02-02
> **r-senior said:**
> The "fopen" function opens a file so that you can read its contents. If you want to run the /usr/bin/vim program, you need the "system" function.

Okay, makes sense... so I modified the path in my program to going from vim to /etc/hosts (and tried another file, '/home/pete/primestest.c' which is just a program I made some time ago in my home directory).

Neither of these open (and this time fopen should work if I'm thinking about it right since I just want to view the contents of these files as opposed to run them)...

---

### Post by Bachstelze on 2013-02-02
> **usernamer said:**
> Okay, makes sense... so I modified the path in my program to going from vim to /etc/hosts (and tried another file, '/home/pete/primestest.c' which is just a program I made some time ago in my home directory).

Neither of these open (and this time fopen should work if I'm thinking about it right since I just want to view the contents of these files as opposed to run them)...

As this point a question is in order: what exactly are you expecting fopen() to do?  Clearly, it's different from what it actually does.

---

### Post by r-senior on 2013-02-02
The files are probably opening, you just aren't doing anything with the open file before you close it again.

Have a look at the fgetc function, which gets a character from an open file. You can echo the character you get from fgetc back to the console using putchar().

All of this would go inside a loop where you test the return value of fgetc to see if you hit end of file (EOF).

---

### Post by usernamer on 2013-02-02
> **Bachstelze said:**
> As this point a question is in order: what exactly are you expecting fopen() to do?  Clearly, it's different from what it actually does.

In that case I probably get it...

<edit> 
for the record, I thought it might do what it seems to do, but would probably open hosts in a file you'd have to run, like your default text editor / program you use to 'open' it, since that's what happens if you go to etc--hosts and double click on the hosts thingymabob (icon). But that would be running the default program, which you'd have to use system for, then in that program opening hosts (well that's what I recon now, possible that's also wrong).

---

