---
title: "Creating a Blogging Software for Linux"
date: 2007-03-01
forum: Programming Talk
---

### Post by timmahhny on 2007-03-01
I have been searching for a good blogging software to use on the new blogger, but have come up empty.
 Wordpress will not work, Drivel will read but will not post. 
I have tried about six or so Linux programs with no results and would like to write my own. 
I have limited programming, in VB, Java, some light C and pthyon. 
 I would like to know what would be, in **your opinion** the best software to use, in my attempt to write this. I would like to get some features of Live Writer, which I think is a great piece of software, too bad it won't run on Ubuntu. 

 Thanks in advanced.
timmahhny

---

### Post by lnostdal on 2007-03-01
edit: oh wait; you want something to use on Blogger? .. something that lets you edit blog-posts using a "real application" instead of editing via a web-page? .. i might have misunderstood what you meant

My opinion: I'd use Common Lisp for programming language and Hunchentoot for web/http server. For back-end storage I'd use PostgreSQL.

I'm not sure what "Live Writer" is, but if you want text-editing which is a little cooler than plain <textarea> you can use: [http://dojotoolkit.org/docs/rich_text.html](http://dojotoolkit.org/docs/rich_text.html)  (try the demo, it is linked to at the top) .. coupling this with Hunchentoot is easy.

edit:
let me know if you need any help getting started .. here is a short guide though: [http://ubuntuforums.org/showpost.php?p=2224105&postcount=21](http://ubuntuforums.org/showpost.php?p=2224105&postcount=21)

---

### Post by timmahhny on 2007-03-01
"edit: oh wait; you want something to use on Blogger? .. something that lets you edit blog-posts using a "real application" instead of editing via a web-page? .. i might have misunderstood what you meant"

Yes, I just want to click on a program on my computer,make an entry, hit post to post it to blogger. Live Writer by Microsoft is actually a great free program that will download the templates, so you can see what it looks like.You can edit, create links, etc... I like Live Writer a lot, but hate Windows, tired of it, so I only have one computer running Windows. 

 I have tried Drivel, KDEblog, and others but nothing will connect to the new blogger. 

 So what I would like to do, is attempt to create a piece of software, that I can grab my posts, make posts, etc... from my  computer, without having to log in and use blogger. 

 I will check out the programs that you have suggested and if I do attempt this, trust me you will be asked for help!!!

 Thanks 
timmahhny

---

### Post by lnostdal on 2007-03-01
> **timmahhny said:**
>  I will check out the programs that you have suggested and if I do attempt this, trust me you will be asked for help!!!

well, you should note that i assumed you wanted to create the actual web-blog software itself .. and do posting etc. to it via a web-page

i'm not sure what the best approach for creating an editor-application would be .. do you want  WYSIWYG rich-text editing? if that is the case maybe embedding or exploiting Gecko (firefox's rendering engine) would be an idea .. but this might turn out to be a somewhat complex task; i haven't tried this

edit: well, what i mean is that i'm not sure the rich text widget in for instance gtk is "good enough" for you

