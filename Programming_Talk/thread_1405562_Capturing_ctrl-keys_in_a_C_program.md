---
title: "Capturing ctrl-keys in a C program"
date: 2010-02-12
forum: Programming Talk
---

### Post by trilobite on 2010-02-12
Hi all - 

 As part of getting into some simple C coding, I've done the code below which reads input from the user and takes action according to what is entered. Here's the code - 
```
 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <termios.h>
#include <ctype.h> 

void func1(void)
{  
   printf("Hey, you entered foo! \n"); 
} 

void func2(void) 
{  
   printf("Hey, you entered bar! \n"); 
} 
     

void ctrl_g(void)
{ 
   printf("Hey, you pressed CTRL g! \n"); 
}   

    
int main(void) 
{   
  char word[80]; 
  char ch; 
  
  do { 
    puts("Enter some text :"); 
    scanf("%s", word);  
    
   if ( !strcmp(word, "foo") ) { 
      func1(); 
  } 
  
   else if (!strcmp(word, "bar") ) { 
      func2(); 
  } 
  
   else if (!strcmp(word, "^G") ) { 
      ctrl_g(); 
  } 
    
   else  { 
   printf("Nope - I do not recognise that phrase.... \n"); 
  }     
  
   printf("Try again? (y/n) : "); 
   scanf(" %c%*c", &ch);  
  } 
  
    while( toupper(ch) != 'N' );         
  return 0; 
} 


``` 

Ok, this works nicely for the strings "foo" and "bar" - it runs the functions as expected. However, when I press Ctrl-G, the program doesn't recognise that as such. It does not run the ctrl_g function, but instead prints my "Nope - I do not recognise that phrase...." message. 

So, I'm wondering - how does one capture/read ctrl-keys entered by the user? 

Many thanks in advance - bye for now - 
- trilobite

---

### Post by MadCow108 on 2010-02-12
^G is just the representation in output
the actual ascii code is different
see:
[http://www.scotek.demon.co.uk/ascii.html](http://www.scotek.demon.co.uk/ascii.html)

But these codes are actually control charcters and the ctrl + X just seem to be mapped to these characters in some linux terminals.
So this may be highly unportable!
Also you will probably have to block the handling of the signals emitted by this in your program (most obvious SIGINT from ^C)

edit: did some testing, you'll have to block almost all signals, a few work without blocking on my system: ^A (=1) ^H (=8) ^T (=20) ^Y (=25)

I don't really think you can do this elegantly with standard C terminal input/output. You should resort to some library like ncurses which should be able to do that.
Or use a gui where you have no problems of the terminal using the same keys.

---

### Post by trilobite on 2010-02-13
> **MadCow108 said:**
> ^G is just the representation in output
the actual ascii code is different
see:
[http://www.scotek.demon.co.uk/ascii.html](http://www.scotek.demon.co.uk/ascii.html)

But these codes are actually control charcters and the ctrl + X just seem to be mapped to these characters in some linux terminals.
So this may be highly unportable!
Also you will probably have to block the handling of the signals emitted by this in your program (most obvious SIGINT from ^C)

edit: did some testing, you'll have to block almost all signals, a few work without blocking on my system: ^A (=1) ^H (=8) ^T (=20) ^Y (=25)

I don't really think you can do this elegantly with standard C terminal input/output. You should resort to some library like ncurses which should be able to do that.
Or use a gui where you have no problems of the terminal using the same keys.

Hi MadCow - thanks very much for that! 
Good news! While poking around with the code, I've now managed to solve this problem.  

The magic snippet of code is as follows - 
```
 
 else if (!strcmp(word, "\007") ) { 
      ctrl_g(); 
  } 

```  

So, the string "\007" equates to Ctrl-G. I even tried another one, just to confirm things. I tried "\001", guessing that that was Ctrl-A, and sure enough, it was!  

So, that's great! 

Now, I'm working on trying to read the arrow keypresses. They're a challenge - when I press the Up arrow, for example, it shows "^[[A" on the terminal. But I'm sure it should be possible to capture those keys as well.... 
- trilobite

---

### Post by nvteighen on 2010-02-13
The correct way to catch POSIX signals is by using the signal() function from singal.h. Look at **man 2 signal** if you've got manpages-dev installed.

---

### Post by MadCow108 on 2010-02-13
> **trilobite said:**
> Hi MadCow - thanks very much for that! 
Good news! While poking around with the code, I've now managed to solve this problem.  

The magic snippet of code is as follows - 
```
 
 else if (!strcmp(word, "\007") ) { 
      ctrl_g(); 
  } 

```  

So, the string "\007" equates to Ctrl-G. I even tried another one, just to confirm things. I tried "\001", guessing that that was Ctrl-A, and sure enough, it was!  

So, that's great! 

Now, I'm working on trying to read the arrow keypresses. They're a challenge - when I press the Up arrow, for example, it shows "^[[A" on the terminal. But I'm sure it should be possible to capture those keys as well.... 
- trilobite

you could just do
```

if (input == somenumber)

```
where some number would be 1-26 in this case

it are just char's (which are 8 bit integers)
no need for a whole strcmp which works on char arrays.
e.g. 'X' is equal to 88. Single quotes are used to get the ascii value of printable chars


but note that this whole technique is very terminal dependent

---

### Post by r_s on 2010-02-13
You need to use signal.h , as they are signals sent as interrupts.

---

### Post by trilobite on 2010-02-13
> **r_s said:**
> You need to use signal.h , as they are signals sent as interrupts.

Thanks very much, r_s (and thanks also to nvteighan and MadCow (again!) ). 

Ok, I'll check out signals.h to do this correctly - always the best way.... :)  

Thanks again, bye for now - 
- trilobite

---

### Post by wmcbrine on 2010-02-13
> **trilobite said:**
> Now, I'm working on trying to read the arrow keypresses. They're a challenge - when I press the Up arrow, for example, it shows "^[[A" on the terminal.Yes, the up arrow sends a sequence of three bytes -- ESC, '[', 'A'. Or, "\033[A".

But you might want to take a look at ncurses. It simplifies input, among other things. (It can be overkill, though.)

---

