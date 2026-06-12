---
title: "[C++} Brace Wars: K&amp;R vs ANSI/ISO"
date: 2008-04-18
forum: Programming Talk
---

### Post by samjh on 2008-04-18
Most of us will be aware that there are two very popular styles of C++ coding: K&R and ANSI.

On the whole, they aren't really all that much different from each other, and have their merits.

The most visible and obvious difference is, I think, the treatment of whitespace and the use of braces in compound statements.

Some examples (surrounding code omitted for brevity):

**K&R style**:
```
    while (j != 1) {
        i++;
        if (i == 100) {
            j = 1;
        }
    }
```

**ANSI and ISO C++ style:**
```
    while (j != 1)
    {
        i++;
        if (i == 100)
        {
            j = 1;
        }
    }
```

With C, the choice is clear.  ANSI/ISO seem to follow the K&R style in its C standard documentation.

With C++, ANSI/ISO differ from K&R.  ANSI/ISO have a coding style which advocates placing the opening "{" brace on a line of its own.

Which style is your preference? :)

For me, I prefer K&R due to my C and Java background (note: Java uses a style similar to K&R but not identical).  ANSI/ISO's style appears to waste too much space.  I appreciate the clarity of having the opening brace on its own line, but it is usually unnecessary.

---

### Post by WW on 2008-04-18
Years ago I settled on this style:
[php]
    while (j != 1)
        {
        i++;
        if (i == 100)
            {
            j = 1;
            }
        }
[/php]
 I just didn't like those braces lined up immediately under the key words "if", "while", etc, in the ANSI style, and I didn't like the dangling closing braces of K&R.  (And the obsessive/compulsive part of me didn't like that function definitions generally didn't follow the style. :) )

But as long as a style is used consistently within a piece of code, I don't really care.  If I modify someone else's code, I stay with the existing style (if there is one).

---

### Post by ruy_lopez on 2008-04-18
> **samjh said:**
> 
Which style is your preference? :)

I'm with you. K&R pleases my sensibilities. However, I've got used to reading the other styles, even if I don't like them. 

[Whiltesmith's]("http://en.wikipedia.org/wiki/Indent_style") style particularly offends me.

EDIT: some of the best people use Whitesmiths ;)

---

### Post by WW on 2008-04-18
> **ruy_lopez said:**
> 
[Whiltesmith's]("http://en.wikipedia.org/wiki/Indent_style") style particularly offends me.
Sorry, dude! :)

Heh... I didn't know it had a name.

---

### Post by samjh on 2008-04-18
> **ruy_lopez said:**
> I'm with you. K&R pleases my sensibilities. However, I've got used to reading the other styles, even if I don't like them. 

That is an important point.  Even if one doesn't like a style, one should be able to decipher it fluently.

