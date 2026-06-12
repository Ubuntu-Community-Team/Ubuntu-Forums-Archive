---
title: "General Programming Statements"
date: 2009-06-07
forum: Programming Talk
---

### Post by Alias1407 on 2009-06-07
This thread is more of personal interest than an actual question. I would just like someone to explain to me why (using C as an example) we use...

```
int main()
{
        printf("BLAHBLAHBLAH");
}
```

A different line to define our {} curly braces however when we use *if* statements and such we use...

```
if(x>5) {
      printf("BLAHBLAHBLAH");
      }
```

For our curly braces...


Why?

---

### Post by Can+~ on 2009-06-07
> **Alias1407 said:**
> This thread is more of personal interest than an actual question. I would just like someone to explain to me why (using C as an example) **we** use...

```
int main()
{
        printf("BLAHBLAHBLAH");
}
```

A different line to define our {} curly braces however when **we** use *if* statements and such **we** use...

```
if(x>5) {
      printf("BLAHBLAHBLAH");
      }
```

For our curly braces...


Why?

Who are "we". I've never used that notation.

---

### Post by unknownPoster on 2009-06-07
> **Can+~ said:**
> Who are "we". I've never used that notation.

Same here. 

It's not good to make sweeping generalizations of the entire community.

It's more personal preference than anything...

I've had professors tell me that it doesn't matter which way I choose to format my code, as long as I'm consistent...

So just pick a method and go with it..

---

### Post by krazyd on 2009-06-07
Yeah, so long as it's readable and consistent, use whatever you want!

---

### Post by ushimitsudoki on 2009-06-07
There are many [brace styles]("http://en.wikipedia.org/wiki/Indent_style") - just pick one and be consistent.

Often, if you are joining or starting a project, the indention style will be dictated so the whole team follows the same format. So, don't too attached to any one way as [The One True Brace Style]("http://c2.com/cgi-bin/wiki?OneTrueBraceStyle").

---

### Post by pbrockway2 on 2009-06-07
The inconsistecy between bracing statements and functions/methods dates back to Kernigan & Richie.  This [Wikipedia article]("http://en.wikipedia.org/wiki/Indent_style#K.26R_style") suggests quirks of the original C syntax as part of the reason for the difference.  (I also seem to recall seeing somewhere that the "Bible"'s publishers or printers had a hand in this: wanting to save printed lines.)

---

### Post by Nemooo on 2009-06-07
The straight forward answer to your question would be that the bracket placement is different for different control structures. One way to visualise this (as in your example) is by putting brackets on their own line when your declaring a function's scope, and on the same line when it's a conditional's scope.

---

### Post by lloyd_b on 2009-06-07
> **pbrockway2 said:**
> The inconsistecy between bracing statements and functions/methods dates back to Kernigan & Richie.  This [Wikipedia article]("http://en.wikipedia.org/wiki/Indent_style#K.26R_style") suggests quirks of the original C syntax as part of the reason for the difference.  (I also seem to recall seeing somewhere that the "Bible"'s publishers or printers had a hand in this: wanting to save printed lines.)

Here's what a typical function definition looked like back in the days of yore:```
void
myfunc(arg1, arg2, arg3)
    int arg1;
    char * arg2;
    float arg3;
{
    ...
}
```With this syntax, having the open brace on a line by itself makes the code MUCH more readable than having it after the last argument.

With the advent of ANSI C and its many improvements, function declarations became more compact, and the *need* for having the open brace on a line by itself became unnecessary.  But it had already become standard practice.

Lloyd B.

---

