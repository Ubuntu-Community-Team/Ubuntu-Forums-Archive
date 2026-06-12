---
title: "JavaScript for system admin scripts"
date: 2019-10-02
forum: Programming Talk
---

### Post by jason.jackal on 2019-10-02
Does anyone use JavaScript for system admin scripts or tasks? I usually do everything in Bash and/or Perl; however, I am learning JavaScript for a project with HTML files. Due to the latter, I wanted to stick with the language during the project time, to learn it better.

---

### Post by jessica-0 on 2019-10-04
I am not sure I understand what you are referring to. JavaScript is a "Browser" (I.E. FireFox, Chrome, IE) language. Now I don't want to get into a NodeJS or React system, these are entirely different JavaScript Environments. Although if you are referring to actual Terminal programming with JavaScript, it is something that I have not heard of, nor dealt with.

---

### Post by jason.jackal on 2019-10-04
> **jessica-0 said:**
>  NodeJS or React system, these are entirely different JavaScript Environments. 

I suspect NodesJS is what I am wondering about, since it can be used locally on machine or server. In addition, I have been reading about administrators leveraging JavaScript for system admin scripts. Due to the latter, is why I wanted to know their experience with such use cases.

Thank you

---

### Post by sdsurfer on 2019-10-04
Here is a primer straight from Mozilla. A very short, terse summary of server-side Javascript with examples:
[https://developer.mozilla.org/en-US/docs/Archive/Web/Server-Side_JavaScript/Walkthrough](https://developer.mozilla.org/en-US/docs/Archive/Web/Server-Side_JavaScript/Walkthrough)

Node.js uses Google's Javascript engine as it's backbone.
[https://opensourceforu.com/2016/01/an-introduction-to-node-js-the-server-side-javascript/](https://opensourceforu.com/2016/01/an-introduction-to-node-js-the-server-side-javascript/)

Should you use it? Like anything else, "it depends." The following is strictly opinion, this is a good opportunity for those working with such frameworks to chime in.

Pros:
- Server side JS in any implementation is a growing trend.
- If you have a strong JS background, it can only widen your skillset.
- I see a LOT of opportunities for employment in server side JS framework scripting.

Cons:
- Requires a dependence on **something,** Java, C, Google's engine, or other resources to execute it.
- Ability to install and configure these resources may be the real challenge, not just using the chosen framework.
- IMO we have so many awesome existing and growing server side resources to work with, I haven't found a good reason (yet) to replace them with a technology originally intended for client side scripting.

---

### Post by TheFu on 2019-10-04
I'm an old *nix admin from the early 1990s.  IMHO:
```
Priority        Languages
   1            bash, sh
   2            perl, awk, ksh
   3            C
   5            Python
   15           Ruby (3x worse than python)
   20           GoLang, Php, Javascript, <insert lang>
                 only if the primary reason for the server
                 is an application written in the language
   50           Avoid. Languages not connected to the project.
```

Compiled languages that don't need any runtime help, shipped in binary would be like C.  If building an executable locally 
is required, like Rust, then it drops to Php level, or lower. Avoid.  We decided against using puppet and chef because they required another dependency, Ruby.  We do use ansible and decided the python dependencies were worth it to have agentless devops on our systems.  When we first started, we did have to install python and a few python libraries.  We did that using ssh + bash as the bootstrap.  Then later Linux releases started including python dependencies so ansible "just worked."  

For tools based on php or golang or any other extra language, the use for tools written in those languages should be tied to the application.  For example, nextcloud is written in php. The upgrade/maintenance tool, /var/www/html/nextcloud/occ, for nextcloud is also written in php.  I'd never seen any php used as an admin tool before that point anywhere.  In a situation where an entire app is written in a language, then a strong case could easily be made that the maintenance of that application should also be in the same language.  It would not be acceptable to require node.js for maintenance scripts of Nextcloud while nextcloud has no other dependency.  Also, mandating that some GUI web-browser be installed on any server to provide an engine for maintenance tools should be illegal.  Oracle did something like this with some of their expensive software. We had to install xvfb to get the main daemon running, which was a web-app server. How stupid is that?  The servers we deployed the "server" onto didn't have any graphics hardware. They were 100% console-based systems.

I was a professional C++ software developer for 15 yrs also.  I love Ruby, use Perl most days.  Also coded in about 20 other languages.  My thoughts above aren't about the languages, just the suitability for admin tasks on systems seen today.

Please don't use javascript for admin needs. Be part of the solution, not another one of the problems, please.  Just because something is possible, that doesn't mean it is a good idea.

---

### Post by jason.jackal on 2019-10-04
> **TheFu said:**
> I'm an old *nix admin from the early 1990s.  IMHO:
```
Priority        Languages
   1            bash, sh
   2            perl, awk, ksh
   3            C
   5            Python
   15           Ruby (3x worse than python)
   20           GoLang, Php, Javascript, <insert lang>
                 only if the primary reason for the server
                 is an application written in the language
   50           Avoid. Languages not connected to the project.
```

Compiled languages that don't need any runtime help, shipped in binary would be like C.  If building an executable locally 
is required, like Rust, then it drops to Php level, or lower. Avoid.  We decided against using puppet and chef because they required another dependency, Ruby.  We do use ansible and decided the python dependencies were worth it to have agentless devops on our systems.  When we first started, we did have to install python and a few python libraries.  We did that using ssh + bash as the bootstrap.  Then later Linux releases started including python dependencies so ansible "just worked."  

For tools based on php or golang or any other extra language, the use for tools written in those languages should be tied to the application.  For example, nextcloud is written in php. The upgrade/maintenance tool, /var/www/html/nextcloud/occ, for nextcloud is also written in php.  I'd never seen any php used as an admin tool before that point anywhere.  In a situation where an entire app is written in a language, then a strong case could easily be made that the maintenance of that application should also be in the same language.  It would not be acceptable to require node.js for maintenance scripts of Nextcloud while nextcloud has no other dependency.  Also, mandating that some GUI web-browser be installed on any server to provide an engine for maintenance tools should be illegal.  Oracle did something like this with some of their expensive software. We had to install xvfb to get the main daemon running, which was a web-app server. How stupid is that?  The servers we deployed the "server" onto didn't have any graphics hardware. They were 100% console-based systems.

I was a professional C++ software developer for 15 yrs also.  I love Ruby, use Perl most days.  Also coded in about 20 other languages.  My thoughts above aren't about the languages, just the suitability for admin tasks on systems seen today.

Please don't use javascript for admin needs. Be part of the solution, not another one of the problems, please.  Just because something is possible, that doesn't mean it is a good idea.

I as well use mostly Perl, and some Python, but mostly Perl for every day tasks. Most of my own personal scripts or applications are done in Perl even though I had a number of class/semesters of C. I never learned OOP design, since I am not a programmer by trade, nor am I Linux administrator. I mainly do network engineering; however, I needed to build a resource page, and I found some easy concepts with JavaScript, which enabled me to build something without having to install PHP and Mysql. I was keeping it very simple and the KISS principle.

---

### Post by sdsurfer on 2019-10-04
> Please don't use javascript for admin needs.

Heh. Preaching to the choir here, but I said the same thing 13 years or so ago (wasn't it 1995?) when PHP was making a strong move for the web. I swore it would never outdate Perl, my language of choice, my first love . . . .

Well. I am lucky to even see a Perl script or framework nowadays, unless it's one I write. Luckily I had the foresight to learn PHP quickly lest I become extinct . . . it could happen with JS server side frameworks too. It's just never going to end.

---

### Post by Skaperen on 2019-10-04
13 years ago is 2006.  1996 is 23 years ago.  and i use Javascript for web pages like this [picture of my church]("http://ipal.net/vance/").  for admin and user scripts (numbering in the high hundreds) i use Bash, Pike, or Python3.  for computational programs i use C.

---

### Post by TheFu on 2019-10-04
> **sdsurfer said:**
> Heh. Preaching to the choir here, but I said the same thing 13 years or so ago (wasn't it 1995?) when PHP was making a strong move for the web. I swore it would never outdate Perl, my language of choice, my first love . . . .

Well. I am lucky to even see a Perl script or framework nowadays, unless it's one I write. Luckily I had the foresight to learn PHP quickly lest I become extinct . . . it could happen with JS server side frameworks too. It's just never going to end.

Please name 1 general purpose admin tool that isn't a webapp written in php.  You know, something that would be installed inside an enterprise on every Linux machine - say 500-2000 systems. Or a tool that comes preinstalled in the Ubuntu Server distro written in php.  Teach me Obi Wan.

Perl is still used by at least 50 tools used by admins on every Linux system today. Didn't look too hard to find them.  ```
$ file /usr/sbin/adduser
/usr/sbin/adduser: a /usr/bin/perl script, ASCII text executable
```

---

### Post by Skaperen on 2019-10-04
this is my Xubuntu 18.04 laptop:

```

lt2a/forums /home/forums 21> find /usr/bin -type f -exec file '{}' ';'|fgrep -i perl|wc -l
185
lt2a/forums /home/forums 22> find /usr/bin -type f -exec file '{}' ';'|fgrep -i php|wc -l
0
lt2a/forums /home/forums 23> find /usr/bin -type f -exec file '{}' ';'|fgrep -i java|wc -l
0
lt2a/forums /home/forums 24> find /usr/bin -type f -exec file '{}' ';'|fgrep -i python|wc -l
70
lt2a/forums /home/forums 25>

```

---

### Post by sdsurfer on 2019-10-04
Totally got me on the math, I was only saying PHP came out around 95. I don't even recall exactly when I got into coding it. Too long ago.

TheFu you totally missed my point, I've just learned being "language agnostic" just increases my skillset and allows me to evolve. They're just tools. I am always actively looking for new opportunities, and a lot of them are asking for server side JS developers. I mean, a LOT. Which I haven't dug into enough. If I'd have stuck to my guns with Perl, I'd be living in the street today. I don't mind evolving if it pays well enough. :-P

---

### Post by TheFu on 2019-10-04
> **sdsurfer said:**
>  TheFu you totally missed my point, I've just learned being "language agnostic" just increases my skillset and allows me to evolve. They're just tools. I am always actively looking for new opportunities, and a lot of them are asking for server side JS developers. I mean, a LOT. Which I haven't dug into enough. If I'd have stuck to my guns with Perl, I'd be living in the street today. I don't mind evolving if it pays well enough. :-P

Sorry, I was looking at the title of this thread.  Figured we were on that topic.  My mistake.

There is a shortage of perl developers, BTW.

---

### Post by Skaperen on 2019-10-05
i did not learn perl.  i don't know if i could learn it today.  i had difficulties understanding many of the details.  and i was turned off by many other like the leading characters of variable names to mean the type.

but i did learn python about 7 years ago.  it is very much like one configuration of a language i designed back in the 1980s.  it was more like a language matrix where python could fit in.  i also learned pike in the interim, which could also fit in, in a different spot, with a few changes (think of python with a C-like syntax)

i did learn javascript but have disliked it because of many limitations.  python was the show stopper for me as it fulfilled those limitations.

this [blog post]("https://stackoverflow.blog/2017/09/06/incredible-growth-python/") from 2017 is interesting reading. it shows stunning growth of python.

---

### Post by sdsurfer on 2019-10-07
^^ That's another one I need to work on!

> **TheFu said:**
> There is a shortage of perl developers, BTW.

WHERE? LOL . . . whenever I mention Perl the reaction is mild. I was a freelancer for years when we still had an chance on Elance (now Upworthy, I think.) I encountered a Perl project that blew me away.

Most Perl scripts I see are procedural, maybe with some subs but still largely procedural. This project was a front controller maybe 80 lines long and completely OOP, followed SOLID before it was really a "thing." It was beautiful. It was a unicorn. :-D

---

### Post by jason.jackal on 2019-10-07
> **TheFu said:**
> Sorry, I was looking at the title of this thread.  Figured we were on that topic.  My mistake.

There is a shortage of perl developers, BTW.

To be honest, I didn't know perl was still being used heavily. I still use it since it was the first language I learned after: Commodore Basic, 6502 ASM and C.

I started picking up Python since it now has bindings for all things, including Cisco and Ansible. Currently, I am an network engineer; however, I like to roll my own tools at times or play around with some hobby projects.

Yet, I been doing some web front end work in JavaScript and read about Nodes.js and wanted to see what folks had to say about it from a System Side perspective.

---

### Post by jason.jackal on 2019-10-07
> **Skaperen said:**
> i did not learn perl.  i don't know if i could learn it today.  i had difficulties understanding many of the details.  and i was turned off by many other like the leading characters of variable names to mean the type.

but i did learn python about 7 years ago.  it is very much like one configuration of a language i designed back in the 1980s.  it was more like a language matrix where python could fit in.  i also learned pike in the interim, which could also fit in, in a different spot, with a few changes (think of python with a C-like syntax)

i did learn javascript but have disliked it because of many limitations.  python was the show stopper for me as it fulfilled those limitations.

this [blog post]("https://stackoverflow.blog/2017/09/06/incredible-growth-python/") from 2017 is interesting reading. it shows stunning growth of python.

Thank you for the link, it was a great read and very interesting. I never learned Pike; however, back in the 90s (I think) I heard of it. I never really learned Python, since in the early 90s I learned Perl. Perl did everything and anything for me coming from a C university background, and much easier. I never did programming professionally, after I learned Cisco and Juniper networking. However, a good scripting language was needed, and perl came to the rescue.

Now days, everything has an API or you can install with PIP. Funny, perl had cpan for a number of years and you could use libraries or packages from installing. So it is a pain to see perl get dropped by the way side; however, maybe if Google hired the maker of Perl oppose to Python.... maybe it will be a different story. Either way... Python is the future until Go can rule the world... "EH... HEE HEE HEE!!!". Would love to see more GO API for things.

Thank you

---

### Post by Skaperen on 2019-10-10
one thing i don't like about GO is having to also mush the shift key for every assignment i type in.

---

### Post by Skaperen on 2019-10-11
i understand that an entire web page can be constructed by javascript code filling in the document object model.  i also understand that javascript has a full suite of network access, at least for UDP and TCP.  my current thought is to build something like a forum with a javascript front end and a python back end, loading the javascript just once, starting with a small static web page, and going extreme dynamic from there.  the front end connects to the back end and exchanges data in JSON format.  javascript will be the UI and python will be the API.  anyone can plug in their own UI by just making a page anywhere that loads their own javascript (maybe just a hack of the original).  the back end won't need to deal with any UI, at all.  the front end won't need to deal with any database access since the whole FE<->BE interface is just JSON over TCP (with SSL in there).

---

### Post by TheFu on 2019-10-11
> **Skaperen said:**
> i understand that an entire web page can be constructed by javascript code filling in the document object model.  i also understand that javascript has a full suite of network access, at least for UDP and TCP.  my current thought is to build something like a forum with a javascript front end and a python back end, loading the javascript just once, starting with a small static web page, and going extreme dynamic from there.  the front end connects to the back end and exchanges data in JSON format.  javascript will be the UI and python will be the API.  anyone can plug in their own UI by just making a page anywhere that loads their own javascript (maybe just a hack of the original).  the back end won't need to deal with any UI, at all.  the front end won't need to deal with any database access since the whole FE<->BE interface is just JSON over TCP (with SSL in there).

Never trust any client-side input data. Always re-re-scrub it for allowed values.

A website that uses javascript on the front end and Python on the back end is called a webapp. Extremely common.  Check out Flask for the toolkit, unless you want to do it the hard way. A bunch of guys in my LUG was learning the Flask framework.
If you are into Perl5 webapps, Dancer2, Mojolicious, and Catalyst are the most common.  Dancer is the easiest. I've written about 20 Dancer webapps. It has lots and lots of dependencies, so plan for 1-2 hours in metacpan for those to download, get tested and installed. Mojolicious is a practical framework with very few limitations and some rough edges.  Catalyst can handle anything, but it is complicated. People say it takes 6 months to understand the local implementation for any Catalyst webapp.  Amazon was (is?) a Catalyst webapp for years.  With Dancer, you can create a single DB table CRUD webapp in about 5 lines of code.  Plackup/PSGI can handle horizontal scaling to almost any level needed.  It is crazy fast.  Be certain to use perlbrew for environment management.

But webapps really don't have anything to do with administrative scripting.

---

### Post by jason.jackal on 2019-10-21
> **TheFu said:**
> Never trust any client-side input data. Always re-re-scrub it for allowed values.

A website that uses javascript on the front end and Python on the back end is called a webapp. Extremely common.  Check out Flask for the toolkit, unless you want to do it the hard way. A bunch of guys in my LUG was learning the Flask framework.
If you are into Perl5 webapps, Dancer2, Mojolicious, and Catalyst are the most common.  Dancer is the easiest. I've written about 20 Dancer webapps. It has lots and lots of dependencies, so plan for 1-2 hours in metacpan for those to download, get tested and installed. Mojolicious is a practical framework with very few limitations and some rough edges.  Catalyst can handle anything, but it is complicated. People say it takes 6 months to understand the local implementation for any Catalyst webapp.  Amazon was (is?) a Catalyst webapp for years.  With Dancer, you can create a single DB table CRUD webapp in about 5 lines of code.  Plackup/PSGI can handle horizontal scaling to almost any level needed.  It is crazy fast.  Be certain to use perlbrew for environment management.

But webapps really don't have anything to do with administrative scripting.

Little off topic on my part - But do you still do Perl5 webapp programming? I really like using Perl5 for my personal scripts and small applications that need to use regex, or some GUI (Tk) based applications. Most of my production/work scripts are in Python, which is due to libraries, other resources, or API being used by vendor. (Cisco... this is for you ..|..) support Perl again...well at lest it they still support TCL on the chassis.

I know Perl is way behind in publicity compared to Python. Yet, you still see a number Perl5 dependencies being installed with some Linux applications, you just need to watch or review the additional installed applications when installing some applications.

---

