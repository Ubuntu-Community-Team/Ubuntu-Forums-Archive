---
title: "Python Project"
date: 2008-03-09
forum: Programming Talk
---

### Post by nesh87 on 2008-03-09
Hey guys,

im working on a new project in Python. I started because i wanted to experience python and its features as well as messing with the MSN protocol. Im working on an MSN Messenger, i know there is emesene, but i wanted to create one on my own. Ive created the basics, im currenlty working on file transfers and stuff. Its currently a one man army, so if anyone is interested, please do email me.

You can check it out:

[http://momsn.blogspot.com](http://momsn.blogspot.com)

ideas are welcome
feedback ( + and -)

---

### Post by Acglaphotis on 2008-03-09
Can i haz source? I wanna see if i can help, i've never been in a "big" project so i just wanted to check it out.

---

### Post by mssever on 2008-03-09
> **nesh87 said:**
> ideas are welcome
feedback ( + and -)

It's impossible to offer feedback without access to the program--especially the source code.

---

### Post by nesh87 on 2008-03-09
> **mssever said:**
> It's impossible to offer feedback without access to the program--especially the source code.

[http://momsn.blogspot.com/2008/03/google-code-is-up.html](http://momsn.blogspot.com/2008/03/google-code-is-up.html)

just uploaded the source to google-code

please please try to avoide criticisim on the coding style and the lack of comments. Just keep in mind that this im still in the alpha alpha phase.

Thanks

---

### Post by Acglaphotis on 2008-03-09
I have a suggestion:

-Separate the code from the GUI. It makes it easier for more than 2 people to work on the same code (eg, one codes the gui and the other one the backend, thus making callbacks easier to read/understand and mantain.

---

### Post by pmasiar on 2008-03-09
> **nesh87 said:**
> please please try to avoide criticisim on the coding style and the lack of comments.

Writing code in commonly accepted style makes your code easier to understand. So not doing it you force others to spend more time and effort to help you - hardly a good argument if you need help. Same with comments.

I do not argue for others **not** to read or comment on your code - but for me, if you yourself admit your code is lacking those basics, it would be argument to wait until they are fixed. Others are free to do whatever they want, it is just my feeling.

---

### Post by nesh87 on 2008-03-09
> **pmasiar said:**
> Writing code in commonly accepted style makes your code easier to understand. So not doing it you force others to spend more time and effort to help you - hardly a good argument if you need help. Same with comments.

I do not argue for others **not** to read or comment on your code - but for me, if you yourself admit your code is lacking those basics, it would be argument to wait until they are fixed. Others are free to do whatever they want, it is just my feeling.

Well when i said coding style, i didnt mean totally lacking. Its just that im in the middle of changing styles from camel clutch (myVariable) to underscores (my_variable). You might see some rare occasions of different naming styles. As for the comments, the program is currently very simple to follow, comments are not necessary, but i will try to put some more just to explain how things are going.

---

### Post by nesh87 on 2008-03-11
Before things get too big and out of hand, i decided to listen to the advices given. Any ideas of what style should i go with. What would be the best for another user to read and follow easily?

---

### Post by Wybiral on 2008-03-11
> **nesh87 said:**
> Before things get too big and out of hand, i decided to listen to the advices given. Any ideas of what style should i go with. What would be the best for another user to read and follow easily?

_**The**_ style: [http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)

---

### Post by nesh87 on 2008-03-11
> **Wybiral said:**
> _**The**_ style: [http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)

Yeah i thought so, i re-styled most of the code and i have a little left to go. It actually helped fix some bugs. And as for the comments go, i commented the protocol heavily with examples of the commands received by the server. But the gui part, i didnt cuz it was straight forward, packing and other pygtk basic functions.

the revised code:
[http://momsn.googlecode.com](http://momsn.googlecode.com)

currently @ rev 25 (took me a while to understand svn, still shakey)

as for latest client updates, i managed to tab the chats instead of each in its own separate window. I think its more friendly to have tabs, what do u guys think?

[http://momsn.blogspot.com/2008/03/tabbed-chats.html](http://momsn.blogspot.com/2008/03/tabbed-chats.html)

---

### Post by Acglaphotis on 2008-03-11
Tabs are better than separate windows IMHO.

---

### Post by cdekter on 2008-03-12
If you are interested in others helping along with your project, it would be a very good idea to make your code self-documenting so that you can auto-generate reference material for people interested in helping. Check out Epydoc - [http://epydoc.sourceforge.net/](http://epydoc.sourceforge.net/) - a pydoc system that generates html reference pages on the fly. 

I've used it on several projects and found it extremely good. If you want to see a real world example of its use check out paramiko (an SSH library for python). Its docs are generated using epydoc: [http://www.lag.net/paramiko/docs/](http://www.lag.net/paramiko/docs/)

---

### Post by nesh87 on 2008-03-12
> **cdekter said:**
> If you are interested in others helping along with your project, it would be a very good idea to make your code self-documenting so that you can auto-generate reference material for people interested in helping. Check out Epydoc - [http://epydoc.sourceforge.net/](http://epydoc.sourceforge.net/) - a pydoc system that generates html reference pages on the fly. 

I've used it on several projects and found it extremely good. If you want to see a real world example of its use check out paramiko (an SSH library for python). Its docs are generated using epydoc: [http://www.lag.net/paramiko/docs/](http://www.lag.net/paramiko/docs/)

Thanks cdekter!

that was very useful, with the fact that i just added doc strings to every function and most of the variables that needed explanations. Im working on generating the reference material and will upload them to the googlecode wiki.

Until then, check out the new changes to the project, and please share "do and donts" at the blog.

[Blog]("http://momsn.blogspot.com")
[Code]("http://momsn.googlecode.com")

---

### Post by nesh87 on 2008-03-13
> **nesh87 said:**
> Thanks cdekter!

that was very useful, with the fact that i just added doc strings to every function and most of the variables that needed explanations. Im working on generating the reference material and will upload them to the googlecode wiki.

Until then, check out the new changes to the project, and please share "do and donts" at the blog.


I created the docs using epydoc, but apparently couldnt use googlecode to add them. Do you guys think i should create an individual site for the project, or is a blog enough? I was thinking a site i would have more control, with php and mysql, i can upload files. i'll still use the svn repository from googlecode..
What do u guys think?

Btw, more updates:
[Blog]("http://momsn.blogspot.com")
[Code]("http://momsn.googlecode.com")

---

### Post by nanotube on 2008-03-13
i suggest putting it up on sourceforge (sourceforge.net)

sf provides a lot of free services to open source projects, including web (with php, mysql, etc), CVS or SVN (or both), file release system, forums, mailing lists, bug/issue tracker, wiki... hell, just about anything you can think of. :)

---

### Post by nesh87 on 2008-03-16
> **nanotube said:**
> i suggest putting it up on sourceforge (sourceforge.net)

sf provides a lot of free services to open source projects, including web (with php, mysql, etc), CVS or SVN (or both), file release system, forums, mailing lists, bug/issue tracker, wiki... hell, just about anything you can think of. :)

ive signed up with sourceforge, but i couldnt find where to edit the website. I also couldnt find SVN, only CVS, and i do not want to mess around with a new thing. I barely got SVN ;p..

---

### Post by mssever on 2008-03-16
> **nesh87 said:**
> ive signed up with sourceforge, but i couldnt find where to edit the website. I also couldnt find SVN, only CVS, and i do not want to mess around with a new thing. I barely got SVN ;p..

Good luck figuring out Sourceforge. I have a couple of projects there, and it took me a long time to figure it out. They do offer SVN (I use it). Hope you find it. :)

---

### Post by nanotube on 2008-03-17
> **nesh87 said:**
> ive signed up with sourceforge, but i couldnt find where to edit the website. I also couldnt find SVN, only CVS, and i do not want to mess around with a new thing. I barely got SVN ;p..

yea, getting some of the stuff to work can be a bit convoluted - so you have to read the docs. the good thing is, they have detailed docs on everything. 

[http://sourceforge.net/docman/?group_id=1](http://sourceforge.net/docman/?group_id=1)

---

### Post by nesh87 on 2008-03-18
```

svn co https://momsn.svn.sourceforge.net/svnroot/momsn/trunk
svn: PROPFIND request failed on '/svnroot/momsn/trunk'
svn: PROPFIND of '/svnroot/momsn/trunk': Could not resolve hostname `momsn.svn.sourceforge.net': No address associated with hostname (https://momsn.svn.sourceforge.net)


```

:confused:

---

### Post by nesh87 on 2008-03-19
anyone :)?

---

### Post by mssever on 2008-03-19
You don't have SVN enabled. The Code tab of your sourceforge project page shows CVS, but not SVN. Compare [this project]("http://sourceforge.net/projects/badgeentry"), for example.

---

### Post by nanotube on 2008-03-19
msserver speaks true.

to enable subversion, log in to sf.net, go to your project page, and select admin -> subversion  from the menu.
it will bring you to a page where among other things you can check a box to enable svn for your project.

---

### Post by nesh87 on 2008-03-20
Thanks guys, i must be blind. I was looking SVN not the whole word ;p.. Anyways, i decided to go with a website that holds everything, but ill continue to use the svn from googlecode. I moved most entries from the blog to the site already.

You can check it out here:
[http://momsn.qupis.com/](http://momsn.qupis.com/)

---

### Post by nesh87 on 2008-03-30
Things are moving a bit slow with uni and all, anyone care to join?

---

