---
title: "D520 (new scripting language)"
date: 2012-06-15
forum: Programming Talk
---

### Post by Edgareatis on 2012-06-15
D520 is a new type of scripting language. It takes csharp, adds extra features that i will explain in a moment then allows you to run your script without compiling. Perfect for small apps or when you want to be able to edit code while running your application. 

It takes the power of csharp, and makes it simple. It keeps a similar syntax but is more developed to include extra features such as fcode. This is short for front code, not catchy i know but it is called this because it is converted to csharp in front of the script being run. This is nothing special, but the feature has not been explained yet. When you type in fcode, it is just an abbreviated word or phrase that is linked to a large amount of csharp code. Like all your using statements for example, could just be "[open]". Not only  is this a cool feature to speed up development but allows you to create your own syntax for csharp, in minutes, then have your code, with your syntax, run or be converted to pure csharp. 

More features to come and the compiler will soon be released. Please comment with anything you would like added, suggestions or just to say if you like the idea. 


NOTES
[LIST]
[*]Will be free of charge and open source
[*]Release date not set yet check the [site]("http://d520.wordpress.com/dev-blog/") for details on this date as they become available
[*]this post may not be upto date check the [site]("http://d520.wordpress.com/dev-blog/") for an up to date version
[/LIST]

---

### Post by ofnuts on 2012-06-17
Does the world needs yet another scripting language?

Since very few people write code that they are alone to see (especially in the OpenSource world) what good is it to be able to define one's own syntax?

---

### Post by trent.josephsen on 2012-06-17
> **ofnuts said:**
> Does the world needs yet another scripting language?

Since very few people write code that they are alone to see (especially in the OpenSource world) what good is it to be able to define one's own syntax?
It's a preprocessor. Preprocessors have been known to be useful.

I'm with you on the first point though.

---

### Post by DangerOnTheRanger on 2012-06-18
> **trent.josephsen said:**
> It's a preprocessor. Preprocessors have been known to be useful.

I'm with you on the first point though.

Preprocessor code has also been known to be completely incomprehensible except to the person that wrote it. :)

My main issue with this, though, is I don't think the world needs yet another scripting language (we already have Python, Lua, Boo, JavaScript, Perl, etc...), especially one based on C#.

---

### Post by ofnuts on 2012-06-18
> **DangerOnTheRanger said:**
> especially one based on C#.
All languages should be treated equally, without distinction of syntax or origin. We are equal-opportunity coders :)

---

### Post by nvteighen on 2012-06-18
The everlasting problem of programming languages is that they have to be born for some purpose. All big languages were created for something specific in mind... even those that fail horribly in achieving that purpose (C++...).

So, which is the problem D520 is going to solve that none of the mainstream scripting language hasn't already?

---

### Post by CptPicard on 2012-06-19
Unless the "live code editing" means some kind of really live REPL with some sort of incremental compilation, I fail to see the benefits of this. C# makes a lousy starting point for a scripting language, IMO, and the macro-expansion system appears very basic at first look...

I suggest the OP looks into Lisp :-)

---