Although I'm not a big fan of the ANSI/ISO style (or Allman's, according to that Wikipedia link), I do appreciate its uses, especially when writing Ada code (you've got no choice with Ada, as it uses a comb format with begin...end instead of { } ).

---

### Post by LaRoza on 2008-04-18
I don't care as long as it consistant. As long as the indents make sense (like Python) the braces are just there to take up space.

I use:
```

for (i = 0; i < MAXLENGTH; i++)
{
    printf("%d\n",i);
}

//have used this before, I think it is a good style
for (i = 0; i < MAXLENGTH; i++)
  {
    printf("%d\n",i);
  }


```

I really don't see a point of the "K&R" style, yes, it saves one line, but why have the other brace on a line?

This would make more sense:
```

for (i = 0; i < MAXLENGTH; i++){
    printf("%d\n",i);}

```

---

### Post by samjh on 2008-04-18
> **LaRoza said:**
> I really don't see a point of the "K&R" style, yes, it saves one line, but why have the other brace on a line?

This would make more sense:
```

for (i = 0; i < MAXLENGTH; i++){
    printf("%d\n",i);}

```

Because unlike Python and languages with significant whitespace, C/C++ is freeform.  Programmers who are used to freeform languages rely on start-end symbols/keywords to keep track of statement blocks.

In C/C++/C#/Java and other C-like languages, the marking of statement blocks is facilitated by { and }.  In Pascal, Ada, and other ALGOL-like languages, the begin...end serves the purpose.

A C/C++ programmer will know that do, while, for, if, and switch statements will always begin a statement block.  So there is no need to separate the body of the block with a lone opening brace; therefore the opening brace can be placed on the same line as the do/while/for/if/switch statement.  But the final statement of a block is unpredictable, so you need a clear delimiter to mark the end of a block.  A closing brace on the same line as the final statement in a block is not clear, but having the closing brace on a line of its own cannot be mistaken.

The Allman/ANSI/ISO style uses a lone opening brace to enhance clarity even further.  This is good for writing very large programs with large source files, or for safety critical programs when code-maintainability is essential (one of the reasons why Ada was chosen for its role was its syntax was ALGOL-based with English words to very clearly separate blocks of statements and other portions of code, and therefore very easy to decipher even for non-programmers).

---

### Post by LaRoza on 2008-04-18
> **samjh said:**
> Because unlike Python and languages with significant whitespace, C/C++ is freeform.  Programmers who are used to freeform languages rely on start-end symbols/keywords to keep track of statement blocks.

The Allman/ANSI/ISO style uses a lone opening brace to enhance clarity even further.  This is good for writing very large programs with large source files, or for safety critical programs when code-maintainability is essential (one of the reasons why Ada was chosen for its role was its syntax was ALGOL-based, and therefore very easy to track and decipher even for non-programmers).

I disagree. Programmers who are used to freeform languages rely on indents, not start-end symbols.

There is no way a programmer could find this a readable format:

```

for
(i = 0;
i < MAXLENGth
;i++){printf("%d\n",i);}

```

This has all the requirements. The compiler relies on the start-end symbols, programmers rely on the style (using indents)

---

### Post by samjh on 2008-04-18
> **LaRoza said:**
> I disagree. Programmers who are used to freeform languages rely on indents, not start-end symbols.

There is no way a programmer could find this a readable format:

```

for
(i = 0;
i < MAXLENGth
;i++){printf("%d\n",i);}

```

This has all the requirements. The compiler relies on the start-end symbols, programmers rely on the style (using indents)

I think you misunderstand me.

I did not say that programmers of freeform language rely *exclusively* on start-end symbols/words.  They simply rely on them - meaning there are other factors involved, such as indents as you pointed out.

Your example is very extreme and does not fit the requirements of readability at all.  There is no consistency, no clear grouping of code, and no clear separation between logical groups of code.  You merely pointed out that symbols alone cannot make code readable, which is not the point of K&R or any other sensible coding style.  Readability is a combination of many things, of which grouping and separation of statement blocks is one of them.

The part of my post which you omitted should explain why the bracing style of K&R is what it is.  It's not necessarily the best, but it is one of the better styles for C/C++.  It is personally my favoured style.

It needn't make sense to you in particular.  But it does make a lot of sense to most.

---

### Post by aks44 on 2008-04-18
ANSI/ISO style here.

---

### Post by Balazs_noob on 2008-04-18
K&R ,because it looks better to me :D

---

### Post by days_of_ruin on 2008-04-18
K&R looks cluttered and sloppy to me.
I like being able to line up the brackets.

---

### Post by Steven_B on 2008-04-18
I generally use both, depending on what I feel it makes the code cleaner and easier to read.  For example, I would likely do:
```

    while (j != 1)
    {
        i++;
        if (i == 100) {
            j = 2;
        }
        else if (i == 101){
            j = 1;
        }
    }

```
This keeps the if statements compact, but keeps the while loop easy to read.  Of course, this is entirely my opinion - I'm fine with most styles.

---

### Post by Lster on 2008-04-18
ANSI/ ISO, but I used to prefer K & R.

---

### Post by mike_g on 2008-04-18
I use ANSI/ISO. To me the symmetry looks nicer, even if it does eat up an extra line. Also, its easier to parse; apparently some automated tools specifically look for opening braces on the first column of a new line.

---

### Post by melopsittacus on 2008-04-18
There should be an option "it depends on the language", or something like that:I like to use K&R style for Java and ANSI/ISO for C++ :)

---

### Post by public_void on 2008-04-18
Used to use ANSI/ISO now I use K&R.

---

### Post by aks44 on 2008-04-18
> **melopsittacus said:**
> There should be an option "it depends on the language"

Why, when the thread's title specifically mentions C++? :p

---

### Post by Jessehk on 2008-04-18
K&R

```

#include <stdio.h>
#include <ctype.h>
#include <math.h>

void foo( const char *str, FILE *dest ) {
    const char *iter = NULL;
    
    for ( iter = str; *iter != '\0'; iter++ ) {
        fprintf( dest, "%c\n", *iter );
        
        if ( toupper( *iter ) == 'F' )
            fputs( "Foo Foo!\n", dest );
    }
}

#define BUFFSIZE 256

int main( void ) {
    char buff[BUFFSIZE];
    double result;
    
    while ( printf( "Enter text: " ) &&
            (fgets( buff, BUFFSIZE, stdin ) != NULL) )
        foo( buff, stdout );
   
    
    result = sin( (3 * M_PI) / 2 );
    printf( "\nAnswer is %lf\n", result );
    
    return 0;
}

```

I use a single space to separate parameters for functions and arguments to conditionals and loops. I don't use any spaces when the parenthesis are necessary for order of evaluation.

For example,
```

while ( (ch = getchar()) != EOF ) {
    /* ... */
}

```

---

### Post by Aztek on 2008-04-18
I also prefer to have both braces on there own line.

---

