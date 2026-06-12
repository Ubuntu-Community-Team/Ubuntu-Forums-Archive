---
title: "Working on a textual C game, run into some problems"
date: 2005-07-27
forum: Programming Talk
---

### Post by N'Jal on 2005-07-27
Ok So i am really getting down to some serious programming, but i hit a snag with the C atoi() function, if you have ever played the final fantasy games you will understand the menu driven battle options, i am trying to mimic this type of interface but on the command line... for now. 

However since i have around 400 lines of code so far, and many problems, (one of which is that you can only take one turn so far, before the program exit's i will post that later) i will not post all the source, only where i am having problems.

I am writing this in C under the Apple Mac XCode compiler (since i am on vacation i couldn't bring my desktop, but rest assured as soon as i get home, it'll be back to anjuta).

Ok problem number one...

I need to get the player to choose either option 1, 2 or 3. This you can do (i use switch/case), and if you enter any other number it loops, but the problem begins when you enter a character so i figure that i can use the atoi() function to convert the letters to numbers but im not having much luck... So here's the code im using so far...

```

//game stats
int temp=0;
char choice[2];           //*1

while (temp < 1 || temp > 3)
//while loop to prevent the user from missing a go
//notes: need to create add the atoi function to prevent characters messing up the loop    *1
		{
			printf("Enter a choice:");
			scanf("%d", &temp);
			//getchar(temp);
			temp = atoi(choice);        //*1
		}

```

I beleive that's all the code that's needed for the function, as i said please remember i have 400 lines of code, once it's remotly working i'll post the full source. 


If i havn't made myself clear i wish i could say i don't speak native english, but i do, born in england, my brain just works very differently. If i need to clear things up i will.

Thanks

---

### Post by amohanty on 2005-07-28
> printf("Enter a choice:");
			scanf("%d", &temp);
			//getchar(temp);
			temp = atoi(choice);        

Err... dont mean to sound facetious, but where are you populating _choice_, it has garbage and atoi(<garbage>)  I believe is quite undefined. O:) 


AM

---

### Post by N'Jal on 2005-07-28
Um well thats the problem isn't it, if i knew what i was doing i would have done it :P. I was under the impression that the atoi function worked like this...

int one = 0;
char two[4];

gets(two);
one = atoi(two);

Or the other way round. Could you explain how it works? I have a book at home that helps me remember how to use it, however home is at least 4211 miles  away right now.

I need to have a fool proof method of making a choice, to stop the program running away.

Is it something as simple as giving two a value before use?

---

### Post by amohanty on 2005-07-28
> **N'Jal]
int one = 0 said:**
> ;

gets(two);
one = atoi(two);


