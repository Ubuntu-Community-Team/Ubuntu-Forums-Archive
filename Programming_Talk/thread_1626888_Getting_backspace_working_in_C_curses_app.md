---
title: "Getting backspace working in C curses app"
date: 2010-11-20
forum: Programming Talk
---

### Post by trilobite on 2010-11-20
Hi all - 
 I'm writing a small text-editor in C using curses. I've got a problem with getting the backspace key working as it should (I'm on Ubuntu 10.04). 
 On the command-line, typing Ctrl-V then <backspace> shows ^? .  Ctrl-V and <Delete> gives ^[[3~ . 

However, in my little editor, when I press backspace, it shows ^G. 

Also- the test for KEY_BACKSPACE in the code below is not working. The following is the relevant code for my app - 
```
 
#include <curses.h>

/* Declare our window  */ 
   WINDOW *mywin;  

/* Number of rows and cols */ 
int r, c, nrows, ncols;  

void backspace()
{ 
  noecho();  
  nocbreak();  
  getyx(mywin, r, c);
  move(r, c-1);   
  delch(); 
  cbreak();  
  refresh();               
}     


/*  Handle the keyboard input  */ 
void keyhandler() 
{   
  getyx(mywin, r, c);  
  ch = getch();   
  if (ch == KEY_BACKSPACE) backspace();    
  else addch(ch);                         
}     


int main(int argc, char *argv[])
{             
   /* Initialise the screen  */    
   mywin = initscr();
   noecho();
   raw();  
   keypad(stdscr, TRUE);   
       
   scrollok(mywin,1);    
   idcok(mywin, 1); 
   idlok(mywin, 1);   
   getmaxyx(mywin, nrows, ncols); 
   clear(); 
   refresh();          
   /*  Set row and col */ 
   r=0; c=0; 
      
   /*  The main loop  */  
   while(1) 
   {            
     keyhandler();                 
   } 
                   
   echo(); 
   keypad(mywin, 0); 
   endwin();   
   return 0; 
} 

```                   

Btw - typing "echo $TERM" on the command-line gives me "xterm". Not hugely helpful, as there are about two dozen entries with "xterm" in their name in the terminfo directory. 

So, if anyone is able to let me know how the backspace key can be made to work, that'll be great! I'm sure others must have come across similar problems - I'm keen to hear how they were solved. 
Many thanks in advance - 
- Andy

---

### Post by itcotbtoemik on 2010-11-21
Offhand, I don't see any obvious problems with the program
itself ('c' is an integer, and you did call 'keypad').
However, whatever terminal description you're using (set
with $TERM of course) defines the "kbs" string capability.
That's where ncurses would find the value for KEY_BACKSPACE.
Linux differs from Unix and BSDs since by convention it uses
code 127 rather than 8 for backspace.  Your terminal database
may have an entry (such as xterm-color) which uses 8.

Which terminal emulator are you using?

---

### Post by itcotbtoemik on 2010-11-21
By the way - gcc reports that 'ch' is undefined.

---

### Post by trilobite on 2010-11-21
> **itcotbtoemik said:**
> By the way - gcc reports that 'ch' is undefined.

Hi itcotbtoemik - thanks for your reply -

 The terminal emulator I'm using is gnome-terminal. As to the "ch undefined" message, I think I may have missed copying a line of text in the code (where ch is defined). 

** UPDATE ** 
I've solved it! This was a silly mistake on my part. The code reads a character from the keyboard. I ahd declared this character as a char - it should have been an INT. I changed the declaration to an int, and everything now works perfectly!  

So, for anyone else having this problem in future - make sure that the variable that you read from the keyboard is declared as an int. 
- trilobite

---

