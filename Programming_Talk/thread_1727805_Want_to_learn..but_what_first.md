---
title: "Want to learn..but what first?"
date: 2011-04-13
forum: Programming Talk
---

### Post by cbspace on 2011-04-13
Hello all!

So, I'm looking to learn several languages since I'd like to become a Web developer and system administrator - mainly for Web servers and networking.

I used to be a Web designer, HTML/CSS are second nature to me and I'm a novice with JavaScript.

So, I know I need to learn Bash, Perl, CGI and Python, and I'm already trying (albeit slowly) to learn JavaScript further (and jQuery) and PHP.

Reason I'm doing the switch from front-end design to back-end / system development is because of sight issues (I've had sight issues all my life, and it's on a decline) but I still want to stay in computing, since, that's all I know!

So where should I start?
Suggestions for books, tutorials, videos, etc would be a great help and ideas for small projects would be great too, since I'm going to need something to work towards and keep me motivated.

Anything you got is appreciated!

(I currently use Quanta Plus, and looking to purchase Zend Studio, so any applications I need, please let me know!) 

Many thanks
Craig

---

### Post by Some Penguin on 2011-04-13
Start with the sticky threads.

---

### Post by cbspace on 2011-04-13
Woops! Must of scrolled past the Guides sticky! Thanks!

---

### Post by BkkBonanza on 2011-04-13
Move PHP to the head of the list. 

PHP, JS, HTML, CSS form the core of most web programming today - at least on the bulk of linux based systems. Windows and corporate enterprise are different but you're on this forum so I assume you're more Linux centric.

I would learn by doing. Start a good sized project and develop it solving all the issues by using the PHP online manual. It's all in there and their is heaps of user added notes at the bottom of each page. You don't need any commercial products for any of this, including books - it's all online and free. Whenever you're stumped google the words associated with the problem and look for ideas.

---

### Post by cbspace on 2011-04-13
> **BkkBonanza said:**
> Move PHP to the head of the list. 

PHP, JS, HTML, CSS form the core of most web programming today - at least on the bulk of linux based systems. Windows and corporate enterprise are different but you're on this forum so I assume you're more Linux centric.

I would learn by doing. Start a good sized project and develop it solving all the issues by using the PHP online manual. It's all in there and their is heaps of user added notes at the bottom of each page. You don't need any commercial products for any of this, including books - it's all online and free. Whenever you're stumped google the words associated with the problem and look for ideas.

Thanks BkkBonanza, I certainly won't be touching Windows again, despite it's corporate market share. I've been wanting to get into scripting/programming for some time now, only now I can concentrate on it. 

Thanks again!

---

### Post by JacksSmith on 2011-04-13
You can start with PHP, Java script, HTML and CSS because this are platform independent. You can run websites which are created using these tools any where whatever be the operating system.

---

### Post by slavik on 2011-04-13
html/css/js will be present on any system that is accessed via a web browser, whether it is Java, C#, PHP, Perl, Python, Ruby, C, MIPS assembly that generates it.

In your case, PHP seems to be the simplest choice based on how many tutorials are available and the age of the language.

---

### Post by cbspace on 2011-04-14
Thanks all, 

Well I've grabbed the PHP manual, and sitting down with this and a sandbox.
Thinking perhaps to start making a simple login/content editor (mini CMS if you like)... 
But is that really the best place to start ona  project to work on just to learn PHP?

Or does anybody have any other ideas?

Thanks again

---

### Post by cgroza on 2011-04-14
Python!

---

### Post by cbspace on 2011-04-14
> **cgroza said:**
> Python!

I've had interest in learning Python, but not entirely sure what to do with it or what it's capabilities are... All I know it's very popular.

---

### Post by slavik on 2011-04-15
> **cbspace said:**
> Thanks all, 

Well I've grabbed the PHP manual, and sitting down with this and a sandbox.
Thinking perhaps to start making a simple login/content editor (mini CMS if you like)... 
But is that really the best place to start ona  project to work on just to learn PHP?

Or does anybody have any other ideas?

Thanks again
an advice I was once given (once you understand language basics, like assignment, references and control structures): just jump into it.

