---
title: "[Python] Force exclude keystokes, python newby"
date: 2008-10-11
forum: Programming Talk
---

### Post by dodle on 2008-10-11
I am looking for a way to prevent users from being able to use certain keys.[PHP]user_input = raw_input("Type something here: ")[/PHP]Let's say I don't want the user to be able to use any vowels.  So every time he/she tries to input "a", "e", "i", "o", or "u", nothing happens.  Is there a way to do this?

---

### Post by LaRoza on 2008-10-11
That is called input masking.

Terminal apps typically don't do it. It is common in GUI's though.

---

### Post by gomputor on 2008-10-11
> **LaRoza said:**
> That is called input masking.

Terminal apps typically don't do it. It is common in GUI's though.
I don't think the OP is talking about input masking. As I see it, he means something like a Text Entry in a Gui App that lets you enter only numerals or letters, something like that.


With a gui you can do that, but with raw_input the user has to press the RETURN key first and then work with what he/she typed.

So if you want to give him an error message or something like that (after he hit the Return key), you can do something simple like this:
```
user_input = raw_input("Type something here: ")

for ch in user_input:
    if ch in 'aeiou':
        # if the input has vowels
        # your code goes here
```

Now if you want to get what he/she typed minus the vowels (or whatever), you can do something like this:
```
user_input = raw_input("Type something here: ")
user_input = ''.join([ch for ch in user_input.lower() if not ch in 'aeiou'])

# >> Type something here: Hello there
# >> print user_input
# Hll thr
```
But again it depends on what's your purpose is.

---

### Post by LaRoza on 2008-10-11
> **gomputor said:**
> I don't think the OP is talking about input masking. As I see it, he means something like a Text Entry in a Gui App that lets you enter only numerals or letters, something like that.

With a gui you can do that, but with raw_input the user has to press the RETURN key first and then work with what he/she typed.


I was given information on IRC about the query.

I think this is best done with ncurses, and the person who was writing code with this purpose agrees. It is possible with ncurses and a little work.

---

### Post by gomputor on 2008-10-11
> **LaRoza said:**
> I was given information on IRC about the query.

I think this is best done with ncurses, and the person who was writing code with this purpose agrees. It is possible with ncurses and a little work.
Yes, if you're working on Linux you can use the curses module and probably you can achieve it. Maybe you can do it also if you incorporate some C or c_types, but that's something beyond me and most obviously beyond the OP :).

---

### Post by y-lee on 2008-10-12
> **LaRoza said:**
> I was given information on IRC about the query.

I think this is best done with ncurses, and the person who was writing code with this purpose agrees. It is possible with ncurses and a little work.

And that might have been me talking about this problem. :)

Anyway Python lacks direct support for single character input in "text mode", terminals and such. And certainly pycurses provides many functions allowing for GUI like programming in a CLI environment. There are also other modules one can find to make using the curses module a bit easier. BTW most GUI libraries provide some support to capture key press events which is what the OP needs here, so this problem is better suited for a GUI  or a curses application.

But anyway here is a simple hacked up mess without using curses to accomplish what should be a rather simple goal.

[PHP]
#!/usr/bin/env python

#***************************************************************************
# *   input.py     A simple and flawed replacement for raw_input            *
# *                                                                         *
# *   This program is free software with no restrictions whatsoever placed  *
# *     upon it use, misuse, or distribution.                               *
# *                                                                         *
# *   This program is distributed in the hope that it will be useful,       *
# *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
# *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.                  *
# *                                                                         *
# ***************************************************************************

import sys, tty, termios

#   This function reads a single character off of stdin
#       waiting till a key is pressed

def getchar():
    # This is Unix/linux specific code & will not work in Windows or other OSes
    fd = sys.stdin.fileno()
    old_settings = termios.tcgetattr(fd)
    try:
        tty.setraw(sys.stdin.fileno())
        ch = sys.stdin.read(1)
    finally:
        termios.tcsetattr(fd, termios.TCSADRAIN, old_settings)
    return ch

