---
title: "because i am really...really lazy"
date: 2008-10-15
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-15
is there a fucntion in C that will automatically put \n at the end of the string so i don have to (yes i am that lazy). if not i guess i will just right my own function

same question for perl

(yes i have googled and found nothing)

---

### Post by Sockerdrickan on 2008-10-15
If only at output then you can use puts(foo);

---

### Post by jimi_hendrix on 2008-10-15
wow thanks...now just an answer for perl...

as you could tell i just started C and am completly dumbfouned at my ignorance

---

### Post by cmay on 2008-10-15
i think there is a "say" funktion for perl. i however never had it working from the tutorial .
in ruby i think there is a say function also. if memory serves me right.
(which sadly it almost never does :))

to find the perl tutorial i mention just google begin perl or perl begin i am sure it will pop up.
 i have lost the bookmark otherwise i would have linked to it.
hope it helped anyway.

---

### Post by jimi_hendrix on 2008-10-15
and a question about the puts() function...if i wanted to output an int how would i do that...for printf() i can do 

int var;
printf("here is your variable: %d", var);

but in puts i get an error when i try that

---

### Post by geirha on 2008-10-15
Yes, puts() only accept a string as argument, it does not do formatting like printf(), and I don't think there is a printf-like function that adds a \n for you. Perhaps you should try to create your own function, printfln(), that does just that?

---

### Post by Joeb454 on 2008-10-15
If you want a function, write one ;) All you would need to do is have [php]printf("\n");[/php] As the function code. Then you could write something like [php]printf("I wanted to tell you this number is %d", var); newLine();[/php]

Hope that helps a little :)

---

### Post by jimi_hendrix on 2008-10-15
> **Joeb454 said:**
> If you want a function, write one ;) All you would need to do is have [php]printf("\n");[/php] As the function code. Then you could write something like [php]printf("I wanted to tell you this number is %d", var); newLine();[/php]

Hope that helps a little :)

i would do something more like this but with C code not C++

[PHP]
void println(string line)
{
     cout << line << endl;
}
[/PHP]

but since i am not that far in C thus my questions...i cannot write the equivilent yet

---

### Post by jimi_hendrix on 2008-10-15
quick question for the function i am building

how would i get an infinite amount of parameters for my function so i can use formating in the function

---

### Post by ZuLuuuuuu on 2008-10-15
> **cmay said:**
> i think there is a "say" funktion for perl. i however never had it working from the tutorial .
in ruby i think there is a say function also. if memory serves me right.
(which sadly it almost never does :))

to find the perl tutorial i mention just google begin perl or perl begin i am sure it will pop up.
 i have lost the bookmark otherwise i would have linked to it.
hope it helped anyway.

I am not sure but I guess say() function will come with Perl 6. Some features of Perl 6 can now be enabled in Perl 5 with feature pragma: [http://perldoc.perl.org/feature.html](http://perldoc.perl.org/feature.html) I never tried though...

---

### Post by snova on 2008-10-15
This should do what you want. Read the manpage for "stdarg" if you want to know how it works, but this is a drop-in replacement for printf() that ends the line automatically.

[PHP]
#include <stdarg.h>

void lprintf( const char* fmt, ... )
{
    va_list args;
    va_start( args, fmt );
    vprintf( fmt, args );
    va_end( args );
    printf( "\n" );
}
[/PHP]

---

### Post by jimi_hendrix on 2008-10-15
thanks that helped

now just for the perl function

---

### Post by slavik on 2008-10-15
for perl, there is and there isn't ... Perl5 doesn't have such functionality although it is easy to add, Perl6 has the mentioned function say.

---

### Post by dwhitney67 on 2008-10-15
> **jimi_hendrix said:**
> is there a fucntion in C that will automatically put \n at the end of the string so i don have to (yes i am that lazy). if not i guess i will just right my own function

same question for perl

(yes i have googled and found nothing)
From the C answers that have been posted, and for which you seem happy to see, I get that you want to output your string, and then follow it with a newline.

Your OP indicated that you wanted to add a newline character to your string.  Which is it??

If all you want to do it output your string with a newline, then why not use printf()?
[php]printf( "%s\n", myString );[/php]

Surely you are not that lazy!

P.S.  Please tell me the solution above is NOT what you wanted.  You state you are lazy, but you are willing to waste a lot of time on an otherwise silly thread.

---

### Post by jimi_hendrix on 2008-10-16
no the solution to my problem was what snova suggested.  a prinf() that will just put a \n automatically at the end of output

@slavik thanks...is perl6 out yet?

---

### Post by dwhitney67 on 2008-10-16
> **snova said:**
> ...
[PHP]
#include <stdarg.h>

void lprintf( const char* fmt, ... )
{
    va_list args;
    va_start( args, fmt );
    vprintf( fmt, args );
    va_end( args );
    printf( "\n" );
}
[/PHP]

What is the difference between the following code??

```
printf("%s %s\n", str1, str2);
```
and
```
lprintf( "%s %s", str1, str2);
```

Is it merely the 'l' character and the missing '\n' in the second statement?  Or is the intent to slow the execution of the program?

---

### Post by slavik on 2008-10-16
> **jimi_hendrix said:**
> no the solution to my problem was what snova suggested.  a prinf() that will just put a \n automatically at the end of output

@slavik thanks...is perl6 out yet?
there are some prototype implementations, the two most advanced are rakudo (perl6 on parrot) and pugs (perl6 interpreter written in haskell). so far, from my experience, pugs has more features.

---

### Post by nvteighen on 2008-10-16
> **dwhitney67 said:**
> What is the difference between the following code??

```
printf("%s %s\n", str1, str2);
```
and
```
lprintf( "%s %s", str1, str2);
```

Is it merely the 'l' character and the missing '\n' in the second statement?  Or is the intent to slow the execution of the program?

Well, maybe the interest on learning how to write a function that does what one wants? ;)

