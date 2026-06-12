---
title: "gcc compiled code but code not working"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by rajdroid on 2012-06-15
I have ubuntu 12.04 have gcc 4.6.3. It compile all of my coding in c language but today when I'm compile my code it compiled it successfully but program is not working, the coding is not wrong as I tried in different windows machine where it run correctly. Below I just pasted my code of program if anyone can help me.
[COLOR="Red"]SOURCE CODE:[/COLOR]
[COLOR="DimGray"]
#include <stdio.h>
#include <string.h>
//#include <conio.h>
  char tracks[][80] = {
  	"I left my heart in harvard Med school",
  	"Newark, Newark - a wonderful town",
  	"Dancing with a Dark",
  	"From here to maternity",
  	"The girl from Iwo Jima",
  };
  void find_track(char search_for[])
  {
  	int i;
  	for(i=0; i<5; i++)
  	{
  		if(strstr(tracks[i],search_for))
  			printf("Track %i: '%s'\n", i, tracks[i]);
  	}
    
  }
  int main()
  {
    char search_for[80];
    printf("search for:\n");
    fgets(search_for, 80, stdin);
    find_track(search_for);
    return 0;
  }
[/COLOR]
when I run it in terminal it shows this:
> rajat@rajat-PC:~$ cd Desktop/C\ Programming/
rajat@rajat-PC:~/Desktop/C Programming$ gcc searching.c -o out && ./out
search for:
town
rajat@rajat-PC:~/Desktop/C Programming$ 



---

### Post by anewguy on 2012-06-15
Okay, just me looking in.

Your declaration of "tracks" doesn't contain a "town" entry.  You ran the program, apparently entered "town".  The find_track function does not do anything - no return of "not found", no error code - when the input string isn't found in the table.  Main said to get the string, call find_track, which didn't find anything, and exit.

Looks to me like your program ran as you have it coded. Try entering one of the strings you have in the tracks table.  Bet you'll get what you want then.

Dave ;)

---

### Post by rajdroid on 2012-06-15
> **anewguy said:**
> Okay, just me looking in.

Your declaration of "tracks" doesn't contain a "town" entry.  You ran the program, apparently entered "town".  The find_track function does not do anything - no return of "not found", no error code - when the input string isn't found in the table.  Main said to get the string, call find_track, which didn't find anything, and exit.

Looks to me like your program ran as you have it coded. Try entering one of the strings you have in the tracks table.  Bet you'll get what you want then.

Dave ;)

thanks for reply but second track contains "town" at last.
"Newark, Newark - a wonderful [COLOR="Red"]town[/COLOR]"
so I think coding is right there is some other problem which i can't sort out yet.

---

### Post by jim_24601 on 2012-06-15
We're almost certainly about to get moved to Programming talk, however:

The fgets() function will include the final newline in the returned string if the input is terminated with a newline (according to the C standard). So if you type "town[enter]" in response to the prompt, the search_for variable will contain the string "town\n". There is no newline in "Newark, Newark - a wonderful town", so the search function will find nothing. If you don't want your input string to have a newline on the end, you will have to strip it off yourself.

Why it seems to work on Windows I don't know. Is the code identical?

edit: I just compiled and ran your code with Visual Studio 2008 on Windows XP, typed "town" in response to the prompt and it didn't find anything, as expected. You've got a commented out #include in the code you posted, which suggests to me that the code you were running on Windows wasn't the same, and you introduced the bug when porting to Linux.

---

### Post by rajdroid on 2012-06-15
thanks guys for helping me out.

---

