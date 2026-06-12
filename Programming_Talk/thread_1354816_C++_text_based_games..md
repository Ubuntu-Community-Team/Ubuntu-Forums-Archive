---
title: "C++ text based games."
date: 2009-12-14
forum: Programming Talk
---

### Post by Logan513 on 2009-12-14
Does anybody know of any tutorials / examples that will show me where to start in creating my own text-based C++ video games? I've never had to deal with anything like this before, so I figured this would be the place to ask. :lol:
Thanks.

return 0;

---

### Post by Logan513 on 2009-12-14
I don't know if BUMPs are frowned apon here. So tell me if they are. :)

---

### Post by Logan513 on 2009-12-14
Does no one know? :(

---

### Post by jeffathehutt on 2009-12-14
You can probably get some answers in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") subforum.  That's where most of the programmers hang out. ;)

---

### Post by lewisforlife on 2009-12-14
I don't know of any specific tutorials, but when you say "text based game", do you mean, the computer asks a question, user answers, and based on the answer the computer does something else.  If so, I would learn about:

[LIST]
[*]variables
[*]cout
[*]cin
[/LIST]

---

### Post by Logan513 on 2009-12-14
I'll go hang out in the programmers section! :lolflag:

As for the type of Text-based game I want to make.....

here is an example: [http://www.youtube.com/watch?v=bwLFEnevnFw](http://www.youtube.com/watch?v=bwLFEnevnFw)

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
The idea is similar to pimp wars... a qbasic game I played in BASIC programming in high school. I'll see if I still have it so you can look at the code.

---

### Post by Logan513 on 2009-12-14
That would be very helpful thank you. :)

But I'm only 12 years old, so I'm no sure a title called "Pimp wars" would be appropriate for me... ;)

---

### Post by Logan513 on 2009-12-14
Here is actually the idea that I had in mind for the game....

Space Shooter Idea:

Text based characters:

<|*|> >> Space Ship

* >> Stars flying upward

| >> bullet
[*] >> Enemy

$ >> power-up (+100 points)

+ >> power-up (+1 life)

Game will look like:

Score: 456  *                     *     *
Lives: 003          <|*|>      *      
      *        *                        *
 *          *       *      |       *       *
     *            *               *
*           * $            *             *
*      *              *       |    *  *
  *            
[*]           
[*]

*Looks different in Gedit ^*

Point of the game:

To fly back and forth and shoot bullets at the enemies to gain ten points for each enemy. The enemies WILL shoot back so don't get hit or your dead! Your goal is to get as many points as possible and get on the highscores table. Dollar sighns will occasionally move up across the screen. If you can manage to run into it without getting hit you get an extra 100 points! The same will also happen with a plus sighn, but less often. It will add one extra life if you can manange to snatch one of them. If you get hit by a enemy bullet you lose a life and will continue the game untill there you have no lifes left. When you have no lifes left the game will display a "Game Over" screen along with your score and the highscore. Then the program will check if you got enough points to make it on the leaderboards. If you did it will have you enter you initials and add you to the list. If not, then it will simply display the leaderboards to you. The highscores table will look like:
------------------------
| plc.Name ..... score |
------------------------
| 1.  Jac  ..... 15000 |
| 2.  bob  ..... 14893 |
| 3.  Mac  ..... 12465 |
| 4.  lam  ..... 11000 |
| 5.  zjm  ..... 10534 |
| 6.  sar  ..... 09423 |
| 7.  mam  ..... 08453 |
| 8.  hrn  ..... 07543 |
| 9.  lly  ..... 00453 |
| 10. lmk  ..... 00213 |
------------------------

*looks different in Gedit* ^

The highscores will be saved in seperate file.

**Figure out how to do this and I owe myself $20**

It's not formatted like it is in the Gedit text editor but I think you get the idea.... :P

---

### Post by lisati on 2009-12-14
> **Logan513 said:**
> That would be very helpful thank you. :)

