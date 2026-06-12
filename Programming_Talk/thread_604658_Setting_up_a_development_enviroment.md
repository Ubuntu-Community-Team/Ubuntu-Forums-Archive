---
title: "Setting up a development enviroment"
date: 2007-11-06
forum: Programming Talk
---

### Post by cpetzol2 on 2007-11-06
I have been using linux for about 6 months now, and I am finding myself with so many options that Im not sure how to go about something. I am going to ramble a little bit about my current setup. I apologize for the long post, but I am just trying to be thorough, so that you guys can better help me.

I have gutsy amd64 installed and running on a desktop and a laptop.

I am trying to set up an ideal development enviroment. My work primarily consists of web devel (PHP, Postgres, a little Ruby/Rails, and AJAX), but I also do some C++ and Java. 

I have a huge FAT32 partition on my desktop that I use for all of my storage. I use this partition to share files with Windows on my desktop (I still have to use Flash and Photoshop every now and then) and I have it mounted at /main. 
I have an almost identical setup on my laptop (dual boot, FAT partition to share files).
On both computers, I have apache running. I use symlinks from the docroot of apache to link to projects on /main, and then use [http://localhost/rayswebsite/](http://localhost/rayswebsite/) to access my sites.

As of late, I have been using Bluefish for my programming. When I make changes on either of my computers, I have been using rsync to add the changes to the opposite computer. This has been getting tedious, and I always end up having to manually screw with the files (because I know of no better way) because my current setup is rigged, if you will. I would like to incorporate Subversion into this picture, but I will get to this later.

Now, I am trying to use Eclipse with the PDT packages (PHP) instead of Bluefish. But Eclipse uses "workspaces" for all of its projects, and it creates a custom directory structure. Eclipse has some debug tools built in, but there are times when I need to test and develop my website through my local apache setup. Such is the case when I am in Windows working on a Flash site. I point apache to the project folder, and then I am able to intergrate my flash project with my PHP framework, and do all kinds of testing and development offline.

I use my desktop for most of my development, but my laptop is just as important to the whole process, such as when I go to meet a client, or when I am on the road.

I think I need a fundamental restructuring on both of my computers. How should I go about this. I need both computers to stay synchronized, and I would like to assume that windows must be able to access each project through apache. So, where do I start.
Is my /main partition a good idea? How should I organize everything?
 I would like to have Subversion, so I will need a place to store my repositories (which will need to be accessed from linux and windows). I am guessing that I will put the SVN repos on my desktop, and then keep only working copies on my laptop. I need a way to make my working copies completely functional websites when accessed through localhost. 

My current setup is something like this...
/main
/main/svn
/main/apache
/main/workspace

But when I work on projects through eclipse, I have a total of THREE copies of the website present on my hard drive. I have the repo in /main/svn, I have the working copy in /main/workspace, and then I have a "final" version available in /main/apache, so I can see the site live in both windows and linux. I also always make a mess with image files, when designing websites (raw pictures, alpha versions, beta, final, XCF, PSD, always a mess)

Everything is just so disconnected right now. I am always missing a piece from one folder in another folder, and then I find that 10 of those files in that project are 2 weeks old on my laptop, and I just spent 10 hours developing code that doesnt work when I move it on to my desktop.

I know this was a long post, and I am asking some pretty big questions, but any help is much appreciated. If you could criticize my setup, or tell me yours, whatever you got.

Thanks.

---

