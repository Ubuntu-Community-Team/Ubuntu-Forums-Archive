---
title: "Using PHP to create new linux user"
date: 2007-08-27
forum: Programming Talk
---

### Post by an0malist on 2007-08-27
Newbie here!

I'm taking on a scripting challenge at work.  Essentially what I need to do is, using a web front end, create users on the ubuntu machine that is serving up the page.

For instance:
User goes to web form -> Fills out their contact information -> a script is ran on that same box that served the web form which creates a user based on the information in the form.

This is going to be used as a login account for proftpd.

I'm just getting started with scripting so I'm wondering the very basic: How do I execute a script on that machine to create that user account?

I'm not sure where to start. :)

thanks a lot in advance for the direction!!

---

### Post by bjarneh on 2007-08-27
man useradd

---

### Post by an0malist on 2007-08-27
ok, i understand the linux command to do it, but how do I execute that from a php script through apache?  does that make sense?

---

### Post by an0malist on 2007-08-27
found it:
php function
exec()

there are a few other similar commands as well..

---

### Post by slavik on 2007-08-28
> **an0malist said:**
> found it:
php function
exec()

there are a few other similar commands as well..
except exec never returns.

you should be able to use backticks

---

### Post by twistedtwig on 2007-08-28
This is a little off topic but that could be (if I understand it) a little dangerous.  At least if it is publicly accessable.  Seems to me that it could make the machine alittle more hackable if you give a way for users to be created.

Def not saying don't do it just a word of caution really.

Good Luck and have fun

---