Yeah, such a function is really silly in its purpose, but it's an easy thing you could think of for learning how to use stdarg and also learn C, which is jimi_hendrix's goal. So, its value is more "academic" than something else, I guess.

I also wrote an implementation, just for fun, slighlty more (unneededly) complex. The approach is different: it appends '\n' to the string and then prints that new string. If someone's interested (to compile it, use some library building process):

```
[color=#408080][i]/* Library for printf_nl(), a printf() that inserts a newline.
 * Copyright (C) 2008 Eugenio M. Vigo
 *
 * This program is free software: you can redistribute it and/or modify it under
 * the terms of the GNU General Public License as published by the Free Software
 * Foundation, either version 3 of the License, or (at your option) any later
 * version.
 *
 * This program is distributed in the hope that it will be useful, but WITHOUT
 * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
 * FOR A PARTICULAR PURPOSE. See the GNU General Public License for more
 * details.
 *
 * You should have received a copy of the GNU General Public License along with
 * this program. If not, see <http://www.gnu.org/licenses/>. */[/i][/color]
[color=#BC7A00]
#include <stdio.h>
#include <malloc.h>
#include <string.h>
#include <stdarg.h>
[/color]
[color=#B00040]int[/color] [color=#0000FF]printf_nl[/color]([color=#B00040]char[/color] [color=#666666]*[/color]string, ...)
{
    va_list ap;
    va_start(ap, string);

    [color=#B00040]int[/color] ret [color=#666666]=[/color] [color=#666666]0[/color];
    [color=#B00040]int[/color] src_len [color=#666666]=[/color] strlen(string);

    [color=#408080][i]/* We create a new string that's 1 byte longer than the source, but strlen()
     * doesn't count the final '\0', so we have to add 2. 
     *
     * Also, calloc() avoids us the need to manually set newstring's last
     * character to '\0', as it initializes all memory allocated to 0. */[/i][/color]
    [color=#B00040]char[/color] [color=#666666]*[/color]newstring [color=#666666]=[/color] ([color=#B00040]char[/color] [color=#666666]*[/color])calloc(src_len [color=#666666]+[/color] [color=#666666]2[/color], [color=#008000]**sizeof**[/color]([color=#B00040]char[/color]));
    [color=#008000]**if**[/color](newstring [color=#666666]==[/color] [color=#008000]NULL[/color])
        ret [color=#666666]=[/color] [color=#666666]99[/color];
    [color=#008000]**else**[/color]
    {
        [color=#408080][i]/* We copy all characters, except the source's '\0', by using strlen()'s
         * result. */[/i][/color]
        strncpy(newstring, string, src_len); 

        [color=#408080][i]/* We set the second-to-last character to the new line we want to
         * add. */[/i][/color]
        newstring[src_len] [color=#666666]=[/color] [color=#BA2121]'\n'[/color]; 

        [color=#408080][i]/* Using vprintf(), which accepts an argument list instead of the
         * arguments... quite strange, but very handy. We save the return value
         * to make this function compatible with the standard functions' return
         * values. */[/i][/color]
        ret [color=#666666]=[/color] vprintf(newstring, ap); 

        free(newstring); [color=#408080]*/* Deallocating. */*[/color]
    }

    va_end(ap); [color=#408080]*/* Needed, or things may break... */*[/color]
 
    [color=#008000]**return**[/color] ret;
}

```