---

### Post by llanitedave on 2011-04-15
> **cbspace said:**
> I've had interest in learning Python, but not entirely sure what to do with it or what it's capabilities are... All I know it's very popular.

Python can do anything PHP can do, and more.  Its use as a web backend is not as traditional as PHP's, so there will be less documentation and fewer examples for that particular usage, but they're there, and it is fully capable.  Stylistically, I prefer it over PHP, but a lot of people will feel differently.

Check out [Django]("http://www.djangoproject.com/") as a python tool for creating sophisticated and clean web applications.

---

### Post by ghostdog74 on 2011-04-15
> **llanitedave said:**
> Python can do anything PHP can do, and more.
like what?

---

### Post by llanitedave on 2011-04-16
> **ghostdog74 said:**
> like what?

Threading for one.  Better OOP design and modularity for another.

I'm not here to dis PHP, it's a perfectly good choice for what the OP wants to do.  But the question of Python's capabilities came up, and in that context, Python gives nothing away to PHP as far as I can tell, and improves on it in several areas.

Here's a good discussion:

[http://onstartups.com/tabid/3339/bid/20493/Why-PHP-Is-Fun-and-Easy-But-Python-Is-Marriage-Material.aspx]("http://onstartups.com/tabid/3339/bid/20493/Why-PHP-Is-Fun-and-Easy-But-Python-Is-Marriage-Material.aspx")

---

### Post by honesttech on 2011-04-16
[FONT="Comic Sans MS"]Don't forget to look into the industry you are passionate about, and then look to see what they use. If you want to build websites for an industry find out who is winning (as stated by some random cracked out movie star), and develop skills that are useful. I've many friends who learned programming skills only to find that the industry they were actively seeking to join needed skills they did not have. Remember, you can't die with the most toys if you can't get a job to pay for them. Totally agree about not spending money on answers when you have all you need within this community.[/FONT]

---

### Post by CptPicard on 2011-04-16
Personally I'd say that PHP just needs to die, and a lot of programmers feel the same way. At work we try to migrate as many clients away from PHP as possible and onto Ruby on Rails. For web programming, Rails is a very productive framework, and as general purpose languages, Python/Ruby really are superior to PHP...

---

### Post by myrtle1908 on 2011-04-16
> **CptPicard said:**
> Personally I'd say that PHP just needs to die, and a lot of programmers feel the same way.

Agree.  Having worked in the web development industry for 15 years I rate PHP as one of the worst server side solutions around.  Unless you have skilled Perl programmers, PHP solutions are usually a complete mess.

* Classic ASP - absolutely disgraceful.  If ever you had the misfortune of writing ASP/VBScript you know what I mean.
* PHP - a mess (and I am very fond of Perl).
* .NET - assemblies?  Yuck.  Register this register that.  gacutil and global assembly cache rubbish.  A horrible horrible brain-dead design.
* JEE - the best of a very bad bunch.

Fortunately for me I only have to deal with JEE these days.  In the insurance/finance sector in which I work it's all Java.  I haven't had the opportunity to try Rails but have only heard good things.

---

### Post by slavik on 2011-04-16
Python has better threading? what about the GIL and the fact that it prevents any threads from running concurrently? (unless we move off the CPython implementation). What about the retardedness of the OpenGL bindings calling glError() after every other gl*() call?

J2EE - def best of the worst, more spread out and has more research into libraries and design patterns. Pretty much always, you will see struts, hibernate and spring.

PHP does need to die, but it is still useful and quicker to set up and pick up than most alternatives.

I am a die hard Perl fan (if you haven't been around for the past 5 years on this forum), but at one time, it was quicker for me to set up apache with mod_php and learn enough about connecting to a mysql db in php than it would have taken me with Perl. Although know I really like HTML::Mason. :)

The big point is that the language should not get in your way, if you use PHP properly (as a template language), you'll be fine. OOP is not really needed on small web sites, it is very useful when you need to abstract something away inside the code and need for the object to keep track of it's state.

---

### Post by stealth. on 2011-04-21
> **cgroza said:**
> python!

yes!

---

