---
title: "HOWTO: Plone from scratch"
date: 2005-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Druke on 2005-07-21
Plone is an project development website server/tool using many different "products" running on zope, which is made with python . It is also useful for general websites that aren't geared so much to project development. It supports many languages, and has very nice translation technologies so you don't have to translate. Additionally it works very well with any browser, I can surf it with Elinks and not have any lesser abilities then i would have with firefox.

so you can see what an install might look like, I use Plone for project development at [http://plone.arcane-order.com/](http://plone.arcane-order.com/)

you can read the whole shebang at [http://plone.org/](http://plone.org/)

O.k. this is my first guide, and i must say I am nothing of a Linux guru, however i think I've got this particular sequence down to an art. 

I did this on a fresh install of ubuntu having only changed apt's reps like suggested  in [http://ubuntuguide.org/](http://ubuntuguide.org/)


Preparation

first off you must have the extra reps for apt-get enabled.

additionally, go ahead and have [plone2.0.5 downloaded](http://prdownloads.sourceforge.net/plone/Plone-2.0.5.tar.gz?download) 

ok now you're ready
First thing
> sudo apt-get install zope2.7 
this will install zope2.7, the latest version of zope that works with plone

once all that is finsihed run

> sudo mkzope2.7instance 
and fill out the asked questions
(thanks to iluminate)

now you have zope fully operational on your machine and just need to put plone2.0.5 into the products folder of your newly created instance

Extract the Plone tar file to wherever you like and 'cd' into it

so you should be inside the plone folder (in my case in /home/druke/plone-2.0.5)

type the following command

> sudo mv ./* /var/lib/zope2.7/instance/(instance directory/Products 

note that that line isn't copy and paste'able you have to manualy type in the instance directory that you made up when you made your zope2.7 instance.

now its time to start zope up

> sudo /var/lib/zope2.7/instance/(instance directory)/bin/zopectl start 

now then open up your web browser and goto 

[http://localhost:9673/manage](http://localhost:9673/manage)

you will be prompted for the user name and pass you made up when you created the zope instance.

this is the zope controller, we want to make a plone instance, so in the top right(not zope Quickstart, about an inch down from there, should default say Accelerated HTTP cache manager) scroll down to plone site, hit add, fill out the form, and whola you've got yourself a plone server installed!

an extra side note, this si all case sensitive so when you access your plone instance at localhost:9673/(instance name) remember to be case sensitive, tis not standard HTML anymore.

well heres for my first guide, feel free to post question/rants/I hate you notes!

---

### Post by Stormy Eyes on 2005-07-21
I'd recommend starting your HOWTO by explaining what Plone is and where to get it.

---

### Post by Druke on 2005-07-21
There we go, edited. How is that?

Thanks for the constructive crit btw.

Edit: i also fixxed alot of my gramatical errors

---

### Post by Stormy Eyes on 2005-07-21
[QUOTE=Druke]There we go, edited. How is that?

Thanks for the constructive crit btw.

Edit: i also fixxed alot of my gramatical errors[/QUOTE]

That makes a lot more sense. I hadn't heard of Plone before, but now I at least know what it is if I have to recommend a CMS to somebody wanting to build a website.

---

### Post by Druke on 2005-07-21
shoot me if i'm wrong but I think the ubuntu site and this one use plone

---

### Post by Stormy Eyes on 2005-07-22
[QUOTE=Druke]shoot me if i'm wrong but I think the ubuntu site and this one use plone[/QUOTE]

/me pulls out a .45 and shoots Druke.

Actually, this forum uses vBulletin. :)

---

### Post by christooss on 2005-07-26
Christooss spectaculary caught bullet before it hit Druke.

Ubunu SITE is made with PLONE.

---

### Post by lao_V on 2005-08-09
That's right, the Ubuntu site is Plone-based whereas the forum is vBulletin.

Thanks a lot for the great Howto Druke! Btw, couldn't get your site to work

---

### Post by Druke on 2005-08-09
bleh i know, running it from home, my prmary pc is pooped out so i'm using the server as my NWN box  :razz:

---

### Post by lao_V on 2005-08-10
Still quite new to Zope/Plone...Do you know if its possible to create an instance in the /home directory instead of /var/lib/...?

---

### Post by Druke on 2005-08-10
you would have to install zope2.7 into home,so a fresh isntallation from [http://www.zope.org](http://www.zope.org), the downside of using ap-get i guess

edit:typos

---

### Post by iluminate on 2005-08-12
Hi,

Followed the HOWTO but didn't manage to install it. Recieved some permission errors!
But then I typed "sudo  mkzope2.7instance" and voila it worked!

Cheers!

---

### Post by Druke on 2005-08-13
edited: gave you a lil thank you note  ;-)

---

### Post by uten on 2005-10-09
ok i followed your instructions and when i try to access the management page it prompts me for username and password, i entered the same one i used in make instance, and it just prompts again, and keeps on prompting, what could be the problem?

---

### Post by Druke on 2005-10-09
the only thing that comes to mind is that the password which you specified in the setup during 'mkinstance' is not the one you intedned to type in. may want to note that the password is not your sudo password but rather your password made in the setup.

---

### Post by uten on 2005-10-09
ok i think i figured it out, i may have installed an instance before when i toyed around with zope months ago. i did a apt-get remove, but it must have left behind files, and the new instance didnt overwrite it. ive removed zope from /etc and /var/lib, so im gonna try install again and see how it goes

---

### Post by uten on 2005-10-09
ok so i tried reinstalling zope, only that after creating an instance, i have no instance in /var/lib/zope2.7/instance/

how can someone go about removing zope properly, and then reinstalling it

---

### Post by regeya on 2005-10-09
Nicely done.

I had been tempted to refactor a company Intranet project as a Rails app,  but the relative infancy of the project has me thinking that I should go back to using Zope.  Plone always interests me but it's not exactly, erm, light on its feet. :-)  VERY nice system, though.

For the people who know nothing about Zope:  Zope is a Web application server with a Web-based GUI, and at the most basic level can act as a Web server and stores all its data in a sophisticated object database.  There are a number of pros and cons to this approach, but the huge advantage is that Zope is largely platform-agnostic.  If you have a smallish project with sophisticated requirements but small traffic, just running Zope on its own may be enough.  That's a powerful idea, IMHO.

---

### Post by matw on 2005-10-16
On a Breezy system, I followed the directions up to
```
mat@mog:/var/lib/zope2.8/instance/plone-site/bin$ sudo ./zopectl start
. daemon process stared, pid=31097
```
however, I get a "connection refused" error when I try the URL [http://localhost:9673/manage](http://localhost:9673/manage) in Firefox.

What should I do now?

---

### Post by ChrisDerson on 2006-07-27
> **uten said:**
> ok so i tried reinstalling zope, only that after creating an instance, i have no instance in /var/lib/zope2.7/instance/

how can someone go about removing zope properly, and then reinstalling it

Try:
A complete removal with synaptic or:

```
sudo dpkg -P zope2.7
```

Then look for zope2.7 directories in /var/lib and /etc if they still exist remove them and their contents.  You should now have a clean system to start again with.

---

### Post by bwiewiora on 2006-08-01
Has anyone else had a boatload of trouble trying to get Plone/Zope to work on Dapper?  The new 2.5 release doesn't support Python 2.4, and it seems pretty much impossible to step back to Python 2.3.5 (the latest version Zope/Plone supports) without destroying the system.

---

