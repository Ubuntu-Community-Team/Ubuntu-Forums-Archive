---
title: "How do I get the \b char to appear?"
date: 2010-02-24
forum: Programming Talk
---

### Post by vik_2010 on 2010-02-24
I'm going through the K&R C book, and started doing the problems. One of the early problems ask for a program that takes any input and prints it back, with all indents, backspaces, and \-characters revealed. Simple enough, this is what I provided.
[PHP]
//Exercise 1.10
//This answer appears to be correct, but how do you get the \b character to appear on screen?
#include <stdio.h>

int main(void) {
    int input;
    
    while ((input=getchar())!=EOF) {
        if (input=='\t') {
            putchar('\\');
            putchar('t');
        }
        else if (input=='\b') {
            putchar('\\');
            putchar('b');
        }        
        else if (input=='\\') {
            putchar('\\');
            putchar('\\');
        }
        else
            putchar(input);    
    }
}
[/PHP]My question is: how do you actually get the \b character to appear on screen. Simply typing a sentence ("hello world") deleting the last character(s) before hitting enter doesn't do the trick; the program just spits out your truncated sentence back out at you. How do you actually get the backspace  character to print out.

Also: The first Qs in K&R have while (XX != EOF) loops. Since you can never actually print an EOF char -- EOF is specially chosen so as to be unprintable(i.e. its a negative number where all chars are a subset of unsigned integers, no?) doesn't this just mean that the loop goes forever.

Thanks. :):)

---

### Post by Simon17 on 2010-02-24
> **vik_2010 said:**
> 
How do you actually get the backspace  character to print out.


The console handles things like backspaces and arrows keys, so they don't get sent to your program. If you want to capture every keystroke, you need to set the correct terminal mode. Research termios.

> 
(i.e. its a negative number where all chars are a subset of unsigned integers, no?) doesn't this just mean that the loop goes forever.


The first part is correct. However,
```
int input;
```
That's why input is an int and not a char.

---

### Post by ssam on 2010-02-24
i think you do need to use int
[http://en.wikipedia.org/wiki/C_file_input/output#The_EOF_pitfall](http://en.wikipedia.org/wiki/C_file_input/output#The_EOF_pitfall)

to the challenge it to type in a backspace. i think the problem may be that the terminal will react to the '\b' char by deleting the last character. so if you type
```
helloo\b\n
```
your program is passed
```
hello\n
```
i think some old systems did not do this automatically. there are some compatibility options in gnome-terminal, which may help.

or you could write a text file with a '\b' in it. i made one in vim by writing 'hello' and running
```
:s/o/o\bo/
```
i have attached the file (had to put it in a tar.gz, forum complained the text file was invalid).

if you output the test file with
```
cat test
```
then it just says
```
hello
```
if you look at it in a text editor you will see the backspace char.
if you pipe it to your program then you should see the '\b'

---

### Post by vik_2010 on 2010-02-25
thanks to both of you.

---

