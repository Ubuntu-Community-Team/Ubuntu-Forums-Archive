---
title: "Web programming."
date: 2006-03-12
forum: Programming Talk
---

### Post by Darkness3477 on 2006-03-12
Hi, I'm not sure if this is the right place to put this sort of a question, but it has a little bit to do with programming... So here goes!

Well, I know enough XHTML to make a good website. Now, I want to go one step further with my websites and add a little something more to them, something like scripting. Only thing is, I'm not sure what I want to use to make my pages more dynamic and fun. I'm not sure what scripting/programming language to use. Something like Javascript sounds really fun, but using php to make my pages a bit cooler would be awesom. I dunno, even learning Java to make something would be cool..... But, I'm not really sure about what I should do, and I don't know what to start with.  

By the way, I have a little programming experience with C++ and Python.

---

### Post by Zelut on 2006-03-12
I do work with PHP and its really pretty powerful.  I mean, this forum runs on php :).  Its nice because it integrates perfectly into html, connects with mySQL easily & easy makes your pages dynamic.

I dont have experience with javascript (minimal), but I would suggest PHP

---

### Post by Darkness3477 on 2006-03-12
Thanks, I'll have a look at it very soon (pest inspecter is here).
Do you know if I can do the same sort of...Flashy stuff... That people use Javascript for? Like, when I make some boards (using invisionfree) I often get some javascripts people have made to make news faders and things like that.

---

### Post by Kurt` on 2006-03-13
PHP is a server-side scripting language. All it does is generate a page and send it to the client.

Anything you could do with a static HTML page could be done using PHP as well. So adding Javascript code to an existing PHP-based site is a non-issue. :)

---

### Post by Darkness3477 on 2006-03-13
Cool. I was more asking if you could make the same kinda things using PHP that you can when you use Javascript.... Anyway.

I had a bit of a squiz and it all looks very interesting,

---

### Post by hagen00 on 2006-03-13
PHP is a server side scripting language and Javascipt is a client side scripting language. 

Now what is the difference you ask? 

If you want to build shopping carts, forums, blogs, connect to a database or anything like that, you will need a server side scripting language like PHP. 

If you want to have cool stuff that happens *without * the page having to be refreshed, such as image rollovers, a bouncing ball across the screen, dynamic dropdowns, cool looking tooltips, then you need a client side scripting language like Javascript. 

So ask yourself what you want to do. 

Cheers

---

### Post by LordHunter317 on 2006-03-13
PHP is a *terrible* language.  And I'm not saying that as a troll.  Virtually everything wrong you can do in a language they did.  Even perl isn't nearly as bad.

Anyway, if you use PHP, make sure it's PHP5, make sure you make use of hte PEAR framework, and make sure you don't use the mysql driver, use PEAR::DB, ADODB, or mysqli instead.  Perferably, don't use MySQL at all, but that's another discussion.

I'd encourage you to look at another language, such as perl or python or even ruby.  Most of my web development is J2EE and ASP.NET and those are options, but they'll require more learning before you build anything real and useful.

---

### Post by dermotti on 2006-03-13
ruby on rails

---

### Post by Vinze on 2006-03-13
[QUOTE=LordHunter317]PHP is a *terrible* language.  And I'm not saying that as a troll.  Virtually everything wrong you can do in a language they did.  Even perl isn't nearly as bad.

Anyway, if you use PHP, make sure it's PHP5, make sure you make use of hte PEAR framework, and make sure you don't use the mysql driver, use PEAR::DB, ADODB, or mysqli instead.  Perferably, don't use MySQL at all, but that's another discussion.

I'd encourage you to look at another language, such as perl or python or even ruby.  Most of my web development is J2EE and ASP.NET and those are options, but they'll require more learning before you build anything real and useful.[/QUOTE]
I don't see what's the problem with PHP, it's really awesome. You should give arguments why it's so bad. If you want some tutorials on PHP, be sure to check out the basic PHP tutorial at [http://www.Tizag.com/phpT](http://www.Tizag.com/phpT) and then, when you want to go in a bit deeper, you can find tutorials on all sorts of PHP subjects on [http://Pixel2Life.com](http://Pixel2Life.com)

---

### Post by Thirion on 2006-03-13
[QUOTE=LordHunter317]PHP is a *terrible* language.  And I'm not saying that as a troll.  Virtually everything wrong you can do in a language they did.  Even perl isn't nearly as bad.

Anyway, if you use PHP, make sure it's PHP5, make sure you make use of hte PEAR framework, and make sure you don't use the mysql driver, use PEAR::DB, ADODB, or mysqli instead.  Perferably, don't use MySQL at all, but that's another discussion.

I'd encourage you to look at another language, such as perl or python or even ruby.  Most of my web development is J2EE and ASP.NET and those are options, but they'll require more learning before you build anything real and useful.[/QUOTE]

If PHP is terrible - why is it used? Many Forums, CMS, Wikis, Blogs, ... are running with PHP and it's working.

If you want to learn to make good websites you'll need to learn PHP. PHP is easy and much used.

For a beginner it's NOT useful to learn J2EE or ASP.NET and also PEAR won't be useful at the beginning. Learn PHP and you'll be able to make little but powerful programs for the web.

PHP is, as mentioned a server side language and is needed to store Data to a Database, make Logins and Sessions, create a page out of some Templates and so on. JavaScript is not always needed, mainly to make Popups, change something on the Website or to check if the input of Formulars are right. You'll need both, but i you have experiences with C++ and Python both should be no problem.

By the way, you should learn CSS if you don't know that.

Michael

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=Vinze]I don't see what's the problem with PHP, it's really awesome.[/quote]Not compared to everything else out there.

