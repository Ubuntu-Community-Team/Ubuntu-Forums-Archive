---
title: "Best way to learn language syntax"
date: 2011-07-14
forum: Programming Talk
---

### Post by garth813 on 2011-07-14
Just wondering if anyone out there has any neat tricks for learning programming language syntax.  It can at times look very arcane, and it seems that the best way for me to learn is to just repeat it until I have it memorized. I am pretty much learning through books so I'm kind  of on my own.  Thanks in advance.

---

### Post by papibe on 2011-07-14
I think the same as you, repetition, repetition...

But I think it helps a lot using editors that color the keywords, and point out very basic syntax mistakes. For example gedit while writing bash and python scripts.

Regards.

---

### Post by schauerlich on 2011-07-14
[list=1][*] Use an editor that has syntax highlighting. Once you get a feel for how correct code will look, it is easier to spot syntax errors, as the highlighting will look weird.
[*] Use an editor that does indentation for you automatically. (emacs does this for many languages, and I don't doubt vim or many IDEs do something similar). This is for reasons similar to #1.
[*] Code. A lot. The more you use it, the more you get used to it. Eventually it will become second nature, and you can focus on what you're actually doing and how to do it smarter.[/list]

---

### Post by cgroza on 2011-07-14
> **schauerlich said:**
> 
[LIST=1]
[*] Use an editor that has syntax highlighting. Once you get a feel for how correct code will look, it is easier to spot syntax errors, as the highlighting will look weird.
[*] Use an editor that does indentation for you automatically. (emacs does this for many languages, and I don't doubt vim or many IDEs do something similar). This is for reasons similar to #1.
[*] Code. A lot. The more you use it, the more you get used to it. Eventually it will become second nature, and you can focus on what you're actually doing and how to do it smarter.
[/LIST]

4. Read others code. It will help you spot new cases in the syntax and all you have to do is look it up in the docs.

---

### Post by JupiterV2 on 2011-07-14
And learn more languages. Each language you learn will make learning other languages easier to digest. A loop is a loop. Once you get the premise you'll find it pretty much behaves the same in every language, tweaked to their own specific idiom.

Like the others have already said though, "Code." Repetition is your friend.

---

### Post by Bachstelze on 2011-07-14
> **JupiterV2 said:**
> A loop is a loop. Once you get the premise you'll find it pretty much behaves the same in every language, tweaked to their own specific idiom.

Generally, yes. There are some gotchas, though. for loops for example are dramatically different in Python and sh than in, say, C.

---

### Post by cgroza on 2011-07-14
> **Bachstelze said:**
> Generally, yes. There are some gotchas, though. for loops for example are dramatically different in Python and sh than in, say, C or Java.
If you mean this:

```

ls = [1,2,3]
for i in ls:
    print i


``````

public class Test
{
   static void main(String[] args)
   {
   int[] a = {1,2,3};
   for(int x : a) System.out.println(x);
   }
}

```

---

### Post by Bachstelze on 2011-07-14
> **cgroza said:**
> If you mean this:

```

ls = [1,2,3]
for i in ls:
    print i


``````

public class Test
{
   static void main(String[] args)
   {
   int[] a = {1,2,3};
   for(int x : a) System.out.println(x);
   }
}

```

Fair enough, make it just C then. :p I shouldn't talk too much about languages I know very little...

---

### Post by karlson on 2011-07-14
> **garth813 said:**
> Just wondering if anyone out there has any neat tricks for learning programming language syntax.  It can at times look very arcane, and it seems that the best way for me to learn is to just repeat it until I have it memorized. I am pretty much learning through books so I'm kind  of on my own.  Thanks in advance.

Best way to learn programming language is not to learn the syntax, but to learn algorithms rather then the language itself.  Once you understand those I suggest you pick a problem and a language to implement a solution with and solve that problem.

---

### Post by resander on 2011-07-16
Hi Garth,

I agree with the other respondents.

When I had to learn a new computer language or come back to one I have not been using for a long time I would write a 'cheat' sheet trying to fit the essence of the language onto a small number of physical sheets. For example, like this for C:
```

enum
   {
   MAXBUFLENGTH = 120 ,
   ....
   SIZEMONTH = 9 
   } ;  // sizes typically used in array definitions

typedef enum {
 MONDAY, TUESDAY, WEDNESDAY, THURSDAY , FRIDAY , SATURDAY, SUNDAY
} WEEKDAY ;  // WEEKDAY type names the days 

typedef struct {    // record structure
   char name [ MAXSZNAME+1 ] ;
   int numchildren ;
   bool married ;
   ...
} PERSONINFO ;


char workbuffer [ MAXBUFLENGTH+1 ] ;  // global array
static char eastermonth [ SIZEMONTH+1 ]; // local array

static char * shortmonthlookup [ 12 ]  // local lookup array
   =
   { "jan", "feb", "mar", "apr", "may", "jun",
     "jul", "aug", "sep", "oct", "nov", "dec" } ;


void procedurename ( int a, char array[] , int * passback ) {
   if ( condition ) {
     statements ;
   }
   else if ( condition ) {     // as many as you like
     statements ;
   }
   else {          // if needed
     statements ;
   }

   switch ( expression ) {
     case 1:          // any constant ok, e.g. 'a', or enum defined MONDAY
       statements ;
       break ;
     ....
     case 167:
       statements ;
       break ;
     } 
   
   while ( condition ) {
     statements ;
   } 
....  more loops   
}   
int functionname ( short a, short b ) {...  // function returning int
char * funcname ( int a, char * inarray ) {...  // returning array adress

statement =
   name ( 123 , myarray ) OR   // calling procedure or function
   return OR                   // return in procedure
   return expression OR        // return in function
   break OR                    // break out of loop, end statements in case 
   printf ( formatstring , expr , expr, .... ) // formatted output
   ....

condition = expression

expression = a mix of variables, constants, arithmetic and logical 
             operators

arithmetic ops = +, - , * , /
logical ops = && ,  // logical AND
              ||    // logical OR

xampleexpresson = 123, 123+varname, (age > 20) && (age < 90)

 formatstring = "yourtext<formatitem>yourtext<formatitem>..." e.g. "Hi %s" 

formatitem = list those important to you

and other language constructs you find difficult to remember.

```

So, no rocket science here, but it worked for me.

Happy programming and problem solving!

Ken

---

