---
title: "Your thoughts."
date: 2008-07-28
forum: Programming Talk
---

### Post by NxZDr on 2008-07-28
I'm thinking about making a web page. I've done HTML and CSS, even javascript and flash extensively. So the laws of progress have me considering two similar ideas, one less complicated than the next. (Both are sort of re-inventing the wheel, but this is mostly a learning exercise and to maybe provide a base that others may improve upon).

Idea one is to go the easy route, make a simple PHP/MySQL forum and website that has a front news page and simple forum probably CSS controlled pages providing the ability to change styles quickly, admin user group that can change and perhaps add pages and a moderator user group that can edit/delete posts. The downside is that this is nothing phpbb and all of its related projects can't do.

The other idea, which is the main reason why I'm here requires a widely available, and fast language that can maintain an open connection to the server or at least be able to dynamically update the page as informations changes.

I'd go mostly the same route, most of the page would be preloaded but the userlogin, any content that would be updated could be updated during the page view and perhaps a context sensitive menu system would be dynamic, so that while browsing a topic, any posts added will appear on the bottom of the topic if not instantly than shortly after it was posted.

Now this is more of a challenge (at least to me).

So any ideas or references I could turn to? Books are also fine.
Please don't suggest applications that already do these things, I'm quite set on doing this myself.

I've worked with Java, C, C++ and PHP before, as well HTML.

---

### Post by tamoneya on 2008-07-28
the ideas sound fun but my only suggestion is: "no flash".  Flash is used way to much and while it has recently become searchable by search engine spiders it is really annoying for users.  It has its uses like youtube but most of the time it is used poorly.

---

### Post by NxZDr on 2008-07-28
I wasn't planning on it. Let us also note that it is a pain in the *** for me to use, especially if the whole plot is to be a dynamic and fast website. Besides, bandwidth doesn't grow on trees.

---

### Post by mssever on 2008-07-29
Realtime updates could be useful in some situations. Of course, you'd have to use Javascript to frequently poll the server for changes. That would add quite a lot of load to the server. Also, you'd have to account for your users' varying bandwidth situations. Some have slow connections, and frequent polling would noticably slow them down. Others, like myself, have high-latency connections (my average ping time is about 1.2 seconds), which might interact oddly with such a system if you aren't careful.

---

### Post by NxZDr on 2008-07-29
this is why I'm thinking there must be other solutions, JS polls are just not reasonable. AJAX (Java with XML afaik) apparently minimizes this by only updating what it in the defined application (which could be the thread body itself) Set a delay of the fetch based upon activity, as the server will have instant feedback as to how often the page changes.

I'm wondering if there are other languages that may or may not be better for this sort of relationship before I dive into anything specifically.

---

### Post by mssever on 2008-07-29
> **NxZDr said:**
> this is why I'm thinking there must be other solutions, JS polls are just not reasonable. AJAX (Java with XML afaik) apparently minimizes this by only updating what it in the defined application (which could be the thread body itself) Set a delay of the fetch based upon activity, as the server will have instant feedback as to how often the page changes.

I'm wondering if there are other languages that may or may not be better for this sort of relationship before I dive into anything specifically.
Well, unless you use something that requires a plugin, you're stuck with Javascript. The way HTTP works, the only way to find out about changes on the server is to poll the server; the server can't send out notifications. You'd have to determine an appropriate poll delay, bearing in mind that you can't determine whether something happened on the server until you poll.

By the way, polling has nothing to do with reloading the page; that would be silly. Just make a background XMLHttpRequest and have the server reply in some way that's parseable by your JS.

---

### Post by nvteighen on 2008-07-29
> **mssever said:**
> 
By the way, polling has nothing to do with reloading the page; that would be silly. 

I know some news sites that reload the page to do this... quite annoying, specially when you're looking at an embedded video on them and the page suddenly reloads itself, interrupting the streaming.

---

### Post by mssever on 2008-07-29
> **nvteighen said:**
> I know some news sites that reload the page to do this... quite annoying, specially when you're looking at an embedded video on them and the page suddenly reloads itself, interrupting the streaming.
Yeah, the META REFRESH tag is evil! Even Google News uses it. It's also annoying when there are a number of links I want to read, and I don't middle-click them all at once. The page refreshes, and some of those links might be gone. Also, since the page is reloaded, the tab marks it as unread, adding confusion. So yeah, any refreshing of content should be done in a sane way, not by reloading the entire page.

---

