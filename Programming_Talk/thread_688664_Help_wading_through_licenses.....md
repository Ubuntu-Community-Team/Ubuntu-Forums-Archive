---
title: "Help wading through licenses...."
date: 2008-02-05
forum: Programming Talk
---

### Post by shaggy999 on 2008-02-05
How do I know if it's ok if I use library A which is published under license X and also use library B which is published under license Y in the same project? Is there a good website to go to regarding how 'compatible' various licenses are with each other?

I would also be interested in finding a place that discusses each license and how they work. My main concern is that "open source" and GPL are not 1-to-1, there are many open source licenses out there. I want to make sure that whatever I produce I can pass on to others, but certain licenses may conflict with each other.

Any help?

---

### Post by pmasiar on 2008-02-05
[http://www.gnu.org/licenses/licenses.html](http://www.gnu.org/licenses/licenses.html)

Most software is under GPL and BSD license. GPL can use BSD, BSD cannot (because BSD allows to make changes private, which is preferred by some projects).

Of course best course depends on your project goals. You forgot to mention them, should we guess?

For reliable advice you should consult a lawyer :-)

---

### Post by LaRoza on 2008-02-05
> **pmasiar said:**
> 
For reliable advice you should consult a lawyer :-)

Or use all GPL.

---

### Post by jingo811 on 2008-02-05
Can't help you much but I once stumbled upon this site.  It's got a very short and concise explanation between GPL, LGPL and "open-source".  
[http://www.netrino.com/Embedded-Systems/How-To/Embedded-Linux-Open-Source](http://www.netrino.com/Embedded-Systems/How-To/Embedded-Linux-Open-Source)
But as he says it's not the complete story.  I don't think anybody knows for sure anymore not even the lawyers :)  Licenses popup all over the place like fungus.

---

### Post by pmasiar on 2008-02-05
> **LaRoza said:**
> Or use all GPL.

GPL is popular license, but not best for all apps. ie Django (Python web app framework) and Satchmo (e-shop) are released under BSD, to allow creating private clones - and make living out of it. When I was looking for python e-shop, BSD Satchmo has a big plus. In fact, I would NOT be able to use GPL software.

---

### Post by LaRoza on 2008-02-05
> **pmasiar said:**
> GPL is popular license, but not best for all apps. ie Django (Python web app framework) and Satchmo (e-shop) are released under BSD, to allow creating private clones - and make living out of it. When I was looking for python e-shop, BSD Satchmo has a big plus. In fact, I would NOT be able to use GPL software.

I didn't say it would be best, but it would be less confusing.

---

### Post by pmasiar on 2008-02-05
> **LaRoza said:**
> I didn't say it would be best, but it would be less confusing.

For project like Satchmo, "less confusing" would be totally wrong. That's why I asked for project goals, instead of "one size fits all" suggestion of GPL, and suggested asking a lawyer too.

---

### Post by shaggy999 on 2008-02-05
I am interested in writing some games and so I'm going through all of the various libraries (like SDL, Boost, OpenGL, OGRE, etc...) and trying to figure out which libraries I want to use.  But I don't want to waste my time learning a development library if it ends up being a dead end because I can't use another library in the same project and still release the full source of my program.

---

### Post by shaggy999 on 2008-02-05
Found my compatability list!

[http://www.gnu.org/licenses/license-list.html](http://www.gnu.org/licenses/license-list.html)

---

### Post by vanessa on 2008-04-15
I've decided to start studying in more detail the licenses available to the FOSS community, and to start with I wrote about what you are or aren't permitted to do when you want to use a permissive license (such as the BSD license) in your code.

I wrote it at my blog: [http://bani2.blogspot.com/2008/04/when-permissive-licenses-dont-permit.html](http://bani2.blogspot.com/2008/04/when-permissive-licenses-dont-permit.html)

Any comments are very welcome.

About using a GPL library in a BSD code, the position of the FSF is that you can't do it, but there are people who (try to) disagree.

---

### Post by Tuna-Fish on 2008-04-15
The technical jargon is that if your work is a derivative of some other work, you cannot use any license that is incompatible with it. 

What constitutes 'derivative work' in software? Outside immediately obvious situations, such as borrowing code, there simply are not enough precedents. Your guess is as good as mine. FSF thinks that linking to their code in some way is derivative work, while many others think it's not. So far FSF has either won, or settled out of court to their advantage, all cases.

---

### Post by samjh on 2008-04-15
> **shaggy999 said:**
> How do I know if it's ok if I use library A which is published under license X and also use library B which is published under license Y in the same project? Is there a good website to go to regarding how 'compatible' various licenses are with each other?

I would also be interested in finding a place that discusses each license and how they work. My main concern is that "open source" and GPL are not 1-to-1, there are many open source licenses out there. I want to make sure that whatever I produce I can pass on to others, but certain licenses may conflict with each other.

Any help?

Go straight to the horse's mouth and ask the experts:
[http://www.softwarefreedom.org/about/contact/](http://www.softwarefreedom.org/about/contact/)

---

### Post by pmasiar on 2008-04-15
Best place to start any similar research is IMNSHO wikipedia:
[http://en.wikipedia.org/wiki/Permissive_and_copyleft_licences](http://en.wikipedia.org/wiki/Permissive_and_copyleft_licences) and follow fins from there :-)

---

### Post by nanotube on 2008-04-15
> **pmasiar said:**
> GPL is popular license, but not best for all apps. ie Django (Python web app framework) and Satchmo (e-shop) are released under BSD, to allow creating private clones - and make living out of it. When I was looking for python e-shop, BSD Satchmo has a big plus. In fact, I would NOT be able to use GPL software.

i must respectfully disagree with your assessment. since these projects (django and satchmo) are (as i understand - correct if i'm wrong) entirely server-side, with no code actually "distributed" to the users, there is no problem taking a gpl django and making a "private" clone. only the affero gpl would force you to release code to server-side apps, normal gpl does not.

yet another exciting kink in the licensing forest (can forests have kinks...?) :)

---

### Post by bruce89 on 2008-04-15
> **pmasiar said:**
> to allow creating private clones - and make living out of it. When I was looking for python e-shop, BSD Satchmo has a big plus. In fact, I would NOT be able to use GPL software.

The GPL allows private modifications - [http://www.gnu.org/licenses/gpl-faq.html#GPLRequireSourcePostedPublic:](http://www.gnu.org/licenses/gpl-faq.html#GPLRequireSourcePostedPublic:)

> The GPL does not require you to release your modified version, or any part of it. You are free to make modifications and use them privately, without ever releasing them. This applies to organizations (including companies), too; an organization can make a modified version and use it internally without ever releasing it outside the organization.

---

### Post by LaRoza on 2008-04-15
> **bruce89 said:**
> The GPL allows private modifications - [http://www.gnu.org/licenses/gpl-faq.html#GPLRequireSourcePostedPublic:](http://www.gnu.org/licenses/gpl-faq.html#GPLRequireSourcePostedPublic:)

Satchmo isn't private.

[http://www.satchmoproject.com/](http://www.satchmoproject.com/)

---

