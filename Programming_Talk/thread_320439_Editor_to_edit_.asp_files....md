---
title: "Editor to edit .asp files..."
date: 2006-12-17
forum: Programming Talk
---

### Post by Betelgeuse on 2006-12-17
Hello,

I'm a new ubuntu user. I write asp programs for living so I need to have an editor to edit .asp files. in windows, I'm using MS Visual Interdev to edit asp files. it's a part of Visual Studio 6.0. I do not want to edit .net or aspx file. .Net is the main reason I give up using windows but still I had to use asp for programming becouse all my customers use windows servers and ms databases. In my office, I have a windows 2000 server running IIS and MS SQL server to run the web based applications. I can open the asp files on the server via samba shares and I run them in firefox browser for testing. On my windows work machine, I have interdev and firefox windows open and I edit on one windows and test on another windows and the server do all the running. Now that this is a simple environment and we have firefox on linux too, so only thing missing in linux i a good editor. I do not neet some bloated IDE. All I need is a simple text editor with syntax coloring. the asp code is actually visual basic code written inside html code... Any suggestions?

---

### Post by pmasiar on 2006-12-17
*Very good* lightweight editor with syntax coloring for many languages is SciTE (package scite). If it not recongnizesASP, try eclipse: it ie heavy and complicated, but (after you learn it) should be able to do everything VS does, and more. And it is free.

For firefox, you are aware and using of web developer extensions, like excellent 'Web Developer'? When looking it up, I found some new interesting extensions, like: lori, Html validator, load time analyzer, etc. Lots of goodies there.

---

### Post by Betelgeuse on 2006-12-17
I do not need anything compted weblopment. I just write the asp code inside html files and some web designer making those files for me so I do not have to deal with how does it look. I've tried kdevelop but I think I need to mount samba shares to open the asp files, I could not open them directly  like "smb//server/share/file.asp"

---

### Post by lnostdal on 2006-12-17
> **Betelgeuse said:**
> Hello,

I'm a new ubuntu user. I write asp programs for living so I need to have an editor to edit .asp files. in windows, I'm using MS Visual Interdev to edit asp files. it's a part of Visual Studio 6.0. I do not want to edit .net or aspx file. .Net is the main reason I give up using windows but still I had to use asp for programming becouse all my customers use windows servers and ms databases. In my office, I have a windows 2000 server running IIS and MS SQL server to run the web based applications. I can open the asp files on the server via samba shares and I run them in firefox browser for testing. On my windows work machine, I have interdev and firefox windows open and I edit on one windows and test on another windows and the server do all the running. Now that this is a simple environment and we have firefox on linux too, so only thing missing in linux i a good editor. I do not neet some bloated IDE. All I need is a simple text editor with syntax coloring. the asp code is actually visual basic code written inside html code... Any suggestions?

Most editors have these features; I use Emacs.

---

### Post by Betelgeuse on 2006-12-17
I've used Emacs to write fortran programs 20 years ago when I was at school. now that seems too far for me... 

But I found kdevelop and it can edit asp files and that's enough for me for now..

---

### Post by lnostdal on 2006-12-17
btw. you do know that you can connect to MSSQL using almost any language? You do not have to use .NET or ASP. :)

---

### Post by Betelgeuse on 2006-12-17
> **lnostdal said:**
> btw. you do know that you can connect to MSSQL using almost any language? You do not have to use .NET or ASP. :)

I know and I hate .NET, so that's why I still use the good old asp. But My customers have windows servers and have lots of web based database applications so I have to continue using asp. But for the new projects, I'l try using php, but first I have to continue the unfinished projects...

---

### Post by gh0st on 2006-12-17
You might want to try something like Ruby On Rails instead of PHP. I used to develop all my stuff in ASP a couple of years ago, then I moved to .NET and now I think I might move to Ruby. I tried PHP but wasn't that impressed to be honest, sorry to any PHP fans, just my opinion. If you like the ASP 3.0 coding style you might like PHP though. There's always JSP as well.

Here's the link if you wanna check out Ruby On Rails:

