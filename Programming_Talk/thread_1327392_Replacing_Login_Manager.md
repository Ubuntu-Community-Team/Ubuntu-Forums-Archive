---
title: "Replacing Login Manager"
date: 2009-11-15
forum: Programming Talk
---

### Post by wagner89 on 2009-11-15
Hello! 

This is my first post on this forum, please excuse me if I am posting in the wrong place. 

I'm researching Image Based Authentication, and I am planning to implement such a system for my licentiate thesis. Because I want to show that such a system would have practical use, I want to change the way Ubuntu takes care of authentication. 

Because Ubuntu is open source, has a beautiful interface, and is massively popular, I thought it might be worth a try to replace her current login mechanism with my own system. It would be impressive enough to get a good grade, useful enough that I don't consider the time spent on development as wasted, and most importantly I think I would really enjoy the process :) 

From what I understood by now from the stuff I've read, the login for Ubuntu is managed by GDM, which is a part of GNOME, but which also does a lot of other things as well. What I basically want is to write a program that can handle login (local login, I'm not thinking remote stuff just yet): so it can take a username, show a few sets of images, record the users selections, check if they form a match with the users set of password images, and allow login if they do, deny entry they don't. And of course an application with which users can be added, passwords can be changed, and other admin stuff can be performed.

I hope something like this could be done:
  The system starts as normal, my GUI appears, and in case of successful authentication, either does what steps besides these would have been done by the original system, or gives control back to the original system, so it can finish the login process. I actually only want to check which user wants to log in, and if he know the correct password, the rest should stay as much the same as possible.

I would greatly appreciate any feedback in terms of:

  - recommended bibliography
  - advice or explication on what exactly is/are the component/s I have to change
  - links to any tutorials, websites that you consider helpful
  - and finally any acknowledgment on whether you think this project would really be          useful or not

Sorry if I let this run too long, I just wanted to avoid looking like I don't know what I'm asking :P

---

### Post by nvteighen on 2009-11-15
Seems a difficult task, exactly the same you'd do for a licenciate thesis...

The little I know of GDM tells me that it seems to be a rather monolythic piece of software only "customizable" through themes and nothing much more than that. So, possibly, you don't have a plugin API to work with and you'll have to effectively change GDM's source or replace GDM as Display Manager but keeping GNOME to start up.

I'm not sure how GNOME's start up sequence is, but maybe you can find a way to start it correctly up from your own Display Manager. Some people use KDM to start GNOME because they like it better (seems to be more customizable), so it has to be possible.

---

### Post by falconindy on 2009-11-15
Would probably be useful to start with something simpler that accomplishes the same task, like [SLiM]("http://slim.berlios.de/")

---

### Post by Simian Man on 2009-11-15
> **falconindy said:**
> Would probably be useful to start with something simpler that accomplishes the same task, like [SLiM]("http://slim.berlios.de/")

SLiM is very simple, easy to use and is only 3,000 lines of code.  I'd just add what you want to that.

---

### Post by apmcd47 on 2009-11-15
Umm ... sorry if I'm being stupid, but shouldn't you be looking at the PAM (plugin(?) Authentication Module)? This would leave the GUI alone and have the advantage of working for all password-based login methods.

Andrew

---

### Post by wagner89 on 2009-11-15
Wow, great forum, replies come really quickly :D Thanks a bunch!

I've downloaded SLiM source code, I'll try to figure it out in the following days.
I'm getting sleepy, but I'll also check out PAM, I don't know anything about that yet.

Nothing you think has something to do with the subject is stupid, I really want to do thorough research, and contributions are appreciated.

BTW, I hope I'm not being a pain, asking such general questions. I'm not lazy to read the f*** manuals, but I am still in the phase of figuring out what manuals need to be read :D
Thanks for the tips, keep them coming :D

---

