---
title: "what's the difference between EOF in a file &amp; EOF entered through a terminal?"
date: 2011-12-01
forum: Programming Talk
---

### Post by ask_ on 2011-12-01
Hello,

I am a beginner to C programming and Ubuntu/Linux in general. Trying out simple programs on terminal.

when giving keyboard input via terminal to a C program(or any shell command for that matter) , when I wish to enter EOF,  after pushing ctrl  + D, I have to do so twice/thrice in case previous character wasn't a newline. While if previous character is newline, ctrl + D is accepted straightaway. Can someone explain this behavior?


Note - I had a problem with EOF in a file as the title suggests, but it got solved.Keeping only that problem which is unsolved.Hence title maybe a bit misleading. :(

---

### Post by F.G. on 2011-12-01
I didn't think that you could enter C via the terminal? if you can clarify i would love to know what you mean.  do you mean entering C at the command prompt?

-> edit i think i see what you mean, but i think that ctr+c or ctr+d or ctr+z (if you're using python) aren't EOF characters, they're interrupts from the environment that kill the process, rather than a character that the program reads and processes.

---

### Post by bikewrecker on 2011-12-01
try ctrl + Z? Are you sure your program has a catch to make sure that if you type the EOF character it exits the program?

---

### Post by ask_ on 2011-12-01
> **F.G. said:**
> I didn't think that you could enter C via the terminal? if you can clarify i would love to know what you mean.  do you mean entering C at the command prompt?

-> edit i think i see what you mean, but i think that ctr+c or ctr+d or ctr+z (if you're using python) aren't EOF characters, they're interrupts from the environment that kill the process, rather than a character that the program reads and processes.

I am using bash. But even if it is interrupt signal, why do I have to press ctrl+D twice in a case when I am on same line but once when I am on newline ?

---

### Post by ask_ on 2011-12-01
> **bikewrecker said:**
> try ctrl + Z? Are you sure your program has a catch to make sure that if you type the EOF character it exits the program?

I had written a simple code to count characters in the input.
I then gave input via terminal. I wanted to see what happens when input is exactly 1 character. After pressing the single character I have to press ctrl+D twice. As some have pointed out ctrl+D may not be exactly EOF , but rather interrupt signal. But when a newline is entered, ctrl+D needs to be pressed once. This is not the case with just this program, whatever programs I have tried out from terminal this seems to be the case.


```
#include <stdio.h>

int main(void)
{
	int c, i;

	i = 0;
	while((c = getchar()) != EOF)
	 	i++;
	printf("value of i is %d\n", i);
	return 0;
}
	
```

note - Whenever I used a file as input a peculiar thing happened. I simply kept 1 charater in the file. But in some 1 character files, the program counts input as 1 character,in some 1 character files  as 2 character.This was the other half of the problem which I edited out of 1st post,since in some cases it gives proper output. But this behavior also seems odd.

---

### Post by F.G. on 2011-12-01
i think your issue is to do with whitespace characters and escape sequences, sorry i don't know why it is. this may also change from OS to OS (although i think in linux it should all be the same). i think maybe some methods of saving put EOF on a new line.

edit->maybe when you press 'enter' you append \n and \r , rather than just \n like most saved text files, i think windows uses \n\r (newline + return carriage)rather than just \n for newlines, maybe this is happening??

---

### Post by ask_ on 2011-12-01
It is common practice that a file ends with a newline. Hence EOF is mostly expected after a newline. But this isn't binding, and I am flummoxed , why the file input is acting weirdly.

Sometimes, it gives character count as 2 sometimes as 1.

(I simply type 1 character in the file, save it and exit, no newline,no escape sequences.)

Here is what I found on wikipedia when I searched for EOF, 
> In UNIX and AmigaDOS, the translation of the keystroke to EOF is performed by the terminal driver, so a program does not need to distinguish terminals from other input files. By default, the driver converts a Control-D character at the start of a line into an end-of-file indicator. [http://en.wikipedia.org/wiki/End-of-file](http://en.wikipedia.org/wiki/End-of-file)

So, the start of line is necessary in some sense for it to function properly?

---

### Post by gardnan on 2011-12-01
Control - D does not map to end of file directly. Basically, it flushes the line input buffer for the terminal into the programs stdin file. So, if a program is reading stdin, and the user presses control - D after typing something, whatever they typed is then given to the program, but if it is an empty input line, then the attempt to read the file returns 0 bytes read, which will cause the program to interpret it as an EOF.

The first answer on this thread did a better job of explaining it.

[http://stackoverflow.com/questions/1516122/how-to-capture-controld-signal](http://stackoverflow.com/questions/1516122/how-to-capture-controld-signal)

---

### Post by ask_ on 2011-12-01
> **gardnan said:**
> Control - D does not map to end of file directly. Basically, it flushes the line input buffer for the terminal into the programs stdin file. So, if a program is reading stdin, and the user presses control - D after typing something, whatever they typed is then given to the program, but if it is an empty input line, then the attempt to read the file returns 0 bytes read, which will cause the program to interpret it as an EOF.

The first answer on this thread did a better job of explaining it.

[http://stackoverflow.com/questions/1516122/how-to-capture-controld-signal](http://stackoverflow.com/questions/1516122/how-to-capture-controld-signal)

Thanks. That cleared the garbage from my own mental buffer :) !!

---

### Post by Bachstelze on 2011-12-01
> **bikewrecker said:**
> try ctrl + Z? Are you sure your program has a catch to make sure that if you type the EOF character it exits the program?

There is no such thing as an "EOF character".

---

### Post by F.G. on 2011-12-01
> **Bachstelze said:**
> There is no such thing as an "EOF character".

can you explain?

---

### Post by Bachstelze on 2011-12-01
> **F.G. said:**
> can you explain?

In what way? If you want to know what EOF is in C, it is the value some input functions, for example getchar(), return where they are at the end of the file and there are no more characters to be read. Almost by definition, it can't be a character, since it precisely means that there are no characters to read.

---

### Post by Bachstelze on 2011-12-01
From Wikipedia (already quoted above, emphasis mine):

> In UNIX and AmigaDOS, the translation of the keystroke to EOF is performed by the terminal driver, so a program does not need to distinguish terminals from other input files. By default, the driver converts a **Control-D character** at the start of a line into an **end-of-file indicator**. 

Control-D is a character (namely, [EOT](http://en.wikipedia.org/wiki/End-of-transmission_character)). When the terminal (not the program!) reads this character, it tells the program that there is no more input, in whatever way this is done in the OS in question, and getchar() returns the special value EOF.

---

### Post by F.G. on 2011-12-01
really, i thought it was something like '\0' rather than \n or \r\v\t\a or anything else escapee. then again i'm probably wrong.

---

### Post by Bachstelze on 2011-12-01
Of course not. '\0' is the NUL character, and it is perhaps the most common character in anything that is not a plain text file, so if it was treated as meaning "end of file", things would go havoc pretty quickly. ;)

---

### Post by F.G. on 2011-12-01
you're right, of course \0 is null. i have am interview for a job tomorrow (were talking ruby python tcl sql c and c++, and linux, i should be fine, but...), i think everything i've ever known is falling apart, piecmeil. 
hopefully i will still remember my name.

---

### Post by 11jmb on 2011-12-01
> **F.G. said:**
> you're right, of course \0 is null. i have am interview for a job tomorrow (were talking ruby python tcl sql c and c++, and linux, i should be fine, but...), i think everything i've ever known is falling apart, piecmeil. 
hopefully i will still remember my name.

Relax. I have been on both sides of the interview table plenty of times, and in my experience, there is rarely enough time to get into technical details like that. If they do have time to grill you a bit, a good interviewer will opt for the "is this person a good critical thinker/problem solver" type question over the "does this person understand every detail" type question.

Not to say that it is not worthwhile to develop a deep understanding of the finer points of your language of choice.

---

