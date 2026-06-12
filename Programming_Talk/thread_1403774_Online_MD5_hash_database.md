---
title: "Online MD5 hash database"
date: 2010-02-10
forum: Programming Talk
---

### Post by R33D3M33R on 2010-02-10
I have been thinking about building a MD5 hash database for a long time. Here I will write down what this is all about.

I download mods and patches a lot, because I'm a gamer. Sometimes they are really huge and take some time to download. I burn them to CD/DVD because it can happen the mod will be lost in years coming. But what if there has been a interrupt while downloading. Maybe my client has messed up or the server did something unexpected. Maybe the connection was interrupted. How to check if the file is correctly downloaded?

I use MD5 mostly and I think it is ok enough to check if the file is really the correct one. But there is a problem. The MD5 sum is not always included on the download page. What then? Hope that the file is OK?

I was thinking of creating a user contributed database of MD5 hashes. How will it work? There are three possible situations:

a) contributer downloads the file. He checks it with MD5 generators and finds out it matches the MD5 sum posted on the website he has downloaded from. He than creates an entry to this base with MD5 sum, file size and file name so others will be able to check (via google?) if the original site with the MD5 sum dissapears, but the file still can be found on some other servers

b) user downloads the file and checks it with MD5 generator. Then he searches via google or this site for matches with the sum. He finds the match and voila, he is happy because the filesize and sum matches.

c) user downloads the file and checks it with MD5 generator. Then he searches via google or this site for matches with the sum. He doesn't find it, then he searches for the exact filename. He finds it and he knows now that his download is corrupted.

There could also be a type of: "request if MD5 sum is correct" entries in which other users could upload their results if they have the file with that exact filename


OK, before I continue with my idea, I must know for sure if such site doesn't already exists.

---

### Post by R33D3M33R on 2010-03-01
Ok, it's been two weeks and I only got two votes. That is no problem. I will eventually do it myself, but if there will not be enough help, I will put it on hold for a while.

Ok, here are some things I've been thinking about:

1) Simple design: The design should be really simple. Textbox with big search button on the first page and maybe top contributors/recently uploaded list, sign in, download helper programs. Thats all.
2) Free hosting, approx 100 MB (maybe even less) of space and SQL and NO ADS. I'm not willing to risk my personal website server for this or invest any cash in this. Sorry.
3) No ads: This database should be AD free. I don't need any cash from it, so no ads are needed. If it will eventually be successful and will have own server with domain, then maybe PayPal donations would be received, but this would have to be handled by someone else.
4) Public Source: When the site will near final release, the source code should be public under a license that would prevent commercial exploitation. So the page can be improved and optimised and bug fixed.
5) Registration: Because of tons of spam bots on the web, registration will be needed. I just don't have time to clean the userbase and waste time on those ******* spammers. This should be simple: username, e-mail (for confirmation, password recovery) and password. Any mail should be allowed (even mailinator and such).
6) Applications: In order to simplify upload process, there could be applications that help do that. I can't program well, so here would I need lot of help. App would get size in bytes, name and md5sum and uploaded it to server (I currently don't know how could it be done the simplest way - passing encoded string to the default browser maybe).

Reply to this thread if you are interested...

---

### Post by Penguin Guy on 2010-03-01
Just stick the md5s on your blog, then when people Google the md5 they will be able to see that it is, indeed, valid. There's no need for a database, but you *could* make an app' to automatically check Google.

---

### Post by Simon17 on 2010-03-01
I like the idea. Would anyone use it? I don't know. I never check the md5.

But it seems simple and useful and I would be willing to help.

(As for the app, you could just use libcurl to submit a form to the site)

---

### Post by R33D3M33R on 2010-03-01
Penguin Guy: The problem with using a blog is IMHO lack of control (sorting, similar entries, conversions, search suggestions etc.). I can't imagine going through tons of blog code just to integrate my functions. I think it's easier to write a simple website. But if it would be a blog, what blog system do you suggest?

Simon17: Thanks. I'll update this topic as soon as I go through some more ideas I have.

If any of you has an improvement idea, please add it! ;)

---

### Post by Penguin Guy on 2010-03-02
> **R33D3M33R said:**
> Penguin Guy: The problem with using a blog is IMHO lack of control (sorting, similar entries, conversions, search suggestions etc.). I can't imagine going through tons of blog code just to integrate my functions. I think it's easier to write a simple website. But if it would be a blog, what blog system do you suggest?
The only functions you need are:
[LIST]
[*]The ability to upload hashes - you can use any blog/forum
[*]The ability to search for hashes - you can use Google
[/LIST]

For example, if you hash "[FONT="Courier New"]Penguin Guy is right.[/FONT]", you get "[FONT="Courier New"]df46a5e44f9bdae48c9a06f0a04d28f1[/FONT]". [Search Google for this]("http://www.google.com/search?q=df46a5e44f9bdae48c9a06f0a04d28f1") and you'll get a link to this page.
This is because Google indexes everything on websites, and although it doesn't recognise ^ above word as a hash, it indexes it, and, because it's very long, it will almost certainly be unique on the web - allowing a very reliable hash search.

What I would suggest is that you create a nautilus extension that automatically md5sums a file and checks Google for any matches, then adds a tick or cross emblem depending on the results - I'd be willing to help with a project like this.

---