>  You should give arguments why it's so bad.With pleasure, and off-hand:[list][*]Lack of namespaces.  This means groups of releated functions are written as group_a(), group_b() (e.g., pgsql_connect(), pgsql_query()).  This is terrible for readability.[*]Lack of required variable declarations.  This has two problems:```
$abc = "bar";
echo $acb; // Bug, should have been $abc
```[*]Lack of scoping outside function scope (and class scope, now).  This creates a problem if you do something like:```
require('include/somescript.php');    // This uses $foo

$foo = "myvalue";
somescript_function(); // Doesn't  want 'myvalue' in $foo
```This means you have to walk all your included files to verify they don't cause any problems.[*]Lack of a standard, fully functional, universal database access layer.[/list]

---

### Post by Kurt` on 2006-03-13
PHP is not a good language for people new to web programming/scripting in general, as there are many pitfalls. Example:

```
<?php

        $var = "this is a string";

        if(0 == $var)
                echo "why hello there :)";

?>
```

Running (viewing in a browser) that script will display "why hello there :)". Why? Because == isn't a "type-safe" comparison, and the string will be converted to binary 0 for whatever reason. The proper way to do the above comparison would be:


```
<?php

        $var = "this is a string";

        if(0 === $var) // note: 3 equals signs
                echo "why hello there :)";

?>
```

Even a simple oversight can be a security nightmare for your web application (forums, dynamic content site).

This is just one of many problems that newbies to PHP will face. After 2 years of doing PHP, I feel pretty confident in my ability to write solid code, and I like PHP very much. However I do not recommend it as one of your first languages.

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=Thirion]If PHP is terrible - why is it used?[/quote]MySQL is also terrible, why is it used?  They got popular for whatever reason (no one really knows) and now they're used because they're popular and they're what everyone *has heard of.*

IOW, your argument is a non-sequitur: popularity has nothing to do with quality: an example would be American cars in the 80's and early 90's.  There were more of them on the road, but they were inferior in quality to their Japanese counterparts of that time.

> Many Forums, CMS, Wikis, Blogs, ... are running with PHP and it's working.For certain definitions of working, yes.  This forum installations has been compromised on two occassions I can remember.  PHPBB2 is a security nightmare.  So is PHP-Nuke, which for a while had a major security exploit nearly every week for a long time.

> If you want to learn to make good websites you'll need to learn PHP.No, I don't see how this is true in the least.  Plently of major stuff is done without any PHP.

Learning how to do server-side web programming is important.  Choice of language is less so.  I'd recommend against learning PHP to prevent learning bad habits initially and possibly learning it in the future if a job requires it.

> For a beginner it's NOT useful to learn J2EE or ASP.NETWhy not?  They're heavily used in the enterprise and can do all sorts of things PHP can't.  

> and also PEAR won't be useful at the beginning.Yes, it will.  The very fact you even said this highly suggests you have no clue what you're talking about.  PEAR has an incredible set of useful utility stuff that nearly every website can leverage.

---

### Post by commodore on 2006-03-13
If you want your site to look cooler then AJAX is the way ;)

---

### Post by Vinze on 2006-03-13
> **LordHunter317]Not compared to everything else out there.

With pleasure, and off-hand:[list][*]Lack of namespaces.  This means groups of releated functions are written as group_a(), group_b() (e.g., pgsql_connect(), pgsql_query()).  This is terrible for readability.[*]Lack of required variable declarations.  This has two problems:```
$abc = "bar" said:**
> 

What's the problem with the above?

> 
[*]Lack of scoping outside function scope (and class scope, now).  This creates a problem if you do something like:```
require('include/somescript.php');    // This uses $foo

$foo = "myvalue";
somescript_function(); // Doesn't  want 'myvalue' in $foo
```This means you have to walk all your included files to verify they don't cause any problems.

Emm... Wait. Is it me, or would somescript_function() first declare $foo to be global before it would be affected by the $foo = 'myvalue'?
[QUOTE]
[*]Lack of a standard, fully functional, universal database access layer.[/list]

Yeah, so?

---

### Post by knalle on 2006-03-13
> **LordHunter317]
Lack of namespaces.
[/QUOTE]
i agree php is terrible for reading but including namespace into a language does it even more unreadable, one of the first things programmers in java strugle with is to undertand the namespace, and even in professional packages a lot of strange usage of namespaces can clutter code as much as help it

[QUOTE=LordHunter317]
Lack of required variable declarations.
[/QUOTE]
isset() is used in php to prevent variable borks, in java you have the equals() and == operator

[QUOTE=LordHunter317]$foo = "myvalue" said:**
> This means you have to walk all your included files to verify they don't cause any problems. 

tru, but good practice in all programming languages is to wrap code into functions, and the functions does have variablescoope even in php

[QUOTE=LordHunter317]
Lack of a standard, fully functional, universal database access layer.
[/QUOTE]
show me a "standard" "universal" sql database then

---

### Post by LordHunter317 on 2006-03-13
> **Vinze]What's the problem with the above?[/quote]Your code doesn't work.  


> Emm... Wait. Is it me, or would somescript_function() first declare $foo to be global before it would be affected by the $foo = 'myvalue'?$foo was declared within 'include/somescript.php' outside the function scope, yes.  The point is, there is no 'file level' scope, and there really ought to be.

> Yeah, so?It makes database programming all the more painful when I can't use the same functions to make database calls.  It makes abstraction far more difficult for a common set of operations.

[quote=knalle]i agree php is terrible for reading but including namespace into a language does it even more unreadabl[/quote]No, it doesn't.  It enhances readability, provided they're used correctly.  Unlike name prefixes, which always hurt readability.

> isset() is used in php to prevent variable borks,So you want me to wrap **every** variable access in:```
if (isset($foo))
    //something with $foo
else
    die('$foo not set') said:**
> in java you have the equals() and == operatorThey don't do the same thing as isset().

> tru, but good practice in all programming languages is to wrap code into functions,PHP's interpretation of a page makes that unwidely.  That's how misdesigned the language is.