edit2: hmm .. [http://www.mozilla.org/unix/gtk-embedding.html](http://www.mozilla.org/unix/gtk-embedding.html) .. edit3: is probably not what you're after .. in short i do not know the best approach for this potentially quite big task depending on what features you want

edit4:
i have on several occasions thought about using OpenOffice for these kinds of tasks .. seeing as it outputs XML it should be possible to .. say use a template the user can fill in and manipulate (to keep things within certain limits and sanity)..   then either:

* send the result from OOo to a custom web-service that does the actual conversion and posting
* have something written that converts and does the post directly from OOo

should be quite interesting .. and since OOo is portable it will work under many platforms

---

### Post by Note360 on 2007-03-01
Why don't you just use Blogger. The main problem is finding out the specifications for login into and posting to Blogger, which could be difficult. This actually probably fairly easy though.

Here is a link to some one trying to do something similar in Python. You probably could figure out how to do it in LISP or Ruby if you wanted to. I may draft up a simple CLI app to understand whats going on. Maybe ill make an app for you (GTK). Try to do it yourself first (I cant do GTK I am really bad at it).

EDIT: [http://groups.google.com/group/bloggerDev/browse_thread/thread/2da7900837c41c6f/f0f55682ceae44af%23f0f55682ceae44af](http://groups.google.com/group/bloggerDev/browse_thread/thread/2da7900837c41c6f/f0f55682ceae44af%23f0f55682ceae44af)

---

### Post by qamelian on 2007-03-01
Personally, I really like the Performancing extension for Firefox. It has a very easy account setup wizard, a decent set of tools and is very comfortable to use. It also supports most of the major blogging engines.

---

### Post by zanglang on 2007-03-01
Have you tried looking at w.bloggar on Windows? [http://www.wbloggar.com/](http://www.wbloggar.com/)
It was fairly compact yet fully featured.

Adding to the Mozilla idea, you can look into XULRunner for portable richtext apps too. :D
[http://developer.mozilla.org/en/docs/XULRunner](http://developer.mozilla.org/en/docs/XULRunner)

---

### Post by deuce868 on 2007-03-01
check out BloGtk. I use that to post to my blog and it works out fine. It doesn't have all the features, but should work for what you need.

---

### Post by timmahhny on 2007-03-01
> **Note360 said:**
> Why don't you just use Blogger. The main problem is finding out the specifications for login into and posting to Blogger, which could be difficult. This actually probably fairly easy though.

EDIT: [http://groups.google.com/group/bloggerDev/browse_thread/thread/2da7900837c41c6f/f0f55682ceae44af%23f0f55682ceae44af](http://groups.google.com/group/bloggerDev/browse_thread/thread/2da7900837c41c6f/f0f55682ceae44af%23f0f55682ceae44af)


I use blogger  when I am on my Linux machine. The problem I have most of the time using blogger, is that Opera doesn't see the page good enough, Firefox keeps refreshing blogger making it hard for me to do any writing, plus I it is a pain when I see a webpage and want to blog it, it is much harder to copy the web page url, then paste. It makes it much simpler to write it on my desktop, change it over a period of days, then post it. 

 But, hey if I can't find a good poster, then I will have to keep on using blogger. 

 Thanks for the info and help.

timmahhny

---

### Post by timmahhny on 2007-03-01
> **qamelian said:**
> Personally, I really like the Performancing extension for Firefox. It has a very easy account setup wizard, a decent set of tools and is very comfortable to use. It also supports most of the major blogging engines.

I think I have it installed, but Firefox is not the main browser, Opera is. I can't remember how well it worked. I will have to try it out again. 

 Thanks. Can't believe I forgot all about that.

 But I would still like to be able to write on my desktop, then post it, after I ensure that it is a coherent piece of writing. Not very good at writing off the top of my head without at least three revisions. 

 Thanks for the reminder of performance. 

timmahhny:lolflag:

---

### Post by timmahhny on 2007-03-01
> **deuce868 said:**
> check out BloGtk. I use that to post to my blog and it works out fine. It doesn't have all the features, but should work for what you need.

I have that installed but it didn't work out for me. Maybe I am doing something wrong. I had problems with drivel; then I installed the newer version, and could download the posts, but could not post to blogger. 

 I think I am going to try to make my own software, just for the fun of it, not that programming is fun; then try to incorporate the qualities of Live Writer and others into it, if it is possible. I know it is possible, just have to figure it out.

---

### Post by timmahhny on 2007-03-01
> **zanglang said:**
> Have you tried looking at w.bloggar on Windows? [http://www.wbloggar.com/](http://www.wbloggar.com/)
It was fairly compact yet fully featured.

Adding to the Mozilla idea, you can look into XULRunner for portable richtext apps too. :D
[http://developer.mozilla.org/en/docs/XULRunner](http://developer.mozilla.org/en/docs/XULRunner)

I already have a blogger account; but thanks for the w.blogger, as I was not aware it was running again. 

 For the XULRunner, you are over my head when you talk about richtext apps. 

 Thanks for the help and input from everyone!!

timmahhny

---

### Post by timmahhny on 2007-03-01
I would like to thank everyone for their help.
I would like to say this:
 
 I forgot all about the Firefox plug-in Performance, which I think works, but can't remember why I don't use it. 

 I think what I will do is try to do a blogging program for the fun of it, and in the meantime
I will use blogger to do my writing. Although on my laptop I have Windows Live Writer which I really like, but hate Windows Operating system. Windows will be removed from this laptop in a very short period time and hope that by then, I can either find a good solid piece of software for Linux. 

timmahhny
\\:D/

---

### Post by timmahhny on 2007-03-02
Performance is not working on Firefox. I can input the title but no text. However there is another plug-in for Firefox that I forgot all about, **Just Blog It** [https://addons.mozilla.org/firefox/329/]("https://addons.mozilla.org/firefox/329/")
Just Blog It works well with Firefox. But I still am looking for one that I can use on the desktop.
 
 Just thought I would let you guys know about JustBlogit.

Thanks 
timmahhny

---

### Post by darxoul on 2007-11-28
I know this thread is a bit old (a bit!) but i have been searching for a desktop application to post to my blogger account for the last few days (after installing ubuntu on my laptop).

my point is very close to that of timmahhny's. i used to use windows live writer when i used windows. since i dislike the online editor of blogger just because it is a pain to add images into you post using that editor, i started looking for an editor. at the end, microdoft released this program (which is very slow compared to what it is doing but) working very well for me. i really like using it because:

it is very easy to:
set up your accounts (multiple account possible)
add images
add video
do all the formatting

it supports all the major blogging engines

so i believe it is an application very close to a perfect product for my needs. it is not just writing the text and sending (as most of the clog clients i have tried before either in Windows or Linux). you feel you are formatting your post with a rich text editor. anyway, i need all those features in my ubuntu and couldn't find anything closer to that. so, if there is an application please let me know. if not, i am ready to contribute to a project that has these requirements. just need a mentor :)

one note: performancing requires you to have an ftp account to add images to your post (that was the case at least when i checked it), i am looking for a native blogger support using blogger services to add/ upload images and doesn't require ftp access.

---

### Post by timmahhny on 2007-11-28
darxoul:
I found the blogging software used in Firefox to be OK. I still have yet to find anything that works like Live Writer.
 I am sure that there will be someone in the near future that will create a new blogging software for Ubuntu. I hope.
Timmahhny

---

### Post by darxoul on 2007-11-28
hi timmahhny,

unfortunately, scribe fire (formerly performancing) doesn't support the new blogger api to upload images (please correct me if i am wrong). since i am posting a lot of images it is painful for me to use a tool like that. anyway, you understand what i feel. the odd thing is i ccouldn't even see an attempt from the linux community to fulfill this requirement. if only i could see a project aiming that, that would be good enough for me :)

image posting
video posting
mp3 posting (even WLW doesn' support that)

thank you.

---

### Post by timmahhny on 2007-11-28
>  doesn't support the new blogger api to upload images 
I found it difficult to even upload images from any blogging software into Blogger. Maybe I did not have the right settings.

> the odd thing is i ccouldn't even see an attempt from the linux community to fulfill this requirement. if only i could see a project aiming that, that would be good enough for me 


This might be true. I have notice that many people who use Ubuntu or any Linux distro, use wordpress. I am sure that sooner or later someone will make something like Windows Livewriter, at least I hope so. 

As I had said in previous posts, I just might take on this task. I have limited programming ability, but what a great way to learn. Just need to figure out the first step. 

 If you find anything post it here.
T

---

### Post by darxoul on 2007-11-29
> **timmahhny said:**
> I found it difficult to even upload images from any blogging software into Blogger. Maybe I did not have the right settings.

I feel quite comfortable with WLW about that. You can edit nearly everything about an image in the blog with it. But not as advanced as directly editing the HTML (who cares?)

> **timmahhny said:**
> 
As I had said in previous posts, I just might take on this task. I have limited programming ability, but what a great way to learn. Just need to figure out the first step.

i am plannaing to have a look into this, but i am quite new to linux. so i will post it here whenever i feel like really doing something in case people would like to contribute.

> **timmahhny said:**
> If you find anything post it here.


sure i will :)

---

### Post by xtacocorex on 2007-11-29
Instead of waiting for someone to write it, learn Python and do it yourself.  There are libraries that will talk to blogs, just need to learn how to use them.

Or you can help out on an existing blog writer software and put improvements and bug fixes into it. 

Complaining without taking action is worthless.

---

### Post by darxoul on 2007-11-29
xtacocorex: i completely agree on what you say. the reason i wrote my thoughts here is to make sure that i am not really missing some good program that i can use. otherwise that is what i am planning to do whenever i find some time to do so. if you know of any projects that needs this kind of support (i only read about python, didn't use it before) i can go with that, otherwise, i will have a look what i can do on my own. i would appreciate any "mentoring" help in the meantime just to make the learning faster. if anyone would like to comment on this kind of a project (or an add on to a project) please feel free to do so, because i am quite determined to have such kind of an application as soon as i get.

thanks for your reply,
d.

---

