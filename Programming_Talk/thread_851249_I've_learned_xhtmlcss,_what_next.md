---
title: "I've learned xhtml/css, what next?"
date: 2008-07-06
forum: Programming Talk
---

### Post by T2manner on 2008-07-06
I'm almost done with my book on xhtml/css and I was wondering what I should learn next.
Javascript and other web languages, or should I go with application programming like python or something.

---

### Post by LaRoza on 2008-07-06
> **T2manner said:**
> I'm almost done with my book on xhtml/css and I was wondering what I should learn next.
Javascript and other web languages, or should I go with application programming like python or something.

I'd learn the client side first. Unfortunately, the web is full of bad uses of ECMAScript.

I recommend getting the book: [http://domscripting.com/book/](http://domscripting.com/book/)

It is beyond compare, although you might want to learn the basics of ECMAScript elsewhere (check out the w3c tutorials on it, see my wiki)

---

### Post by henchman on 2008-07-06
JavaScript aka ECMAScript will give a good entry into application programming, because you learn all the structures which will be needed to program these. + You can embed it into the stuff you already learned. + Javascript is shiny and you see results very fast :)

So that's propably the next logical step if you haven't a favorite :)

---

### Post by pmasiar on 2008-07-06
What you want to learn? What is your goal?

If you want to program web-based applications, you need to learn server-side language (like Python, Ruby, or maybe PHP or Java), SQL for database, and JavaScript for browser-side AJAX.

Python is easy to learn and good to know, because you can use it outside web apps: Quick passing and manipulating files, non-CPU intensive calculations, etc.

If you are aiming for a job programming industry, be prepared to learn many languages, and because you cannot become real expert in all (it takes couple of years), decide by area, industry, and your interests. But even if you decide to learn Java or C#, Python is good to know, because it is simpler and makes you more productive (uses flexible dynamic typing instead of more rigid static typing, you will understand difference when you learn both).

If you are deciding between JS and Python, I'll suggest Python first: both are dynamically typed and very close, but Python is IMHO simpler to learn and has better facilities to help learning, like interactive shell. After learning basics of programming in Python, learning JS is simple project for couple of weeks max (but to be effective in AJAX, you need to learn DOM and other stuff - and have to way to program server actions).

For web-based apps in Python, use MVC web app frameworks:  Django (for beginners) or Turbogears (if you need more flexibility).

See wiki in my sig for links how to learn Python, including training tasks and simple web app.

---

### Post by rye_ on 2008-07-06
I recently formed a clandestine organisation bent on taking over the world.  As yet we've had limited success, but were are an above average 5 a side football team.

We're thinking of expanding our evil operations to a possible 11 a side football team.  membership open. evil laugh required.

---

### Post by T2manner on 2008-07-06
> I recently formed a clandestine organisation bent on taking over the world. As yet we've had limited success, but were are an above average 5 a side football team.

We're thinking of expanding our evil operations to a possible 11 a side football team. membership open. evil laugh required. 

umm..

well thanks for the bump i guess..

---

### Post by henchman on 2008-07-06
hm... its not rot13...

---

### Post by tinny on 2008-07-06
> **pmasiar said:**
> What you want to learn? What is your goal?

If you want to program web-based applications, you need to learn server-side language (like Python, Ruby, or maybe PHP or Java), SQL for database, and JavaScript for browser-side AJAX.

Python is easy to learn and good to know, because you can use it outside web apps: Quick passing and manipulating files, non-CPU intensive calculations, etc.

If you are aiming for a job programming industry, be prepared to learn many languages, and because you cannot become real expert in all (it takes couple of years), decide by area, industry, and your interests. But even if you decide to learn Java or C#, Python is good to know, because it is simpler and makes you more productive (uses flexible dynamic typing instead of more rigid static typing, you will understand difference when you learn both).

If you are deciding between JS and Python, I'll suggest Python first: both are dynamically typed and very close, but Python is IMHO simpler to learn and has better facilities to help learning, like interactive shell. After learning basics of programming in Python, learning JS is simple project for couple of weeks max (but to be effective in AJAX, you need to learn DOM and other stuff - and have to way to program server actions).

For web-based apps in Python, use MVC web app frameworks:  Django (for beginners) or Turbogears (if you need more flexibility).

See wiki in my sig for links how to learn Python, including training tasks and simple web app.

What, learn a programming language now and deny the OP the privilege of being able to completely mess up their nice HTML with ugly JS hacks. haha

No just joking I agree, time to move on probably.

OP it sounds to me like you are ready to move on to some sort of "real" programming language. JS is mostly just used to Hack pages to make them do what you want (due to the limitations of HTML). You can pretty much learn this on a case by case bases when you need these "Hacks". (that's how I learnt JS)

---

### Post by hanniph on 2008-07-06
Actually I am in the same situation. I already know xhtml/css quite well and would like to learn more in web development. Now I am learning javascript. I intended to learn python as a server-side scripting language but as far as I seen, there are much less job opportunities in python than php. (I would like to gain extra money as a freelancer)  So after I learn basics of javascript, I will dive into php and only then into python. ( even though I would like to learn python instantly)

---

### Post by pmasiar on 2008-07-06
> **hanniph said:**
> as far as I seen, there are much less job opportunities in python than php.

It might depend where are you looking. Python community has python jobs maillist for ages, everybody knows about it, so managers who want to hire people connected to the Python community do not waste time posting Python jobs on generic job websites. See python.org website.

---

### Post by T2manner on 2008-07-06
Well I'm not worrying about jobs or making money off of this since I'm just 14.
I just want to move in the best direction.

---

### Post by Can+~ on 2008-07-06
-**Javascript** will run on the clientside, embedded (or linked) to the web page, adding certain effects/features. Some examples in this forum, when you click on a smily, it automatically inserts the code in the window, or the buttons on the header which open sub menus, etc. It's a big annoying to work with it since it has no debugger (you can install an extension for firefox though).

-**PHP** adds dynamic content, while javascript works on the clientside, PHP is ideally used as a server-side programming language embedded into (x)html. You can request information on a Database or file-like object and insert it on a web page, basically, how this forum works. You create a message, it is stored in the database, and when you load a certain section, php pulls that from the DB.

-**SQL** is the Structured Query Language. It's the language in which you ask a database it's information or addition, or other tasks. It is commonly paired with others (mostly, but not limited to: php).

-**Python** is multi purpose. One of the big features of python, is that it has a big community that adds libraries to almost everything; that's why it is not surprise that you can work server-side as php does, or client-side as a local application.

All depends on what you want to do. The thing is, that webpages are just files that are stored in a certain fashion that browsers can read it (known as the SGML notation) (some of them better than others...), any language that can create a file parsed in (X)HTML notation can do a dynamic webpage, you could even do it on C (but it will be a major pain in the ***).

---

### Post by mssever on 2008-07-07
> **pmasiar said:**
> If you are deciding between JS and Python, I'll suggest Python first: both are dynamically typed and very close, but Python is IMHO simpler to learn and has better facilities to help learning, like interactive shell.
I agree that Python is easier to learn than Javascript, in part because of its superior documentation. But if you install The Firebug extension for Firefox, then you can get a Javascript interactive shell, as well.

As far as interactive shells go, irb (the Ruby shell) is the nicest one I know, once you tweak a few settings. It has tab completion (not enabled by default), which is a great way to explore, or to make educated guesses, or just to save typing.

---