But I'm only 12 years old, so I'm no sure a title called "Pimp wars" would be appropriate for me... ;)

:) Well called! 

I did have a gwBasic text-based game for MS-DOS somewhere once.......I must have a look some time.

---

### Post by TheBuzzSaw on 2009-12-14
Bumping threads is OK but not within a few minutes of your last post. Goodness, have some patience!

---

### Post by jeffathehutt on 2009-12-14
Though I don't have any specific examples, you will probably want to learn [ncurses.]("http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/")  You can get precise control over the terminal using the ncurses library.

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
I will run through it again if I find it to make that there's no inappropriate content, but I seem to recall that the wort that you did was "sell" drugs and hit people. It was a text based map with dialogs that would pop up when an event happened. I'm not suggesting game mastery, but rather code study. The reason that I suggested a qbasic game is due to the similarities that I've seen with the sections of code that I've seen.

---

### Post by Logan513 on 2009-12-14
Well, do you guys get the idea? I know enough C++ I just don't know how to apply it to creating video games. :D

EDIT: Wait, a second page? *see's all the posts on the second page*

@BuzzSaw - The forums I normally visit lets you BUMP when you reach the second page...

@jeffathehutt - Will do! Thanks for the link!

@ST3ALTHPSYCH0 - Uhh, if it's just text characters it shouldn't be too much a problem... Just no sex or realistic violence....

EDIT EDIT: @jeffathehutt - Will I need to download ncurses or should I already have it? I am using GCC....

---

### Post by JLinden on 2009-12-14
Out of curiosity, why do you want to create a text based space-shooter? :)

---

### Post by Logan513 on 2009-12-14
> **JLinden said:**
> Out of curiosity, why do you want to create a text based space-shooter? :)

I get bored easy, since I am so young. So I make up little projects that make learning C++ fun! So it's kinda just one of those ideas I got.. :)

As of right now my goal is to eventually get to the shooter, but right now I would be fine with a simple maze game or something...

EDIT: @jeffathehutt - I am looking for C++, not C...