Should work fine.
Some docs:
[http://www.keil.com/support/man/docs/c166/c166_atoi.htm](http://www.keil.com/support/man/docs/c166/c166_atoi.htm)

AM

---

### Post by ep_ on 2005-07-29
scanf is designed to take structured, formated input and isn't a safe choice for user input because its hard to do error recovery and there is no telling what a user might input.

For a detailed explanation, refer the [C FAQ](http://www.eskimo.com/~scs/C-faq/top.html)   

Here's a slightly improved version of your code:

```
    int temp = 0;
    char choice[100] = "";
    /* note: sizeof choice is 100 */

    while (temp < 1 || temp > 3)
    {
        printf("Enter a choice: ");
        if (fgets(choice, sizeof choice, stdin) != NULL)
            temp = atoi(choice);
    }

    printf ("Your choice was %d\n", temp);

```


Note, now the last character (not the null terminator) in the 'choice' buffer is a new line character '\n'.  It was not necessary to remove it for the call to atoi() but in other cases it might be. The technique to do so is fairly simple.

A better version would of verified that there is indeed a '\n' in the string given by the 'choice' buffer   If not, then the stupid user typed too many characters and you'd need to clear standard input.

Here is an [example of bullet proof integer input](http://home.att.net/~jackklein/c/code/strtol.html) which  expounds on the points alluded to above.

---

### Post by N'Jal on 2005-07-29
Ok that code worked, but i don't understand what it's done, i presume that fget is an input method thats better than scanf, getchar and gets?

Could you break it down a little bit for me? I would like to know my code inside and out, it's how i work, i feel like i am cheating of i don't understand everything.

```
if (fgets(temp, sizeof temp, stdin) != NULL)
```

So 

if (get input(varible to pass input into, size of string, standard input) not equal to nothing)

Is that close to it?

Also can you explain to me why it does what it does? If i don't understand somethings purpose then i have trouble using it.

---

### Post by ep_ on 2005-07-29
I  pointed out why there are better alternatives to scanf in this case.  As for gets, it is simply [evil](http://home.att.net/~jackklein/ctips01.html#safe_gets), never use it!

Yes, [fgets](http://www.cplusplus.com/ref/cstdio/fgets.html) is an input function, it reads a line of data from an external source. 'stdin' is the standard input stream (it is usually the keyboard). Functions like get and getchar read from 'stdin' by default. However, you must explicitly tell fgets to use it as it can also be used to read lines from a plain ol file and lots of other devices (everything is a file in C).

fgets is a function, it expects certain parameters and it returns a value. It reads lines, so it must have a place to put the data, right?  Hence, the first parameter is a pointer to a char buffer and that is where fgets will put the data for us.  We can't go passing it an int called 'temp' here or the compiler will balk, cuss and complain.  The second parameter tells fgets how many characters our buffer will hold, this prevents fgets from overrunning the buffer in case it happens to read an extremely long line of data. (Note, gets does not have this same buffer overrun protection and evil hackers can use this to their advantage.)  'choice' was dimensioned to 100 in the above example and that's what we passed as our second parameter.  We just did it in a tricky way, using the 'sizeof' keyword. (more flexibility).  The third parameter is defined for us in stdio.h, as i mentioned it is the standard input stream, usually the keyboard.

Checking the return value of fgets is good form.  On success, fgets simply returns a char pointer to the string read.  In the example above, it returns a pointer to the 'choice' buffer.  However, on failure or end of file (EOF) fgets will return NULL. I think of this as zero but using 'NULL' lets us know we're referring to a pointer data type. 


Again this is all covered more throughly in the [FAQ](http://www.eskimo.com/~scs/C-faq/top.html) if that's not in over your head.

This is a bit better (include stdlib.h)
```

    int temp = 0;
    char choice[100] = "";
    /* note: sizeof choice is 100 */

    while (temp < 1 || temp > 3)
    {
        printf("Enter a choice: ");
        if (fgets(choice, sizeof choice, stdin) != NULL)
            temp = atoi(choice);
        else
        {
            fprintf(stderr, "Unexpected Input Error, Bailing out");
            exit(EXIT_FAILURE);
         }
    }

    printf ("Your choice was %d\n", temp)
```;

-- ep

---

### Post by N'Jal on 2005-07-30
Thank you! I'm not new to programming, i have endured two years of my introduction to programming in VB *shudders* so i decided to learn something that i found easier, the whole visual thing confused me too early on, so C being very text based is easier for me.

Also thank you for even the way you explained it, it's a lot like the book im reading (or rather would be reading if i had thought to bring it with me on holiday). C for dummies, tis great. I was about to post my second problem 2day, but late last night the answer came to me, and is was a really stupid mistake that quite frankly now realising what it was would be embaressing... kinda like my crap spelling.

So thank you, i can assure you that this isn't that last time i'll post here, im sure i will have more problems, but for now, i'll see what i can do, and will have a look at those links.

---

### Post by N'Jal on 2005-08-01
Ok i have almot finished the first mile stone here, the two characters (player and computer) each take turns unfortunatly i cannot change the switch case behavior yet, still learning, and for some strange reason my while do-loop states that it should only happen while both characters current hp s above 0 or the escape option is selected, however both characters fight each other, and once the weaker has been destroyed it stop's taking it's turn, however the character still 'alive' continues to attack, while this make good TV, on the terminal it's rather dull.

I will upload my code tomoro (bit late now to compress it all etc) since i am very happy to have written all but one line, i would appriciate it if the code wasn't written for me, more if you could point out where my error's might be.

Once the swich case and the continued attacking is complete that will be the first mile stone complete, mile stone two will comence, and while i do not know what it is yet im sure it'll come to me.

---

### Post by N'Jal on 2005-08-01
Source code, compiled on a G4 iBook running Mac OS X Tiger. Simply because i don't have access to my linux box

EDIT: Another quick question, is there a C function to clear the screen? That would make life easier. I have googled and tryed system("cls"); but i think thats windows only and cls(); this has not worked on either my Mac or Ubuntu box.

---

### Post by Stuka on 2005-08-02
In Linux, text screen manipulation is usually handled through the ncurses library, though I'm fairly sure some guys I used to talk with regularly knew all sorts of crazy ANSI escape codes including ones that would clear the screen.

---

### Post by N'Jal on 2005-08-02
Yes i have heard of the ncurses library do i just #include it? And is it native to mac too? Since that the dev platform i have atm.

EDIT: Ok i now have what i am happy with as a first mile stone, lots of things still needed to implement but i am 2-3 days ahead of schedule, i figured i would still be on the first mile stone on the plane home. If anyone want's to check it out, if so please do not rip off my code, It's GPL, It's also really only an introduction to the C language, but if i can make something of it i would like to.

---

### Post by ummo on 2005-08-03
Hello N'Jal
I am pretty new to programming myself and have been working on my own text-based program.  I have been looking into writing code that does similar things that the ncurses lets you do , like take over the entire terminal screen, and animate it or refresh its contents without generating extra lines and lines of output that would cause the contents of the screen to scroll up.  

Like you i want to have a good grasp of what the code i am using is doing.  Although using ncurses would give me the effects i want, i feel that i wouldn't learn much other than learning how to use ncurses and i wouldn't know what ncurses is doing behind the scenes.  After a couple of days of searching i havent found any of ncurses' secrets but i have found some things about the ANSI escape sequences that were also mentioned by Stuka that provide similar results.

Here are two pages that have listings of the escape sequences and what they do.  Some of them are pretty cryptic but there are sequences for changing the text colors, clearing the screen and moving the cursor around the screen.  check em out:
[http://www.bluesock.org/~willg/dev/ansi.html](http://www.bluesock.org/~willg/dev/ansi.html) 
[http://astronomy.swin.edu.au/~pbourke/dataformats/vt100/](http://astronomy.swin.edu.au/~pbourke/dataformats/vt100/)

I am using python to so i dunno if my advice is relevant to C but for example this escape sequence clears the screen:
>   ESC [ 2 J             -erase entire screen (cursor doesn't move)
in order to use this code in Python it looks like this:
```
print u"\033[2J"
```
print   is python's   printf().   The 'u' before the quotes tells python that the text is a unicode string.  The escape sequence is similar to a \n but apparently more complex.  After the \  is 033, I am not sure what that is but basically replace the "ESC" in the codes listed on the two above sites with \033.  I got the \033 from looking in my .bashrc file at this line where it would change the text color:
```
# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\] \$ '

```


If its any help, here is the Python documentation page where i found the info about printing the escape sequence as unicode text using the 'u' before the text in quotes.  see half-way into the second paragraph:
[http://www.python.org/doc/current/ref/strings.html](http://www.python.org/doc/current/ref/strings.html)

Using these sequences i can draw ontop of the same areas over and over creating some animated effects, but they are still primitive compared to what ncurses can do.  In particular, i am curious to achieve the effect that nano does when it exits, and restores the terminal to its state before nano was started.

Hopefully some of the above makes sense, it barely does to me! ](*,) 
If you find out any info about how ncurses does what it does please share it because i would love to know.

Also i would like to try your program but i dont know how to compile it, could you provide some instruction?

---

### Post by N'Jal on 2005-08-04
Um those python links were not of much use, but thank you anyway.  Ok to compile my program, unzip it anywhere in your home directory, open what should be the game folder, open a terminal cd to the game folder and simply type gcc main.c -o main, to run the program type ./main in the game directory, if it pop's up with errors, crap, i'll have a look on saturday when i get home, if it does work cool, i need to make the game have an option to re-run the battle, but im wrestling with that damned atoi function. but that's in a version i am working on now. 

Thanks for your interest! I have posted links to the sources of a RP forum i post in, in the hopes that the RP gamers will test it, though not many of them are technically adept, so i figure i will be building all the binarys.

---

### Post by celloandy on 2005-08-04
[QUOTE=N'Jal]Um those python links were not of much use, but thank you anyway.[/QUOTE]

The control sequences mentioned in the pages he linked are ANSI standard, and aren't Python-specific.  Those examples were in Python, but you can use the exact same mechanism to do the same things in C, instead (or in Java, Perl, etc.).  You just need to "translate" them, so to speak, into C, and I think the above post explains with relative clarity what each Python statement does, in C terms.

Andrew

---

### Post by N'Jal on 2005-08-04
perhaps then i just didn't understand them

EDIT: I need some more help with that damned atoi function again. I literally copied the previous code and it's not doing what i expected it to. I don't actually need this function in my game, i wrote it to work out what the letters Y, y, N and n are as an int value, since i need to create a function where a question is asked and for ease of use i want the user to reply either y or n. But i need to account for caps lock being on etc. If that makes sense.

```

#include <stdio.h>
#include <stdlib.h>

int choice = 0;
char temp[2] = "";

int main () 
{
	printf("Enter a letter: ");
	if (fgets(temp, sizeof temp, stdin) != NULL)
	//pass the input character into temp
	{
	choice = atoi(temp);	
	//convert char temp into int choice
	}
		
	else
	{
		;
	}
	
	printf("%s\n", temp);
	//print temp
	printf("%d", choice);
	//print choice: not working as expected
	
    return (0);
}

```

---

### Post by ummo on 2005-08-04
If i understand you correctly you are looking for the ascii numerical value of a letter?
If that is the case then i think that atoi() is the wrong function.
I believe atoi() converts a number that is saved as a char type into a number that is  an integer type.  If the char entered is not a number it returns a zero.

When i ran the code you gave it would give a zero if i entered a char such as 's' at the prompt.  However if I entered a number like 4 at the prompt it would return 4.  I believe zero is an error message, pointing out that the char entered is not a number so the function cannot convert it.

If you want the ascii value of the char ue the function  toascii() and include the header ctype.h

```
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
int choice = 0;
char temp[2] = "";

int main () 
{
	printf("Enter a letter: ");
	if (fgets(temp, sizeof temp, stdin) != NULL)
	//pass the input character into temp
	{
	choice = toascii(temp[0]);	
	//convert char temp into int choice
	}
		
	else
	{
		;
	}
	
	printf("%c[00;46m", '\033');
// this is how you use the ansi escape sequences mentioned earlier.
// change the [00;46m to something else on the list from one of 
// the pages linked above to do different things.
// For example change it to [2J to clear the screen.
// [00;46m in this case changes the back ground of the text cyan.
	printf("%s\n", temp);
	//print temp
	printf("%d", choice);
	//print choice: not working as expected
        printf("%c[00;00m", '\033');
// the [00;00m here resets the colors and style of your text to normal
	printf("\n");
    return (0);
}
```

note that when you use toascii() you have to specify which char in your char array to convert.  Since you made temp an array that can hold two chars, you have to tell toascii() to use the first char in the array, that char being [0], the second char would be [1].

also i added in an example of how to use the ANSI escape sequences in C.

---

### Post by ep_ on 2005-08-08
> **N'Jal]perhaps then i just didn't understand them

EDIT: I need some more help with that damned atoi function again. I literally copied the previous code and it's not doing what i expected it to. I don't actually need this function in my game, i wrote it to work out what the letters Y, y, N and n are as an int value, since i need to create a function where a question is asked and for ease of use i want the user to reply either y or n. But i need to account for caps lock being on etc. If that makes sense.

```

#include <stdio.h>
#include <stdlib.h>

int choice = 0 said:**
>  = "";

int main () 
{
	printf("Enter a letter: ");
	if (fgets(temp, sizeof temp, stdin) != NULL)
	//pass the input character into temp
	{
              // code snipped
	}

```


N'jal  Couple of glaing problems here.  One, you're using global variabes temp and choice and you shouldn't be.  Two, your string buffer temp is not large enough to hold the input data. It should be large enough to hold all the chars you expect the user to type plus an additional newline character '\n' which fgets()  includes in the output string plus the null ''\0' terminator which is appended to strings in the c language.

Fortunely, fgets() has buffer overrun protection and it won't overwrite past the
end of the temp buffer and corrupt anything that happens to be there.  Unfortunely,  you'll still have unread characters in the input stream.  When your program continues, you'll get unexpected input behavior unless you take corrective action and clean things up.

Moral of the story:  Use extra large string buffers.

Also, atoi() converts strings to integers.  A string such as "123" will be converted to  the number 123.   The string "ABC" will be converted to 0. You can check the first character of a string buffer using something like this:

// untested, beware of typos
// assumes C has a bool type (C99)
// anything other than a 'Y' is assumed NO

bool answer(const char* prompt)
{
      char tmpstr[64] = "";
      if (prompt && *prompt)
           printf("%s", prompt);
       fgets(tmpstr, sizeof tmpstr, stdin);
      return (tmpstr[0] == 'Y' || tmpstr[0] == 'y');
   
}

int main()
{
      if (answer("Should I use big buffers"))
             printf("You answered yes!\n");
      else
             printf("Okay, you're asking for it!\n");
      return 0;
}

---

### Post by LordHunter317 on 2005-08-08
[QUOTE=ep_]It should be large enough to hold all the chars you expect the user to type plus an additional newline character '\n' which fgets()  includes in the output string[/quote]It does nothing of the sort.  If a newline is in the input to begin with, it retains it.

> Moral of the story:  Use extra large string buffers.The correct moral is to write an input function that actually reads in all the available input.

---

### Post by ep_ on 2005-08-08
[QUOTE=LordHunter317]It does nothing of the sort.  If a newline is in the input to begin with, it retains it.

The correct moral is to write an input function that actually reads in all the available input.[/QUOTE]

Wrong. fgets() does not retain the '\n' character if the buffer is not large enough to hold the line.  It stops reading.  If it's reading a line longer than than the provided buffer, two statements will be true:

   - The input buffer does not contain a newline.
   - end-of-file has not been reached.

You can pigeon hole me if you want, but the simple fact of the matter is that 2 characters is not enough allocation to "read all the available input".

---

### Post by LordHunter317 on 2005-08-08
[QUOTE=ep_]Wrong.[/quote]Not wrong.  You said:> . It should be large enough to hold all the chars you expect the user to type **plus an additional newline character '\n' which fgets() includes** in the output string(emphasis mine) which is just patently false.

fgets() doesn't add anything to the input string, except a terminating null character.

> fgets() does not retain the '\n' character if the buffer is not large enough to hold the line.That's not in contradiction with my statements.

> - The input buffer does not contain a newline.And you implied one would be added into the returned string, even when the actual end of line hadn't been reached.

> You can pigeon hole me if you want, but the simple fact of the matter is that 2 characters is not enough allocation to "read all the available input".And did I say anything about that?  No.  What I said was that your explanation of fgets() behavior was wrong.

---

### Post by ep_ on 2005-08-08
[QUOTE=LordHunter317]Not wrong.  You said:(emphasis mine) which is just patently false.

fgets() doesn't add anything to the input string, except a terminating null character.

That's not in contradiction with my statements.

And you implied one would be added into the returned string, even when the actual end of line hadn't been reached.

And did I say anything about that?  No.  What I said was that your explanation of fgets() behavior was wrong.[/QUOTE]


Wrong you said (not implied) > It does nothing of the sort. If a newline is in the input to begin with, it retains it. 

This is **patently false** because fgets stops reading when it reads n - 1 characters, 'n' being the second argument from the stream pointed to by the third argument into the buffer pointed to by the first argument. The whole point of my post was that n wasn't large enough!

What I implied was that the buffer should be sufficently large enough (and then some) to hold all the expected characters, plus the additional null character (i.e. '\0', aka as ASCII NUL, not NULL, aka a null pointer constant),plus the '\n' that you get at the end when fgets reads a line because that's what the language definition says is supposed to happen.

I added the word *"additional"* only because it is clearly not obvious to a newbie that  the string might include this character.  fgets was being given as an alternative to gets() which as you  know, does not retain the newline character.

-- ep

---

### Post by LordHunter317 on 2005-08-09
[QUOTE=ep_]This is **patently false** because fgets stops reading when it reads n - 1 characters,[/quote]So?  How is that in contradiction with what I said?
If in those n-1 characters, it reads a newline, it will pass it along.  If it doesn't read the newline, it won't add one.

You need to look up the meaning of the word 'retain'.  I took it's usage almost verbatim from the fgets(3) OpenBSD manpage.

> plus the '\n' that you get at the end when fgets reads a line because that's what the language definition says is supposed to happen.See, you when you say plus, you walk on the verge of being in error.  More correct would be to say: "The character that indicates the end of the line will be at the end of the string, before the null character.  Typically, this is the '\n' escape."

[edit]To be 100% clear, the above should be prefaced with: "When the end of the line is reached," and probably have this added, "When a newline doesn't occur within the number of request characters, no action is taken besides appending a NUL character to the end of the input."  

Being unambiguous is difficult, to say the least.


> I added the word *"additional"* only because it is clearly not obvious to a newbie that  the string might include this character.The problem is the way you said that is ambiguous, which is arguably worse.  A newbie could just as easily assume it adds a character that doesn't normally exist, which isn't true at all.

---

### Post by jayded on 2005-08-09
Why on earth would one want to write a text based game in C in 2005 ?

---

### Post by ep_ on 2005-08-09
You're right, being unambiguous is difficult, to say the least.

To my way of thinking, *"If a newline is in the input"* is not equivalent to * "if reads a newline, it will pass it along"* and *"If it doesn't read the newline, it won't add one."* is in direct contradiction to *"it retains it".* 

Anyway, I don't really care to quible about semantics, wording and definitions. I'll leave that for the theorists. Mainly, I just try to get thinks done. I hope I was some help to N'jal.

---

### Post by LordHunter317 on 2005-08-09
[QUOTE=ep_]To my way of thinking, *"If a newline is in the input"* is not equivalent to * "if reads a newline, it will pass it along"* and *"If it doesn't read the newline, it won't add one."* is in direct contradiction to *"it retains it".* [/quote]But it's not.

I think I see the problem now.  You're looking at the entire input stream: including the part that fgets() won't return, because there are more than n characters in the input stream.  And that fact has *no* bearing on fgets()'s semantics.

The behavior when fgets() never reads a newline from the input stream is irrelevant, unless it did something like added on.  Which it doesn't.  So the behavior when no newline is read has no bearing on whether it does or does not retain a newline.

The only case that matters is when fgets() reads a newline before '\n' characters.  If it does, it won't remove it from the input stream, like gets() will.  That's all 'retains' means and that's the scope of it's meaning.

The contents of the rest of the input stream fgets() is reading from is completely and totally irrelevant.

> Anyway, I don't really care to quible about semantics, wording and definitions.You really shouldn't be programming C then, as most of the differences between anything is semantics.

---

### Post by ep_ on 2005-08-09
[QUOTE=LordHunter317]But it's not.

I think I see the problem now.  You're looking at the entire input stream: including the part that fgets() won't return, because there are more than n characters in the input stream.  And that fact has *no* bearing on fgets()'s semantics.

The behavior when fgets() never reads a newline from the input stream is irrelevant, unless it did something like added on.  Which it doesn't.  So the behavior when no newline is read has no bearing on whether it does or does not retain a newline.

The only case that matters is when fgets() reads a newline before '\n' characters.  If it does, it won't remove it from the input stream, like gets() will.  That's all 'retains' means and that's the scope of it's meaning.

The contents of the rest of the input stream fgets() is reading from is completely and totally irrelevant.

You really shouldn't be programming C then, as most of the differences between anything is semantics.[/QUOTE]
 > I think I see the problem now. You're looking at the entire input stream: including the part that fgets() won't return, because there are more than n characters in the input stream. And that fact has no bearing on fgets()'s semantics.

No, I understand how fgets works, I'm only looking at what you said, nothing else.

> You really shouldn't be programming C then, as most of the differences between anything is semantics.


Again, you twist what I say and add a insult.  I didn't say, I don't appreciate semantics. I said I don't appreciate quibbling.  And that's  why I'm done with this.

---

### Post by N'Jal on 2005-08-09
> Why on earth would one want to write a text based game in C in 2005 ?

My university course that i will be enroling on uses C my former programming experience was VB so i figure id get a head start, unfortunatly programming books only teach you the programming principal's but not any practical application, i lke game's so i started writing a game.

Ok this fget's argeument is way over my head, i increased the buffer to 100 way more than required can we move on?

Also here is an update of what i have written, the problem's i have atm are in the xp.h file if you have a look at it you will probably see what i mean.

---

### Post by LordHunter317 on 2005-08-09
[QUOTE=ep_]No, I understand how fgets works, I'm only looking at what you said, nothing else.[/quote]And you never explained how what I said is in contradiction with fget()'s behavior, stated or observed.

> Again, you twist what I say and add a insult.The only insult is the one you're creating.  There was none implied.

>  I didn't say, I don't appreciate semantics. I said I don't appreciate quibbling.I misread your statement and apologize.

---

### Post by N'Jal on 2005-08-11
Ok i have recieved info from the uni, im on the course, however it's C++ they teach, so i will be rewriting this to C++ now.

---

