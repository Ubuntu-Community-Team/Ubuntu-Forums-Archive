---
title: "Hosting Silverlight on Apache / Linux"
date: 2007-09-17
forum: Programming Talk
---

### Post by Tylo on 2007-09-17
Is it possible to host Silverlight programs off of an apache server in linux? I don't need to have the Silverlight programs run in a browser inside linux, I just need to be able to host them off the server.

---

### Post by pmasiar on 2007-09-18
Warning: I am not an expert in this, just interested in what is next after AJAX/flash. I am way out of my deep here, wild guess follows:

Looks like it requires DOM on server. So maybe Mono might have it. 

But of course it is proprietary MSFT technology, and everything MSFT does, MSFT does to support Windows, and Windows only, as much as possible. Sadly, Silverlight looks good, and free/open standard software variant is missing.

---

### Post by qamelian on 2007-09-18
> **pmasiar said:**
> Warning: I am not an expert in this, just interested in what is next after AJAX/flash. I am way out of my deep here, wild guess follows:

Looks like it requires DOM on server. So maybe Mono might have it. 

But of course it is proprietary MSFT technology, and everything MSFT does, MSFT does to support Windows, and Windows only, as much as possible. Sadly, Silverlight looks good, and free/open standard software variant is missing.

Not missing at all. The devs over at Mono having been working on an OSS equivalent for a while. The OSS implementation is called Moonlight.
[http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

---

### Post by pmasiar on 2007-09-18
That's great news. Maybe Mono might be a good idea after all... :-)

...but I am not switching yet! :p

---

### Post by moephan on 2007-09-18
If you are using version 1.0 of Silverlight (the current supported version), it's just HTML, XAML, and javascript being rendered on your server. The proprietary bits are in the plugins on the client side.

You shouldn't have any issues at all hosting it on any web server platform. Have you tried it and seen issues?

HTH

Cheers, Rick

---

### Post by Tylo on 2007-09-18
No I have not yet. I am most interested that Silverlight works with IronPython, and it looks like Silverlight 1.1 is the piece of work that I want. However, you mentioned only Silverlight 1.0 would work without a hitch in Apache.

I'll develop some HelloWorld Silverlight 1.1 piece and see how it works.

---

### Post by Tylo on 2007-09-18
Good news all. I downloaded [this]("http://www.voidspace.org.uk/ironpython/webide/webide.html") and found out that it works in Apache2!

This one runs with IronPython and SilverLight 1.1.

Next I'd like to see if C# stuff will run in Apache2 with SilverLight 1.1.

I have a strong feeling it does, because I believe all the code is ran inside the browser whenever the client requests it.

---

### Post by timothyp on 2008-01-30
The way I see it all code is executed on the client.
The problem is adding the correct mime types on the server
and allowing the client download the dll files from the server
(for silverlight 1.1).

I've been able to add the MIME types:


There seems to be a problem with the plugin though
if you try this [http://www.zendurl.com/t/timheuer/v1_1/Default.html](http://www.zendurl.com/t/timheuer/v1_1/Default.html)
or [http://www.itcrowd.be/silverlight/netrissilver.html](http://www.itcrowd.be/silverlight/netrissilver.html) you'll get the same exception. They work when hosted with IIS however.

The MIME Types are

Extension
	

MIME Type

.manifest
	

application/manifest

.xaml
	

application/xaml+xml

.dll
	

application/x-msdownload

.application
	

application/x-ms-application

.xbap
	

application/x-ms-xbap

.deploy
	

application/octet-stream

.xps
	

application/vnd.ms-xpsdocument

---

