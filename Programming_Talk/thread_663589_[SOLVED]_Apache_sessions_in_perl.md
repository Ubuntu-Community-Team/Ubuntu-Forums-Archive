---
title: "[SOLVED] Apache sessions? in perl"
date: 2008-01-10
forum: Programming Talk
---

### Post by teryowen on 2008-01-10
Im currently writing a program where im making a login system, basically all the users and encrypted passwords are stored on a MySQL database. So i am able to create users and verify if the credintials are correct.

Now what i need to do is create sessions. I am using apache and im not really sure how to go about it. Once the user logs in i know how to generate it but how do i store it in the URI or URL and then every time they jump to a restricted page how do i make sure their session is valid with what was giving in the begging. So basically if the session is correct it loads the page but if its wrong or non existence it redirects to the login page.

I would really appreciate some help with this, either a really good tutorial somewhere or if someone would be kind enough to explain it.

By the way im using perl. 

Thanks in advance.

---

### Post by teryowen on 2008-01-12
bump. help anyone?

---

### Post by pmasiar on 2008-01-12
Google says (searching CPAN) [http://www.google.com/search?q=perl+cpan+session](http://www.google.com/search?q=perl+cpan+session) :
[http://search.cpan.org/dist/Apache-Session/](http://search.cpan.org/dist/Apache-Session/)
[http://search.cpan.org/dist/CGI-Session/](http://search.cpan.org/dist/CGI-Session/)

---

### Post by teryowen on 2008-01-12
thanks for the reply, i searched up on there but still having difficutly comprehending :S

but ill keep trying.

---

### Post by pmasiar on 2008-01-13
Perl's way of doing web apps is quite hard. More modern languages, like Python or Ruby, have web app frameworks which solve a lot of repetitive tasks, like session is. If you are reasonable Perl hacker (beyond beginner), you will learn eithet Python or Ruby in a week, max.

If you have to stick to Perl, at least use some of the web frameworks, even if they cannot match simplicity of Python/Django or Ruby/Rails. Years ago when I was hacking Perl, I used CGI::Application (very lightweight, but still MVC) and I believe it is still around, give it a try.

If you are Perl beginner, and don't have resident Perl guru to help you out, don't waste time and switch to Python/Django.

---

### Post by teryowen on 2008-02-17
So I figured it out a while ago but I thought i would share the solution:

To get sessions working under perl with apache and mysql I used CGI::Session and the driver for mysql, heres the code for creating the session:

```

use CGI::Session;
use CGI::Session::Driver::mysql;
use webDB; 

$db=webDB::connect("db","user","pw");

$session = new CGI::Session("driver:mysql", undef, { Handle => $db, TableName => "sessions" } );   #makes the session in table sessions the table should have an id column and an a_session column at the least

$session->expire('+8h'); #the expiration of the session

$id=$session->id();  #returns the session id which was generated

$session->param("username", $username); #stores $username in the session under username

$session->flush(); #syncronizes the buffer with the database

print STDOUT '<META HTTP-EQUIV="refresh" CONTENT="0;URL=whateverv.pl?',"$id",'">'; #redirects user with the session to whetever.pl 
```

Heres the code on another page where it will test if the user is logged in
```

$id=$ENV{QUERY_STRING}; #Get the session id passed through

$session = new CGI::Session("driver:mysql", $id, { Handle => $db, TableName => "sessions"}); #gets the session which was passed

$username=$session->param("username"); #Get the username from the session

```

you can also test for the ip

```

$ip_stored=$session->param("_SESSION_REMOTE_ADDR"); #getting ip stored in the session

$ip_remote=$ENV{REMOTE_ADDR}; #getting remote ip

```

Then you can compare the 2, this adds more security.

That should do it, i know when i started with this stuff it was kind of hard finding the right thing so hopefully this will help whoever interested.

---

### Post by shawnhcorey on 2008-02-17
> **pmasiar said:**
> Perl's way of doing web apps is quite hard.

More Perl bashing?

I got news for you:  the web, or as it was once known, the world-wide web is not set up for sessions!

Any sort of sessions set up on it will be flakely, not because of the language their written in, it's because they were never meant to be sessions in the first place.

No, Perl, Python, Ruby, any language you care to mention will not get around this.

I have dug into Apache trying to find why two different people, in two different parts of the country, at two different times, had the same session.  And everything I found lead to something else, something outside of Apache, that was causing the problem.  All the logs and traces we put on the input to Apache said it was coming from the same session, even the ones we knew were different.

YOU CANNOT DO SESSIONS ON THE WEB!

Well, maybe, you can get away with liteway sessions, but don't bet the farm on them.

In other words, don't blame your tools, blame the cause of your problems (and that's not Apache, it's the WWW).

---

### Post by pmasiar on 2008-02-18
> **shawnhcorey said:**
> 
No, Perl, Python, Ruby, any language you care to mention will not get around this.

Good web frameworks have sessions included. At least Python and Ruby does.

**Edit:** I meant: Python and Ruby **frameworks** do.

OP said that he has hard time comprehending it (and I am not surprised) so I suggested next step: use decent framework which does is out-of-the box.

Of course Perl expert like you can figure it out, but OP apparently cannot. Overcoming hard problems builds character, using simple tools solves problems easy. IMHO it is up to OP to decide now if priority is build character or solve problems :-)

> YOU CANNOT DO SESSIONS ON THE WEB!

Maybe you use again some different definitions of some words like in the other thread, but definitely many people including me **CAN** use sessions in our web applications. :-)

---

### Post by slavik on 2008-02-18
> **pmasiar said:**
> Good web frameworks have sessions included. At least Python and Ruby does.

OP said that he has hard time comprehending it (and I am not surprised) so I suggested next step: use decent framework which does is out-of-the box.

Of course Perl expert like you can figure it out, but OP apparently cannot. Overcoming hard problems builds character, using simple tools solves problems easy. IMHO it is up to OP to decide now if priority is build character or solve problems :-)



