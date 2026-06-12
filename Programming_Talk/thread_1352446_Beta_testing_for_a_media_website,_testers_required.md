---
title: "Beta testing for a media website, testers required"
date: 2009-12-11
forum: Programming Talk
---

### Post by gillespiea on 2009-12-11
Hi folks, seeing as i love the help that everyone on here gives me i would quite like it if people from here would be kind enough to help beta test my forums ([LINK HERE]("http://tiny.cc/5gCqQ "))

Please tell me of any errors you find and be aware that the forums are only at the very beginning stage of development. As is the rest of the site. I just want to make sure that the forums work as they should just now before i go onto making the next part of the site.

If you know what is causing any errors or of any security problems please contact me.
The site is written in PHP and uses mysql databases.
cheers.

---

### Post by SuperSonic4 on 2009-12-11
I'd rather not sign up, can't I browse as a guest?

(Arora shows the main page)

---

### Post by gillespiea on 2009-12-11
i can make you a fake account (understand that you dont want random people knowing your email address) and you can use that to look about and post if you wish :)

---

### Post by gillespiea on 2009-12-11
Actually just a thought. the email address does not need to be a real one. nothing is emailed to you to help the signup process.

---

### Post by Physical Hook on 2009-12-11
Your site is vulnerable to cross-site scripting, various pranks from people who know basic HTML, etc. - I wouldn't call this *Beta* O:)

---

### Post by gillespiea on 2009-12-11
hehe cheers. how can i make sure people cant post like this?

---

### Post by zipperback on 2009-12-11
> **gillespiea said:**
> hehe cheers. how can i make sure people cant post like this?


First you should fix your website so that it has a default page, or set your web server to not allow directory viewing.

If you go to: [http://yarp.kicks-***.net/](http://yarp.kicks-***.net/)

You will see that you don't have a default index document, so your directory layout is visible to the world

Next you should make sure that you are using proper validation for all user input and make sure you properly sanitize any data queries to your database.

In general I find it easiest to build the code base for a site and then once it's all working and tested I will usually start adding the eye candy and such to the site.

Perhaps your website might be better managed if you were to use an already existing system, and then slowly over time make the desired changes to move your website in the direction that you would like to take it.

For example, you could use one of several open source CMS or Forum systems such as Wordpress or vbulletin.

It's just a suggestion of course.

- zipperback
:popcorn:

---

### Post by Can+~ on 2009-12-11
I created a user with all fields with "test".

Btw, all this trouble for a forum? Also, the red on the background, really hurts on the eyes.

---

### Post by gillespiea on 2009-12-11
> **Can+~ said:**
> I created a user with all fields with "test".

Btw, all this trouble for a forum? Also, the red on the background, really hurts on the eyes.

This is not going to only be a forum site. Just the first part that i want to test and hopefully get help with making secure.
Thanks for letting me know about the colour scheme, i'm not too sure of it myself yet.

---

### Post by gillespiea on 2009-12-11
> **zipperback said:**
> First you should fix your website so that it has a default page, or set your web server to not allow directory viewing.

If you go to: [http://yarp.kicks-***.net/](http://yarp.kicks-***.net/)

You will see that you don't have a default index document, so your directory layout is visible to the world

Next you should make sure that you are using proper validation for all user input and make sure you properly sanitize any data queries to your database.

In general I find it easiest to build the code base for a site and then once it's all working and tested I will usually start adding the eye candy and such to the site.

Perhaps your website might be better managed if you were to use an already existing system, and then slowly over time make the desired changes to move your website in the direction that you would like to take it.

For example, you could use one of several open source CMS or Forum systems such as Wordpress or vbulletin.

It's just a suggestion of course.

- zipperback
:popcorn:

Cheers mate :)

As for using an open source system, used them all before. And this website is basically just a hobby project that i can do so i wont waste all my hard earned cash on my other hoby project (motorbike that needs a fair amount of work lol)

I know that the directories are viewable, the site is currently on a test server and will be moving to another one soon. probably tomorrow. Going to have a go at making it secure tomorrow hopefully.

Will be turning the server off now. Will post up when i've changed it over to the other one. Thanks for the help so far folks :D

---

### Post by Hellkeepa on 2009-12-12
HELLo!

First off: Show error messages. When I tried to log in using a non-existing username/password, I got nothing. Registered, and tried to log in: Nothing again, and I got no reason for why.

Also, make sure you validate the input, not just escape it. Validation of input should be the *first* action you do on said input, and show a warning/error message if the input fails outside of expected parametres. Use whitelisting when validating too, blacklisting is like fighting a house fire with a garden hose.

Also found 19 errors with your HTML code, using [W3C's HTML validator](http://validator.w3.org/). I recommend correcting these.

Then I was unable to reach your website, so I guess I'll have to end this here.

Happy codin'!

---

