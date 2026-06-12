---
title: "jsp:include, Sitemesh and character encoding problems"
date: 2007-10-14
forum: Programming Talk
---

### Post by CptPicard on 2007-10-14
Hey,

Ran into an annoying issue with my client's web application. Here's the deal: I'm using Sitemesh to decorate the various jsps I'm using. Most of my stuff has page-encoding in UTF-8, with output encoding set at ISO-8859-15 (because Tomcat's Unicode form handling sucks). We're in Finland, so the problem children of the alphabet are öäå.

My client uses Windows mostly, and he dumps these multi-megabyte static html files on the server daily, that are then served out and decorated nicely by Sitemesh. Because Sitemesh is bad at decorating static content -- it insists on caching the outcome, so changing decorators don't *change* -- I wrap the static html into a little jsp page that just jsp:includes the html. Now I get the problem..

The static big .html is in ISO-8859-15, but äöå become the typical question marks you get when it's being read as UTF-8, I suspect. The outcome of the whole page is however nicely in ISO-8859 (and the fronting apache also reports this in headers). Now, I tried adding the proper content-type headers to the static file, but it didn't work, caused a further Sitemesh bug (which I think I'll talk on Sitemesh forums further if it is significant), and would confuse my who is barely technical and who shouldn't have to write html anyway.

So we need to be including a big html fragment, essentially. Now, the content-type simply doesn't get recognized right, even when the including jsp is ISO-8859. Is there a way to force content-type for a jsp:include? I really can't do this via the include directive that actually has a switch for this, as it would just compile me a massive servlet...

---

