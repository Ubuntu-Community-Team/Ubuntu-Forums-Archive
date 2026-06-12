---
title: "Help Wanted - Creating a website client in C#"
date: 2011-08-09
forum: Programming Talk
---

### Post by Zeikcied on 2011-08-09
I have the urge to attempt to create a client for a website I use.  The website has an API with documentation.  But I've never made a C# app that uses anything related to HTTP or any other web protocol.

So, where do I start?  The website uses cookies and SSL.  I'd love it if there's a tutorial or something out there on how to handle these (as well as sending and receiving HTTP requests and anything else that may be required).  For now I'm just going to be working on text stuff, but perhaps I could add file upload functionality in the future.  I would hope that's not too complicated.

This is completely foreign territory for me, and I tried looking around a few C# websites I bookmarked, but I didn't find anything on clients.  (Just ASP.NET for server-side apps.)

---

### Post by Fallen_Demon on 2011-08-09
This is actually quite simple. The HttpRequest class wraps around all of this and SSL will be handled for you automatically. After that, it's just a matter of decoding the response. .NET was built for XML, so if that's what the site uses, you're in luck. If it's in JSON, I'm pretty sure there'd be a Mono class around to handle it.

---

### Post by Zeikcied on 2011-08-09
According to the documentation, the API uses JSON by default, but it can be changed to XML by using a certain parameter with the query.

But as I said, I haven't done anything related to desktop apps that connect to websites.  So I don't even know where to begin getting the program to go online, never mind getting it to start interfacing with a website API.  I need some help getting to that very first step.  I don't know where to find a tutorial, and diving right into source code (like I did when looking at the source of a C# Twitter client) just leaves me lost and confused.

Add to that the fact that I've never done much programming (outside of a few college courses), and haven't done anything programming-related in six years (except for a few very brief bursts of activity), and I'm more or less a complete newbie who doesn't know what he's doing. ^_^;

---

### Post by directhex on 2011-08-10
If you have an xsd file (XML Schema Definition), the "xsd" tool will generate classes for you which let you treat your website like a normal object. I've used it to access the Amazon Web Services API before.

---

### Post by Zeikcied on 2011-08-26
Maybe I should have just gone step by step instead of lumping all my questions into one post.

So, step one, how do I even begin making a program that connects to the internet?  I know nothing of TCP/IP, sockets, or any of that stuff.  Total newbie here.  A nice tutorial would be great, or if you're willing to help me out here, that would be awesome.  Honestly this is the most basic, and for obvious reasons the most important part of what I wanted help with.

---