Maybe you use again some different definitions of some words like in the other thread, but definitely many people including me **CAN** use sessions in our web applications. :-)
Sorry, but I can't agree with you.

Decent framework that supports sessions? Pardon me, but I don't think that Python was conceived as a web framework, furthermore in the wikipedia page for Python, the following is stated:
> Python was conceived in the late 1980s[4] by Guido van Rossum at CWI in the Netherlands as a successor of the ABC programming language capable of exception handling and interfacing with the Amoeba operating system.[5]

It wasn't even conceived as a teaching language (which Scheme was). Neither Python, nor Ruby can even remotely be considered frameworks. They are languages. The reason Perl was used to create dynamic HTML was because it was conceived as a text processing language (like AWK) which could also be used for programming and such languages inherently make things in the WWW easier.

As for what is a simple tool to solve an easy problem, I think you might be reffering to PHP. PHP is when you take Perl and make it easier to use for creatic dynamic HTML.

If you want to learn how to use a sledgehammer and can lift it, then learn how to use it by practicing, not by playing with a hammer or a screwdriver.

---

### Post by lnostdal on 2008-02-18
> **shawnhcorey said:**
> 
I have dug into Apache trying to find why two different people, in two different parts of the country, at two different times, had the same session.  And everything I found lead to something else, something outside of Apache, that was causing the problem.  All the logs and traces we put on the input to Apache said it was coming from the same session, even the ones we knew were different.


you might know this, but apache has nothing to do with the handling of sessions

