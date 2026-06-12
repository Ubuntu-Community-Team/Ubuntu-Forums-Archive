---
title: "Any free RoR/Django hosts?"
date: 2008-03-16
forum: Programming Talk
---

### Post by Majorix on 2008-03-16
OK so I am a newbie, wannabe web developer.

I am learning RoR and Django. Don't ask me why I do both.

Anyways, I am looking for a free host for the two. I have found something from a free web hosts list, but it said that it supports "Python" but no sign of Django or anything. When I search that list for Django nothing shows up.

Same goes for RoR. When I search for "Rails" only 3 hosts show up, and they don't somehow include the word "Rails" anywhere. When I search for Ruby 5 hosts show up.

So what I am asking is, what do these mean? I mean, does a host that supports "Python" also automatically have Django or something? Or perhaps TurboGears? Or does a host that includes the word Ruby have Rails? If not, can I have the name of one or two free RoR/Django hosts?

BTW I would be glad if the RoR host was 1.2, as the book I read (Agile Web Dev) doesn't talk about 2.0, and none of the books/tutorials I found so far do either.

Thanks for the interest.

---

### Post by pmasiar on 2008-03-16
I am not sure why you try to learn both - pick either one.

I am also not sure why you expect free hosting. For development, both Django and TurboGears come with self-hosted development server. For production deployment, I don't see why anyone would let you run long-running processes for free. If you need free Python web hosting, use plain CGI module (which is short-running process), I assume that it should be easier to find free hosting for those.

---

### Post by mssever on 2008-03-16
If you can run Ruby, you can run Rails; if you can run Python, presumably you can run Django. I don't know about Django, but Rails performs badly when Ruby is run as a standard CGI.

---

