---
title: "Apache/Perl"
date: 2008-04-11
forum: Programming Talk
---

### Post by Oxnigarth on 2008-04-11
Hello.

I have just recently switched from windows to linux and everything seems to be going fine. But there is one thing that has been bugging me for a while and since I do not know a lot of people who use linux I guess this is the best way to find out.

On windows I used to program using the IIS with files .asp using Perlscript and I would like to know if there is a way to do the same process in linux, by this I mean creating some sort of file which is supported by apache and that when I write Perl script code a browser can interpret it.

I have already installed Apache2 on my computer.

I hope someone can tell me if this is possible and if it is how can I do it.

Thanks,
Ox.

---

### Post by LaRoza on 2008-04-11
> **Oxnigarth said:**
> 
On windows I used to program using the IIS with files .asp using Perlscript and I would like to know if there is a way to do the same process in linux, by this I mean creating some sort of file which is supported by apache and that when I write Perl script code a browser can interpret it.

I have already installed Apache2 on my computer.

I hope someone can tell me if this is possible and if it is how can I do it.


I don't know what "Perlscript" is, but you can use Perl with Apache easily.

Did you install LAMP? 

```

sudo tasksel

```

(select "LAMP" and don't unselect anything)

You need to start the script with a shebang pointing to the interpreter, and Apache has to know to interpret it as a program.

---

### Post by Oxnigarth on 2008-04-11
It is bascially perl but it has certain special features. It is used instead of CGI in windows you run it in the .asp files and the servers does all the process.

Anyway the thing is that is a way of developing perl websites without cgi supposedly because cgi is more  hackable.

I'll try to install that and I'll see if it works.

Ox.

---

### Post by LaRoza on 2008-04-11
> **Oxnigarth said:**
> It is bascially perl but it has certain special features. It is used instead of CGI in windows you run it in the .asp files and the servers does all the process.

Anyway the thing is that is a way of developing perl websites without cgi supposedly because cgi is more  hackable.

I'll try to install that and I'll see if it works.

Ox.

You can use mod_perl.

Remember, Apache isn't IIS.

---

### Post by Oxnigarth on 2008-04-11
So what you are saying is that I won't be able to program in the exact same way as I did for the IIS on windows.

For example basically what I am looking for is to be able to code like this:
*******************************************************
<%@LANGUAGE="Perlscript"$>

<$Response->Write("Hello World </ br>");

<%
$Request->Form("select")->Item();
%>

<html>
<body>
hello world
</body>

</html>
*******************************************************

With mod_perl is this possible? or is it going to be different.

Ox.

---

### Post by LaRoza on 2008-04-11
> **Oxnigarth said:**
> So what you are saying is that I won't be able to program in the exact same way as I did for the IIS on windows.

For example basically what I am looking for is to be able to code like this:
*******************************************************
<%@LANGUAGE="Perlscript"$>

<$Response->Write("Hello World </ br>");

<%
$Request->Form("select")->Item();
%>

<html>
<body>
hello world
</body>

</html>
*******************************************************

With mod_perl is this possible? or is it going to be different.

Ox.

There is probably some way to do that, but not that I know of or that is popular. You can try PHP, it may be what you want.

See my wiki.

---

### Post by Oxnigarth on 2008-04-11
I guess I will give PHP a try. I am little concerned though but of what I have seen PHP seems very friendly.

Now I know that PHP must have a way to connect to MYsql but what about XML?

And do you know if PHP handles hashes the way perl does? or does it support hashes at all??

---

### Post by Oxnigarth on 2008-04-11
I did some more research about my original question and it seems that this way of coding perl dependes on active state perl which is only for windows so I guess it is not possible :/

---

### Post by slavik on 2008-04-11
if you are very comfortable with Perl, using PHP should not be an issue since you can think of it as Perl for the web.

even using straight Perl will work (as it has been said), there are also frameworks for Perl web programming that do similar things (I think Mason is one of these).

unfortunately, I am not a web developer :(

---

### Post by Oxnigarth on 2008-04-11
I do not think that PHP will represent big problem for me but the thing that I like about Perl is the great number of modules that one can find on CPAN to help you solving almost any task.

Anyway Thanks everyone for your help :)!

---

### Post by pmasiar on 2008-04-11
If you are ready to stretch little your mind and skillset, consider instead of PHP using web application framework, one of those supported by Google App Engine. See [http://ubuntuforums.org/showthread.php?t=749285](http://ubuntuforums.org/showthread.php?t=749285)

If no< at least use PHP with a MVC framework, instead of mixing business logic, HTML presentation, and SQL data layer together. Read up Model-view-controller design pattern.

Perl has also plenty of MVC frameworks, I was involved with CGI::Application. But Python/Django+Turbogears and Ruby on Rails work much harder for you that Perl frameworks.

---

### Post by stevescripts on 2008-04-11
> **Oxnigarth said:**
> I did some more research about my original question and it seems that this way of coding perl dependes on active state perl which is only for windows so I guess it is not possible :/

Active State does have an Active Perl distribution for Linux- it does however, appear that the windows version has some added goodies.

Again, you may want to investigate mod_perl, note, however,
I do almost no Perl.

Steve

---

### Post by pmasiar on 2008-04-11
If you know Perl, you will learn Python is less than a week. Actually, Python is simpler than Perl. And Python has better web app frameworks than Perl ever has.

---

### Post by ghostdog74 on 2008-04-11
> **pmasiar said:**
> If you know Perl, you will learn Python is less than a week. Actually, Python is simpler than Perl. And Python has better web app frameworks than Perl ever has.

you are starting yet another useless debate. can i refer you to [comp.lang.perl.misc ]("http://groups.google.com.sg/group/comp.lang.perl.misc/topics?hl=en&lnk=srg"). you can post your opinions there and see what those ppl say about it

---

### Post by slavik on 2008-04-11
> **pmasiar said:**
> If you know Perl, you will learn Python is less than a week. Actually, Python is simpler than Perl. And Python has better web app frameworks than Perl ever has.
learning a language is not just learning the syntax but also learning about the libraries that are available (by default or mostly used) and also learning about how those libraries organise themselves.

and I agree with ghostdog74.

---

### Post by pmasiar on 2008-04-11
Well, OP has a problem, and this might be good forward-looking solution, no? Suggesting PHP is ok, but Python is not?

---

### Post by slavik on 2008-04-11
> **pmasiar said:**
> Well, OP has a problem, and this might be good forward-looking solution, no?
not in this case since it is clear that OP is very proficient in Perl.

---

### Post by ghostdog74 on 2008-04-11
> **Oxnigarth said:**
> 

With mod_perl is this possible? or is it going to be different.

Ox.

[Apache::ASP::Perlscript]("http://www.google.com.sg/search?hl=en&q=APache+ASP+perlscript&btnG=Search&meta=")
and [mod_perl]("http://perl.apache.org/")
I am not familiar with them, but you could certainly put in some reading/research before deciding if you want to switch to another alternative.
Another resource you can go to is [comp.lang.perl.misc]("http://groups.google.com.sg/group/comp.lang.perl.misc?lnk=srg"). You will get more suggestions to your problem there.

---