### Post by dribeas on 2008-07-29
> **mssever said:**
> Well, unless you use something that requires a plugin, you're stuck with Javascript. The way HTTP works, the only way to find out about changes on the server is to poll the server; the server can't send out notifications.

Agree in Javascript as the solution, but not in that the server cannot notify users. Search for AJAX server push or web server push. Unless Firefox has crippled that functionality out in the last 3 years. Also, IE did not allow for pushes (neither planned toback in 2005 as they considered them a security threat), but I managed to write a small Java applet (hidden in an invisible frame) that kept a connection to the server open and received notifications that where then passed to Javascript in the main frame. It might not scale well with the number of connections, but trials with up to 500 simultaneous users performed fine.

Try to search into existing AJAX libraries, they probably have that solved already.

---

### Post by mssever on 2008-07-29
> **dribeas said:**
> Agree in Javascript as the solution, but not in that the server cannot notify users. Search for AJAX server push or web server push.I said that HTTP can't push content, and that's true. Back in the Netscape 3 days, Netscape's HTTP server supported a proprietary push mechanism. You used to be able to type about:fish to see a webcam of Netscapes aquarium, which used server push for updates. I don't doubt that other ways to push content have been devised, but they're not part of HTTP.

> but I managed to write a small Java applet (hidden in an invisible frame) that kept a connection to the server open and received notifications that where then passed to Javascript in the main frame.
Which is why I said, "Unless you use something that requires a plugin."

---

### Post by NxZDr on 2008-07-29
Okay, so what would the plugin options be? What would be the easiest for the client?

---

### Post by mssever on 2008-07-29
> **NxZDr said:**
> Okay, so what would the plugin options be? What would be the easiest for the client?
Flash and Java are probably the only plugins you can count on being available for most users. I have no experience with Flash and almost none with Java applets, so I can't comment on the code side of things. But from a user's perspective, I think that Flash works more seamlessly.

---

### Post by NxZDr on 2008-07-30
Okay, so given my detest of flash, and lack of my own copy, I'm thinking Java is the way to go. So it looks like the forum system will be just one big Java applet this way.

With the Server Polls, it is possible to update the update interval, right? So a dynamic interval based upon activity would be possible allowing fewer updates for pages and topics that change rarely.

---

### Post by mssever on 2008-07-30
> **NxZDr said:**
> Okay, so given my detest of flash, and lack of my own copy, I'm thinking Java is the way to go. So it looks like the forum system will be just one big Java applet this way.Well, I guarantee that I'd avoid such a forum. Java applets have many usability issues when used on a large scale. Plus, they're usually slow to load. If you use Java at all, I'd recommend dribeas's suggestion to use a small, essentially hidden Java applet that simply receives server pushes on some appropriate protocol and simply hands the data off to Javascript for processing and display.

> With the Server Polls, it is possible to update the update interval, right? So a dynamic interval based upon activity would be possible allowing fewer updates for pages and topics that change rarely.Sure, the server could send back an updated polling interval, or the polling script could use its own adaptive polling.

---

### Post by NxZDr on 2008-07-30
Now what would this be possible with a PHP based system? Or would another language be perferred.

Right now I gather it doesn't matter until I get into the specific polling routine.

Or do you reccommend something other than PHP?

---

### Post by mssever on 2008-07-30
> **NxZDr said:**
> Now what would this be possible with a PHP based system? Or would another language be perferred.

Right now I gather it doesn't matter until I get into the specific polling routine.