a session is defined by an ID that is stored on both the server and the client(#1)

the server stores the ID in a variable in your script or in the framework you're using

the client stores the ID in either a cookie(#1) or stores it in the URL and supplies this ID for every HTTP request it does to the server

..so for each HTTP request done by the clients the server will simply lookup the session-data stored on the server that is associated with the session ID the client supplied and "use that" to handle the request and the response to the client

these two clients you are talking about must somehow have gotten the same session ID .. every browser has a feature that lets you browse the "cookies" stored and one can then delete a cookie .. so these clients must do this (delete the cookie that represents or identifies the session in question), and this will lead to both clients supplying no ID on their next request to your application/server, which in turn will force your application/server to generate two new unique session IDs to these clients

edit:
you can of course solve this on the server side also by simply deleting the session these two clients currently are sharing .. this will force the server to generate a new session ID, and thus session - for each client


#1: there are other schemes like using the IP of the client to identify that as a session, but that is a stupid idea and no one does it - or should do it, so i won't talk about that

#2: cookies are just simple name/value pairs stored in the browser

---

### Post by pmasiar on 2008-02-18
> **slavik said:**
>  I don't think that Python was conceived as a web framework,

Sorry, I typed too fast. I ment "Python and Ruby web app frameworks", not language itself, of course.


> [QUOTE]Python was conceived in the late 1980s[4] by Guido van Rossum at CWI in the Netherlands as a successor of the ABC programming language capable of exception handling and interfacing with the Amoeba operating system.

It wasn't even conceived as a teaching language (which Scheme was).[/QUOTE] 

ABC was language for non-programmers, scientists. Python was conceived as scripting language for Amoeba.

> As for what is a simple tool to solve an easy problem, I think you might be reffering to PHP 

Yes, but solving problem in PHP creates messy solution, not a clean one. Probably it does not feel so for an ardent Perl supporter :-)

---

### Post by teryowen on 2008-02-18
Wow, i didnt intend on this debate happening.

To my knowledge which might be very limited, Perl is a very reliable and durable language, unlike php which is useally for fast easy set up but tends to break mroe often and is very bad when it comes to security.

---

### Post by slavik on 2008-02-18
There are security problems with any language that can access the underlying system (and sometimes, it doesn't even need that), That is why you have to learn to write secure code.

As for me being an ardent Perl supporter, I am not. Think of me as someone to counter your "Learn Python ..." attitude. :)

---

### Post by lnostdal on 2008-02-18
if you want to see someone flame Perl check out our Erik Naggum back when he was active: [http://groups.google.no/group/comp.lang.lisp/msg/fc76ebab1cb2f863](http://groups.google.no/group/comp.lang.lisp/msg/fc76ebab1cb2f863) .. isn't he great? =)

he has some very nice posts about other topics also .. even though many "hate" him -- i really miss his posts, as they had some truly great insights or points of view

(edit: these days he seems to be wasting time trying to explain common sense to people on (mostly norwegian i believe) forums about religion/politics .. futile imho)

---

### Post by slavik on 2008-02-18
> **lnostdal said:**
> if you want to see someone flame Perl check out our Erik Naggum back when he was active: [http://groups.google.no/group/comp.lang.lisp/msg/fc76ebab1cb2f863](http://groups.google.no/group/comp.lang.lisp/msg/fc76ebab1cb2f863) .. isn't he great? =)

he has some very nice posts about other topics also .. even though many "hate" him -- i really miss his posts, as they had some truly great insights or points of view

(edit: these days he seems to be wasting time trying to explain common sense to people on (mostly norwegian i believe) forums about religion/politics .. futile imho)
Everyone, let's learn Lisp ... forget everything else ...

---

### Post by lnostdal on 2008-02-18
> **slavik said:**
> Everyone, let's learn Lisp ... forget everything else ...

everyone is already doing this .. "slowly but surely, the programming world is finding Lisp..."

just look at where we are headed with C#/.NET and recent (or upcoming) developments in Java/JVM (mainstream) ..  the popularity of "modern"(#1) languages like Python and Ruby are also sure signs that this is in fact already happening

..all the recent changes or additions are stuff or ideas that already exist in Lisp -- or could be implemented in Lisp without having to change the compiler or wait for a new version of the compiler/language .. (you instead extend the language in the language itself when using Lisp; it's a programmable programming language)

why should you not welcome these changes or this direction? .. they are definite improvements over the current situation

for me these are very exciting times .. we now have mainstream corporations actually interested in improving the situation around programming and programming languages .. even MS is active here -- we should be also

#1: "Lisp nearing the age of 50 is the most modern language out
there. GC, dynamic, reflective, the best OO model extant including
GFs, procedural macros, and the only thing old-fashioned about it
is that it is compiled and fast."   
-- Kenny Tilton, comp.lang.python

---

### Post by slavik on 2008-02-18
I meant it as a satirical response. :)

But that's the interesting thing about Lisp (IMO) is that the result of a Lisp procedure is not the result but another procedure that produces the result. That is why it is great for AI.

But Lisp is difficult to teach to someone who had Python implanted into their head. ;) (or C, as is the case for me), that is why there is Scheme. :)

---

### Post by pmasiar on 2008-02-18
> **slavik]Everyone, let's learn Lisp ... forget everything else ...[/quote]

[QUOTE=slavik said:**
> I meant it as a satirical response. :)

Good, because I considered it a flamebait and stupid namecalling - personal attack. 

And in that case, you forgot to add a smiley.

Would you like if I replied on any/all your comments "OK lets all drop everything and switch to Perl?" Can we discuss issues in hand calmly without associating advice given with a favorite language of a poster?

> But Lisp is difficult to teach to someone who had Python implanted into their head. ;) (or C, as is the case for me), that is why there is Scheme. :)

