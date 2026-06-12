---
title: "DHARMA Clock (from LOST) - major issues"
date: 2008-10-04
forum: Programming Talk
---

### Post by yoda2031 on 2008-10-04
This post is, essentially, me giving up.  I've proved the concept using BBC Basic but cannot for the life of me create a C program that outputs a clock counting down from 108 minutes to 0 which can be interrupted at any point by the user inputting the correct sequence of six numbers ("4 8 15 16 23 42").

The BBC Basic proof of concept is given below:
```

   10 CLS
   20 TIME=0
   30 q=0
   40 limit=6100
   50 password$=""
   70 REPEAT
   80   REPEAT
   85     PRINT TAB(10,5) "Time Remaining: ";
   86     PRINT TAB(10,20) "> ";
   90     k$=INKEY$(0)
  100     IF k$=CHR$(8) THEN PROCback
  110     IF (ASC(k$)>47 AND ASC(k$)<58 OR ASC(k$)=32) THEN password$=password$+k$
  120     IF k$<>"" THEN CLS:PRINT TAB(10,20) "> "+password$;
  130     IF TIME=limit THEN k$=CHR$(13):q=1
  140     sec=(limit-TIME) DIV 100:min=sec DIV 60:sec=sec MOD 60
  141     PROCmin
  142     IF sec<10 THEN sec$="0"+STR$(sec) ELSE sec$=STR$(sec)
  145     IF (limit-TIME<6001 AND TIME MOD 100=0) THEN VDU 7
  147     IF (limit-TIME<30001 AND TIME MOD 500=0) THEN VDU 7
  150     PRINT TAB(10,10) min$+":"+sec$;
  160   UNTIL k$=CHR$(13)
  170   IF password$="08" THEN END
  180   IF password$="4 8 15 16 23 42" THEN TIME=0:password$="":CLS
  190   IF q=1 THEN PROCbang
  200 UNTIL FALSE
  210 REM
  220 END
  230 DEF PROCback
  240 IF password$="" THEN ENDPROC
  250 l=LEN(password$)
  260 password$=LEFT$(password$,l-1)
  270 ENDPROC
  300 DEF PROCbang
  310 PRINT TAB(1,1) "bang!"
  320 END
  330 ENDPROC
  400 DEF PROCmin
  410 IF min<10 THEN min$="  "+STR$(min):ENDPROC
  420 IF min<100 THEN min$=" "+STR$(min):ENDPROC
  430 min$=STR$(min):ENDPROC

```
While it doesn't work -exactly- as intended, it DOES do everything in spec.  If I can get the C program working as well as that one, I can alter the rest of it to conform better with my specification.