> show me a "standard" "universal" sql database thenNo such beast exists, but I do perform **the same operations** on all SQL databases (e.g., connect, query, disconnect) meaning I should have an abstract layer that lets me perform these identical operations regardless of DB.  PHP has never provided a fully working, fully standard one.

---

### Post by knalle on 2006-03-13
[QUOTE=LordHunter317]No, it doesn't.  It enhances readability, provided they're used correctly.  Unlike name prefixes, which always hurt readability.
[/QUOTE]
ok, how should the namspace be implemented in php iyo?

[QUOTE=LordHunter317]So you want me to wrap **every** variable access?[/QUOTE]
yes if the variable is system critical, but this isn't really php's fault you know, this is because php is interprented language and not a compiled language with var checking

and equals() and == is the same in java, and the reason i mentioned java is because it is a compiled lanuage with var checks, but it still need runtime object check because opjects can be created at runtime

[QUOTE=LordHunter317]No such beast exists, but I do perform **the same operations** on all SQL databases (e.g., connect, query, disconnect) meaning I should have an abstract layer that lets me perform these identical operations regardless of DB.  PHP has never provided a fully working, fully standard one.[/QUOTE]

i wish for that too you know, neither php, java or c that i have programmed proved one single db api, it sux

---

### Post by knalle on 2006-03-13
i think its time for a reality check here, the question is not if php is ugly or not from a language view, hell its only for generating web pages with man!

you cannot be serious if you write an large application in php, and thus all these teoretical arguments about php's language shortcommings is really just criticising the honda for not being a lamborghini

---

### Post by Thirion on 2006-03-13
> MySQL is also terrible, why is it used? They got popular for whatever reason (no one really knows) and now they're used because they're popular and they're what everyone has heard of.

IOW, your argument is a non-sequitur: popularity has nothing to do with quality: an example would be American cars in the 80's and early 90's. There were more of them on the road, but they were inferior in quality to their Japanese counterparts of that time.

Ok - you're right.

> For certain definitions of working, yes. This forum installations has been compromised on two occassions I can remember. PHPBB2 is a security nightmare. So is PHP-Nuke, which for a while had a major security exploit nearly every week for a long time.

That's a problem of the program, not the language. You can write secure programs with every language and you can write unsecure programs with every language. The programs do what they need and you might find some which are secure. Where is the problem?

> No, I don't see how this is true in the least. Plently of major stuff is done without any PHP.

Learning how to do server-side web programming is important. Choice of language is less so. I'd recommend against learning PHP to prevent learning bad habits initially and possibly learning it in the future if a job requires it.

Of course it's possible without PHP. But PHP is at the moment a much used language and you should know it. PHP is really easy to learn and i think there's no problem if he learn PHP. If he decide later to use another language its no problem. If you are a PC Newbie it's better or not wrong to start with Windows because you might need it in your company later, too.

> Why not? They're heavily used in the enterprise and can do all sorts of things PHP can't. 

PHP is much easier to learn and use, much more webspaces support PHP than other languages and you should have known this if you want to work as a web program developper.

> Yes, it will. The very fact you even said this highly suggests you have no clue what you're talking about. PEAR has an incredible set of useful utility stuff that nearly every website can leverage.
PEAR is useful, of course. But if you are a beginner it's more useful to learn how a server sided program works and to know the import things of the language and what's different to C++ and other languages. If you are able to use PEAR you won't be a beginner and of course then you should use it. But we are talking about a beginner!

A little example from the real world. If you have a little child who wants to learn a language the child should learn the language which is spoken in the country, even if the language is *terrible* and you won't need the language later. But its much easier to learn and you won't waste much time, because you can use the language later and other languages are often similar to this language.

Michael

---

### Post by LordHunter317 on 2006-03-13
> **knalle]ok, how should the namspace be implemented in php iyo?[/quote]Simple.  Classes are declared into a namespace with a scoping directive:```
namespace mynamespace {
}
```And imported via using, just like C# or C++:```
using mynamespace said:**
> yes if the variable is system critical, but this isn't really php's fault you know,Yes, it is.

>  this is because php is interprented language and not a compiled language with var checkingAnd?   Interpreted doesn't mean you can't do static type and variable checking first.

> and equals() and == is the same in java,No, they're not.  The former may do a valuewise comparsion (i.e., do two objects have the same value) and the latter does a reference comparions (i.e., do they point to the same object in memory?[/quote]Consider this, for example:```
String a = "1";
int one = 1;
String b = Integer.ToString(one, 10);

System.out.println(a.Equals(b));
System.out.println(a == b);
```You'll get output of true and false.  They're not the same operation.  They have different meanings.

> but it still need runtime object check because opjects can be created at runtimeOnly in two specific situations: dynamic casting and reflection.  And both of which yield an instanteous error if you can't complete the operation, unlike PHP which attempts to continue for as long as possible.

> i wish for that too you know, neither php, java or c that i have programmed proved one single db api, it suxJava does have one, so you don't know what you're talking about.

---

### Post by Kurt` on 2006-03-13
```
$abc = "bar";
echo $acb; // Bug, should have been $abc
```

That will throw an error if you enable warnings. :)

[quote=vinze]Emm... Wait. Is it me, or would somescript_function() first declare $foo to be global before it would be affected by the $foo = 'myvalue'?[/quote]
Yes you are correct, therefore the example would not be a problem after all. :)

---

### Post by knalle on 2006-03-13
> **LordHunter317]And?   Interpreted doesn't mean you can't do static type and variable checking first.[/QUOTE]
no it means php chooses not to do it because its time consuming, and php aims to render html as fast as possible, what ever the cost

