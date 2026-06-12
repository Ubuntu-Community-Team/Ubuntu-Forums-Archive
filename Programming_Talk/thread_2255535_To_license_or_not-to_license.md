---
title: "To license or not-to license?"
date: 2014-12-05
forum: Programming Talk
---

### Post by SagaciousKJB on 2014-12-05
Recently I've entered the phase of "finalizing" a program where I want other eyes on it, and in this particular case some of these eyes may belong to professionals in various industry positions, that could be kind of "vetting" me for a position at their company--entry level but that's where I want to start anyway.  So I figured it would be a wise idea to license my software, even though I really have no intention or desire to redistribute it.

My question is what is a more appropriate license for a program to have in this situation?  From what I've read my program is actually incompatible with the GPL licenses because it uses the OpenSSL kit which is licensed under the 1.1 version of Apache.  Further reading, I would find kind of broad statements like, "Corporate organizations prefer the Apache license over GPL" but the only one that really detailed what that means, only gave vague mention of patent rights being transferable under the Apache license but not under GPL?  Can anyone elaborate on that?

To me it doesn't really matter, because I'm only really applying one as kind of like I don't know, standard practice I guess?  I'm entirely NOT worried about my intellectual property being stolen, in fact I really like the whole OS software principle and feel like the GPL is more inline with that than the Apache license and would prefer using that.

Licensing is a really complex issue, and sometimes I really criticize the (lackof)merit in applying one to my particular projects.  I know a number of people just license stuff in the public domain but is there really any benefit to using generally-acceptable OSS license or is it just something people SAY you should do but doesn't really matter?  To me I feel goofy licensing software that 2nd semester programming students would laugh at lol

However I think to a potential employer it might demonstrate some basic knowledge of the use and understanding of software licenses.  I'm not really sure how desirable that knowledge is to employers, and past that kind of wonder if any of them think to themselves, "Why would anyone license this?"

---

### Post by ofnuts on 2014-12-06
What kind of protection are you trying to achieve? You don't want a potential employer to grab the code and not hire you?

---

### Post by Lars Noodén on 2014-12-06
If you want others to use the code, you do have to choose a license since not all countries seem to recognize public domain and even so, it has to be placed explicitly in the public domain.  Material published without a license is still automatically copyrighted in all Berne Convention countries and that means, if a license is lacking, that all rights are reserved; the user gets nothing.

Github has a few pages about how to choose:

[http://choosealicense.com/](http://choosealicense.com/)

But it comes down to a matrix of what you want to allow.   The full list is here:

[http://opensource.org/licenses](http://opensource.org/licenses)

Regarding permissive vs copyleft, that all depends on your business model.  The linux kernel and the mysql database both got enormously popular under copyleft and made a lot of money for a lot of people.  MySQL in particular made use of a dual license business model.  MySQL has changed licenses and languished, perhaps there is a connection, perhaps not.  With either copyleft or dual license, re-distributors (not users) have to contribute either money or improvements.  However, if you are promoting a standard or specification and want *that* spread more than the code, then a permissive license is the way to go.  But even then, it is in the long term interest for redistributors to work upstream as much as possible.

---

### Post by Lars Noodén on 2014-12-06
The GPL v2 is copyright only.  GPL v3 and Apache 2.0 both address patents in addition to copyright.  So if patents are a concern (ie. you are in the US) then you'll probably want a license that addresses both patents and copyright.

---