EDIT EDIT: I found this... [http://www.rdxgames.net/projects/wrathlands/index.html](http://www.rdxgames.net/projects/wrathlands/index.html)

Although I don't want to download all the videos and .wmv won't work on Linux.... :(

EDIT EDIT EDIT: Here is another example I found on youtube...

[http://www.youtube.com/watch?v=mR8NuwpHCfQ&feature=related](http://www.youtube.com/watch?v=mR8NuwpHCfQ&feature=related)

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
I found that file if you'd like to take a look at it. I've not played with any BASIC editors in ubuntu so I don't know if they'd display and parse all the sub routines correctly, but I have the file uploaded [here](http://www.mediafire.com/?2dutoumggmr).
You might want to start the program and just walk around the environment for a couple of minutes then go through the coding to get an idea how it was done.
If you can't view it properly you could always install dosbox and d/l qbasic.

---

### Post by Logan513 on 2009-12-14
Hmm, BASIC? I want to do it in C++... :o

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
I know, like I said, I only mentined it b/c I've noticed some similarities in the coding. I wouldn't recommend coding anything in BASIC anymore.

---

### Post by Logan513 on 2009-12-14
Now, how would I run a BAS file? I do have Windows XP by the way...

*reads you post again*

q/l qbasic? Link please?

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
[Here ya go](http://www.softpedia.com/get/Programming/Coding-languages-Compilers/Qbasic.shtml)

You'll have to run in DOS compatibility mode.

---

### Post by Logan513 on 2009-12-14
Thanks, see you back here when I get done playing! :D

---

### Post by Logan513 on 2009-12-14
[IMG]http://www.city-data.com/forum/members/rita-mordio-129085-albums-funny-images-pic30244-face-palm-apply-directly-face.png[/IMG]

It won't work on the 64-bit version of Windows. NAG NAG NAG. I hate windows. ](*,)

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
You'll have to download and install [Dosbox]("http://www.softpedia.com/get/Programming/Other-Programming-Files/DOSBox.shtml"). It will install in a 64 bit environment (I installed it in Win 7 64). You'll have to mount a directory as your virtual c:\.
For instance, I have QBASIC in a folder on my d:\ drive.
so at the DOSbox prompt (a virtual z:\) I typed 
```

mount c d:\

```This tells DOSbox that when I change to the "c:" to base that on the d:\.
I then cd to qbasic, and run qbasic.
The directory tree in the QBASIC open/save dialogs will bve based off what you have mounted in DOSBOX, not your true directory tree.

You could also install dosbox in Ubuntu and navigate to you QBASIC folder in the same way, except that you'll have to mount using linux syntax:
```

mount c /home/username

```

DOSbox is in the repos
```

sudo apt-get install dosbox

```

---

### Post by Logan513 on 2009-12-14
I'm sorry but it just does not seem worth it to me.... :(

I think I'll pass on the whole PIMPLAND game until there is a way to use it under Linux without DOSbox or all that jazz.

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
N/P
BASIC is the only language I have any experience with, and that's been 11 or 12 years ago. Good luck with your project.

---

### Post by Logan513 on 2009-12-14
Thanks for the luck! :D

---

### Post by jeffathehutt on 2009-12-14
ncurses does have bindings for c++, but I'm not exactly sure what you need to install to use it with c++.  Searching the Ubuntu package list brings up libncurses5-dev, which can be installed through synaptic, so that might be all you need.  Hopefully someone with more experience can help you more, and good luck with your project :D

---

### Post by Logan513 on 2009-12-14
Alrighty then! Let's give her a shot! :)

---

### Post by wmcbrine on 2009-12-14
> **Logan513 said:**
> *Looks different in Gedit ^*Use "code" tags to preserve your formatting. Like so:

```

------------------------
| plc.Name ..... score |
------------------------
| 1.  Jac  ..... 15000 |
| 2.  bob  ..... 14893 |
| 3.  Mac  ..... 12465 |
| 4.  lam  ..... 11000 |
| 5.  zjm  ..... 10534 |
| 6.  sar  ..... 09423 |
| 7.  mam  ..... 08453 |
| 8.  hrn  ..... 07543 |
| 9.  lly  ..... 00453 |
| 10. lmk  ..... 00213 |
------------------------

```

(If you don't get it, quote my message to see what I did.)

---

### Post by Logan513 on 2009-12-14
Alrighty then.

```
Lives: 003                  Score: 0000064258
---------------------------------------------
          *         <|*|>      *      
      *        *                        *
 *          *       * |       *       *
     *            *               *
*           * $            *             *
*      *              *       |    *  *
  *            
[*]           
[*]
```I modified how the game will look a little since the last time I posted this so here you go! :D

EDIT: Maybe if I got rid of some stars...

EDIT EDIT: ```
Lives: 003                  Score: 0000064258
---------------------------------------------
                    <|*|>      *      
      *        *                        *
 *          *       * |       *       
                                
*            $                         
      *              *       |      *
              
[*]           
[*]

```

There, that's not so bad anymore!

---

### Post by Logan513 on 2009-12-14
[IMG]http://www.city-data.com/forum/members/rita-mordio-129085-albums-funny-images-pic30244-face-palm-apply-directly-face.png[/IMG]

*big manly sigh*

[http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/helloworld.html](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/helloworld.html)

```
#include <ncurses.h>

int main()
{    
    initscr();            /* Start curses mode           */
    printw("Hello World !!!");    /* Print Hello World          */
    refresh();            /* Print it on to the real screen */
    getch();            /* Wait for user input */
    endwin();            /* End curses mode          */

    return 0;
}
```

Someone tell me why this isn't working in c plus plus....  ](*,)

---

### Post by Logan513 on 2009-12-14
Why??? **BECAUSE IT'S NOT C++ IT'S C!!!!!**

*slaps myself across the face*

sorry... ](*,)

---

### Post by Logan513 on 2009-12-14
Should I use this?

[http://ndk-xx.sourceforge.net/](http://ndk-xx.sourceforge.net/)

---

### Post by SigmaSanti on 2009-12-14
I have been having fun learning about ncurses recently, and saw your post.
The above code compiles fine in a c++ file, but requires that you link the file properly.
Linking is new for me (and maybe for you too), but it has to find the <ncurses.h> in the /usr/include directory of your computer.

To have it find this header file, you should use the -l flag when you compile e.g.
g++ -Wall -lncurses -o untitled untitled.cpp

This should work if you installed the libncurses...dev-something file earlier in this thread.
I dont know if your using commandline, codeblocks, or geany. But if you know c++ then your probably understand how to add this, if not do a search and you can find out how, or just ask here, I will be happy to answer.
The c++ library you posted should not be necessary because C++ is compatible with C code.

---

### Post by Logan513 on 2009-12-14
Wait, what? :-k

I have ncersus.h in my /usr/include directory... 

I'm not sure I understand your post... :-s

ALRIGHT!!! I got her working!

---

### Post by SigmaSanti on 2009-12-14
I was wondering if you used the 
-lncurses flag in your command to compile and link the file.
You need to do that to have it work. In C or C++.

---

### Post by Logan513 on 2009-12-14
Yah, I did. :lolflag:

---

### Post by Can+~ on 2009-12-14
If you want to do graphic based games, I would suggest Python and Pygame, plus you get to know new languages.

That were my $0.02.

---

### Post by jimi_hendrix on 2009-12-14
btw, you can use C libs/functions in C++, so there is no reason to to use ncurses in C++.

---

### Post by SigmaSanti on 2009-12-14
Ncurses is a C library.
The link he posted was for a C++ version.

---

### Post by SouthOfHell on 2009-12-15
I was actually thinking about doing something similar to this, if anyone remembers a old BBS DOORS game called LORD (legend of the red dragon), thats my inspiration.

---

### Post by nvteighen on 2009-12-15
Slow. Do you have your plan on how you will design your code? How will the player be represented in code? How the bullets? How will you structure the basic game flow? etc. Do you think you can handle that in C++ and/or learn how to do it? I think those are the first questions to be answered before the ncurses issue.

IMO, C++, unless you have a lot of experience with it, will make this task much more difficult for you than what it is. Can+~'s suggestion of Python + Pygame isn't bad; I'd rather go Python + ncurses as I think it is much more suited for your idea. Python will give you much more powerful structures to start with and hide the unnecessary low-level details. Of course, Python means to learn a new language instead of using the one you are already learning and that's always an investement of time. The decision is yours.

If you go for C++, first, polish your OOP skills; you'll need them in order to have a sane and good code; these games became very easy to write in QBASIC because it allowed you to create data structures which could act like classes (like you do in C), while other BASICs didn't have that. Also, rememeber to make your code structured, 1 function = 1 task. 

About ncurses, try using a C++ binding for ncurses. ncurses is annoying even in C because of some of its design principles are outdated these days and only kept for backwards compatibility. Even the Python ncurses binding (which comes bundled with Python, so nothing to install) still reflects that quirks. But, ncurses at the end does its job... :p

---

### Post by Logan513 on 2009-12-15
Meh, I have never really been interested in python or that other one. I just want to see if I can try to get it done in C++... See, I am not doing as much for the end result, as I am the journey that I have to take to get to the end result. I'm pretty much just doing this for experience. I knew from the start that I needed to learn OOP, since I don't know much about it, So I decided that this could be one of those projects that would help me learn about OOP and how to do more than just the avarage cin and cout.

But thanks for all the help you guys have given me! You guy's gave me that first step I needed to badly to help point me in the right direction. :grin:

I'll make sure I post the result here so you guys can play it!

By the way... Do you guys think I am annoying? I try not to be, but a lot of people say I am because I'm 12. Be honest... :-s

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
It's refreshing to me to see someone so young delving into things I don't understand. BTW, have you flowcharted your idea? That step is annoying and seems like a waste of time, but it really does help you keep things where they need to be and keep your code neat (like sub routines and etc).

---

### Post by Logan513 on 2009-12-15
> **ST3ALTHPSYCH0 said:**
> It's refreshing to me to see someone so young delving into things I don't understand. BTW, have you flowcharted your idea? That step is annoying and seems like a waste of time, but it really does help you keep things where they need to be and keep your code neat (like sub routines and etc).


Yah... about the charting..... I have not done it yet, but will soon. :D

---

### Post by nvteighen on 2009-12-15
> **Logan513 said:**
> 
By the way... Do you guys think I am annoying? I try not to be, but a lot of people say I am because I'm 12. Be honest... :-s

Everybody is annoying at a certain point... :p Ok, it's not common to see a 12 years old trying to deal with OOP and C++, but if you can handle it, go ahead!

---

### Post by Logan513 on 2009-12-15
I can handle it... I hope. :lolflag:

---

### Post by Physical Hook on 2009-12-15
> **nvteighen said:**
> Everybody is annoying at a certain point... :p Ok, it's not common to see a 12 years old trying to deal with OOP and C++, but if you can handle it, go ahead!

Welcome to the 21st century :)

---

### Post by nvteighen on 2009-12-15
> **Physical Hook said:**
> Welcome to the 21st century :)

I thought we were in the 24th century...

---

### Post by CptPicard on 2009-12-15
> **nvteighen said:**
> I thought we were in the 24th century...

Meh, in the 24th century, six-year olds start programming in Lisp. And yes, Church-Turing thesis was correct.

---

### Post by Logan513 on 2009-12-15
Lisp... lol. :)

---

### Post by wmcbrine on 2009-12-15
[Lisp might just be the only current programming language still in use in the 24th century.](http://www.paulgraham.com/hundred.html)

But, we digress. :D

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
Heck, why not. Naomi Wildman was helping in Astrometrics at 4 or 5!

---

### Post by Logan513 on 2009-12-16
I need your guys opinion on this... When I am online, I can't read something really long like a manual without getting confused / frustrated. So I've been looking online for some books that might help me. Would this be a book you guys would recommend?

[http://www.amazon.com/Programmers-Guide-NCurses-Dan-Gookin/dp/0470107596](http://www.amazon.com/Programmers-Guide-NCurses-Dan-Gookin/dp/0470107596)

If so, I am going to check to see if the local library has it. If they don't then I'll just ask for it for Christmas.

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
I've usually had luck with the "for dummies" series. That's how I learned MS-DOS when I was about your age.

---

### Post by Logan513 on 2009-12-16
I do have C++ for Dummies fifth edition but no where in there have I seen a reference of NCurses. Would it be in the normal C for dummies book? I don't know. The book I linked too just seemed like it would fit my needs the best. I just wanted to know if you guys agreed before I went out and spent $30 on a book.

---

### Post by Logan513 on 2009-12-16
Meh, this is the only reference to curses that google found in the C for Dummies book.

[http://books.google.com/books?id=ruPPRwBYdjIC&printsec=frontcover&dq=C++for+dummies&cd=1#v=onepage&q=curses&f=false](http://books.google.com/books?id=ruPPRwBYdjIC&printsec=frontcover&dq=C++for+dummies&cd=1#v=onepage&q=curses&f=false)

:(

---

### Post by CptPicard on 2009-12-16
> **Logan513 said:**
> Lisp... lol. :)

Foolish to laugh, the young Padawan is... ;)

---

### Post by nvteighen on 2009-12-16
> **Logan513 said:**
> I do have C++ for Dummies fifth edition but no where in there have I seen a reference of NCurses. Would it be in the normal C for dummies book? I don't know. The book I linked too just seemed like it would fit my needs the best. I just wanted to know if you guys agreed before I went out and spent $30 on a book.

No, the reference for ncurses is installed in a Debian(-based) system at /usr/share/doc/libncurses5-dev. For developing ncurses applications, you need to have the libncurses5-dev package (although I recall there's a "virtual" ncurses-dev package which points to the latest ncurses available).

Otherwise, you'll find it somewhere in the Internet. You'll have to cope with that... nowadays people upload references to the web; it's cheaper than publishing them in paper.

---

### Post by Logan513 on 2009-12-16
> **CptPicard said:**
> Foolish to laugh, the young Padawan is... ;)

The young Padawan has no regrets for his actions... :)

@  [nvteighen]("http://ubuntuforums.org/member.php?u=273037") - Did you not read my previous post?  :-|

[http://www.amazon.com/Programmers-Gu.../dp/0470107596]("http://www.amazon.com/Programmers-Guide-NCurses-Dan-Gookin/dp/0470107596")

---

### Post by CptPicard on 2009-12-16
> **Logan513 said:**
> The young Padawan has no regrets for his actions... :)

Well it seems like he is well on his way to the Dark Side anyway :-k

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
The dark side? Doesn't that depend on his theme? My terminal background is white, not black!!

---

### Post by Logan513 on 2009-12-16
My terminal is classic white text on black.

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
Already gone to the Dark Side, this padawan has.

---

### Post by Logan513 on 2009-12-16
Padawan likes the vintage MS-DOS look! :)

---

### Post by Logan513 on 2009-12-16
The more I read on ncurses, the more it seems that I have to use C instead of C++, and I don't think I am very clear on the compatibility on C and C++. So your saying that if I were to start writing a C++ program and I threw a printf in there instead of cout it would read it like it was C and move along?

So like would this.....

```
#include <iostream>
using namespace std;

int main(){
     cout << "Hello World";
}
```

do the same as this...

```
#include <iostream>
using namespace std;

int main(){
    printf("Hello World");
}
```

... If I were to compile and run them both as if they were a C++ program? :-k

---

### Post by Logan513 on 2009-12-16
Well, would you look at that! It does! :P

So I could write C programs in C++!?! Sweetness!

---

### Post by Physical Hook on 2009-12-16
> **Logan513 said:**
> Well, would you look at that! It does! :P

So I could write C programs in C++!?! Sweetness!

Doh! :)

> 
It was developed by [Bjarne Stroustrup]("http://en.wikipedia.org/wiki/Bjarne_Stroustrup") starting in 1979 at [Bell Labs]("http://en.wikipedia.org/wiki/Bell_Labs") as an enhancement to the [C programming language]("http://en.wikipedia.org/wiki/C_%28programming_language%29") and originally named "*C with Classes*". It was renamed to *C++* in 1983.[[2]]("http://en.wikipedia.org/wiki/C%2B%2B#cite_note-1")
Source: [http://en.wikipedia.org/wiki/C%2B%2B](http://en.wikipedia.org/wiki/C%2B%2B)

---

### Post by Logan513 on 2009-12-16
*facepalm*

You learn something new everyday! :)

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
> **Logan513 said:**
> My terminal is classic white text on black.

> **Logan513 said:**
> Padawan likes the vintage MS-DOS look! :)

It's funny that you say that, b/c this weekend I'll be reconfiguring my second computer as a quad boot with, Ubuntus 9.04, 9.10, 10.04, and MS-DOS 6.22.

---

### Post by Logan513 on 2009-12-16
Cool! Good luck! :P

---

### Post by Can+~ on 2009-12-16
> C / C++ Golden Rule:
int main() << :smile:
int main(void) << [-X
return 0;

Actually:

[FONT="Courier New"][COLOR="#00AAFF"]int[/COLOR] main([COLOR="#00AAFF"]int[/COLOR] argc, [COLOR="#00AAFF"]char[/COLOR] **argv)[/FONT]

To allow program arguments, and it's not even a rule.

---

### Post by Logan513 on 2009-12-16
I know... But I see a lot of n00bs who include the void and wonder why there code won't work... :)

---

### Post by Physical Hook on 2009-12-17
> **Logan513 said:**
> I know... But I see a lot of n00bs who include the void and wonder why there code won't work... :)

```
int main(void)
{
    cout << "It works!" << endl;
}
```

Have you at least tried it ? :-)

---

### Post by Logan513 on 2009-12-17
*facepalm*

```
#include <stdio.h>

int main(void){
    
    int num1;
    int num2;
    char func;
    int sum;
    printf("\n\nEnter your first number:");
    scanf("%d", &num1);
    printf("\nEnter your second number:");
    scanf("%d", &num2);
    printf("\nEnter your function [+,-,*,/] :");
    scanf("%s", &func);

    switch(func){
        case '+':
        sum = num1 + num2;
        break;
        case '-':
        sum = num1 - num2;
        break;
        case '/':
        sum = num1 / num2;
        break;
        case '*':
        sum = num1 * num2;
        break;
        default:
        printf("\nFunction not recognized by computer");
        break;
    }

    printf("\n\n%d", num1);
    printf("%c%d", func, num2);
    printf(" =");
    printf(" %d", sum);
    printf("\n\n");
}
```

Have **you** at least tried it?

---

### Post by Physical Hook on 2009-12-17
> **Logan513 said:**
> *facepalm*

```
#include <stdio.h>

int main(void){
    
    int num1;
    int num2;
    char func;
    int sum;
    printf("\n\nEnter your first number:");
    scanf("%d", &num1);
    printf("\nEnter your second number:");
    scanf("%d", &num2);
    printf("\nEnter your function [+,-,*,/] :");
    scanf("%s", &func);

    switch(func){
        case '+':
        sum = num1 + num2;
        break;
        case '-':
        sum = num1 - num2;
        break;
        case '/':
        sum = num1 / num2;
        break;
        case '*':
        sum = num1 * num2;
        break;
        default:
        printf("\nFunction not recognized by computer");
        break;
    }

    printf("\n\n%d", num1);
    printf("%c%d", func, num2);
    printf(" =");
    printf(" %d", sum);
    printf("\n\n");
}
```Have **you** at least tried it?

Yes, I have. Works like a charm :biggrin:

---

### Post by wmcbrine on 2009-12-17
> **ST3ALTHPSYCH0 said:**
> It's funny that you say that, b/c this weekend I'll be reconfiguring my second computer as a quad boot with, Ubuntus 9.04, 9.10, 10.04, and MS-DOS 6.22.Will MS-DOS even boot on a half-way modern machine? Maybe FreeDOS...

---

### Post by nvteighen on 2009-12-17
> **Logan513 said:**
> The young Padawan has no regrets for his actions... :)

