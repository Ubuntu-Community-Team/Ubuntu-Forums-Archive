---
title: "Website management tool"
date: 2005-10-26
forum: Programming Talk
---

### Post by dizzy1234 on 2005-10-26
Hi folks,

I'm a recent Linux convert (always used plenty of OSS tho) and I'm wanting to experiment a bit with writing my own programmes. I work as a web designer (so I have a bit of programming knowledge) and I want to try and write some applications that will help me be a bit lazier when it comes to uploading and downloading websites.

There are some details on what I'd like the scripts to do below but what I'd like to know is, which language should I be looking to write and where can I find information on how to use this language? The details below aren't especially important, as once I know where to find the information I think I'll be ok.

I have apache installed and working nicely (thanks to these forums) on my laptop and I have a similarly powered remote web server that I keep most of my websites on. What I'd like the scripts to do is:

-- keep a database of the different websites I currently run and where they are to be found. Obviously I'll need to be able to add, copy, edit and delete from this conveniently.

-- when I want to work on a site, I'd like the scripts to automatically download the website folder from the remote server, making sure that the local version is not newer, open that folder in Nautilus, open up a pre-determined set of pages from the local version in SciTE (I don't like Screem) and fire up the local homepage via HTTP in Firefox.

-- when I'm done, I want it to close down the various programmes it opened initially, upload the local folder to the remote server and then prompt me to see whether it should delete the local version to scrimp on the hard drive space.

-- If possible (getting adventurous now) I'd like it to remember which pages I had open (in Firefox and whatever editor) between sessions.


I don't think this will really save me any time in the long run - what with writing the scripts, checking them, etc. I'll probably eat more time than I'll ever save. However, I'd like to learn how to write these things and I thought it would be a useful way to learn.



Any help is always appreciated

Cheers
Nick

---

### Post by David Marrs on 2005-10-26
Hmm, you know you could use this as a way to teach yourself some web development techniques if you want. You're running Linux and apache, have a use for mySQL and require the power of php, perl or python. :P

I'd be inclined to go with either PHP or Python. Perl seems to be losing ground to PHP and Ruby is still quite new on the block.

I still haven't used Python, so I can't really talk about it but I like the way php  augments html. It's very easy to simply drop into web pages and its syntax will be familiar if you've used javascript.

You'll need to install both a mod-plugin for apache and also bindings to the mySQL database server. After that you should be ready to go.

---

### Post by mostwanted on 2005-10-26
[QUOTE=David Marrs]Ruby is still quite new on the block[/QUOTE]

Not really, but I see what you mean...

---

