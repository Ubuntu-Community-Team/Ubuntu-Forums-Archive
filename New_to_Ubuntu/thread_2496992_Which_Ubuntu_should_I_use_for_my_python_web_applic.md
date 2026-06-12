---
title: "Which Ubuntu should I use for my python web application"
date: 2024-04-19
forum: New to Ubuntu
---

### Post by wailoonho on 2024-04-19
Hi
I am very new to Ubuntu.
I'm working on a small project, this web application written using Python and the DB is PostgreSQL.
It is for a small company where the user for this web application is less than 30+ persons. 

I plan to use Ubuntu as the web server to host the application but not sure should I use Ubuntu desktop or Ubuntu server edition.

Please advice.

---

### Post by ActionParsnip on 2024-04-19
Using server will reduce the OS footprint as you won't need to run a display manager, desktop environment and so on. The Ubuntu desktop will also come with a sound server which you don't need and so on.

Keep it small and punchy, I'd go for server (CLI only). You can then manage your web service via SSH or (Ideally) Ansible if the project expands.

---

### Post by TheFu on 2024-04-19
Servers should be hosted on systems that don't waste resources on GUIs, but if your Linux skills don't already include a few years of Ubuntu Server (or some other Unix-like Server), then you should go with a minimal desktop.  That would be something like Xubuntu or Lubuntu if you need a full DE, which you shouldn't.

Linux servers doin't come with any GUI.  All settings are managed through shell/cli commands.  If you don't know how to fully configure networking using those sorts of tools, then you'll need some DE which has a GUI for doing it.  Of course, extra code running on the server means less is available for doing the work that the server is there to do. Also, that extra code brings hundreds of thousands of extra risks which can be attacked by hackers, both external and internal.

For 30 users, you probably don't need much of a server.  If it were me, I'd run that webapp-python inside a container or under a virtual machine, so it wasn't tied to any specific hardware.  This way, should something bad happen or you need to move the service to different hardware, the relocation will be 100x easier.  Moving a VM is much easier than moving an install on a physical system.

If there isn't something specific in Ubuntu that you need for this server to work, you should consider going with a lighter release, say Debian.  This will have many good benefits that you can research, but mainly it will reduce the bloat that any DE brings with it.  If you do install an Ubuntu desktop flavor, you should remove any unnecessary packages.  For example, do you really need the pre-installed LibreOffice package on your server?

---

### Post by wailoonho on 2024-04-19
thank for the information.
1. I really dont have much experience in Unix and Linux. So I think I will choose to use Desktop edition
2. We are using Virtual Machine under a Windows server, to reduce the cost to purchase Windows License. 

Then another question is, what web server service i should install to host python? 
I know there are something call nginx, but since I'm not good in Linux, I will prefer to use the most easier setup 1.
Can recommend some?

---

### Post by TheFu on 2024-04-19
> **wailoonho said:**
> 
Then another question is, what web server service i should install to host python? 
I know there are something call nginx, but since I'm not good in Linux, I will prefer to use the most easier setup 1.
Can recommend some?

It depends on how the webapp is written.  I'm not a python dev, so I don't know the different tools, but in perl, I use PSGI tools for perl to scale out the number of webapp instances (Starman as the pre-forking manager) and only use a reverse proxy for TLS termination before sending the requests to their tagged back-end perl servers.  Those servers can be on the same VM or spread across as many (hundreds) of backend systems across hundreds or more physical servers).   I'm fairly certain that Python and Ruby do the same stuff.  I've used thin for Ruby, but that was about 15 yrs ago, so the preferred tool has probably changed by now.  Ruby likes to re-write everything every other year, which drove me away from that wonderful language.  I was constantly porting my ruby and rails code every year to a new, incompatible, release. After 4 yrs, I'd had enough and ran back to perl.  I have perl scripts that were written in 1993 and still work the same today, just with newer versions of perl5.

Anyway, python most certainly has some sort of scaler for webapps that probably has xSGI in the name.  Writing your apps for that architecture would be smart.  Then the web server matters very little, since you might use it only to serve static files (CSS and images), while the dynamic content is handled through the webapp.

I've used nginx and Apache and litehttp and a few other minimal web servers over the decades.  The more capabilities a web server has, the more complex it is to setup and the harder it is to actually secure.  Smaller and simpler is best, but when you are just starting out, use whatever the book you are following suggests.  Many web-app programming books start assuming people know nothing and will provide step by step instructions for 1 method that the author has used and believes to be solid for people following along in the book.  Sadly, by the time most books are printed, it has been a year and the underlying tech has all moved forward, so the how-to guide in the book isn't 100% valid anymore.  The only way I've seen books successfully address this was by setting up training servers for a minimal cost ($5-$10/month) that were pre-configured exactly as the author dictates.  The problem with this method is that the devs following along will assume that every server will come preconfigured with exactly that software and settings, which doesn't happen.

Sigh. There's no substitute for experience and someone doing exactly what you are trying to do with the requisite experience who is willing to share.  My metro area has a Python User Group that is very active.  Perhaps where you are is one too?  Go. Talk to the people there. Ask how they do it and what they suggest you do.  Go to their weekly/monthly meetings and build a network of friends.  Some day, one of those people may need help or be able to help you find a better job.  At worst, you'll be plugged into the python community and hear all the different things everyone there is working on.

I'm a member of our local Perl group and attend national Perl events every other year.  Being around people with similar interests and learning from those presentations/classes really jumps your level up.

---

### Post by MAFoElffen on 2024-04-19
In your Title "Which Ubuntu..." --- >> Anything in current support as an LTS version. << That is the priority in a production system, hands down.

As having been (among many other things trying to survive over the years) a web dev, on both Apache and IIS webservers... As you specially worded your question in your first post: "Bottle".

RE: [https://binmile.com/blog/top-python-frameworks-for-web-development/](https://binmile.com/blog/top-python-frameworks-for-web-development/)

But that recommendation is based on that it doesn't need anything extra besides the basic Python Libraries. There are better tools out there, but, then they require specific (extra) libraries to go along with those. Each "extra" library, you then need to know what they do and how to use them. There is a bigger learning curve to get productive with those. In the long run, those others save time and add features that you didn't have, unless you hard-coded it, with the standard libraries. In that respect, think of extra libraries as an API. 

So the answer to that is "complicated". Does that make sense to you?

But then again, I'll write HTML & CSS... Then my dB connections/interfaces... Then my web app's ... in just good a program editor. I am not locked into "just one specific way" to do something, unless I am on contract, then have to stay within what "they" use within their organization. ...Which that organization will have to support on their own, after I am gone.

Tools? there is a lot out there, for many languages. Lots of API's to the specific dB's. But if you understand how it works, and how all the pieces fit together, you have more of a chance of success, and can more possibilities of how things "could work".

Just some thoughts on that.

---

### Post by ActionParsnip on 2024-04-20
+1 for LTS in prod. 24.04 is being released soon. You could install it now as prerelease then you will upgrade seamlessly into the release candidate. 24.04 will be supported until 2029 (5 years). Oh and remember to add the server to your backups.

---