[http://www.rubyonrails.org/](http://www.rubyonrails.org/)

As for a good editor to use on Linux. I run Visual Studio for maintaining my .NET projects on a virtual machine with VMWare. I access the data on my Linux machine through Samba from the vm. Have you considered something like this?? It's not as complicated as it sounds. You could install Visual Interdev or Dreamweaver if you want to avoid Visual Studio. It might be a bit of an overkill though I admit.

---

### Post by pmasiar on 2006-12-17
> **gh0st said:**
> check out Ruby On Rails

If you want to try web app frameworks like Rails, for sure check also  python-based [Django]("http://en.wikipedia.org/wiki/Django_%28web_framework%29") and [TurboGears]("http://en.wikipedia.org/wiki/TurboGears"). Python, has one bonus point over Ruby: .NET version [IronPython]("http://en.wikipedia.org/wiki/IronPython") (released by Microsoft), I am not sure which framework is better supported in .NET.

---

### Post by Betelgeuse on 2006-12-17
> **gh0st said:**
> You might want to try something like Ruby On Rails instead of PHP. I used to develop all my stuff in ASP a couple of years ago, then I moved to .NET and now I think I might move to Ruby. I tried PHP but wasn't that impressed to be honest, sorry to any PHP fans, just my opinion. If you like the ASP 3.0 coding style you might like PHP though. There's always JSP as well.

Here's the link if you wanna check out Ruby On Rails:

[http://www.rubyonrails.org/](http://www.rubyonrails.org/)

As for a good editor to use on Linux. I run Visual Studio for maintaining my .NET projects on a virtual machine with VMWare. I access the data on my Linux machine through Samba from the vm. Have you considered something like this?? It's not as complicated as it sounds. You could install Visual Interdev or Dreamweaver if you want to avoid Visual Studio. It might be a bit of an overkill though I admit.

I have a virtual windows server ruinning happly in vmware server. I have Visual interdev and MS SQL server client tools (to write and edit SQL stored procedures and design database). But aur testing web server runs on another machine and it runs windows 2000 server, IIS 5.0 and SQL Server 2000. The inetpub directory on that server is shared so I can access then from my virtual machine and I can edit asp files with visual interdev. But I want to edit them from linux so I do not need to enter my vmware server. Now I'm trying to use kate and kdevelop on kubuntu to edit those asp files, it's as easy as using interdev but it need some getting used to. Now I'm thinking of setting up wine and install ms sql server client tools for my database tasks and if I manage to setup sql server tools on linux, I'll not need to run vmware all the time... I think I'll still need a vmware machine when I'm mobile because I'll need to access IIS server and MS SQL server but that vmware server can run in the background so I do not need to see windows, I'll access it just like I'm accessing a windows server on the network. My test server at the office is actually a virtual machine too. The server box runs windows 2000 and vmware server and there are 3 virtual servers running on it. When I go out, I just copy the test server virtual machine to my laptop and I continue working as if I'm still at the office and when I come back, I transfer the changes I've made to the office test server and continue working.

---

### Post by gh0st on 2006-12-20
> **Betelgeuse said:**
> I have a virtual windows server ruinning happly in vmware server. I have Visual interdev and MS SQL server client tools (to write and edit SQL stored procedures and design database). But aur testing web server runs on another machine and it runs windows 2000 server, IIS 5.0 and SQL Server 2000. The inetpub directory on that server is shared so I can access then from my virtual machine and I can edit asp files with visual interdev. But I want to edit them from linux so I do not need to enter my vmware server. Now I'm trying to use kate and kdevelop on kubuntu to edit those asp files, it's as easy as using interdev but it need some getting used to. Now I'm thinking of setting up wine and install ms sql server client tools for my database tasks and if I manage to setup sql server tools on linux, I'll not need to run vmware all the time... I think I'll still need a vmware machine when I'm mobile because I'll need to access IIS server and MS SQL server but that vmware server can run in the background so I do not need to see windows, I'll access it just like I'm accessing a windows server on the network. My test server at the office is actually a virtual machine too. The server box runs windows 2000 and vmware server and there are 3 virtual servers running on it. When I go out, I just copy the test server virtual machine to my laptop and I continue working as if I'm still at the office and when I come back, I transfer the changes I've made to the office test server and continue working.

Wow sounds like you have a pretty sweet setup then. I like the idea of using the VMs as dev servers and copying them over to different machines. I might have to pinch that ;)  

KDevelop is pretty cool, I didn't know it worked with VBScript thats a bonus. Sounds like you've got it sorted.

---