### Post by supirman on 2008-04-18
ANSI/ISO style here.  My first teacher used this so I chose it.  Then, when I got out of school and headed to work, their standards were a very verbose form of coding that is ANSI/ISO, but they also extended it to where even simple if/else/for statements had to have braces.  I like it.  

I have no problem with K&R.

Those who use whitesmith's should be shot ;)  It irritates the hell out of me.

---

### Post by Can+~ on 2008-04-18
I got a friend who, apparently, created his own:

[IMG]http://img.photobucket.com/albums/v517/CanXp/rancacode.png[/IMG]

And, btw, no one omits the bracers when there's a single line?

[PHP]
while (j != 1) 
{
	i++;
	if (i == 100)
		j = 1;
}

	
[/PHP]

---

### Post by supirman on 2008-04-18
> **Can+~ said:**
> 
And, btw, no one omits the bracers when there's a single line?

[PHP]
while (j != 1) 
{
	i++;
	if (i == 100)
		j = 1;
}
	
[/PHP]


I don't anymore.  In the old days when screen real estate was limited then I could see trying to condense code, but I work on a 30" monitor with a tiny 8pt font so I'd rather have my code spaced nicely and consistent.

---

### Post by JupiterV2 on 2008-04-18
I use ANSI/ISO. I originally used K&R, likely because I started with C before learning C++. I find ANSI/ISO much easier to identify code-blocks with.

[php]
if( some_incredibly_long
   _line_of_checks_and_or_statements) {
  ...
}[/php]

vs.
[php]
if( some_incredibly_long
   _line_of_checks_and_or_statements)
{
  ...
}[/php]

---

### Post by paintba||er on 2008-04-18
I don't really follow any standard, but my style seems to be similar to K&R.

> **Can+~ said:**
> And, btw, no one omits the bracers when there's a single line?

I do...

---

### Post by nrs on 2008-04-19
GNU. I will pray for the souls who prefer K&R.

---

### Post by stratavarious on 2008-04-19
.

---

### Post by melopsittacus on 2008-04-19
> **aks44 said:**
> Why, when the thread's title specifically mentions C++? :p

Sorry, I completely overlooked that. I was just reading the title of the poll :D

---

### Post by Nemooo on 2008-04-19
I prefer the K&R style, since it is more compact. To be more precise, I am using the linux kernel coding style, as described here: [http://www.chris-lott.org/resources/cstyle/LinuxKernelCodingStyle.txt](http://www.chris-lott.org/resources/cstyle/LinuxKernelCodingStyle.txt)

Well, I program C mostly now, when I was using C++, I used the ANSI style.

---

### Post by ipatfrmww on 2010-09-22
I didn't vote since this is an old thread and it would be unfair to skew the results like that.
I personally like the ANSI/ISO standard better. Because when I search for the start of a block I look for '{' instead of text. I think it helps distinguish between a block :
{

}

and something that looks more like a statement:
stuff(more stuff) {

}

That's just how I learnt to skim read. If I had learnt to look for the header instead then I would be quite happy with the K&R style, but I'm too used to the ANSI/ISO style now to change.
It being a draw pretty much sums this debate up -there is no "right" way.

---

### Post by lisati on 2010-09-22
> **WW said:**
> Years ago I settled on this style:
[php]
    while (j != 1)
        {
        i++;
        if (i == 100)
            {
            j = 1;
            }
        }
[/php]
 I just didn't like those braces lined up immediately under the key words "if", "while", etc, in the ANSI style, and I didn't like the dangling closing braces of K&R.  (And the obsessive/compulsive part of me didn't like that function definitions generally didn't follow the style. :) )

But as long as a style is used consistently within a piece of code, I don't really care.  If I modify someone else's code, I stay with the existing style (if there is one).

+1. Having it like the ISO but indented is what I like.

---

### Post by worksofcraft on 2010-09-23
ooh what brought this old topic back up?

I think Stroustrup endorses K&R style. Standards committees have presented no reasons for doing it differently, but the great thing about free format languages is that you can format it the way you think is easiest to understand.

Personally I don't like the opening brace on it's own line because it doesn't show the structure: Which statement does the enclosed block belong with?
```

while (getch() != '\n'); // erroneous semicolon perhaps?
{
    do_something();
}
// does this comment end on this line or the next? \
do
{
    something_else();
}
while (getch() != '\n');

```
With curly at the end of the line there can be no doubt what programmer intended. So Stroustrup and K&R is just common sense IMO.

p.s. Look see how much more clear what the intention is even though there is a bug!
```

while (getch() != '\n'); { // extraneous semicolon for sure!
    do_something();
}
// does this comment end on this line or the next? \
do {
    something_else();
} while (getch() != '\n');

```

---

### Post by formaldehyde_spoon on 2010-09-23
I never knew there were names for these... 

BSD style is the only Truth.  Everything else is heresy! ;) (ie KNR but applied to both statements *and* functions.)

---