[QUOTE=LordHunter317]No, they're not.  The former may do a valuewise comparsion (i.e., do two objects have the same value) and the latter does a reference comparions (i.e., do they point to the same object in memory?Consider this, for example:```
String a = "1" said:**
> 
excuse me are you trying to fool me or don't you simply know better? The reason that example works for you is because Integer and String objects are immutable, see the java documentation

[QUOTE=LordHunter317]Java does have one, so you don't know what you're talking about.
and if you're talking about jdbc, oh yeah thats really universal and works perfectly on oracle, db2 and mysql and pgsql without any vendor spesific SQL or cursor movement, you obviously just discovered jdbc, good for you

and why start with this shitthrowing i wanted an actuall discuassion about programming languages, not being told by an lamer that i don't know what im talking about, jeezes

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=knalle]i think its time for a reality check here, the question is not if php is ugly or not from a language view, hell its only for generating web pages with man![/quote]What?  This makes no sense.

But the cleanliness of the language is very relevant here.  If you're starting to learn, the worse things to learn are bad habits.  PHP, by design, tends to engender these habits if you're not very careful.  The same is true of several other languages.

The problem is that there is a ton of bad PHP code out there.  Which makes being careful hard.  Contrast this to C++, which tends to be very carefully authored, at least for learning material.

[quote=Thirion]
That's a problem of the program, not the language. You can write secure programs with every language and you can write unsecure programs with every language.[/quote]PHP makes this particularly difficult, however.  The included mysql driver before PHP5 didn't even support **parameterized queries**.  PHP is full of all sorts of security tricks that are half-assed and don't really fix the problems (e.g., magic_quotes_gpc, addslashes(), safe_mode).

Yes, it's not solely the language's fault, but the lack of any standardized, useful security facilities make these things very difficult.

> 
Of course it's possible without PHP. But PHP is at the moment a much used language and you should know it. PHP is really easy to learn and i think there's no problem if he learn PHP.Easy to learn doesn't mean good to learn.  C is arguably eaiser to learn than C++ but that's not a good thing.

And as I said, it's really easy to learn bad habits with PHP.  There's no good, authortative reference that teaches you good habits to my knowledge.

> PEAR is useful, of course. But if you are a beginner it's more useful to learn how a server sided program works and to know the import things of the language and what's different to C++ and other languages.What?  This statement makes no sense and is a non-sequitur.

