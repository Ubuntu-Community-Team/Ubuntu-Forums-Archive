---
title: "Web Dev Help Needed: Do I need mysql?"
date: 2008-07-10
forum: Programming Talk
---

### Post by ddixonr on 2008-07-10
Hey guys. I have been slowly learning web design, html to be exact. I was able to pick that up rather quickly and get a pretty nice looking website from it (in my opinion).

Specifically, I'd like to add the ability for visitors to leave comments on the material. I don't want to use Shoutbox or similar, nor do I want to just redirect users to a blog that I could easily create. I'd like to learn how by using examples (how I learned html) and possibly fill-in-the-blank code from others.

Learning php or python wouldn't be a bad place to start, but I'm having a hard time getting going. I figured out Apache2 fast, and I'm sure I will need to learn mysql soon. If this is the easiest way to accomplish my goal, please point a newbie in the right direction.

Thanks.

---

### Post by mssever on 2008-07-10
You'll need some way to save the data. A database such as MySQL is a good way to go, though it isn't the only option. I suggest that you look into [Code Igniter]("http://codeigniter.com") for PHP, as it will abstract away many of the tedious bits. If you use their Database classes, then you'll get compatibility with several different DBs. If you use Active Record, basic queries become trivial.

If you choose another language such as Python (which I recommend), look for a framework for that language. Django is a popular Python framework. Rails is a popular Ruby framework, though Rails isn't very easy to learn, IMO.

---

### Post by themusicwave on 2008-07-10
You don't absolutely need MySQL, there are several other databases around.  I like PostgreSQL, but MySQL would be perfect for the task as well.

You truly don't need a database, but it will make things much much easier.  You could just store all the comments in flat files(text files), but I would not recommend this approach.

What I would suggest is that you use (X)HTML and CSS to do your markup, a database to store the data and a server side scripting language to do the processing and page generation.

For databases there are lots of options, it usually depends what your web host provides.  Mine gives me both PostgreSQL and MySQL.

For scripting, once again it depends on your hosting company.  Almost every host supports PHP, but others support Perl, Python, Ruby on Rails and Java.

I would recommend you choose either Python or PHP depending on server availability.  If you don't yet have a web server, maybe give them both a shot and see which you prefer.  You are learning after all.

Then when you buy hosting you know what to shop for, for instance I wanted Python and PostgreSQL for my web page.  So I shopped only hosts that provided them.

Hope that helps.

---

### Post by pmasiar on 2008-07-10
While it is excellent idea to learn programming, and Python is the best for beginners (see my sig), you do not need programming to have guestbook or a forum. Get any (free) blog or forum software, preferably one supported by your webhosting provider, and learn how to customize it (styles).

---

