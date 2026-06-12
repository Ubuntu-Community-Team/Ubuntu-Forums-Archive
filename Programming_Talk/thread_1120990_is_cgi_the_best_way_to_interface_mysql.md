---
title: "is cgi the best way to interface mysql?"
date: 2009-04-09
forum: Programming Talk
---

### Post by pavel989 on 2009-04-09
hello everyone,
I have a lampp server box.
and i learned a lot from it, i have a very good understand of protocols, in general the way the Internet works, ftp, basic understand of mysql, etc.

but ive come to a new problem. I know C++ sorta well, i forgot ruby (im sure i can remember quickly), same with python, i got some vb, and almost no HTML or anything alike.

i know that i can use any of them for cgi-bins.

and i want to make a cgi bin because apparently its the best way to interface apps and the web.

My main goal, is that i want to make a quick web interface for my mysql table. at first i tried to do it through rails, but i can't set it up with rails, constant problems.

but the benefit, as i see it, is that with cgi, i can really expand, outside of mysql since i know those languages. 

so i wanted to see what people have to say. Should i learn PHP, PERL? shoudl i use C++ through CGI? Maybe just learn Flash? Is there even a better way?

For the record, ima be learning JAVA next school year.

any input would help. even some help with my Rails install would be appreciated (although i think thats so broken that its not worth it.)

---

### Post by soltanis on 2009-04-09
There is no "best way" to interface to your database. What works best for your set-up is going to be the best way for you. You could use CGI or FastCGI; you could spice it up with AJAX on the client-side; or you could use Java servlets/JSPs, Active Server Pages, php, etc.

I suggest you pick up Perl (it's Perl for the language, perl for the interpreter, but never PERL) if you're looking to learn another language, you'll find its usefulness in CGI or in general purpose automation amazing. It's a pretty easy way to write and maintain cgi scripts, if that's how you choose to go.

---

### Post by slavik on 2009-04-09
I did cgi in C (interfacing with MySQL) ... not fun ... but you want something (anything) that makes handling strings easy.

---

### Post by FrankT-Qc on 2009-04-09
Well, C is my all time favorite but if you want to do rapid dev, mono/C# makes things incredibly easy... If you find that monodevellop is a little behind other IDEsm a new one, incredibly better, is available with Jaunty (you'll have to wait a few days for the cool stuff, which will leave you some time to read about mono !!!)

---

### Post by ZuLuuuuuu on 2009-04-10
If your intent is just web programming than PHP is the easiest way (and pretty powerful). Other languages are more general-purpose and a little harder to setup for web programming. Also finding a web server to upload your work on internet will be a problem after some point and it is hard to find servers for other languages than PHP and Perl.

---

### Post by evymetal on 2009-04-10
Personally I'd recommend Python - but Perl used to be the standard way, and most of my old code is in Perl. (I've got nothing against it, just prefer Python these days)


Edit: 

ZuLuuuuuu makes a good point - unless you have a dedicated machine / VM somewhere then you'll rely on what interpreters are provided on your host - which will normally just be for PHP (and possibly Perl)

---

### Post by CptPicard on 2009-04-10
Just doing raw CGI is totally archaic. You generally hook up any higher-level thing to apache using whichever means, and then use that to actually code your app.

I'm recently been hacking on Django and quite like it... I would suggest not going the PHP route as it is a language that tends to suggest bad habits and bad design, and that it is IMO a fairly ugly language in general...

---

### Post by pavel989 on 2009-04-10
well i do have a server box right here, and i forgot to mention that i do now C#.

Well so far its down to Python, PHP and Perl.

---

### Post by ghostdog74 on 2009-04-11
> **pavel989 said:**
> 
Well so far its down to Python, PHP and Perl.
if you can't decide, roll a dice.

---

### Post by pmasiar on 2009-04-11
Python + Django, without hesitation.

Django will generate all basic data access screens, all you need is to define your data model (describe the tables).

---

### Post by s1ightcrazed on 2009-04-11
PHP with a PDO - depending on the complexity. For me simple things seem perfect for a few snippets of PHP code, anything really complex and I'll dive into something else. 

I agree with most everyone else, cgi-bin is really adding an unnecessary layer and adding quite a bit of unnecessary work to your plate.

---

### Post by pavel989 on 2009-04-12
i think i might just end up learning all three and using them for whichever specific app i need. but i think ima focus more on python since i actually kidna know it, as compared to the other 2

---

### Post by ghostdog74 on 2009-04-12
> **s1ightcrazed said:**
> ```

for beer in $(ls /home/fridge); do

    drink $beer

done

```

```
for beer in /home/fridge/*
```

---

### Post by s1ightcrazed on 2009-04-21
> **ghostdog74 said:**
> ```
for beer in /home/fridge/*
```

Dude - if it wasn't apparent from the quote, I was drunk when I wrote it. 

:-)

To each his own.

---

