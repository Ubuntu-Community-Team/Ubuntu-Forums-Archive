---
title: "Django flexibility?"
date: 2008-12-22
forum: Programming Talk
---

### Post by trivialpackets on 2008-12-22
Here is my thoughts, I've been learning ruby, and having read and done some python in the past, I think both are solid languages.  Now, my area of interest is in the development of web applications, and in particular, I have one in mind.  I won't get into any details, but it's a database driven app, and mostly form driven.  Would need authentication, and viewable divs based upon the authentication, ability to handle blob files, for uploading file storage, and ideally some kind of plugin to assist with processing credit cards payments, or even check transfers.  

Now, I know that rails has the flexibility to work with this in mind, but I don't have any experience with django, yet am very interested in any feedback.  Is it less flexible than rails, or am I reading into the framework wrong as a CMS type design.  Anyone with any experience with either Django, or preferably both Django and rails would be terrific!  Definitely not a Flamewar.

---

### Post by trivialpackets on 2008-12-22
Honestly, I'm sure that part of this is lack of knowledge on my part, which is why I'm asking the question here.  Python has a pretty strong following here as far as I can tell.

---

### Post by pmasiar on 2008-12-22
I cannot compare with Rails (never used it), but Django follows mostly the same philosophy ("conventions instead of configuration") and has rather nicely designed "plugins" (they call it "applications") for basic tasks.

If you need guaranteed maximum future flexibility, consider Turbogears (which was designed to be more flexible than Django from very beginning: using multiple templating engines, O/R mappers, etc), or Pylons (which is metaframework used by Turbogears). So you can start with TG now, and replace parts you don't like. Of course Django is simpler than TG - because there is less choice.

My bet is, because Python community is so much bigger than Ruby's, growth will be bigger in Python.

---