---

### Post by slavik on 2008-10-16
please consider using errno and not using the string library for copying the string (less dependencies that way).

---

### Post by nvteighen on 2008-10-16
> **slavik said:**
> please consider using errno and not using the string library for copying the string (less dependencies that way).
It's the same dependency... string.h is part of the C Standard Library, as all of the other functions included.

---

### Post by dwhitney67 on 2008-10-16
> **nvteighen said:**
> Well, maybe the interest on learning how to write a function that does what one wants? ;)

Yeah, ...
But why in this particular case?

It's overkill based on the information provided in the OP.

From reading his (or hers?) various posts, jimi-hendrix is all over the spectrum with their questions.  It would be nice if he/she were to ask a legit question with a practical purpose than some nonsense.

I'm still on holiday, so I have nothing better than to critique the posts on UF.  Now where's my beer...?

---

### Post by nvteighen on 2008-10-16
> **dwhitney67 said:**
> But why in this particular case?

It's overkill based on the information provided in the OP.

From reading his (or hers?) various posts, jimi-hendrix is all over the spectrum with their questions.  It would be nice if he/she were to ask a legit question with a practical purpose than some nonsense.

I'm still on holiday, so I have nothing better than to critique the posts on UF.  Now where's my beer...?
Being very honest, in the very early beginning when I was learning C, I also missed a function like jimi_hendrix was asking for... :p Maybe because I was used to PRINT in BASIC, which adds a newline unless you use PRINT "..."**,** (the same behaivor as Python's print). Well, it seems I finally learned a little and don't miss it any longer.

Yeah, it's nonsense; I agree with you. But, maybe was it just curiosity? Anyway, I had nothing to do and wanted to write some C (I've been too much time in Scheme and Python these days).

---

### Post by Canis familiaris on 2008-10-16
I actually like that C doesn't automatically put an endline after each prinf(). Gives more control IMO.
Alhough Python's way is also good.

---

### Post by snova on 2008-10-16
> **dwhitney67 said:**
> From reading his (or hers?) various posts, jimi-hendrix is all over the spectrum with their questions.  It would be nice if he/she were to ask a legit question with a practical purpose than some nonsense.

First, I'm almost certain that this is a he. I think I also know his name.

jimi_hendrix has been asking all kinds of things recently. I find it interesting to note that they almost all intrigue me- compilers, kernels, and so on.

To dwhitney67: There is no difference between those two lines in what they do. And my function would only be a few cycles slower anyway, since printf() is implemented almost exactly the way lprintf() is. The overhead is equivalent to an additional call to printf()- which could easily be replaced with putchar('\n') if you're concerned. Besides, I think GCC optimizes it to putchar anyway (by reading the assembly dumps, I've noticed that calls to printf() aren't always there).

To nvteighen: Wouldn't it be easier to use sprintf()? And calloc() is just slow, since you're only avoiding one write and strncpy() has to copy the whole string over the zeros anyway.

I don't know if this is academic or not, but assuming it isn't, who likes to remember that pesky newline anyway? From the Ruby home page:

```
# The famous Hello World
# program is trivial in
# Ruby. You don't need:
#
# * a "main" method
# [COLOR="Red"]*** newline escapes**[/COLOR]
# * semicolons
#
# Here's the code:

puts "Hello World!"
```

The same lesson applies here. Often enough a newline was what you wanted anyway.

nprintf() would be a better name than lprintf(), though...

---

### Post by dwhitney67 on 2008-10-16
> **snova said:**
> ...
I don't know if this is academic or not, but assuming it isn't, who likes to remember that pesky newline anyway? ...
My point exactly.  From the OP, I understood that jimi-hendrix (btw, where are u?) wanted to append a newline-character to a string.  But if all he wanted to do is output a string, followed by a newline-character, well then there is puts() or printf() with a '\n' in the format statement.

I'm bored with this thread, btw.

---

### Post by mssever on 2008-10-16
> **snova said:**
> From the Ruby home page:

```
# The famous Hello World
# program is trivial in
# Ruby. You don't need:
#
# * a "main" method
# [COLOR=Red]*** newline escapes**[/COLOR]
# * semicolons
#
# Here's the code:

puts "Hello World!"
```
Note that Ruby actually provides two methods. Kernel#print prints the string exactly as given without adding any newlines. Kernel#puts adds a newline before printing if the string doesn't already end with \n.

---

### Post by nvteighen on 2008-10-16
> **snova said:**
> 
To nvteighen: Wouldn't it be easier to use sprintf()? And calloc() is just slow, since you're only avoiding one write and strncpy() has to copy the whole string over the zeros anyway.


I think you can't: I don't know any method to pass the variadic arguments from the built function to another one other than using the va_list and therefore, the target function would be one of the vprintf() family. vsprintf() would probably work.

About calloc(): it's about safety. If I used malloc(), and then just use strncpy(), I might get uninitialized data, specially at the end. I don't like that to happen and that's why I always use calloc(). Yes, it's slower, but in this case I prefer to trade speed for safety.

---

### Post by snova on 2008-10-16
Well yes, but you're overwriting the entire thing anyway with the string, so why bother initializing it with zeros? Just append a newline and a zero and you get the same thing.

And you're right, it's not sprintf(), but vsprintf(). Oops. :oops:

Another interesting note- strncpy() can be replaced with strcpy() because you already know that enough memory has been allocated to fit the entire string.

> Note that Ruby actually provides two methods. Kernel#print prints the string exactly as given without adding any newlines. Kernel#puts adds a newline before printing if the string doesn't already end with \n.

I discovered that yesterday. Is "Kernel" similar to Python's __builtin__? It looks like it. I thought it was an actual module (though probably a built in one) but I noticed earlier than a call to exit() worked when it was supposed to be in Kernel#exit.

---

### Post by mssever on 2008-10-16
> **snova said:**
> I discovered that yesterday. Is "Kernel" similar to Python's __builtin__? It looks like it. I thought it was an actual module (though probably a built in one) but I noticed earlier than a call to exit() worked when it was supposed to be in Kernel#exit.Kernel is a module. It's mixed into Object, so all classes inherit its methods. The reason calling exit worked, is because of that. Keep in mind that Ruby has no functions, only methods. While you can write methods that work like Python functions, they're still methods (usually of Object). Because of that, there's usually no need for an explicit call to self. But calling self.exit *would* work.

---

### Post by snova on 2008-10-16
A little confusing... I get it, though. Thanks. :)

"self" seems to have the same meaning as in Python. Am I right?

---

### Post by mssever on 2008-10-16
> **snova said:**
> "self" seems to have the same meaning as in Python. Am I right?
"self" refers to the current instance, so yes. But it's rarely needed, because it's usually implicitly assumed. You only need to specify self for disambiguation and to work around reserved words.

---

### Post by jimi_hendrix on 2008-10-16
> **dwhitney67 said:**
> (btw, where are u?)

at school most of the day and homework most of the night

i love how all of my posts turn into debates...informative ones though

---

### Post by snova on 2008-10-16
> **jimi_hendrix said:**
> at school most of the day and homework most of the night

i love how all of my posts turn into debates...informative ones though

Possibly related to the fact that your threads usually interest me, and in no way related to the fact that I can be argumentative sometimes.

---

### Post by nvteighen on 2008-10-17
> **snova said:**
> Well yes, but you're overwriting the entire thing anyway with the string, so why bother initializing it with zeros? Just append a newline and a zero and you get the same thing.

And you're right, it's not sprintf(), but vsprintf(). Oops. :oops:

Another interesting note- strncpy() can be replaced with strcpy() because you already know that enough memory has been allocated to fit the entire string.

Yeah, I see what you mean. But you're not overwriting the whole string: without calloc() the last character of the new string wouldn't be zero, as the source string is one character shorter. Therefore, the string wouldn't be null-terminated, exactly the point where initialization is most needed (otherwise any I/O function **may** fail... and that's the problem... "may", not "will/won't"!).

EDIT: But... I guess I can just malloc() and then first only initialize the last character... :p

> **jimi_hendrix said:**
> at school most of the day and homework most of the night

i love how all of my posts turn into debates...informative ones though

And I also love it: you always put a bit of programming on the Programming Talk (and not only you learn... all of us learn something). Sometimes I don't post in the threads you open, but I read them almost always.

---

### Post by jimi_hendrix on 2008-10-17
@snova and nvteighen

thanks and you guys always seem to have a correct answer

---

