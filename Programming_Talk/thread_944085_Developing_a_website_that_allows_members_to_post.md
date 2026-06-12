---
title: "Developing a website that allows members to post"
date: 2008-10-10
forum: Programming Talk
---

### Post by TorchlightJay on 2008-10-10
Hello,
   I am trying to build a kind of craigslist for my university. I want to use PHP and I have an idea of how to do the messaging portion. What I do not know how to do is create a new page when someone creates a post, automatically create a separate page for that post (and place it properly on the sitemap), message the webmaster that a post is made, and add it to the list of posts.

I don't know if I made sense but any idea can help us. 

FYI, I am trying to use Joomla!, maybe phpBB and Wordpress. Let me know. Thanks.

---

### Post by apetresc on 2008-10-11
The PHP style isn't to actually physically create a new page every time a post is made, but rather to have a generic "viewPost.php" page which takes (through POST or GET) some arguments specifying which post to view, and then grabbing that data from a SQL database and displaying it as part of viewPost.php. The corresponding logic and presentation is stored in the .php file itself, while the per-post data (the text, date, author, etc) is stored in the database.

---

### Post by TorchlightJay on 2008-10-11
Cool,


Ya I kinda of figured that the PHP was there just to communicate with the database (help enter and retrieve data). What I wanted to know is how to create a new page with the data just entered so that when someone comes onto the site after a post is made, they can see the post that was just made (and previous posts as well). Any ideas?

---

### Post by apetresc on 2008-10-11
> **TorchlightJay said:**
> Cool,


Ya I kinda of figured that the PHP was there just to communicate with the database (help enter and retrieve data). What I wanted to know is how to create a new page with the data just entered so that when someone comes onto the site after a post is made, they can see the post that was just made (and previous posts as well). Any ideas?

That's what I'm saying though -- you don't "create a new page"... you have just ONE page that simply displays the newest thing in the database. Subtle but important distinction. Even when there's 500 posts there's still only ONE physical .php file in your webserver's directory.

---

### Post by LaRoza on 2008-10-11
> **AdrianP said:**
> That's what I'm saying though -- you don't "create a new page"... you have just ONE page that simply displays the newest thing in the database. Subtle but important distinction. Even when there's 500 posts there's still only ONE physical .php file in your webserver's directory.

For example, look at the URI's of this forum, and even my personal website: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

---

### Post by apetresc on 2008-10-11
> **LaRoza said:**
> For example, look at the URI's of this forum, and even my personal website: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

Exactly :) Keep in mind that everything after the '?' in a URL is simply GET parameters being passed to the server, and not part of the actual filename. Read up on GET and POST for more details.

---

### Post by LaRoza on 2008-10-11
> **AdrianP said:**
> Exactly :) Keep in mind that everything after the '?' in a URL is simply GET parameters being passed to the server, and not part of the actual filename. Read up on GET and POST for more details.

Ah, yes. Forgot about that, it was too "obvious" (to me) to mention :-)

---

### Post by TorchlightJay on 2008-10-11
Awesome, that sounds like it'll work. Well we are going to use multiple pages just to subdivide categories and stuff. The university wants every post to have a page so I can see how your idea can work in listing all the posts in one category (I may have to create a database for every category? Maybe just a table for every category? Thoughts?). I will look at that tutorial. 

Can I do all of this on Joomla! or will I just do this the old school method? Thanks.

---

### Post by apetresc on 2008-10-11
> **TorchlightJay said:**
> Awesome, that sounds like it'll work. Well we are going to use multiple pages just to subdivide categories and stuff. The university wants every post to have a page so I can see how your idea can work in listing all the posts in one category (I may have to create a database for every category? Maybe just a table for every category? Thoughts?). I will look at that tutorial. 
Not even a table. You could just have a VARCHAR column called 'category' in your Posts table. Then if you wanted all the posts in the 'math' category, for instance, you could just do "SELECT * FROM Posts WHERE category = 'math';". Voila!

> **TorchlightJay said:**
> Can I do all of this on Joomla! or will I just do this the old school method? Thanks.

I'm not a Joomla expert, but I'm fairly sure all CMS have at least this basic functionality, so you should be all set with Joomla :)

---

### Post by TorchlightJay on 2008-10-11
I think I am following. One quick question, anyone know of a good tutorial I can use? Just want to make sure I do it write. I know how to parse data to a mysql database with PHP, I am just not sure how to get it to show up the way you guys mentioned. Thanks.

---

### Post by DemonBob on 2008-10-12
The best way to learn how to do this or to learn php in general is to rip apart a premade script peice by peice. 

I learned by downloading phpbb2 (a forum, uses atlot of post and get's) and ripping it apart, after a while i got the hang of php, and eventually was using it every day as a system admin to automate task like billing for a Citrix/Exchange hosting envrierment, also made it so the companys had a master account they could log into from the outside to add/remove/disable users or change/add aliass to thier employee's accounts.

For the database i would create a dbal (database abstraction layer) class to handle the reading and writing to the database, or use a premade one, i think php pear has one. I personally still use a heavly modified version of phpbb2 dbal in alot of my home made stuff, even though i have made my own, i find thiers to be lightweight for what i need.

---