> If you are able to use PEAR you won't be a beginner and of course then you should use it. But we are talking about a beginner!Huh?  using PEAR is no different from using any other classes in PHP...

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=Kurt`]That will throw an error if you enable warnings. :)[/quote]The point is, it should throw an error all the time.

> Yes you are correct, therefore the example would not be a problem after all. :)Yes, it would be.  Variables declared not in function scope are global everywhere.  This means that if you use that name accidently, you could break other code.

[quote=knalle]no it means php chooses not to do it because its time consuming, and php aims to render html as fast as possible, what ever the cost[/quote]That's not a good reason, though it is a reason.  It doesn't defend your statement though, you implied interpreted languages can't do static checks.  That's simply silly.

> excuse me are you trying to fool me or don't you simply know better?No, but it's apparent you do not.

> The reason that example works for you is because Integer and String objects are immutable, see the java documentation[b]I don't need to read it, but you do: [Object (Java 2 Platform SE 5.0)](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Object.html#equals(java.lang.Object)).  The documentation makes it clear the default implementation is equvalent to "==", but makes it clear that any implementation is free to override it provided it meets the rules above.

And I've written several classes that indeed, do so.  equals() is intended for valuewise comparions.  The fact that Integer and String are immutable have nothing to do with it: **it's clear from the test that equals() is not calling == or vice-versa.**  If they were, they'd yield the same result.

> and if you're talking about jdbc, oh yeah thats really universal and works perfectly on oracle, db2 and mysql and pgsql without any vendor spesific SQL or cursor movement,For the tasks I mentioned, it certainly does.  It cannot do **everything**, but for most applications, it's more than sufficient.  

At anyrate, it's better than what PHP provides.

> and why start with this shitthrowing i wanted an actuall discuassion about programming languages, not being told by an lamer that i don't know what im talking about, jeezesIt's apparent from multiple statments you've made that you have some fundamental gaps in your knowledge.  equals() and == aren't the same thing in Java.  They never have been.  They never will be.   They have totally different semantic meanings.

---

### Post by knalle on 2006-03-13
[QUOTE=LordHunter317]It's apparent from multiple statments you've made that you have some fundamental gaps in your knowledge.  equals() and == aren't the same thing in Java.  They never have been.  They never will be.   They have totally different semantic meanings.[/QUOTE]

hey shithead, i said isset() is used as equals() and == in java to prevent variable bork like null, you know NULL? ever done NULL check or is that below you the ulimate programmer.

and the reason i picked futher on it was that equals() and == is the same when it comes to strings and integers, but in your lamer example you didn't know that String and Int uses equals() for ==, i never said all java variables does, please don't try to make me say thing i don't you egofucking ******* that seems to have some issue with a: having a discussion b: php, 

now im looking forwar to a million post on how "i dont know shit" just because you did a mistake, hehehe i get some pizza

"you dont know shit" is by the way a very very good argument in any discussion, use it more and show your real character

poor bastard

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=knalle]hey shithead, i said isset() is used as equals() and == in java to prevent variable bork[/quote]And they're not.  They aren't equivalent: all three have different semantics.

>  like null,You didn't mention null checks originally.  That is a valid use of '==' and isset(), but not Object.equals() in Java.

> you know NULL? ever done NULL check or is that below you the ulimate programmer.I do them all the time, but they're irrelevant to my original point.

> and the reason i picked futher on it was that equals() and == is the same when it comes to strings and integers,**No, they're not.  My code above clearly proves that.**

>  but in your lamer example you didn't know that String and Int uses equals() for ==, No, they don't.  My code clearly proves it is overriden.  If you don't believe me, poke in the src.jar file in your JDK installation and you'll see they've indeed overriden equals().

**Answer me this: If they weren't overriden, how can the two operations return *different values***?  What you suggest is a logical impossibility.

> i never said all java variables does,Yes, you did.

> that seems to have some issue with a: having a discussion b: php, I have no issue with having a discussion.  I do have an issue with your personal attacks and the fact you can't cope with the fact you've made mistakes in what you've said.

poor bastard[/QUOTE]

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=knalle]now im looking forwar to a million post on how "i dont know shit" just because you did a mistake, hehehe i get some pizza[/quote]Except I never said that.  I said that you have a few fundamental gaps (which you do if you don't understand the difference between == and Object.equals()) and that you didn't know what you were talking about when it came to DB APIs, which you clearly did not.

> "you dont know shit"Perhaps, but I never said that.  You OTOH, have personally attacked me and insulted me several times.

---

### Post by knalle on 2006-03-13
[QUOTE=LordHunter317]No, they don't.  My code clearly proves it is overriden.  If you don't believe me, poke in the src.jar file in your JDK installation and you'll see they've indeed overriden equals().
[/QUOTE]

**Answer me this: If they weren't overriden, how can the two operations return *different values***?  What you suggest is a logical impossibility.

Yes, you did.

[QUOTE=LordHunter317]I have no issue with having a discussion.  I do have an issue with your personal attacks and the fact you can't cope with the fact you've made mistakes in what you've said.
[/QUOTE]

you seem very much like the kinda persions i avoid talking with because i wasn calling your names or accusing you for "not knowing shit" i was discussing php with you paranoia brain, then when i dissagrees with me, YOU start saying i don't know shit. I've been a professional java programmer since 1997, and that doesn't mean i know shit, but that shows that you attack me for "not knowing shit" even you don't know the single thing about me, your a freak, you should go to therapy for that

and the string 1 and the integer 1 is the same, ofcourse, but the String a1="hey and the string a2= "hey" actually is calcuated from its equal and they both return the same immutable reference.

---

### Post by GazaM on 2006-03-13
This thread seems to have turned into a why does / doesn't PHP suck thread, but I have no experience with PHP so I'm just gonna go ahead and answer the thread Author's original question as best I can...

If you simply want your page to have some nice effects and be a bit more fun for your users to browse, then what you're looking for is some pretty simple Javascript stuff. Check out [moo.fx]("http://moofx.mad4milk.net/") for a really nice, ready made Javascript library of nifty effects for your website. I'm making use of them in my new personal website project and I haven't got a clue about Javascript at all! It has really good documentation and forums from which you'll get all the help you'll need.

Now, if you want to make use of dynamic content and bigger and more complicated features under the hood of your website, there are a tonne of languages and methods to consider. The most popular are PHP, Ruby on Rails and Python (don't shoot me if I didn't mention the one you love, I may have missed out on one or two, I'm just trying to get this reply finished sometime today :P).

I've heard especially good things about Ruby on Rails, but I personally use Python. If you have full access to the server running your site, or you can get into contact with the administrator, then mod_python is a must when using Python. It opens up a lot of really cool opportunities, including using .psp pages just like you would a .php (meaning the python code is written directly into the xHTML)... for the afformentioned personal project I'm working on at the moment, I'm using purely .py files and writing pretty much a full backend in Python myself, including Templating etc. It's really easy, and since you have some experience in Python it may be a good choice for you.

Note that you can use both Javascript and Python (or RoR or PHP etc) in unison, and it's really not as hard as you might think. There are myriad tutorials available on the web for any type of language you find yourself using, so good luck in any case.

---

### Post by hod139 on 2006-03-13
Before this thread gets killed, hopefully a 3rd party can end the == versus equals argument. Equals and == are not the same, even for strings. From [http://www-128.ibm.com/developerworks/java/library/j-ebb0917a.html]("http://www-128.ibm.com/developerworks/java/library/j-ebb0917a.html")

> 
The equals() method compares the *characters* that make up String objects. It performs this comparison by putting the characters of the String objects into two char arrays and comparing the two arrays. The method returns true if all the elements of the char arrays match and false otherwise.
  
The == operator compares two object references to see whether they refer to the same *instance.* A pool of strings, initially empty, is maintained privately by the class String. All literal strings and string-valued constant expressions are interned there. You can also add your own strings to this pool by calling the intern() method. If the pool already contains a string equal to your String object, as determined by the equals(Object) method, then the string from the pool is returned. Otherwise, your String object is added to the pool and a reference to it is returned. It follows that, for any two strings s and t, s.intern()==t.intern() is true if and only if s.equals(t) is true.
  
To sum up: The equals() method determines whether two strings have the same *characters,* whereas the == operator determines if two operands refer to the same String *object.* == actually tests to see if the references in the variables point to the same memory address.
 

```

//adds "literal" to the intern pool
String strObj1 = "literal";  		

//uses "literal" from the pool
String strObj2 = "literal";	
			
//creates a new string.
String strObj3 =  new String("literal"); 	

//checks in the pool for a match and if found, returns the match.	
String strObj4 =  strObj3.intern();	            