Or do you reccommend something other than PHP?
You can write the backend in whatever language you like (provided it's supported by your server). Personally, I don't like PHP that much, but there are others who disagree. At any rate, save yourself several headaches and use an MVC framework. For PHP, I like CodeIgniter. I'm just learning Django for Python, and even though I like Ruby as a language, I've found the documentation for Rails to be lacking.

---

### Post by NxZDr on 2008-07-30
So you're suggesting python for the frontend? I can track down webhosting that fits the system later, for my testing computer it'll take whatever I decide it needs.

---

### Post by mssever on 2008-07-30
> **NxZDr said:**
> So you're suggesting python for the frontend? I can track down webhosting that fits the system later, for my testing computer it'll take whatever I decide it needs.
No, the frontend is HTML/CSS/Javascript, and maybe a Java applet if absolutely necessary. I can't choose the backend language for you. You should do some research on that based on your goals, your skills, what you hope to learn, your personal style, etc.

---

### Post by NxZDr on 2008-07-30
Obviously HTML will need to used for the layout, but I wonder what will be used to tie in to the database, generate the pages based upon the HTML templates, ect.

If this really doesn't matter than PHP should suffice.

---

### Post by mssever on 2008-07-30
> **NxZDr said:**
> If this really doesn't matter than PHP should suffice.
It's not that it doesn't matter, so much as that there are several options that can do what you want. PHP is fine, but so are some other languages. We've fought several language wars in this forum, and I don't want to bait anyone into starting another.

But some factors to consider include what you already know and the availability of help. Based on those factors, I think the choice comes down to PHP vs. Python (with Django, TurboGears, or some other framework) and Ruby/Rails as the wildcard. If you're happy with PHP, stick with it for nowm but plan to eventually learn the other options, so you can make a more informed decision on future projects.

---

### Post by pmasiar on 2008-07-30
For a beginner, Python/Django is excellent choice (even over TurboGears), because Python is easy to learn and Django automagically generates default table updating screens. Does PHP have such packages? Are as easy to use as Django?

BTW, OP: next time please think 15 secs and invent better title for your post. Read "how to ask questions" in my sig.

---

### Post by mssever on 2008-07-31
> **pmasiar said:**
> For a beginner, Python/Django is excellent choice (even over TurboGears), because Python is easy to learn and Django automagically generates default table updating screens. Does PHP have such packages? Are as easy to use as Django?CodeIgniter (CI) can do some of that stuff for PHP, but you'll wear your fingers out if you do much OO in PHP--and CI is an OO framework. Nevertheless, when I must use PHP, CI is my choice, with plenty of templates defined in my editor to save typing.

---

### Post by NxZDr on 2008-07-31
I'd rather not start and sorts of debates over languages, I was comfortable doing PHP in the past, and the Idea behind this project was to use as little outside work as required, essentially to make my own framework.

Also, in this thread I'm just looking for input IE your thoughts. I'm not looking for links to every little framework, library, and tutorial. Though I do appreciate your input.

Edit: I'll fix it a bit.

---

### Post by mssever on 2008-07-31
> **NxZDr said:**
> I'd rather not start and sorts of debates over languages, I was comfortable doing PHP in the past, and the Idea behind this project was to use as little outside work as required, essentially to make my own framework.

Also, in this thread I'm just looking for input IE your thoughts. I'm not looking for links to every little framework, library, and tutorial. Though I do appreciate your input.

Edit: I'll fix it a bit.
The way things tend to work around here is that threads tend to drift off-topic, especially when it seems like the original problem is solved (or mostly solved).

As far as frameworks go, I don't know your skill level, but I will say that while I used to write everything from scratch, I wouldn't dream of writing a website without using a framework nowadays; frameworks simplify the process greatly. So the choice is a) use a pre-existing framework or b) roll my own. I don't have the time to roll my own framework, since there are pre-existing frameworks that meet my needs. Furthermore, I doubt whether I have sufficient experience to be able to design an adequate framework myself. Perhaps you have enough experience.

---

### Post by NxZDr on 2008-07-31
2 years Java and C++. I've done plenty of work on webpages during Highschool and University, so I figure that this shouldn't be too much trouble. I enjoy finding new challenges in programming. I think I'm ready, if not, I'll make sure I have the appropriate reference books on hand when I begin.

---

### Post by pmasiar on 2008-07-31
> **NxZDr said:**
> the Idea behind this project was to use as little outside work as required, essentially to make my own framework.

If you are asking this questions, you are obviously not skilled enough to create better framework than popular existing one (to start, you should be familiar with guts of couple frameworks, and be able to compare them, and improve on them). 

And from your attitude it seems to me that you are sadly also not experienced enough to understand this lack of skills. But one way of learning is to hit the wall, go ahead and create your own framework: next time you will appreciate more the existing ones! :-)

[Learn programming in 10 years](http://www.norvig.com/21-days.html)

---

### Post by mssever on 2008-07-31
> **pmasiar said:**
> But one way of learning is to hit the wall, go ahead and create your own framework: next time you will appreciate more the existing ones! :-)[]("http://www.norvig.com/21-days.html")
I've used that method of learning before. It was very effective. :) But it also took a lot of time.

---

### Post by NxZDr on 2008-07-31
> **pmasiar said:**
> you are obviously not skilled enough to create better framework than popular existing one[/url]

When it comes to education projects, it isn't that it needs to be better, it just needs to work. I'm not proposing to launch some massive framework to be used by all, I'm just making something that works and maybe has some nifty features. And I know the ever-popular phpBB wasn't made over night, I expect this to take at least a year to get a working prototype, likely more.

---