I'm a little embarrassed to show it, because it's become a bit of a mess of workarounds, but the C code is here:
[http://dev.yoda2031.co.uk/lost/lost.c](http://dev.yoda2031.co.uk/lost/lost.c)

Replies of the following nature will be ignored:
"I don't know BBC Basic"
"That BBC Basic program wouldn't work" - it does.  simple as.
"Your code is buggy" (without providing a solution)
"Your code is messy"
"Use more whitespace/comments" (delete as appropriate)
"Use less whitespace/comments" (delete as appropriate)
"I could do this in <insert programming language>" (I want to do it in C)
or anything else unhelpful, really.

By the way, if Supirman is out there - this post should help explain to you why I needed that non-interrupting getchar() function...

EDIT: See my last post on page 2 for the code that now works, or the following link will work for the time being:
[http://dev.yoda2031.co.uk/lost/lost.c](http://dev.yoda2031.co.uk/lost/lost.c)

---

### Post by Mordred on 2008-10-04
Hi,

Can you be a bit more specific about what is wrong with it?

I suggest you try to find the problem using a debugger; 
try stepping through your code and search why it is not behaving
as you intended.

You can use gdb from the command line or you can choose for a
graphical frontend:

ddd : data display debugger - an X frontend for gdb
nemiver : a gtk frontend for gdb

next to these also eclipse and netbeans have C/C++ plugins that
provide debugging support.

Good luck!

---

### Post by yoda2031 on 2008-10-04
It's not failing, it just isn't working as intended.  I was hoping someone could look over my C code and say "well duh, that's not what you did in BBC Basic" - preferably with a line number...

Basically, the output is erratic and still waits for input on each loop despite a clever little "is_key_pressed()" function that supirman crafted for me.

What's interesting is that nobody has yet noticed the mistake in my BBC Basic example...

I only just spotted it myself, when I ran the program again.  During test, I set the "limit" to 6100 (1 minute 1 second) so I didn't have to wait for 108 minutes to test the "beep every second" functionality.  I forgot to set this back to 648000 in my finalised PoC (I also included a 08 escape key sequence which won't be in the end program but that was left in on purpose as if it isn't in there you have an infinite loop program on your hands)

---

### Post by pp. on 2008-10-04
> **yoda2031 said:**
> What's interesting is that nobody has yet noticed the mistake in my BBC Basic example...

You explicitly stated in your first post that you were going to ignore anyone who said that the Basic program did not work. Hence, you have no way of knowing whether anyone has noticed any mistakes or not.

Anyway, what's the question?

---

### Post by yoda2031 on 2008-10-04
> **pp. said:**
> You explicitly stated in your first post that you were going to ignore anyone who said that the Basic program did not work. Hence, you have no way of knowing whether anyone has noticed any mistakes or not.

Anyway, what's the question?

Good point.  I forgot about that... I guess I only put in those conditions because I'm fed up of having this query met with unhelpful or unrelated responses.

The question is outlined in great deal at the top of my code now, which can be found here:
[http://dev.yoda2031.co.uk/lost/lost.c](http://dev.yoda2031.co.uk/lost/lost.c)

Basically, it doesn't behave as I expect it to and I kinda wanna know why not.  I've been through the code line-by-line about ten dozen times now, using ddd or my own brain.  I simply cannot see why the program doesn't work as intended as it stands.  I'm happy to be told I'm being an idiot, to the point where you could say "can be done like this:<insert 3 lines of extremely basic C code here>" and I wouldn't care - for my sanity's sake I need this problem solved!

---

### Post by pp. on 2008-10-04
> **yoda2031 said:**
> 
Basically, it doesn't behave as I expect it to and I kinda wanna know why not. 

The silly answer would be: Change the code so that it does what you want it to do.

What do you think your code ought to do, and what does it in fact do?

If you want anyone to help you, you should not make your case into a guessing game.

---

### Post by yoda2031 on 2008-10-04
*sigh* I thought I'd outlined it pretty clearly actually.  Especially if you actually read the code itself.

What I want it to do: count down from 108 minutes, accept input at any point without interrupting the countdown, reset the timer if the input string is "4 8 15 16 23 42", beep every second for the last minute and every 5 seconds for the last 5 minutes
What it does: counts down from 108 minutes but waits for input before updating the timer's output, behaves erratically when the "enter" key is pressed after input - I don't know if the beeping works, I've changed a lot since it last did work.

Is that clear enough for you, or do you want me to write a formal specification?

---

### Post by pp. on 2008-10-04
> **yoda2031 said:**
> Is that clear enough for you, or do you want me to write a formal specification?

Actually, a formal specification of the expected and the observed behaviour would be quite helpful, but for yourself and the debugging of your program-to-be rather than for me. According to the stringent requirements of your OP I might not be qualified enough to help you here.

> **yoda2031 said:**
> I thought I'd outlined it pretty clearly actually.  Especially if you actually read the code itself.

A bit of advice you did not ask for: If you want people to help you here, you'd better make it terrribly simple for people to understand your problem. Deriving the actual behaviour of your admittedly less-than-stellar code and comparing said behaviour with what we might suppose you could want it to do is a bit more work than even very helpful members are prepared to perform for your sake.

> **yoda2031 said:**
> 
What it does: counts down from 108 minutes but waits for input before updating the timer's output, behaves erratically when the "enter" key is pressed after input - I don't know if the beeping works, I've changed a lot since it last did work.

How do you know that it 'counts down'?
Can we assume that 'waiting for input' is unexpected behaviour?
What are we to understand what 'erratic behaviour' consists of? Does the screen turn purple, the keyboard issue greek letters or what?
How can we advise you on beeping if you have no idea whether it does or does not beep?
Is the code you have attached to an earlier post the same version as the one which exhibits the behaviour you are describing here?

Please understand that I know how to program and how to debug. I do not, however, program in C and I do not read programs written in Basic.

---

### Post by yoda2031 on 2008-10-05
The basic code is a proof of concept, it is there to show that what I want to achieve is possible.  If you don't want to read it - don't.

If you don't program in C, I don't really see what the point of you posting is.  You have so far simply told me that I have not been specific enough despite the comments in the code itself being EXTREMELY clear about what I want to achieve and how I think I'm doing it.  There's practically a comment per line.

And if you're going to say my code is "less than stellar" then the least you can do is tell me how to make it "stellar".  I do not mind being called an idiot but I do mind being called an idiot by someone who is not prepared to show me how I can improve.

How do I know it counts down? because after I press a key the output updates.  I thought I made that clear.  Waiting for input IS unexpected behaviour, reading the code should tell you this because I have if (is_key_pressed()) wrapped around my getchar().  Couldn't be simpler.

Erratic behaviour is my way of saying "I don't know how to describe this in less than a thousand words, if you want to know specifically what it's doing - compile and run it".  I don't need you to advise me on beeping.  The code I linked to in my earlier post is my working copy of the code.  The webserver at dev.yoda2031.co.uk is my personal computer.

Do you have any more questions, and could I please ask you treat me with a little more respect in future?  I can show you code that's a thousand times worse than mine in a project I offered to help - my help was refused on the grounds that I thought making the comments more understandable, the code more modular and the variable names more descriptive was as important if not more important than adding features.  If you care to deride my work, also be prepared to instruct me in how to improve it.

---

### Post by pp. on 2008-10-05
> **yoda2031 said:**
> If you don't program in C, I don't really see what the point of you posting is.

And if you're going to say my code is "less than stellar" then the least you can do is tell me how to make it "stellar". 

could I please ask you treat me with a little more respect in future?

You yourself commented on the quality of your code. I took your assessment at face value.

Since you seem to think that debugging a C program requires experience in coding to the C convention, I will grant you your wish.

Respectfully yours
pp.

---

### Post by yoda2031 on 2008-10-05
My assessment of the quality of the code is based on the fact I'm a self-taught 19 year old coder with no qualifications and little experience - coupled with the comments I've received from the users of ##c.  Criticism or praise of one's own work should never be taken at face value.

Thank you for your posts, and sorry for "having a go", I'm sure you can appreciate the frustration that coding problems can cause sometimes.

Granted, I was a little rash in saying the you needed to be able to program in C in order to help - but I am, regardless, struggling to find anything helpful in your posts. If I were to ask if you are intending to be unhelpful, would you take offence?

---

### Post by nvteighen on 2008-10-05
OK, I've seen your code and have some (I hope) constructive criticism:

1. You don't know what you want. No, not about the features, but about what you want the program behaive. The current code does exactly what needed: it takes input each second and **after** input has been received, it continues. That's reflected on the linear approach of your code: print the time, get input, react on input... it's a single sequence executed sequentially, not two sequences running at the same time parallelwise (one for the counter; the other for input).

For this, you possibly will need threads, which I don't know how to use them, but as far as I've seen, they seem fairly complicated: as you have to synchronize the threads and also give them a way to communicate between both. That way, you can make the "clock thread" react when the "input thread" has received some data and have both running simultaneously.

2. You're not initializing ncurses ever (initscr() and friends). Please, refer to the docs (/usr/share/doc/libncurses5-dev) and see what initializing procedure fits better to your needs (there are a lot of factors to look at... after initscr() you'll have to set some stuff up).

3. OK, you wanted to comment code... but you did it in excess... Usually, what I do is to comment at the beginning of the function what it does and what steps it takes and then just comment some lines where a bit deeper information is needed. That keeps comments unobstrusive.

4. Please, don't use global variables. Transfer them to main() and then pass them as arguments. Why? Because if you don't use any global variables, you know that only parameters and local variables will affect some function's behaivor and therefore, debugging gets very much easier, as you can isolate the problem. And this is the very reason why I hate ncurses, which relies on some hidden global variables to set the terminal.

5. Supirman helped you. OK... but do you understand what he did? There's nothing bad in asking for help, but if you want to learn, you should study (or ask him) what's going on his code.

---

### Post by yoda2031 on 2008-10-05
I've restarted with the project - it was become a tangled mess of workarounds anyway and I could do with starting on a clean slate with it.

---

### Post by pp. on 2008-10-05
> **yoda2031 said:**
> I'm sure you can appreciate the frustration that coding problems can cause sometimes.

Granted, I was a little rash in saying the you needed to be able to program in C in order to help - but I am, regardless, struggling to find anything helpful in your posts. If I were to ask if you are intending to be unhelpful, would you take offence?

No offense meant and none taken.

Have I posted anything meant to be helpful? Yes, I certainly have by offering you advice in how to proceed with a stuck project:
[LIST]
[*]Carefully state what you expect your code to perform
[*]Carefully state whatever you can observe your code to actually do
[*]When seeking help, make it as clear as you possibly can what your problem consists of (essentially the both points above).
[/LIST]
By implication, do not
[LIST]
[*]Lure your audience to an offsite server of unknown reputation
[*]Post just code and say "does't work"
[*]Answer with "read my bloody code" when someone asks particulars.
[/LIST]

What I have not yet told you:
[LIST]
[*]If stuck with a recalcitrant piece of code, remove everything not immediately related to the problem so that you can study the problem in its simplest form
[*]Liberally add debugging code even if it has to be beeps and strings written to the terminal
[*]Reduce your problem description to the barest bone.
[/LIST]

If you are still interested, you gave the most important information which will contribute to the solution in the post in which you replied to my answers:

> Waiting for input IS unexpected behaviour, reading the code should tell you this because I have if (is_key_pressed()) wrapped around my getchar(). Couldn't be simpler.

Without even glancing at your code I can tell you that your understanding of is_key_pressed() and - more importantly - of getchar() is not yet complete enough. You are working from the assumption that is_key_pressed() states if there has been a character placed into some buffer, and that the next invocation of getchar() will just fetch that character without blocking the process in which it is running.

I am not the first to point out here that your best strategy would be to re-read the documentation of the library which contains getchar(), with particular emphasis on the handling of keyboard buffers and blocking of processes.

---

### Post by pp. on 2008-10-05
> **yoda2031 said:**
> I've restarted with the project - it was become a tangled mess of workarounds anyway and I could do with starting on a clean slate with it.

IOW, it has become less than stellar?

:lolflag:

---

### Post by yoda2031 on 2008-10-05
Touche.

---

### Post by yoda2031 on 2008-10-05
Right, stuck again!  I started again using ncurses from the offset.  It's behaving a lot better, but...

```

WINDOW *input_window = newwin(1,20,1,0);
WINDOW *output_window = newwin(1,20,0,0);
wprintw(input_window,"foo");
wprintw(output_window,"bar");
/* output: foo */

```

why no bar?

---

### Post by yoda2031 on 2008-10-05
never mind, found the answer - didn't understand curses properly, I need a wrefresh(output_window) in there.

---

### Post by nvteighen on 2008-10-06
> **yoda2031 said:**
> never mind, found the answer - didn't understand curses properly, I need a wrefresh(output_window) in there.
Yeah, ncurses development is a set-refresh cycle.

---

### Post by yoda2031 on 2008-10-06
Solved.  Here's how I did it:

```

#include <stdio.h>
#include <stdlib.h>
#include <curses.h>
#include <time.h>
#include <string.h>
#include <unistd.h>

#define LIMIT 6481

int counter(WINDOW *output_window,time_t ctr_now,time_t ctr_start);
char my_wgetstr(WINDOW *from_where,unsigned int buffer_size,WINDOW *errors);
void output_hex(WINDOW *where,WINDOW *input);

int position = 0; /* THERE IS A DAMN GOOD REASON WHY THIS IS A GLOBAL */

int main(void)
{
  int rv = EXIT_SUCCESS;
  unsigned int buf = 200;
  time_t now = time(NULL);
  time_t start = time(NULL);
  time_t last_loop = time(NULL);
  WINDOW *screen = initscr(); /* warning: variable 'screen' is not used */
  WINDOW *output_window = newwin(1,22,0,0);
  WINDOW *input_window = newwin(1,20,1,0);
  WINDOW *errors_window = newwin(5,50,2,0);
  char *password = malloc(buf);
  int time_remaining = 0;
  char numbers[] = "4 8 15 16 23 42";
  int secs_remaining;
  int mins_remaining;
  int i = 0;
  halfdelay(5);
  noecho();
  mvwaddstr(input_window,0,0,">:");
  while (now-start<LIMIT)
  {
    i = 0;
    now = time(NULL);
    time_remaining = counter(output_window,now,start); 
    mins_remaining = time_remaining/60;
    secs_remaining = time_remaining%60;
    if (now-last_loop>=1 || time_remaining<=30)
    {
      if ((secs_remaining%5==0 && mins_remaining<=5) || mins_remaining<=1 || secs_remaining==0)
      {
        printf("\a");
      }
      last_loop=time(NULL);
    }
    password[position]=my_wgetstr(input_window,buf,errors_window);
    if (password[position+1]==0x7f)
    {
      password[position]=0x20;
      password[position+1]=0x20;
    }
/* -- debugging window output
    mvwprintw(errors_window,0,1,"%s",password);
    wrefresh(errors_window);
*/
    if (strstr(password,"\n"))
    {
      if (strstr(password,numbers))
      {
        if (mins_remaining<=1)
        {
          start=time(NULL);
        }
      }
      else if (time_remaining<=300)
      {
        wclear(errors_window);
        wprintw(errors_window,">: UNRECOGNISED COMMAND\n");
        wrefresh(errors_window);
        while (i<=position)
        {
          password[i++]=0x20;
        }
      }
      else if (strstr(password,"hanso"))
      {
        start=now-(LIMIT-60);
      }
      else if (strstr(password,"dharma"))
      {
        while (i<=position)
        {
          password[i]=0x20;
          i++;
        }
        output_hex(errors_window,input_window);
      }
      else
      {
        wclear(errors_window);
        wrefresh(errors_window);
      }
      while (i<=position)
      {
        password[i]=0x20;
        i++;
      }
      position=0;
      mvwaddstr(input_window,0,0,">:");
    }
    wrefresh(input_window);
  }
  wclear(input_window);
  wclear(output_window);
  wclear(errors_window);
  wprintw(output_window,"You are now stuck in an infinite loop.  Have fun!");
  refresh();
  while (true)
  {
    sleep(1);
  }
  endwin();
  return rv;
}

/* this function calculates the remaining time (from 108 minutes) and displays the output in output_window
 * the reason for the secs_remaining only being calculated in the last 5 minutes is due to the original
 * inspiration for the idea behaving in this way.
 * it also beeps once a second for the last minute and once every 5 seconds for the last 5 minutes
 */
int counter(WINDOW *output_window,time_t ctr_now,time_t ctr_start)
{
  int time_remaining = LIMIT-(ctr_now-ctr_start);
  int mins_remaining = time_remaining/60;
  int secs_remaining = 0;
  if (mins_remaining<=5) 
  { 
    secs_remaining = time_remaining%60;
  }
  mvwprintw(output_window,0,0,"Time remaining: %.3d:%.2d",mins_remaining,secs_remaining);
  wrefresh(output_window);
  return time_remaining;
}

/* I found it necessary to rewrite the wgetstr function as it seems to be blocking regardless of my halfdelay() setting
 * this function does the exact same thing as wgetstr() only it returns a char * instead of filling a passed argument's
 * array.  Pretty self-explanatory how I'm doing it.
*/
char my_wgetstr(WINDOW *from_where,unsigned int buffer_size,WINDOW *errors)
{
  int returnvalue = 0;
  int temp_returnvalue=0;
  temp_returnvalue=mvwgetch(from_where,0,position+2);
  switch (temp_returnvalue)
  {
    case ERR:
      break;
    case 0x7f:
    {
      if (position<1) { break; }
      wprintw(from_where,"\b \b");
      returnvalue=0x7f;
      position--;
      break;
    }
    case 0x0a:
    {
      returnvalue=0x0a;
      wmove(from_where,0,0);
      wclrtoeol(from_where);
      mvwaddstr(from_where,0,0,">:");
      wrefresh(from_where);
      break;
    }
    default:
    {
      returnvalue=temp_returnvalue;
      waddch(from_where,returnvalue);
      position++;
      break;
    }
  }
/* -- debugging window output
  mvwprintw(errors,0,0,"%d",position);
  wrefresh(errors);
*/
  return returnvalue;
}

void output_hex(WINDOW *where,WINDOW *input)
{
  int i = 0;
  int hex_values[44] = { 0x53, 0x6F,
                          0x6D, 0x65, 0x74,
                          0x69, 0x6D, 0x65,
                          0x73, 0x20, 0x61,
                          0x20, 0x50, 0x6F,
                          0x6C, 0x61, 0x72,
                          0x20, 0x42, 0x65,
                          0x61, 0x72, 0x20,
                          0x69, 0x73, 0x20, 
                          0x6A, 0x75, 0x73, 
                          0x74, 0x20, 0x61, 
                          0x20, 0x50, 0x6F, 
                          0x6C, 0x61, 0x72,
                          0x20, 0x50, 0x65, 
                          0x61, 0x72, 0x00 };
  char testin;
  wclear(where);
  wprintw(where,">:");
  while (i<44)
  {
    testin=wgetch(input);
    if (testin==ERR)
    {
      wprintw(where,"%.2x ",hex_values[i++]);
      wrefresh(where);
    }
    else
    {
      wclear(where);
      wprintw(where,">:\n>:[BRK]");
      wrefresh(where);
      break;
    }
  }
}

```

For those of you who are interested :)

For those who aren't - well, why did you read this far then? :P

---

### Post by pp. on 2008-10-06
I am happy to see that you have become unstuck, twice. I sense some pride in your last post. Cheers!

---

### Post by mssever on 2008-10-06
> **yoda2031 said:**
> ```
int position = 0; /* THERE IS A DAMN GOOD REASON WHY THIS IS A GLOBAL */
```
A suggestion: There may well be a good reason for this (I haven't read your code carefully), but this comment isn't very useful. It'd be much better to explain your reason in the comment. Other people who read your code can't read your mind.

---

