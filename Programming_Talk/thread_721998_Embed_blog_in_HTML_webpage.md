---
title: "Embed blog in HTML webpage?"
date: 2008-03-11
forum: Programming Talk
---

### Post by xelapond on 2008-03-11
Hello, 

Does anyone know of a good way to embed a blog into a web page written in HTML?  I am making the blog in KompoZer, and writing some of the HTML myself, where the WYSIWYG limits me.  Are there any programs or modules that would do this for me?  I would *prefer* to stay away from scary language that I do not know(Ruby, AJAX, Java), but it doesn't look like that is very likely:)

Thanks, 

Alex

---

### Post by CptPicard on 2008-03-11
The only thing that comes to my mind is an "iframe"... generally what you're trying to do is pretty difficult without server-side coding.

---

### Post by mssever on 2008-03-12
I don't think that it's possible to write a real blog in HTML. HTML isn't a real language; it's merely a file format.

It would pay to learn a programming language. If you're going to do web work, you'll need to learn Javascript. But don't start there or you'll end up frustrated. Python and PHP are both good choices. PHP is handy because it's designed for web work out of the box and there's a great manual on the website. Python is good because it'll teach you good habits and concepts. Ruby is my language of choice, but it has a lot of syntax that could confuse a beginner.

Overall, I recommend learning PHP (the manual has enough to get you started), and making a note to yourself to learn another programming language as soon as is practical so you don't end up scarred for life by some of PHP's stupidity.

Even if you use PHP for nothing more than includes (as my brother does), you'll still come out ahead by knowing a real language. And don't be too scared by it. With a little effort, you can grasp the basics, at least.

EDIT: By the way, AJAX isn't a language; it refers to a particular type of Javascript code. Also, Java and Javascript have almost nothing in common, despite their similar names. Don't mess with Java unless you need to get a job as a code monkey or unless you enjoy self-torture.

---

### Post by xelapond on 2008-03-12
Thanks everyone, 

I am not a beginning programmer, I know C and Python pretty well, and I really don't have much trouble picking up a new language.  Between Ruby and PHP which one would you recommend?  I really hate C and everything about it, so if PHP is at all like it I think I would want to go with Ruby.

EDIT: If I learn Ruby would I want to learn Ruby, Ruby on Rails, or Ruby then Ruby on rails?  I have no problem spending a good amount of time learning any language, as it is good to know a lot of them.

Thanks, 

Alex

---

### Post by bmeyer on 2008-03-12
> **xelapond said:**
> Thanks everyone, 

I am not a beginning programmer, I know C and Python pretty well, and I really don't have much trouble picking up a new language.  Between Ruby and PHP which one would you recommend?  I really hate C and everything about it, so if PHP is at all like it I think I would want to go with Ruby.

Thanks, 

Alex

Ruby and Python are definitely elegant languages, but I'd recommend picking up PHP and MySQL.  It's relatively easy to learn.  But, more importantly, if you want to implement a blog, it might be more beneficial to use a free, customizable commercial product (Wordpress, Joomla, etc) -- almost all of them are written in PHP/MySQL.

---

### Post by mssever on 2008-03-12
> **xelapond said:**
> Thanks everyone, 

I am not a beginning programmer, I know C and Python pretty well, and I really don't have much trouble picking up a new language.  Between Ruby and PHP which one would you recommend?  I really hate C and everything about it, so if PHP is at all like it I think I would want to go with Ruby.

EDIT: If I learn Ruby would I want to learn Ruby, Ruby on Rails, or Ruby then Ruby on rails?  I have no problem spending a good amount of time learning any language, as it is good to know a lot of them.

Thanks, 

Alex
For someone who already knows something about programming, I'd definately recommend Ruby over PHP--no contest. PHP is annoying:
[LIST]
[*]it requires semicolons at the end of every line, a needless source of syntax errors
[*]No namespaces
[*]ad hoc, inconsistant design
[*]PHP's type system is problematic. PHP uses weak typing, so that you can wind up with bad data and not realize it right off. Ruby'd typing isn't static as in C, but it's strong enough to prevent type errors
[*]PHP didn't get exceptions until recently. Most of the core functions report errors through return values instead of exceptions.
[*]the include path design is brain dead
[*]OO is awkward[/LIST]Ruby is quite elegant and much easier to use (though it isn't perfect). I'd recommend learning Ruby first, before Rails. Rails uses extensive metaprogramming to make all kinds of things work with one or two lines of code. But if you don't already know Ruby, you'll probably find Rails confusing.

One area where Ruby (and especially Rails) is lacking is documentation. Documentation is PHP's biggest strength.

---

### Post by Modred on 2008-03-12
Since you already know Python, you might want to investigate [TurboGears](http://turbogears.org/) or [Django](http://www.djangoproject.com/) for dynamic web development.

But if you just want a blog up and running, then you might do well to just use something already written, such as WordPress, and then integrate it into your site.

---