@  [nvteighen]("http://ubuntuforums.org/member.php?u=273037") - Did you not read my previous post?  :-|

[http://www.amazon.com/Programmers-Gu.../dp/0470107596]("http://www.amazon.com/Programmers-Guide-NCurses-Dan-Gookin/dp/0470107596")

Ugh... not seen that. Nice! :P

> **Logan513 said:**
> The more I read on ncurses, the more it seems that I have to use C instead of C++, and I don't think I am very clear on the compatibility on C and C++. So your saying that if I were to start writing a C++ program and I threw a printf in there instead of cout it would read it like it was C and move along?

So like would this.....

```
#include <iostream>
using namespace std;

int main(){
     cout << "Hello World";
}
```

do the same as this...

```
#include <iostream>
using namespace std;

int main(){
    printf("Hello World");
}
```

... If I were to compile and run them both as if they were a C++ program? :-k

Ok, some things. Don't write C in a C++ compiler because there are differences regarding how type casting is performed and also operator precedence changes a bit. There is a certain degree of backwards compatibility in order to be able to use C libraries, so use it only when you've got no other chance to use a C++ library. It's usually very bad and messy to mix completely different languages just because you can... C++ code usually looks much similar to Java code than C code.

> **Logan513 said:**
> I know... But I see a lot of n00bs who include the void and wonder why there code won't work... :)

You're wrong! That "Golden Rule" is not valid for C (this is precisely a good example to show you that C is **not** a subset of C++!)

The **correct** thing in C is **int main(void)**. **int main()** is tolerated just because of an accidental issue you'll quickly understand.

In C and C++, declaring a function like e.g. **int *abc()** means that your function accepts an arbitrary number of arguments of any type. This is critical when you use pointers to functions, as you sometimes don't know what arguments will use the function you'll be pointing to (e.g. you'll determine it at runtime). Another issue it can raise is that if you, by mistake pass an argument to that abc function, the compiler won't warn you at all (because it's actually not an error). If you want the compiler warn you, you have to use **int *abc(void)** in this case.

The issue is that main is just called at the beginning and there's no harm in having it declared as **int main()** as nobody will try calling it.

Try this compiling it with **gcc -o blah blah.c -Wall -Wextra -pedantic** (i.e. all warnings activated):
```

/* This will compile in C. It won't in C++. */
int a()
{
    return 6;
}

int main(void)
{
    a(5); /* Passing an argument! No error will be raised. */

    return 0;
}

```

vs.

```

/* This won't compile in any language. */
int a(void)
{
    return 6;
}

int main(void)
{
    a(5); /* Compiler will shout at this. */

    return 0;
}

```

If you want a language that is a 100% C superset, look at Objective-C.

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
> **wmcbrine said:**
> Will MS-DOS even boot on a half-way modern machine? Maybe FreeDOS...

I've read a couple of how tos for dual booting DOS 6.22 and XP or Vista. Besides, the machine I'm putting it on is 10 yrs old, so it's not that far removed from the DOS days. The only limitation that I've seen is the 2 Gb FAT16 limit, and obviously less than 4 Gb of RAM.

---

### Post by Logan513 on 2009-12-17
Fine! I'll change my sig... :rolleyes:
What should I change her to?

Ugh. I think I am going to get that book. This whole manual thing is driving me nuts! :-x

---

### Post by Logan513 on 2009-12-18
BUMP! :popcorn:

---

### Post by nvteighen on 2009-12-19
> **Logan513 said:**
> BUMP! :popcorn:

Why?

---

### Post by Logan513 on 2009-12-19
So you want this topic to die???? [-(

---

### Post by Physical Hook on 2009-12-19
> **Logan513 said:**
> So you want this topic to die???? [-(

I believe your questions have been answered. Why to keep it alive ?

---

### Post by lightstream on 2009-12-19
are you using gedit to do your coding?

hopefully not and you have a decent IDE installed, such as Code::Blocks, which I'm experimenting with at the moment.

if you are trying to use a simple text editor, you're making things unnecessarily hard for yourself!

---

### Post by Logan513 on 2009-12-19
Meh, I don't care for IDE's. All I need is Gedit and GCC. :)

---

### Post by nvteighen on 2009-12-20
> **Logan513 said:**
> Meh, I don't care for IDE's. All I need is Gedit and GCC. :)

Gedit + plugins can be as good as its "big brother" Geany.

But, consider learning Emacs and/or Vi in a future, as they are text editors with a lot of power.

---

### Post by Logan513 on 2009-12-20
I am learning VI...

---

### Post by Logan513 on 2009-12-22
Bump

---