#   This function is a response to backspace being pressed
#   input s is a list of characters entered so far the last character is deleted
#   The cursor then moves back one space and erases the character there

def backspace(s):
    if len(s) != 0:
        s.pop()
        sys.stdout.write('\b')
        sys.stdout.write(' ')
        sys.stdout.write('\b')

#   The instr function is a simple somewhat buggy replacement for raw_input
#
#   it displays a prompt & doesn't accept any character in the list except_list
#   If show is True characters are echoed to the screen and if not they are not
#       this latter case is useful for passwords
#   if newline is True the cursor advances to the beginning of the next line
#       and if False the cursors position remains at its last position.
#
#   Note also Ctrl+C is disabled in a sense: it will be inputted and displayed

def instr(prompt = '', except_lst = [], show = True, newline = 'True'):

    # initialize some variables and print prompt
    s =[]
    ESC = chr(27)
    sys.stdout.write(prompt)
    ###   Process key press, echo result if show is true & it is an allowed char
    #     when enter is pressed we are done
    done = False
    while not done:
        c = getchar()
        new = []
        if c == '\r':
           done = True
        else:
            if c not in except_lst:
                if c == '\x7f':
                    backspace(s)
                else :
                    new += c
                    if show  and c != ESC:
                        sys.stdout.write(c)

        ############## WARNING UGLY HACK FOLLOWS ############################
        #                                                                   #
        #   A hack to disable inserting control characters for arrows       #
        #   as well as insert, del, home, end, pageup and page down         #
        #   This method has a Known bug that if user presses Esc key then    #
        #       the nest two key strokes will be ignored !!                 #
        if ESC in new:                                                      #
            getchar()                                                      #
            c = getchar()                                                   #
            if c in ['2','3','5','6']: getchar()                            #
        else:                                                               #
            s += new                                                        #
        #                                                                   #
        ##############  End of ugly hack and while loop   ###################

    # If new line is true move cursor to next line
    if newline:
        sys.stdout.write('\n\r')

    # Make a string out of our list of characters and return that string
    result = ''
    for ch in s:
        result += ch
    return result

#   Code to test functions
#
if __name__ == '__main__':

    name = instr("Enter name ")
    print name
    password = instr("Password ", show = False)
    print password
    reject =['a','e','i','u']
    ins = instr('Enter anything, does not allow aeiu :', reject)
    print ins

# ---       On second thought, let's not go to Camelot. It is a silly place.
[/PHP]

A few notes on this code it is sloppy and nothing I am proud of :(

It does allow the *backspace* key to be used in a natural way **but** *home* and *end* and *left* and *right* arrow keys and *delete* are ignored (hopefully).

The **Ctrl-C** combo does not act in a natural way, it will be printed and returned in the inputted string.

This code is not portable and will not work in windows or other OSes (and that includes Mac OS as far as I know). A google search can find a solution to making this more portable btw. Knock yourself out if ya want to implement that. :)

I make no guarantee this code will even work on all Linux systems as the **ugly hack** part of this code uses some *magic numbers* that may be possibly hardware dependent :confused:

It should be possible tho to alter this code so that *Home* *Delete* *Insert*  *End* and Arrow keys all work as expected. Briefly one would need a getchar like function that did not wait till a key was pressed to use in the Ugly hack. And maybe make use of something like [tput]("http://www.bigwebmaster.com/General/Howtos/Bash-Prompt-HOWTO/x405.html") to control cursor location as well as keeping track in the input list of the current character location. On second thoughts maybe tput is overkill and one could simple write blanks over the displayed string when it is edited and reprint it. Note sys.stdout.write('\r') will move the cursor to the beginning of the current line. 

Well regardless this is as much thought as I am putting into this now and I plan on reimplementing this kind of thing using curses  just for the fun and experienced of it. As soon as I have time that is. Any improvements to this code would be appreciated of course and any comments about it not working correctly will be promptly ignored unless they come with a patch :lolflag:

---

