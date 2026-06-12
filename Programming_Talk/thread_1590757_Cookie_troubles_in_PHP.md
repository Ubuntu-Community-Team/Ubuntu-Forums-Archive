---
title: "Cookie troubles in PHP"
date: 2010-10-08
forum: Programming Talk
---

### Post by Scott Read on 2010-10-08
Hey Sorry if this is in the wrong channel (if so please direct me, first time poster)

I have an application which I'm writing in PHP, and it's giving me a hard time with cookies in both firefox and IE.

Basically you go to a login page (login_form.html) and enter your credentials, it passes them to login.php which queries the DB for your username / password.

If everything checks out it embeds a cookie (setcookie("uname", $uname, time()+3600);) and passes you to the mainpage (main_page.php)

Now main_page.php has a checker so that if you don't have the uname cookie, it tells you you're not logged in and kicks you out. simple enough.

It works the first time you get to your mainpage (I've used print_r($_COOKIES); to ensure this) but as soon as you go to another page, or refresh the current page it kills the cookie.
I'm scratching my head trying to figure out why it's doing this but can't figure it out.

Furthermore, i have another cookie called num_of_profiles which is set on loading of mainpage.php. This cookie has no issues with refreshes and isn't vanishing like it's counterpart uname.

I'm new to PHP, so please be kind!

p.s. If it's relevant, login.php calls mainpage via a javascript redirect ....  
echo "<script>location.href='/mainpage.php'</script>";

Thanks!

---

### Post by DanielWaterworth on 2010-10-08
It could be the expire settings on the cookie. Are all the pages on the same domain?

In any case it is better practice to set attributes on the session rather than the cookie unless you have to. Did you choose to use PHP? There are "better" languages out there (in quotation marks so as not to offend the php community).

Seeing as your new at this, watch out for possible:
SQL injection attacks,
XSS attacks,
CSRF attacks,

you'll find all the information you need on wikipedia.

---

### Post by Scott Read on 2010-10-08
Thanks for the quick input.

This tool is for company internal use only, so I'm not too worried about attacks at this point, but it is something I should be wary of down the road.

anyways I solved this issue after some digging. Instead of using

setcookie("uname", $uname, time()+3600, );

I used

setcookie("uname", $uname, time()+3600, '/'); 

I'm still unclear on specifically what the '/' denotes, but it's fixed my issue beautifully. 

(p.s. what other language might you suggest?, I'm new to web programming as a whole)

---

### Post by donsy on 2010-10-08
> **Scott Read said:**
> 
(p.s. what other language might you suggest?, I'm new to web programming as a whole)

This forum is heavily biased in favor of Python, so I'm sure that's the advice you'll get from many. You're doing fine in PHP: Notice that this forum uses PHP, as does Facebook.

---

### Post by Scott Read on 2010-10-08
> **donsy said:**
> This forum is heavily biased in favor of Python, so I'm sure that's the advice you'll get from many. You're doing fine in PHP: Notice that this forum uses PHP, as does Facebook. I wonder why the developers of Facebook chose not to use a "better" language.

Well this application that I'm making is based on a calculator which was developed in python for unix command line.

Basically we want to migrate it into a web app so that managers and non-technical people have easy, graphical access to it. 
So it does have a CGI-python component in it, but I've found PHP easier to manage.

Again though, I'm new into the field. What are the differences other than syntax between Python, Perl, and PHP?

---

### Post by Dragonbite on 2010-10-08
> **Scott Read said:**
> Again though, I'm new into the field. What are the differences other than syntax between Python, Perl, and PHP?

While I haven't used it myself, I hear good things about Ruby on Rails too.

---

### Post by DanielWaterworth on 2010-10-08
If it was developed in python, it would be easiest to use python for the web app. cgi is deprecated, wsgi is the future (and the present). If you need login I'd suggest using Django, it's not the best framework I've come across, but if you need to make a simple website quickly there's no substitute, otherwise straight wsgi with some templating language (like jinja2 or mako or cheetah or spitfire or ...) is the way to go.

There are definite differences other than syntactic differences. They are too numerous to iterate here.

---

### Post by Scott Read on 2010-10-08
> **Dragonbite said:**
> While I haven't used it myself, I hear good things about Ruby on Rails too.

Thanks Dragonbite, 

I'll have a look into Ruby. What does 'on rails' mean?

---

### Post by Dragonbite on 2010-10-08
> **Scott Read said:**
> Thanks Dragonbite, 

I'll have a look into Ruby. What does 'on rails' mean?

Not sure.  I don't know if Ruby can be a local programming language and Rails is the web framework?  I honestly have never looked into it, but have heard a lot of people talk positive about it.

---

### Post by v8YKxgHe on 2010-10-08
> **Dragonbite said:**
> Not sure.  I don't know if Ruby can be a local programming language and Rails is the web framework?  I honestly have never looked into it, but have heard a lot of people talk positive about it.

Ruby is the language that Ruby on Rails is written in. One is a programming language, the other is a framework. Much like PHP is the language and Zend Framework is a framework.

---

