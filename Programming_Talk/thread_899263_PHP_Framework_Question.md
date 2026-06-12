---
title: "PHP Framework Question"
date: 2008-08-24
forum: Programming Talk
---

### Post by rhapster on 2008-08-24
Hello. I'm developing an enterprise system and was looking for a good php framework to work on. It is mainly a web based application that has to be dynamic, flexible and should be able to handle login credentials and parsing of excel files submitted to it.

So far I have 2 options. First is CodeIgniter (had some experience with this before) and the second is Joomla (no experience). Which is more suited for the project? A framework like CodeIgniter can give me a lot of control over the code but will require me to learn more (since it's the first time I'll be leading a project). Joomla is said to be easy to use but I'm not sure if it's capable of meeting the dynamic requirement of the company.

Thanks in advance. Hope to hear from your suggestions.

---

### Post by dootzky on 2008-08-24
I've been working in CodeIgniter for over 6 months, and it's really great, but you need some time to get used to it, and figure it all out, of course.

On the other hand, Joomla and Drupal are more "already completed solutions", which you can adapt to your needs in some smaller level, but it's production-ready (meaning you can launch a site in 2 days (?!) ).

Overall - if you need good and stable PHP framework - it's CodeIgniter or CakePHP.

And I don't think Joomla/Drupal/Wordpress are "frameworks" at all. They are Content Management Systems (CMS), more then a framework.

Best of luck in your work! :)
cheers,
dootzky

---

### Post by drubin on 2008-08-24
First question is who good is your php? If your php is not bad I would recommend working with your own code. :) 

Some of the stuff you are trying to do can be complicated when trying to fit in with pre existing frameworks out there.

Reading excel files is pretty basic, there are a couple of php scripts that do it. [http://sourceforge.net/projects/phpexcelreader/](http://sourceforge.net/projects/phpexcelreader/) That might help you a little.


As for the login in part I would take a look at php session handling.  [www.php.net/session](www.php.net/session) .

---

### Post by rhapster on 2008-08-26
> **dootzky said:**
> I've been working in CodeIgniter for over 6 months, and it's really great, but you need some time to get used to it, and figure it all out, of course.

On the other hand, Joomla and Drupal are more "already completed solutions", which you can adapt to your needs in some smaller level, but it's production-ready (meaning you can launch a site in 2 days (?!) ).

Overall - if you need good and stable PHP framework - it's CodeIgniter or CakePHP.

And I don't think Joomla/Drupal/Wordpress are "frameworks" at all. They are Content Management Systems (CMS), more then a framework.

Best of luck in your work! :)
cheers,
dootzky

Thanks for the reply. I've already had some experience with the MVC framework. It's quite easy to use once you get the hang of it. I've already decided to work with the CodeIgniter Framework. The only problem now is teaching it to my groupmates who has very very little (close to none) php experience. haha.

Thanks again.

---

### Post by rhapster on 2008-08-26
> **rubinboy said:**
> First question is who good is your php? If your php is not bad I would recommend working with your own code. :) 

Some of the stuff you are trying to do can be complicated when trying to fit in with pre existing frameworks out there.

Reading excel files is pretty basic, there are a couple of php scripts that do it. [http://sourceforge.net/projects/phpexcelreader/](http://sourceforge.net/projects/phpexcelreader/) That might help you a little.


As for the login in part I would take a look at php session handling.  [www.php.net/session](www.php.net/session) .

Thanks for the reply. That's just what I needed. Better start parsing those excel files. hehe. I already decided to go with CodeIgniter.:D

---

