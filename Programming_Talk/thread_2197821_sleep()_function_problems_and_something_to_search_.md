---
title: "sleep() function problems and something to search through the system"
date: 2014-01-05
forum: Programming Talk
---

### Post by brick2 on 2014-01-05
```
#include <iostream>
#include <cstdlib>
#include <string>
#include <stdio.h>

#include <unistd.h>

using namespace std;

int main()
{
    string x = "gsettings set org.gnome.desktop.background picture-uri file:///home/relax/Desktop/Space/Space_01.jpg";
    char buff[1];

    for( int i=1; i<=30; i++ )
    {
        sleep( 20 );
        if( i<10 )
        {
            sprintf( buff, "%d", i );
            x[95] = buff[0];
            system( x.c_str() );
            cout << x << endl;
            sleep( 20 );
        }
        else if( i > 10 )
        {
            sprintf( buff, "%d", i );
            x[94] = buff[0];
            x[95] = buff[1];
            system( x.c_str() );
            cout << x << endl;
            sleep( 20 );
        }
        //Note for self
        //YOU MUST FEED A C STRING TO SYSTEM() OTHERWISE IT WILL NOT WORK, THAT IS WHY YOU HAVE C_STR() FUNCTION
    }
}


```

This is my code thus far, I am relativley new to programing. I am trying to make a program which I will put into init.d to run at start up. However the sleep function does not seam to be working at all, no errors are reported and the program executes and it does work but there is no delay and the pictures change too fast.

The program is ment to change my desktop background every 20 seconds, this does not happen, instead it the change takes place really fast. I have tryed uspeel() as well but nothing has been achieved, same thing, it runs but there is not delay.

One more thing I would like to ask that is related to this program.
Can anyone sugest a way to make a piece of code that I will be able to incorporate here, which will without knowing the location of images search for them and as it finds them, use them, regardless of their location, ( image names are known ).

This was written in c++ using Eclipse Kelper
Ubuntu 12.04 LTS
Dell inspiron 5537

---

### Post by brick2 on 2014-01-05
Thank you all for your time.

---

### Post by brick2 on 2014-01-05
Ok so after a while of trying to figure it out, turn out it was a proble mwit heither the Eclipse or me as it was compiling the same program over and over again without memorizing any of the changes even though I saved them, in any case one problem solved the first one, but I ll leave the thred open to see if anyone can shed any light on the second question.

---

### Post by steeldriver on 2014-01-05
Is your intention here to practice C/C++ programming? if not, then what you want to do would be easier using a shell script (using the 'find' command for example)

If you *are* trying to learn C++ (or C - which is it?) then there are several issues with your code e.g. you are overflowing buff (it needs to be at least 3 bytes - not 1 - to allow for the 2-digit value plus null terminator), the hoops you are jumping through to construct the filename are unnecessary (either use C++ string concatenation, or use C sprintf to write the decimal value straight into the formatted command string)

Also you will want to run it on session-startup (not from init) I think since gsettings will be interfacing to the user's dconf database

---

### Post by brick2 on 2014-01-05
I do need to do in c++. It does work, it changes 30 diffrent desktop backgounds and I managed to get the sleep() working as well. However I would like to know of a way to search through the whole system for images so that they do not have to be in any particular place, rather instead they can be anywhere, and the program needs to be able to find them and go through them, changing the backgound. That is what I wish to do, that was the second part of my question.

A yeah it needs to be written in c++. Several reasons for that:
1. At the moment I am learnign c++ in collage, jsut started
2. The original idea was to make a presentation in this way, I wanted to have two pictures, and to rotate them, so that it would look like a beating heart for my GF and it is also for a school project.

As I am jsut starting I am sure that the code is badly written but at least it works, how don t ask me please :) , took me several hours for this.
But you see now whay I need it to search the computer for the images.
Because when I send the program to someone and the images separetly it needs to be able to find them no matter where they are, otherwise only I will be able to use it.

As always thx to all for the time invested.

---

### Post by ofnuts on 2014-01-05
> **brick2 said:**
> As I am jsut starting I am sure that the code is badly written but at least it works, how don t ask me please :) , took me several hours for this.

If you don't know why your code works it's not worth the disk space to hold it. It may be working for the wrong reasons (no code is completely miracle-proof). You have to know why it works so that you know what to fix when it breaks.

---

### Post by Tony Flury on 2014-01-06
As for your other question - how do you search the entire system to find the appropriate graphics files : 

There are two standard Unix ways for an application to use user defined files (like you are trying to do) : 
1) The files are always in a known location defined by the application - it is the users job to place the files in the right folder.
2) The file can be stored anywhere, but there is a configuration file at a fixed location which the application reads, and which the user is responsible for editing to record the path of the graphics files.

I would plump for option 2 - it feels more "right" to me.

I think in Windows you can use either technique too - i am not sure if there is a preffered method for Windows or Mac OS.

I would argue it is not a good idea for an application to search the entire system for a particular file name - you can't guarantee that the other user does not have any other files of that name that they don't want to be used/displayed.

---

### Post by brick2 on 2014-01-06
Thank you for your help and the idea. Will try to do it as the option 2 states.

---

