---
title: "trying to learn website developement"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by nynoah on 2008-05-12
I am trying to learn how to do websites.  I use a Ubuntu based computer and do not have windows at this time.  I am looking for some good tutorials.  Also I am trying to figure out what is the best program to use to make web pages under Ubuntu.  Is there any that do a great graphical interface that let me draw out like I am using Gimp to make a page and then turn that into code in some way.  I heard Dreamweaver does something like that.  I am not trying to do flash, I am trying to learn how to do a basic page for now with lots of links.  Maybe in the future be able to imbed streaming video on my pages.  If anyone can direct me in a direction I would appreciate it.

I have for programs already (I am not on my home computer so this is from memory)
Screem, Kompozer, Blue Fish and a few others.  But which one is the best for a newbie who can not hand code yet?

Thanks
Noah

---

### Post by id1337x on 2008-05-12
The best program and the one I like to use is Aptana which uses the Eclipse platform. It is the only program I know of that actually offers auto-complete and other rich features like that.

[http://www.aptana.com/](http://www.aptana.com/)

Umm then for page design I suggest inkscape. With inkscape you can design rich sites like you would with Flash except you are using SVG instead. SVG is a free software alternative that is gaining traction. I find it to be superior. Another program that is good is scribus. These programs are open source. 

[http://www.inkscape.org/](http://www.inkscape.org/)
[http://www.scribus.net/](http://www.scribus.net/)

---

### Post by nynoah on 2008-05-12
Thanks I will check that out.  I read a little about it.  It said that I had to download adaptina as a plugin for eclipse.  I don't know what eclipse is, but I will try to find out more I guess.  I am running 64bit linux.  Is it going to be harder for me to get programs than if I was on a 32 bit?

---

### Post by nynoah on 2008-05-12
Anyone else have any ideas or words of wisdom?

---

### Post by nynoah on 2008-05-12
Does anyone know how to get the Adaptina to work on Eclipse?  I have 64 bit system so I can not download it instantly because it is 32 bit.  Does anyone know how to make the 32 bit version run or how to get this as a addon like the adaptina site says?

---

### Post by id1337x on 2008-05-12
Go to add and remove and just search for eclipse and download it, you can go to this site too:

[http://www.eclipse.org/](http://www.eclipse.org/)

Then to plug it in:

[http://www.aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration](http://www.aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration)

---

### Post by shae on 2008-05-12
If you already have hosting arranged and you will have PHP/MySQL, you should use [drupal]("www.drupal.org")!

It is an absolutely amazing CMS system.

---

### Post by friendofpugs on 2008-05-12
Hi!

There are several excellent web designer/developer tools for Linux. I too just installed Eclipse with the Aptana plugin for x64, but I had to download the Manual Install .zip plugin from Aptana because for some reason, it wasn't working from the instructions on the Aptana site. [http://update.aptana.com/install/studio/3.2/]("http://update.aptana.com/install/studio/3.2/")

You might want to look into Quanta Plus; it allows code/design view at the same time; it's widely regarded as the most extensive web authoring platform for Linux and it's similar to DW. The WYSIWYG isn't bad, but be sure to check in the browser as you code. I begged off buying a Mac and forking out $$ for CS3 and I went with Linux instead. I only wish there was something as sexy as coda for linux, but beggars can't be choosers. :) 

Hope that helps!

---

### Post by nynoah on 2008-05-12
Great thanks for the hints........any one else have any other ideas.  Just trying to pick the brains of my fellow Ubuntu users.

Thanks guys

---

### Post by pearjam on 2008-05-12
A good way I picked up on it was "view > page source" on simple to complex sites. I'd find a chunk of code, and google it till I understood it.

Then start with basics like open gedit, go to view, highlight, markup, html - then build a basic body and keep adding to it. You'll see each page has at least:
<html>
<head>
<title></title>
</head>
<body>

</body>
</html>

(save your file as a .html or .htm and view with a browser)

To me, the majority of html is just page formating. The fun stuff is CSS, and the juicy stuff is dynamics, like php and mysql.

As far as editors, I started on Allaire Homesite 4.5 and "Macromedia Flash 4" (in like '99), but I don't think they are free if they even exist anymore.

As far as web sites, I've learned a lot from:
webmonkey.com
w3.org
w3schools.com
phpbuilder.com

Hope this helps!

---

### Post by nynoah on 2008-05-13
Thanks guys for all your help.  I have learned a lot from everyone here on the forum.  Its stuff like this that makes me love Ubuntu and its users.

---

### Post by MaindotC on 2008-05-13
You can also get free training of web design concepts and programming at [W3 Schools]("http://w3schools.com/").

---

### Post by dynamethod on 2008-05-13
I found this site pretty good: [http://www.tizag.com/](http://www.tizag.com/)

and also for css once you get the hang of html: [http://tutorials.alsacreations.com/deroulant/](http://tutorials.alsacreations.com/deroulant/)


which is excellent

---

### Post by nynoah on 2008-05-13
So much to learn, but it should be fun to learn it.  

Tomorrow is going to be fun.  I am going to install linux on 3 computers for some people at work.  Spreading the Ubuntu love.  

Thanks for the links if anyone else has any other ideas, send em my way.

;)

---

### Post by Primefalcon on 2008-05-13
One good program I've found is kate, you'll probably have to use your synaptic package manager to find it though.

it has syntax highlighting for a lot of different languages has its own file browser thingy built in, and a lot of other cools help tools, for css I'd recommend cssed its got a great tool for the color codes.

though using any of these would require you learn the code rather than just a tool like dreamweaver, for learning I'd receomend w3schools, htmltutorial amnd maybe good visual learning html/xhtml and css by Elizabeth Castro, then start moving on up to php.

I know thats a little different than what you asked, but that'd be my suggestion

---

### Post by Xiong Chiamiov on 2008-05-13
Personally, I use Komodo Edit, because it has tabs, code folding and the ability to work directly off my server through FTP.  I don't believe it's in the repos though; you'll have to download it from their site.

There is quite a wide variety of what people consider "web development".  Do you have more priority on pretty things, or things that work well?  I'm a coder, not a graphic artist; I absolutely *love* the design of [isnoop.net]("http://isnoop.net").  Learning to code by hand will require more effort, but it gives you an incredible amount of flexibility, since you can design whatever you want, rather than being limited to what the tools will do.

As far as learning, I picked up HTML through some crappy tutorial and ended up just fine.  I'm in the process of making a tut that builds good habits for the future, but it's... [not very complete]("http://tilde.awardspace.com/article.php?id=2"), at all.  For learning CSS, a good place to go is [CSS Zen Garden]("http://csszengarden.com/").  Download a few of their designs, then start hacking them apart to see what does what.  If you're looking into buying books, then don't bother with anything not published by [O'Reilly]("http://oreilly.com/") - that actually goes for pretty much all computer books.  Their "Learning *" series are really good, and the pocket books are quite good references.

---

