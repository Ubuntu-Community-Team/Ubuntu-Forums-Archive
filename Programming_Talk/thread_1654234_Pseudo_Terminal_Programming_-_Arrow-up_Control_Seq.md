---
title: "Pseudo Terminal Programming - Arrow-up Control Sequence"
date: 2010-12-28
forum: Programming Talk
---

### Post by ierosvin on 2010-12-28
Hello!

Does anyone know what control sequence should be given to the terminal when arrow-up is pressed? So that i can access the previously executed commands.

thanks!

---

### Post by worksofcraft on 2010-12-28
> **ierosvin said:**
> Hello!

Does anyone know what control sequence should be given to the terminal when arrow-up is pressed? So that i can access the previously executed commands.

thanks!

ESC[A is cursor up

you can find them all [on this wiki page]("http://en.wikipedia.org/wiki/ANSI_escape_code")

---

### Post by nvteighen on 2010-12-28
I just want to note that the most portable way to do this is by using ncurses. Otherwise, you'll probably be writing terminal-specific code.

```

/* Compile using (assuming the filename to be up.c):
 * gcc -o up up.c -Wall -Wextra -pedantic -std=c99 -lcurses 
 */

#include <curses.h>

int main(void)
{
    /* I tend to avoid relying on the functions that modify stdscr implicitly. I
     * prefer to get the pointer from initscr and modify everything using
     * that... which points to same place to stdscr, btw :P */
    WINDOW *my_scr = initscr();
    (void)keypad(my_scr, TRUE); /* This does the key mapping trick */
    (void)nl(); /* Forcing NL -> CR/LF translation */
    (void)cbreak(); /* Disable line-buffering */
    (void)echo(); /* Turn echo on */

    waddstr(my_scr, "Press q to exit\n");
    wrefresh(my_scr);

    int input = 0;
    while((input = getch()) != 'q')
    {
        if(input == KEY_UP)
            waddstr(my_scr, "Up!");

        waddstr(my_scr, "\n");
        wrefresh(my_scr);
    }

    (void)endwin();

    return 0;
}

```

---

### Post by ierosvin on 2010-12-28
hey,

> **worksofcraft said:**
> ESC[A is cursor up

you can find them all [on this wiki page]("http://en.wikipedia.org/wiki/ANSI_escape_code")


thanks for your reply. by the way, ESC[A is the control sequence that the terminal gives back to you. Am i right?

But anyway i tried giving ESC[A, that is 033 [ A, to the terminal but it behaves like how tab key behaves:

$ <tab pressed>
Display all 1633 possibilities? (y or n)

$ <arrow-up pressed with value sent as ESC[A> 
Display all 1633 possibilities? (y or n)

Any thoughts? :p

---

### Post by trent.josephsen on 2010-12-28
Don't do that.  Use nvteighen's suggestion if you need to capture specific keystrokes in a program; otherwise, forget about it.  Different programs, and even the same program operating in different modes, will handle the same keystrokes differently; ncurses is just about the only portable way to handle them consistently.

---

### Post by ierosvin on 2010-12-29
> **trent.josephsen said:**
> Don't do that.  Use nvteighen's suggestion if you need to capture specific keystrokes in a program; otherwise, forget about it.  Different programs, and even the same program operating in different modes, will handle the same keystrokes differently; ncurses is just about the only portable way to handle them consistently.

actually, im not going to use his suggested solution ( thank you though for the code/suggestion :p ) cause lets just say i have my own key mapping. all i want to know is the exact escape/control sequence being sent to the terminal when we press arrow-up,say in Konsole or LXTerminal. and sending ^[A is apparently not the right way to do it.

help please. :confused:

---

### Post by ierosvin on 2010-12-29
got it guys! the way to it is to send the control character ^[A to the terminal. Then the terminal will send back the next command in your history. 

cheers!

---

### Post by nvteighen on 2010-12-29
Wait a second, in which language are you doing this? The only way to access the shell's history would be using the shell's own scripting language.

If that's what you're trying, then I can see why my code is useless for you.

---

### Post by Arndt on 2010-12-29
This won't get you further than before, since you already know that you get ^[[A when you press uparrow, but one way of finding out what the keyboard gives you is to run the program 'script', then 'cat', and then input things.

When you're done, give end-of-file and look in the file "typescript" (using a serious editor) what was actually received. ('cat' will probably echo those things visibly anyway, without 'script', but one never knows.)

---

### Post by trent.josephsen on 2010-12-29
What I was trying to say is that if you depend on arrow-up mapping to a particular control sequence, you'll likely be foiled when trying to run the same program under different terminals.  "^[[A" is not universal, and though it may be an appropriate hack for the here-and-now, it's likely to bite you sooner or later.

Dare I ask, if you're trying to access history, why don't you just press the up-arrow key instead of worrying about the control characters it sends to the terminal?  What are you actually trying to do?

---

