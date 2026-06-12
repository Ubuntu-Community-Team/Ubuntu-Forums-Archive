---
title: "Creating a Weblog from Scratch"
date: 2008-12-31
forum: Programming Talk
---

### Post by thenocturnalhoodie on 2008-12-31
Hello everybody!
So, my Uncle is being kind enough to lend me some serverspace. I think I am going to take it and use it as a place to test out my HTML and Javascript knowledge.

One major thing that I would really like to do is create my own personal blog from scratch. I've been blogging for years, and love it. I checked the source code on livejournal and blogger, and I'm still a little confused. I was wondering exactly what language I would need for this task. I think it was basically just HTML with Javascript embedded in it. So, I'm capable of doing that. But I don't know if anyone has any experience or tips on it? I think it would be a really useful and fun project.

---

### Post by escapee on 2008-12-31
Read into PHP, Python, or Ruby.  You'll need a server-side programming language if you want to make a legitimate blog that you can go in and update without editing source code.  Also, may want to take a look at MySQL databases for an easy way to store your blogs.

---

### Post by thenocturnalhoodie on 2008-12-31
> **escapee said:**
> Read into PHP, Python, or Ruby.  You'll need a server-side programming language if you want to make a legitimate blog that you can go in and update without editing source code.  Also, may want to take a look at MySQL databases for an easy way to store your blogs.

Alright, thanks.
I know a little of Python. I haven't really messed with it for a good year or so. But I'm sure some refreshing would be all that's needed for that.

You wouldn't happen to know of any sort of guide or tutorial or other thread on a similar subject? (or would anyone else, for that matter?)

---

### Post by .Maleficus. on 2008-12-31
If you know some Python and want a refresher, check out Django ([http://www.djangoproject.com](http://www.djangoproject.com)).  It's a framework for building rapid web applications and simplifies a lot of it (database calls, rendering the pages, etc).  It also has a built-in admin interface that can be completely customized to your needs.  There are quite a few good resources for learning it, but the most complete free solution would be the Django Book ([http://www.djangobook.com](http://www.djangobook.com)).

---

### Post by pmasiar on 2008-12-31
Server-side programming is quite different beast than just plain HTML, but with some persistence, you will get there.

Best choice for you would be Python+Django: very simple wiki is in tutorial, in less than hour. You can trivially use wiki as blog.

Of course Python can do much much more just simple blog. See wiki in my sig for links.

---

### Post by Gleen Globes on 2008-12-31
You could download and use already existing open source blogging software like Wordpress from [COLOR=Blue][http://wordpress.org/](http://wordpress.org/)[/COLOR] rather than building your own from scratch.T hen you would benefit from the Wordpress community's activities and maybe contribute some ideas back yourself.

---

### Post by MattBD on 2008-12-31
I'd probably second the Django recommendation, but if you didn't want to get so far into the nuts-and-bolts of it you could check out a content management system of some kind.
WordPress is the best known CMS for blogging, or there's also Joomla! and Drupal.
If you do want to build it from scratch, it still might be a good idea to look at these for ideas.

---

### Post by hessiess on 2009-01-01
Pearsonally I would recomend PHP over python, as its supported by more hoasting providers.

---

### Post by .Maleficus. on 2009-01-01
> **hessiess said:**
> Pearsonally I would recomend PHP over python, as its supported by more hoasting providers.
There are still quite a few hosting providers that have mod_python installed and after that it's just a matter of installing Django and setting it up to work with Apache.  PHP is pretty much the standard right now but Python is a great language and Django is a great framework.

@thenocturnalhoodie: Check out who your host will be and see what they have as far as Python goes.  Otherwise, RoR (Ruby on Rails) is a pretty well accepted framework, and if they don't have that, PHP is the next best choice.

---

### Post by Emill on 2009-01-01
Checkout Ruby on Rails.
[http://rubyonrails.org/screencasts](http://rubyonrails.org/screencasts)

[http://media.rubyonrails.org/video/rails_blog_2.mov](http://media.rubyonrails.org/video/rails_blog_2.mov)
Older:
[http://media.rubyonrails.org/video/rails_take2_with_sound.mov](http://media.rubyonrails.org/video/rails_take2_with_sound.mov)

---

### Post by my_key on 2009-01-01
I think it's wise to start by learning html and css first. There's some good tutorials around on the web e.g. w3schools 

Css zengarden is an eyeopener if you don't know css.

Just make some simple scrap pages in these markup languages first. If you get the hang of it, learn a web programming language like php, python, ruby on rails or perl or bash cgi. Do get a thorough understanding of the security implications of what language you're writing in before hosting it on the net though. You're not the first one who's machine gets owned because of some code or sql injection vulnerability in his own code. 

Tip: download a well known application written in the language you're writing in and check what kind of input validation etc. they use.



Have a nice learning experience ;)

---