Maybe for C-heads like you it might be hard :-) (you admitted it yourself), but I can see relation of Lisp and Python's list comprehension. What makes Lisp hard for me to dive into is syntax, with it's lack of differentiating between data and code. Seven  parens closing definition is something I dread to encounter... :-)

---

### Post by slavik on 2008-02-18
> **pmasiar said:**
> Good, because I considered it a flamebait and stupid namecalling - personal attack. 

And in that case, you forgot to add a smiley.

Would you like if I replied on any/all your comments "OK lets all drop everything and switch to Perl?" Can we discuss issues in hand calmly without associating advice given with a favorite language of a poster?



Maybe for C-heads like you it might be hard :-) (you admitted it yourself), but I can see relation of Lisp and Python's list comprehension. What makes Lisp hard for me to dive into is syntax, with it's lack of differentiating between data and code. Seven  parens closing definition is something I dread to encounter... :-)
if you say "let's all switch to Perl", I won't argue. ;) (even though using a single language is a problem in search of a problem).

as for the parenthesis, I have the same attitude towards differentiating blocks by using indentation.

here's an interesting view on creating documents ... in word/writer it is content, format, edit. In something like LaTeX, is format while you input content. As in, if you need to put in the sum formula, in word/writer you put in some kind of a statement of what formula goes there, in LaTeX, you just write the formula function that makes the sum formula.

When I write C code, it is code, then indent. In Python it is indent while coding and this approach just doesn't suit me, sorry.

As for sessions, since I am not a web dev, is it possible for client A to give all his info to client B and for client B to appear as client A to the server? (to move session from one system to another).

---

### Post by teryowen on 2008-02-18
Its possible to transfer sessions if the server thats issueing the sessions is not checking for IPs then yes it can be giving to another client. Or if the client decides to spoof their IP then its also possible.

---

### Post by pmasiar on 2008-02-18
> **slavik said:**
> if you say "let's all switch to Perl", I won't argue. ;) 

No. Been there, done that, run away screaming, so thanks but no thanks: no more Perl for me, I hope :-) I was lazy to write up my own reasons, but I linked two rants I agree with and written more eloquently than I can, in [ Why I love/hate Perl](http://ubuntuforums.org/showthread.php?t=577596) (post #34)

Enjoy, or disagree! :-)

---

### Post by lnostdal on 2008-02-18
> **slavik said:**
> I meant it as a satirical response. :)

hehe, ok -- it's kinda hard to transfer intent via text sometimes =)

> 
But that's the interesting thing about Lisp (IMO) is that the result of a Lisp procedure is not the result but another procedure that produces the result. That is why it is great for AI.


i think you're talking about macros here .. well, more generally macros are great when creating abstractions .. and you need a lot of abstraction when dealing with a lot of complexity .. and AI usually has some of that so that's where, or why, macros are nice

they allow you transform or generate code in a 100% safe way as an extra step before actual compilation happens .. this is usually extremely hard to get right in other languages but is trivial in lisp because the language itself is a direct representation of the AST and you can manipulate it directly and freely using all the tools provided by the language, and also even your own user-defined tools/functions

> 
But Lisp is difficult to teach to someone who had Python implanted into their head. ;) (or C, as is the case for me), that is why there is Scheme. :)


someone with a background in c or python should be able to learn it on their own actually (i did) .. [http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/) is nice 

it's challenging to learn something truly new .. if it wasn't challenging it probably wasn't worth learning in the first place as it was too similar to what you already knew (or know) .. think about it .. =)

---

### Post by slavik on 2008-02-18
the reason why it is difficult is because it requires a different way of thinking, that is why many people would not be able to program, because programming is a different way of thinking.

---

### Post by lnostdal on 2008-02-18
ok, so .. hm .. maybe it is a different-different way of thinking, yeah

*goes into a recursive loop* ... hehe :)

---

### Post by lnostdal on 2008-02-18
maybe posting some examples of how to do some simple tasks in each language would be interesting? ... as a way to compare in some way

i could either try to make it as similar as possible -- and/or as simple as possible (while still keeping a somewhat lispy-style) .. 

this talk about "lisp is hard" kind of bothers me to the point i'm asking "why?", and it would be interesting to see how similar a solution i could provide in lisp

edit: this might have already been done before in other threads .. i don't know

---

### Post by pmasiar on 2008-02-18
Yes, please do create examples, and do it in separate thread. It will be interesting learning experience.

I am sure that LaRoza will have no problem to link it from sticky FAQ.

---

