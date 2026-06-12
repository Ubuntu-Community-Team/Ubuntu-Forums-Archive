---
title: "Whats the best way to make a website?"
date: 2007-11-04
forum: Programming Talk
---

### Post by zenkaon on 2007-11-04
Hey guys,

I am looking to build my own website and I would like some advice on what to use to build it. I don't really want to open up emacs and start typing html. I'm looking for a dreamweaver type thing for Linux.

Work is going to host it on a RHEL lamp server, so I don't need to worry about anything technical like setting up apache, thats for IT to worry about, I just need to build the damn thing.

So, what is the best web publishing program that I can install in gusty??

---

### Post by smartbei on 2007-11-04
Here are several - It is somewhat a matter of taste:

[LIST]
[*]Quanta+
[*]Screem
[*]Bluefish
[*]Nvu
[/LIST]

You can also install some of (older I believe) versions of DreamWeaver with WINE.

---

### Post by zenkaon on 2007-11-04
Hi,

I used to use Nvu a while back, but I cant find it in gusty. Anyone know whats going on there?

---

### Post by happysmileman on 2007-11-04
> **zenkaon said:**
> Hi,

I used to use Nvu a while back, but I cant find it in gusty. Anyone know whats going on there?

It's now been forked to Kompozer I think since original developer stopped working on it, I don't really know much about them though so can't give advice

EDIT:
> In 2007, Nvu was removed from Ubuntu Feisty repositories because it was no longer maintained upstream.
So better off using something else

---

### Post by tkharris on 2007-11-05
vim :)

:syntax on

---

### Post by Cochise on 2007-11-05
kompozer is in the gutsy repo or maybe its the medibuntu but it does the job

---

### Post by mdpalow on 2007-11-06
You'll want to use Photoshop or Gimp for the design; unless you plan on having a pretty bland site. Since you're not a pro designer, I would say to use Gimp for initial graphical design. It's a contender with Photoshop. However, professional Photoshop users won't use Gimp until a few things are added.

Then you'll need something to actually do the code in HTML.

I just don't think you'll find anything linux compared to Dreamweaver unfortunately. The linux apps. just haven't matured enough. I did try Kompozer and it's OK, but it's just not Dreamweaver yet.

I'm running VMware with Windows XP just so I can use those two programs. I'd prefer to go straight linux, but can't just yet until linux apps mature.

For you, it does sound like you could get away with using Kompozer and Gimp. If so, you're set... Just get them from your Synaptic Package Manager.

---

### Post by LaRoza on 2007-11-06
> **tkharris said:**
> vim :)

:syntax on

Do this first:
```

sudo aptitude install vim-full

```

---

### Post by zenkaon on 2007-11-07
Thats for all the advice,

I have decided to go with TWiki. Easy to create and me and my buddies (and only us) can edit it in firefox.

Web 2.0 feels a lot different from putting "<html> ....." in emacs in web 1.0. I like it.

---

### Post by timcredible on 2007-11-07
you  need to check out joomla before you do anything - it's better than anything else that was listed.
[http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=16&Itemid=32](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=16&Itemid=32)

---

### Post by pmasiar on 2007-11-07
Twiki is rather powerfull, but inside design was ugly last time I looked.

If you need a wiki to support software development, much better value is Trac: integrates wiki, code repository, code viewer, and bug tracker.

Trac's internal structure is much cleaner too - and plugins are simpler to write.

---

### Post by MicahCarrick on 2007-11-07
> you need to check out joomla before you do anything - it's better than anything else that was listed.

Joomla is a CMS system. Others include xoops, phpnuke, etc. If you know your website is going to be of a specific type, and you're not looking to learn how to create websites, you could use an open source CMS system (such as Joomla) or blog (such as wordpress).

If you want to create websites in Linux, you'll find that most people use text editors. I'm a professional web developer and I do all my work with gedit. IYou may want to read _[Web Development in Linux (GNOME)]("http://www.micahcarrick.com/09-28-2007/web-development-linux.html)")_.

As you said you don't want to "start typing", then you may want a WYSIWYG editor. The quickest solutions are Quanta, Kompozer, or Amaya. Any of those WYSIWYG editors can be installed through apt. You could also give Aptana a go which is Java-based.

---

### Post by silent1643 on 2007-11-07
if your not the technical inclined use a service (web service) to help you build a website and host the damn thing... for basic websites that is (not sure what your looking for)
goto simplespark.com to find a free service and website host

you can use gimp or whatever you want to create your images for the website and even use [splashup online photo editor]("http://www.splashup.com/") to do alot of it .


also there is not good sub for dreamweaver - just get dreamweaver and use wine. bla

---

### Post by KCPokes on 2007-11-07
> **pmasiar said:**
> Twiki is rather powerfull, but inside design was ugly last time I looked.

If you need a wiki to support software development, much better value is Trac: integrates wiki, code repository, code viewer, and bug tracker.

Trac's internal structure is much cleaner too - and plugins are simpler to write.

Just to add to your statement regarding Wikis.  If you are looking for a Wiki system, there are tons of options, depending on your comfort zone and what your intentions are.  Twiki is Perl, while Trac is Python (surprise, surprise  :)  ).  There are also numerous options that are Ruby and Php based (Wikipedia is based off of MediaWiki, which is PHP based).    Trac looks interesting and powerful out of the box, especially if you are looking to support code development.  If you plan n extending your Wiki (we've integrated authentication into our AD domain), I'd highly recommend you going with a language you are comfortable with.

Now if you just want a simplistic site that you can update content, then you may look into something like Joomla or Wordpress.  Joomla can be a bit of a hog and perhaps a bit of overkill for a basic site, but fits a community model better.  Wordpress is just easy, once you have your design integrated, and can be extended quite a ways.

---

### Post by ThinkBuntu on 2007-11-07
You say this is for work...do you have a budget for the assignment?

And if you have to do it on your own from scratch, and you don't want to code, Dreamweaver is far and away your best bet.

---