//prints true - strObj4 and strObj3 have the same string.
System.out.println((strObj4.equals(strObj3));	

//prints false - strObj4 and strObj3 do not refer to the same 
//string object.
System.out.println((strObj4 == strObj3));      

//prints true - strObj4 and strObj2 have the same string.
System.out.println((strObj4.equals(strObj2));

//prints true - strObj4 and strObj2 refer to the same string object 
//in the pool.
System.out.println((strObj4 == strObj2));  
```

**edit**:  Added code examples

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=knalle]Yes, you did.=/quote]WTF?  I never suggested anything but that question above.  Answer or retract.



> you seem very much like the kinda persions i avoid talking with because i wasn calling your names or accusing you for "not knowing shit"And then you started. 

>  then when i dissagrees with me, YOU start saying i don't know shit.No, what I said is that you made some fundamentally incorrect statements.  One of those statements implies a large hole in your knowledge.

>  I've been a professional java programmer since 1997, and that doesn't mean i know shit, but that shows that you attack me for "not knowing shit" even you don't know the single thing about me,Non-sequitur: invalid appeal to authority.  And I never personally attacked you.  If you don't understand the difference between == and Object.equals() in Java, you have a fundamental gap in your Java knowledge.  

> our a freak, you should go to therapy for thatI'm not the one slinging insults.

> and the string 1 and the integer 1 is the same, ofcourse, but the String a1="hey and the string a2= "hey" actually is calcuated from its equal and they both return the same immutable reference.That's because constant strings are folded to the same memory location.

---

### Post by knalle on 2006-03-13
offf,,,

[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html)

equals() and == are not the same for object except String and Integers (and other immutable objects)

two independantly String that is character equal has the same memory reference in the jvm until its reassigned, i'm not pulling your legs here , instead of saying liar lair lair read alittle about the thing first.

and why the hell do you think i'm lying? what the hell do i gain from that? more bean points? oh, yeah thats what im really after, more bean points

grow up a little

god damn same thing when the admin password  bug was discovvered, idiots and freaks jumped on me an accused the messenger instead of actually testing it

---

### Post by knalle on 2006-03-13
[QUOTE=LordHunter317]And then you started. I'm not the one slinging insults.
[/QUOTE]

thats just shows your paranoia, you posted "Java does have one, so you don't know what you're talking about." and was waiting to kick me in the head withc jdbc, but i outflakned you that was all, so you said "so you don't know what you're talking about." as your great argument

oh king of logic, ruler of forums, always right always attached, its hard to be on top

---

### Post by knalle on 2006-03-13
[QUOTE=LordHunter317]Non-sequitur: invalid appeal to authority.  And I never personally attacked you.
[/QUOTE]

liar, and speed reader, i said i the same centence i said i was a java programmer that that doesnt mean i know shit, it just show that you dont know anything about me, and still you attack me

your got a terrible personal character, but i'm glad i dont have to deal with it

---

### Post by knalle on 2006-03-13
and whats next? why don't you correct my spelling or my english too?

but you got waaaay more forumpoint than me so you gotta be a hotshot of a guy, a real g

i think i might have wanered into forum lands where i don't belong, **** i got out of most linux zelot forums just to escape fuckers like you

are all linux forums like this? what to do

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=knalle]offf,,,

[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html)

equals() and == are not the same for object except String and Integers (and other immutable objects)[/quote]**That's still *wrong and not what you said anyway.***

> two independantly String that is character equal has the same memory reference in the jvm until its reassigned,No, they're not.  Only if they were constants to begin with.  Read what hod139 posted.

> i'm not pulling your legs here , instead of saying liar lair lair read alittle about the thing first.I've yet to make an error, and you've made several.  **In fact, you still have yet to make a correct statement about semantic differences between Object.equals() and ==**

> and why the hell do you think i'm lying?I don't think you're lying, I think you honsetly don't understand what's going on.

> grow up a littleYou're the one flinging insults.

> hats just shows your paranoia, you posted "Java does have one, so you don't know what you're talking about."And?  That's not an insult.  You posted something that's factually incorrect.   That means you don't know what you're talking about.

> and was waiting to kick me in the head withc jdbc, but i outflakned you that was all,No, you didn't.  You never refuted my claims.

>  so you said "so you don't know what you're talking about."**No, I said that originally, *and then YOU brought up JDBC.***

Your defense of yourself would be helped by actually keeping to how the events occurred.

> 
liar, and speed reader, i said i the same centence i said i was a java programmer that that doesnt mean i know shit,And you went on to say:> but that shows that you attack me for "not knowing shit" even you don't know the single thing about meWhich is attempting to use your Java experience from 1997 to imply that I shouldn't be refuting what you're saying.  It was an invalid appeal to authority, albiet a disguised one.

> and still you attack meI've done nothing of the sort.  I haven't even insulted you.  I'm not sure you understand what a personal attack is.

> your got a terrible personal character, but i'm glad i dont have to deal with itYou're the one making statements like this, not me.

> are all linux forums like this? what to doHave you considered admitting you were wrong, apologizing for your insults to me, and not posting in this thread anymore?

---

### Post by Thirion on 2006-03-13
Keep cool!

Perhaps PHP is not the right language for very big projects but it should be no problem to learn to write web programs with PHP. PHP is the most used web programming language and because of this it's not wrong to learn that. (It's not wrong to learn to use Windows, right? Its not very secure and Linux might be better but its not wrong to know Windows!).

LordHunter317 you are (perhaps) right,but your "problems" with PHP are not important for a beginner. If the starter of this tread will get professional he'll perhaps change the language but not much time will be lost.

Back to topic, i thinks thats more important than this endless discussion about professional programming.

Michael

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=Thirion]Perhaps PHP is not the right language for very big projects but it should be no problem to learn to write web programs with PHP. PHP is the most used web programming language and because of this it's not wrong to learn that.[/quote]That doesn't mean it's **a good thing to learn it either.**

This is **twice** you've made this same fallacy, please don't make me refute a third time.

> LordHunter317 you are (perhaps) right,but your "problems" with PHP are not important for a beginner. **Yes, they are, because they encourage bad habits.**  And as I said, **that's the most important thing to *not* develop.**

Please, either refute those statements or drop this line of reasoning.  I absolutely abhor having to make the same statements over and over again, and I shouldn't have to.

---

### Post by jerome bettis on 2006-03-13
then don't reply?  nobody reads your giant posts with quotes everywhere anyways.


personally, i'm a fan of j2ee.  but javascript isn't cutting it, i'm wondering if there's something better for client side stuff.  i haven't looked at php and i don't think i will, j2ee is pretty nice.  it seems like php is kinda like the python for web apps, not my cup of tea.

the complaint i have so far with j2ee is that the architecture is kinda complicated.  i really need to learn when to use a jsp, a servlet, a taglib, an ejb, etc etc before i go any further. kinda confusing for a beginner and suns documentation is crap - i need a book still.  once i learn how to architect a web app better things will be great.  also i can not get openejb to work with tomcat for my life!! argh

---

### Post by GazaM on 2006-03-13
Could you please explain what you meant by "it seems like php is kinda like the python for web apps" ?

---

### Post by Thirion on 2006-03-13
> hat doesn't mean it's a good thing to learn it either.

This is twice you've made this same fallacy, please don't make me refute a third time.
I didn't wrote it's a good thing to learn but he could try, couldn't he?

> Yes, they are, because they encourage bad habits. And as I said, that's the most important thing to not develop.

Please, either refute those statements or drop this line of reasoning. I absolutely abhor having to make the same statements over and over again, and I shouldn't have to.

If you write programs you develop, at the beginning you write code you'll later laugh about. At the beginning you make mistakes and time by time you get better and you make less mistakes. Perhaps he'll make much mistakes but if he gets better he learns to make less mistakes. Perhaps in future he won't use PHP because it's terrible and change the language, but he won't use the bad code he used before.

A beginner should start with an easy language and not with a difficult one. He'll make mistakes at the beginning but he'll develop. And the easiest way to write server side programs is PHP - or not?

I think you don't understand me the right way, that's my first english forum, sry for that.

Michael

---

### Post by KiwiNZ on 2006-03-13
Lordhunter317 and knalle please leave the personal stuff out of here .

Thanks

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=Thirion]At the beginning you make mistakes and time by time you get better and you make less mistakes. Perhaps he'll make much mistakes but if he gets better he learns to make less mistakes. Perhaps in future he won't use PHP because it's terrible and change the language, but he won't use the bad code he used before.[/quote]But that doesn't follow *per se*.  Bad habits, once developed are hard to break.

You can only correct them if you know you're writing bad code.  And there are very few PHP tutorials out there that show you how to write good code in the language.

> A beginner should start with an easy language and not with a difficult one. He'll make mistakes at the beginning but he'll develop. And the easiest way to write server side programs is PHP - or not?I'd say no, it isn't.  It's certainly no harder than Ruby or Python.

---

### Post by Darkness3477 on 2006-03-14
Well, that was a read and a half! 

Anyway, that reminded me of when I asked a question about Visual Basic, and I got replies saying that it "Teaches bad coding habbits" and then some other people saying "But it teaches to program rather painlessly" or something like that.... Anyway, I think I've made a decision.

I'll use a little bit of JavaScript where it's needed, and when the time comes where I may need to access a database or something, I'll use PHP. 
Actually, on a side note I was thinking about making a database of alot of work that I've done, and that some of my friends have done..... Anyway.

Also, as I want to learn to code actual applications (Rather then just web based stuff) I think I might look into Java. Just because it is being heavily used in the industry, is supposed to be reletively painless to learn, and is cross-platform (I'm all about equality between OS's).

So, basically I'm taking almost all of your advise, apart from the ones who mention Perl, Ruby and Python. 
Perl, well I cannot stand it. It may just be the syntax of it... I dunno, it's confusing enough just to read it. 
I've no experience in Ruby, and therefor have no biffs with it. And I like Python, as I could make more things within a week using Python, then I could after a month learning C++. I dunno, I just feel like learning something new, mostly because I can (My reply as to why I do not want to use Python for the backend of my websites...)

---

### Post by Darkness3477 on 2006-03-14
Also, I do agree with my good LordHunter (Sorry, couldn't help but writing that). It's important to learn good habbits from the start, rather then doing things the easy way but crappy way. Although I cannot back this up in a programming way, I know it's true with riding horses and other things. Which are surprisingly similar. You tell computers what to do (Programming) and you tell horses what to do (Yanking on the reigns, nudging with your legs or whatnot).

I love my comparisons.

---

### Post by Darkness3477 on 2006-03-14
[QUOTE=Thirion]

By the way, you should learn CSS if you don't know that.

Michael[/QUOTE]

Just felt I should answe that. I know CSS enough to use it to make an alright looking website and it gets validated so I know it works on all browsers... (Again, I like to make sure it works for everyone, as I know I hate it when other people are not polite enough to do the same.

---

### Post by Vinze on 2006-03-14
[QUOTE=Darkness3477]Well, that was a read and a half! 

Anyway, that reminded me of when I asked a question about Visual Basic, and I got replies saying that it "Teaches bad coding habbits" and then some other people saying "But it teaches to program rather painlessly" or something like that.... Anyway, I think I've made a decision.

I'll use a little bit of JavaScript where it's needed, and when the time comes where I may need to access a database or something, I'll use PHP. 
Actually, on a side note I was thinking about making a database of alot of work that I've done, and that some of my friends have done..... Anyway.

Also, as I want to learn to code actual applications (Rather then just web based stuff) I think I might look into Java. Just because it is being heavily used in the industry, is supposed to be reletively painless to learn, and is cross-platform (I'm all about equality between OS's).

So, basically I'm taking almost all of your advise, apart from the ones who mention Perl, Ruby and Python. 
Perl, well I cannot stand it. It may just be the syntax of it... I dunno, it's confusing enough just to read it. 
I've no experience in Ruby, and therefor have no biffs with it. And I like Python, as I could make more things within a week using Python, then I could after a month learning C++. I dunno, I just feel like learning something new, mostly because I can (My reply as to why I do not want to use Python for the backend of my websites...)[/QUOTE]
I think Java is a good place to start for coding "real" applications, however, keep in mind that it is terribly slow, so that wouldn't be good for the popularity of the program (though there are very good Java programs), but then again, it's also cross-platform so that could deliver more audience :D

---

### Post by LordHunter317 on 2006-03-14
[QUOTE=Vinze]I think Java is a good place to start for coding "real" applications, however, keep in mind that it is terribly slow,[/quote]Java's only slow if your application is CPU-bound or coded poorly.

---

### Post by hod139 on 2006-03-14
[quote=Vinze]I think Java is a good place to start for coding "real" applications, however, keep in mind that it is terribly slow ...[/quote]

I really want to second LordHunter317 on the speed of Java.  Some benchmarks will even say [Java is faster]("http://kano.net/javabench/"), though some people have complained about the methodology in that benchmark.  One set of comaparison benchmarks that I think did a pretty good job (It's really difficult to compare to languages based on various language specific options) can be found [here]("http://www.freewebs.com/godaves/javabench_revisited/") or for just the [results/graphs here]("http://www.freewebs.com/godaves/javabench_revisited/results.htm").  The author of these benchmarks tried his best to produce optimimal settings for each complier/language. The clear winner is Intel's C++ complier winning 12 of 14 tests (usually by a large margin); but I'm guessing most of us here are not using Intel's non-free complier but are using GNU's g++ complier.  Here I would say that in 9 out of the 14 tests (author claims 10 but on one test the margin of victory is very small), g++ beats Java.  

Sorry for the long post, but I get aggravated when people always say "Java is slow" without any proof.  The JVM has come a long way since it's 1.1 days.  Also, an argument can be made that the development time for Java applications is less than the time for C++ apps, and the possible small loss in performance is unimportant with the large loss is cost of development.

---

### Post by Thirion on 2006-03-14
Sure it's good to learn good habbits from the beginning but it's more important to start writing programs and not to stop that because it's too difficult. And your first post really seemed a little bit like "start with a very difficult language otherwise you won't be able to write programs later".

In my opionion it's the most important to start writing programs when you are young. I started writing HTML, then senless JavaScript and then PHP. At the beginning i didn't used $_POST['var'] and my code was often bad (e.g. very much database-querys, wrong way of solving problems, ...) but i learned how to write programs, that it's a nice hobby and i got a nice project. Now i think i'm much better but of course not very good. But in some years, after studiing informatics that will b e better.

If you want to write professional programs and want to get professional developer in the next 1-2 years it's of course wrong to choose PHP - but in my opinion not for a 15 years old person who wants to write programs as a hobby.

That's my opionen and i think if i had posted this thread with the age of 14 or 15 in a forum and there were only your post, i would waste time with Java and ASP net and at the end i would develop PHP because it's much easier for me.

Darkness3477, perhaps AJAX, a JavaScript technology could be interesting for you.

Michael

---

### Post by Darkness3477 on 2006-03-15
[QUOTE=Thirion]
In my opionion it's the most important to start writing programs when you are young. I started writing HTML[/QUOTE]
I started with HTML too, aster a friend suggested it.
[QUOTE=Thirion]
If you want to write professional programs and want to get professional developer in the next 1-2 years it's of course wrong to choose PHP - but in my opinion not for a 15 years old person who wants to write programs as a hobby.
[/QUOTE]
I don't want to just write hobby programs. My goal is to go to Uni and do CS so I can do something with Computers. It may, however, not be something with programming (Maybe an admin or something....). However, I have been told that most IT jobs do contain a little bit of programming work. 
BUt, for the time being I just want to learn as much as I can about programming, especially web based stuff because I like making sites, and security stuff which go together quite well.
[QUOTE=Thirion]

That's my opionen and i think if i had posted this thread with the age of 14 or 15 in a forum and there were only your post, i would waste time with Java and ASP net and at the end i would develop PHP because it's much easier for me.

Darkness3477, perhaps AJAX, a JavaScript technology could be interesting for you.

Michael[/QUOTE]

I don't think that if you started to learn something then gave up after awhile in pursuite of something esle, that it would be a waste of time. Everything you learn is useful, even if it only becomes useful when you remind yourself that you have the ability to learn something knew.

Anyway, I think that I may continue with Python for my little apps I make, as it's a fun language. However, on the webbased programming language I Should choose, I've no idea. PHP sounds and looks nice, but some things that have been said in here are making me look more closely into it. I might even pick up Perl, just as it's handy to have when using a Linux Distro (Even though I don't like the look of it). 

Thankyou to everyone who posted in this forum, your input has been most appreciated and taken into account.

Toodles.

---

### Post by zetsumei on 2006-12-22
to the topic starter here are a few links for some php/mysql help

[http://www.php.net/manual/en/](http://www.php.net/manual/en/)
[http://www.pixel2life.com/tutorials/php_coding/](http://www.pixel2life.com/tutorials/php_coding/)
[http://dev.mysql.com/doc/refman/5.0/en/index.html](http://dev.mysql.com/doc/refman/5.0/en/index.html)

and PHP/MySQL is an awesome language, I know it and I'm still learning it.

---

### Post by pmasiar on 2006-12-22
> **Darkness3477 said:**
> 
I don't want to just write hobby programs. My goal is to go to Uni and do CS so I can do something with Computers. It may, however, not be something with programming (Maybe an admin or something....).

Anyway, I think that I may continue with Python for my little apps I make, as it's a fun language. However, on the webbased programming language I Should choose, I've no idea. PHP sounds and looks nice, but some things that have been said in here are making me look more closely into it. I might even pick up Perl, just as it's handy to have when using a Linux Distro (Even though I don't like the look of it). 



Python is great web programming language. With plan cgi module and cgitbm you can start in no time. With Ajax and Turbogears you can do cool things.

And coolest thing is that all you learn for web programming you can use also for command line programs. Or link with big libraries.

---