### Post by LaRoza on 2008-03-16
Free (RoR): [http://xmgfree.com/](http://xmgfree.com/)

List of hosts (RoR): [http://wiki.rubyonrails.com/rails/pages/RailsWebHosts](http://wiki.rubyonrails.com/rails/pages/RailsWebHosts)

---

### Post by elithrar on 2008-03-16
> **Majorix said:**
> I am learning RoR and Django. Don't ask me why I do both.


It just seems a little redundant to be doing this - whilst Django & Rails don't have exactly the same goals in mind, they are similar enough that learning one framework & language (ie. Django & Python) slows down the learning of the other, as well as conflicts when it comes down to processing that knowledge. Sticking to one will both increase your comprehension of the languages, decrease the time it takes you to plan an application (no "Rails or Django for this one?") and increases your productivity by extension.

As for free hosts, if you're just developing applications to test and learn, then use the development servers that come with Django & Rails. They're both decent enough to handle a few users should you want friends/colleagues to test your applications. I've got mine running off a subdomain on port 8000 & 3000, for Django and Rails respectively.

---

### Post by Majorix on 2008-03-17
> **pmasiar said:**
> I am not sure why you try to learn both - pick either one.

I am also not sure why you expect free hosting. For development, both Django and TurboGears come with self-hosted development server. For production deployment, I don't see why anyone would let you run long-running processes for free. If you need free Python web hosting, use plain CGI module (which is short-running process), I assume that it should be easier to find free hosting for those.
I expect free hosting because there are tons of free web hosts for PHP, I thought to myself, "Why shouldn't I be able to host my RoR project for free?"; and thus came this topic to existance.
> **mssever said:**
> If you can run Ruby, you can run Rails; if you can run Python, presumably you can run Django. I don't know about Django, but Rails performs badly when Ruby is run as a standard CGI.
Thanks for the tip. Do I have to install a rails gem or would it work just like that?
> **LaRoza said:**
> Free (RoR): [http://xmgfree.com/](http://xmgfree.com/)

List of hosts (RoR): [http://wiki.rubyonrails.com/rails/pages/RailsWebHosts](http://wiki.rubyonrails.com/rails/pages/RailsWebHosts)
Thanks a lot for that host! I have checked it a bit yesterday, and even though there are some tough rules, I think I can live with it until I find a better host.
> **elithrar said:**
> It just seems a little redundant to be doing this - whilst Django & Rails don't have exactly the same goals in mind, they are similar enough that learning one framework & language (ie. Django & Python) slows down the learning of the other, as well as conflicts when it comes down to processing that knowledge. Sticking to one will both increase your comprehension of the languages, decrease the time it takes you to plan an application (no "Rails or Django for this one?") and increases your productivity by extension.

As for free hosts, if you're just developing applications to test and learn, then use the development servers that come with Django & Rails. They're both decent enough to handle a few users should you want friends/colleagues to test your applications. I've got mine running off a subdomain on port 8000 & 3000, for Django and Rails respectively.
I will be developing a project that has to be up 24/7, and you can't expect a poor, old laptop to do that right?

If anyone knows of another free host like the one LaRoza suggested, feel free to name it. I didn't register there yet :)

---

### Post by mssever on 2008-03-17
> **Majorix said:**
> Thanks for the tip. Do I have to install a rails gem or would it work just like that?
I don't know. I'm no rails expert, but I get the impression that the directory tree you get when you run the rails command is pretty much complete. I might be way off on that, though.

---

### Post by Majorix on 2008-03-17
Wait you tried the "rails project_name" command on a host and it created a complete directory tree?

---

### Post by mssever on 2008-03-17
> **Majorix said:**
> Wait you tried the "rails project_name" command on a host and it created a complete directory tree?

I did it on my local machine and got what I assume is a complete tree. I haven't read the source (and rails documentation is scarce), so I'm not positive that it's a complete tree.

---

### Post by Majorix on 2008-03-17
Ah so... I am looking for a host with Rails enabled though :)

BTW your directory tree is most likely complete, otherwise you would get errors ;)

---

### Post by pmasiar on 2008-03-17
> **Majorix said:**
> I expect free hosting because there are tons of free web hosts for PHP,

PHP starts for every request, there are no long-running processes. **Production, industry-strength web app** is something different - remember that PHP was originally for "Personal home pages".

> I will be developing a project that has to be up 24/7, and you can't expect a poor, old laptop to do that right?

but you expect free web hosting to do it for you? You get what you paid for.

Django website links to many hosting services, some have Django preinstalled. In general, Rails is hard to host, and dev community knows about it. [Zed's rant](http://www.zedshaw.com/rants/rails_is_a_ghetto.html) - warning: really abrasive personality!

---

### Post by Majorix on 2008-03-18
I found another free RoR host:
[http://www.ambitiouslemon.com/](http://www.ambitiouslemon.com/)
Will compare it with the one LaRoza found.

---

### Post by Railsbuntu on 2008-03-18
Hi majorix,

Before looking at a free host, you must understand that the Rails app is simply the tip of the iceberg in the overall website. Setting up and maintaining a reliable and secure website is a hell of a work. I have been working on my server for already 3 weeks, I am not yet finished and my ToDo list is growing daily :lolflag:

You get what you pay for. Some peaople use dreamhost as a super cheap host, but they accept the problems that come with such solution.

---

### Post by skeeterbug on 2008-03-18
While this site isn't free, they over a very good service.

[http://asmallorange.com/services/hosting/index.php]("http://asmallorange.com/services/hosting/index.php")

25 dollars for an entire year. You can't beat that. You can also email them and they will give you SSH access to the box. I have had django and rails both setup on there. Django is my current setup on the box, as I can't stand the rails development/community anymore. You also get MySQL, unlimited sub domains, emails, etc. Great package for the price.

---

### Post by mssever on 2008-03-18
> **skeeterbug said:**
> 25 dollars for an entire year. You can't beat that.
Actually, I can. Under USD 0.30 per month is what I pay at nearlyfreespeech.net. Granted, this is off-topic, since nearlyfreespeech.net's service isn't that great for Rails. But it's still a great deal.

---

### Post by uField on 2011-10-14
you can find list of django free hosts at
[http://freedjangohosting.com](http://freedjangohosting.com)

---

