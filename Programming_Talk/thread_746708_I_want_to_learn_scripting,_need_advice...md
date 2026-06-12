---
title: "I want to learn scripting, need advice.."
date: 2008-04-05
forum: Programming Talk
---

### Post by tuproxy on 2008-04-05
As the topic said, I want to learn how to write scripts. Can someone point me to some good resources or some good books to buy?

I'm looking for personal reflection (if possible) or just insight as to what/where to look. I'm not asking people to write them for me, just point me in the right direction for well written books. Or maybe an exceptional website that will guide me.  Thanks..

PS 

I don't think that is asking too much. I know if someone asked me and I had reada book that was great I would tell them, "check this book out". Or if I had seen a site that was well written for beginners, I'd suggest that. If I were an a-hole,that hadn't read a book on it, or just didn't care, i'd point them to Google. Please don't be the latter.

---

### Post by xelapond on 2008-04-05
Have you picked out a language yet?  If not I would way Python.

Here is a guide for people that have never programmed before:
[http://www.pasteur.fr/formation/infobio/python/](http://www.pasteur.fr/formation/infobio/python/)

This one moves a little faster, but really requires some previous knowledge
[http://docs.python.org/tut/](http://docs.python.org/tut/)

You really don't need any books to learn python, as it has really good online documentation.  As you have probably notices there is a  great community of fast responding people waiting to help you:)

Hope that helps, 

Alex

---

### Post by tamoneya on 2008-04-05
I definately recommend python. They also have very good tutorials on their website.
[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

---

### Post by lnostdal on 2008-04-05
edit: about personal reflection .. Common Lisp is what i arrived at (in 2003-4) after _suffering_ my way through other languages for years(#1) .. i have not found anything better than it yet .. i use it for everything now .. (i talk about CLISP below, but SBCL is my main implementation of the language .. CLISP is nice for scripting type work though)

i'd go for Common Lisp .. the CLISP implementation works great for scripting type tasks as it has a small footprint and quick startup time .. (you'll find CLISP via the ubuntu repositories .. use synaptic or apt-get/aptitude to install it)

[http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)
[http://www.lispworks.com/documentation/HyperSpec/Front/](http://www.lispworks.com/documentation/HyperSpec/Front/)
(download the hyperspec here: [ftp://ftp.lispworks.com/pub/software_tools/reference/HyperSpec-7-0.tar.gz](ftp://ftp.lispworks.com/pub/software_tools/reference/HyperSpec-7-0.tar.gz) )

i made a post about scripting using CLISP here: [http://groups.google.com/group/comp.lang.lisp/msg/7e66031e0660cb21](http://groups.google.com/group/comp.lang.lisp/msg/7e66031e0660cb21) .. it's easy and fun

#1: in 2001, when XP came out - i "gave up" computing and computers totally .. i found the OS and the direction it or the computing world was headed to be an _insult_ ..just plain awful and _disgusting_, no room for anything beautiful and intelligent .. then i discovered linux and it saved me and my interest in computers .. it has potential and the direction(s) is(are) less wrong

 the same thing gradually happened wrt. the programming (language) side of things .. i "gave up" as things where just friggin awful, silly and insultingly _stupid_ ..  eventually lisp "saved me" in the same way linux "saved me"

---

### Post by pmasiar on 2008-04-05
see sticky FAQ for links how to learn programming. Scripting is just like any other programming, only languages are simpler and more powerful. Go with Python. See my sig.

---

### Post by tuproxy on 2008-04-05
Thanks for all the replies!  I have a little experience with VB 6.0 and Cobol. 

What I want to do is be able to do automated Linux commands, auto installs, backups, wireless install, wireless WEP cracks, etc.  

Would that be Bash scripting?  Sorry I should have specified this previously.

---

### Post by lnostdal on 2008-04-05
nope, you don't have to use bash to do this .. you are free to use any language .. but a "scripting type language" (or an "scripting type implementation" of said language) is more suitable

edit:
the reason for this is that you want something that can be changed easily and fast .. you don't want to recompile just to see the effect of a simple change .. you want to edit the file and save it .. then run it/test it directly .. fast cycles

---

### Post by LaRoza on 2008-04-05
> **tuproxy said:**
> Thanks for all the replies!  I have a little experience with VB 6.0 and Cobol. 

What I want to do is be able to do automated Linux commands, auto installs, backups, wireless install, wireless WEP cracks, etc.  

Would that be Bash scripting?  Sorry I should have specified this previously.

See my wiki, the sticky, and other posts.

You will find that there are three "big" scripting languages: Perl, Python, Ruby. They are all cross platform and relatively easy to learn.

There is also shell scripting, which is not cross platform and specific to the shell being used (although most shells are in many ways similiar, they have different features)

If you are able to do what you want using the terminal, shell scripting is what you probably are looking. See my wiki, under the Operating System Specific section in the library.

---

### Post by xelapond on 2008-04-05
For that  I would say Python, because it is more, 'intelligent' then BASH.  It would also allow you to write more complex programs later, should you decide to.

---

### Post by LaRoza on 2008-04-05
> **xelapond said:**
> For that  I would say Python, because it is more, 'intelligent' then BASH.  It would also allow you to write more complex programs later, should you decide to.

Well, for the OP's requirements, the shell seems to be the solution.

Of course, learning is not exclusive, and I do suggest learning more than one language. No reason to have one screw driver in the toolbox.

---

### Post by pmasiar on 2008-04-05
Writing 3-line script is often simpler in bash, but beyond that, Python becomes more productive and flexible. Especially later when you want to add GUI frontend.

---

### Post by LaRoza on 2008-04-05
> **pmasiar said:**
> Writing 3-line script is often simpler in bash, but beyond that, Python becomes more productive and flexible. Especially later when you want to add GUI frontend.

Yes, although I would increase "3" to a higher number. Zenity has similiar use as EasyGUI, and can be quite useful for an interface.

---

### Post by ghostdog74 on 2008-04-05
> **LaRoza said:**
> 
There is also shell scripting, which is not cross platform and specific to the shell being used (although most shells are in many ways similiar, they have different features)
it really depends on how you see it, IMO.
what one needs is the correct interpreter.

---

### Post by ghostdog74 on 2008-04-05
> **tuproxy said:**
> What I want to do is be able to do automated Linux commands, auto installs, backups, wireless install, wireless WEP cracks, etc.  

1) auto installs -> if your software comes in source C packages, you can install it from the command line using stuffs like configure, make.etc..
2) backups -> depends on what you want to backup? files and folders ? or partitions? there are tools like dd (and others) that can backup  your partitions. for simple file and folders , a various combination of cp,  mv, tar, gzip may suffice.
3) wireless install...-> iwconfig, wpa etc ...these tools can be use with the terminal (shell).

---

### Post by LaRoza on 2008-04-05
> **ghostdog74 said:**
> it really depends on how you see it, IMO.
what one needs is the correct interpreter.

Yes, I know. But I think it is different in a way, as the "shell" in *nix can be very different. Even in Ubuntu, many scripts broke when Ubuntu used Dash instead of Bash as the default in 6.10 and up.

The number of shells is amazing: [http://www.freebsd.org/ports/shells.html](http://www.freebsd.org/ports/shells.html)

Interesting table: [http://en.wikipedia.org/wiki/Comparison_of_computer_shells](http://en.wikipedia.org/wiki/Comparison_of_computer_shells)

---

### Post by ghostdog74 on 2008-04-05
> **LaRoza said:**
> Even in Ubuntu, many scripts broke when Ubuntu used Dash instead of Bash as the default in 6.10 and up.

true, but like i said, what one needs is the correct interpreter either defining it by changing the shebang, or linking sh to bash.

---

