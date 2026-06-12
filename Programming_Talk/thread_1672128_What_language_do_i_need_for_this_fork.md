---
title: "What language do i need for this fork?"
date: 2011-01-20
forum: Programming Talk
---

### Post by Kjan32 on 2011-01-20
Hello, I want to *really* learn a programming language. I fooled around with linux scripting, python an C before, but not really mastered any of them.  Now I want to make my own browser, because a) I have bunch of ideas for it b) it sounds like fun. As building from scratch will be beyond my skills(for now), I wish to fork firefox.  I did my homework and found that firefox was made of C/C++ and JavaScript. But not sure if I need them all. To make a real fork, which language(s) I really need to learn?   I though about making extensions with JS, but I need enough control to be able to block IP's, which don't seems to be possible with an extension  I hope to be taken/answered seriously,  Thanks

---

### Post by Kjan32 on 2011-01-20
Hello, I want to *really* learn a programming language. I fooled around with linux scripting, python an C before, but not really mastered any of them.  Now I want to make my own browser, because a) I have bunch of ideas for it b) it sounds like fun. As building from scratch will be beyond my skills(for now), I wish to fork firefox.  I did my homework and found that firefox was made of C/C++ and JavaScript. But not sure if I need them all. To make a real fork, which language(s) I really need to learn?   I though about making extensions with JS, but I need enough control to be able to block IP's, which don't seems to be possible with an extension  I hope to be taken/answered seriously,  Thanks

---

### Post by Kjan32 on 2011-01-20
Hello, I want to *really* learn a programming language. I fooled around with linux scripting, python an C before, but not really mastered any of them.

Now I want to make my own browser, because a) I have bunch of ideas for it b) it sounds like fun. As building from scratch will be beyond my skills(for now), I wish to fork firefox.

I did my homework and found that firefox was made of C/C++ and JavaScript. But not sure if I need them all. To make a real fork, which language(s) I really need to learn? 

I though about making extensions with JS, but I need enough control to be able to block IP's, which don't seems to be possible with an extension

I hope to be taken/answered seriously,

Thanks

---

### Post by DangerOnTheRanger on 2011-01-20
First off, no need to post 3 times.
Answering your question, forking Firefox is probably not the best idea. You'll need to learn all of them.

There's a simple Qt/GTK+ web browser core called WebKit (repo name python-webkit). It's the base for the default Android web browser, and has a Python interface. It's much simpler than Firefox, and should suit your needs better.

---

### Post by fct on 2011-01-21
Hi, I'm compiling firefox releases for work. It's a beast and I'd avoid forking it to start a new browser without years of advanced C++ development experience.

Also, browsers are large complicated projects. Good luck, but I'd look for some other thing for starters.

---

### Post by worksofcraft on 2011-01-21
> **Kjan32 said:**
> Hello, I want to *really* learn a programming language. I fooled around with linux scripting, python an C before, but not really mastered any of them.  Now I want to make my own browser, because a) I have bunch of ideas for it b) it sounds like fun. As building from scratch will be beyond my skills(for now), I wish to fork firefox.  I did my homework and found that firefox was made of C/C++ and JavaScript. But not sure if I need them all. To make a real fork, which language(s) I really need to learn?   I though about making extensions with JS, but I need enough control to be able to block IP's, which don't seems to be possible with an extension  I hope to be taken/answered seriously,  Thanks

A browser is in the first place for viewing HTML files and that is really complicated enough when you add in all the CSS stuff and client side scripting and different image formats and embedded objects.

I do think that making an extension, I mean a plug-in, to existing browser would be a much better starting point for your learning experience. I also think that if you want to block IP addresses then the browser is not the right place. Much more likely you need to do it in your routing tables and I gather nationwide web sites effectively get silenced by excluding them from the domain name servers :shock:

---

### Post by Simian Man on 2011-01-21
Yeah, Firefox is a pretty bad choice as it's an extremely complicated code base.  If you want to fork a browser, I'd look at Arora or Midori, both of which are newer and simpler.  They are also Webkit based which is a lot cleaner than FF's Gecko engine.

Honestly though, I don't think a project like this is a good way to really learn a language.  Existing software projects usually don't have exactly the best code, and will teach you bad habits without you understanding why certain design decisions were made.  Doing a smaller project starting from scratch would be better.

---

