---
title: "Answer to Windows Home Server?"
date: 2007-08-23
forum: Other OS Talk
---

### Post by gaalderman on 2007-08-23
I've been reading up on Windows Home Server for a few weeks.  There's an interesting [article ]("http://tinyurl.com/yr439a") and [discussion]("http://tinyurl.com/29jnmb") on Linux-Watch.com where the point is made that most if not all of WHS' functionality is available for free on Linux.  

One poster listed key WHS functionality that users will want:
* Fast cluster-level incremental backups equivalent to full backups
* Bare-metal client recovery (restore a PC with a bare hard drive)
* Single instance storage (duplicate files don’t waste space)
* Previous versions (file journaling with Volume Shadow Copy Services)
* Remote Desktop gateway (multiple PC support)
* Media streaming with Windows Media Connect
* Print server with auto-driver loading

And another chimes in with
* Easily add and remove any drive of any size on the array.
* Automatic backups for all my desktops and laptops.
* Restore process for my desktops and laptops.
* Remote access

Linux can do this handily, these posters are reminded.  In fact, it occurs to me that **Windows itself** has had much of this capability for years, sometimes provided through 3rd party tools such as Ghost.   But WHS' key advantage is that it provides a convenient, easy-to-use interface for implementing these services that is accessible to mere mortals.  I'm still learning Linux and therefore such convenience is an important selling point.  Thus, advantage to WHS.  

To me, this sounds like a prime opportunity for Ubuntu.  What if someone with strong Ubuntu kung fu were to assemble a tutorial in configuring an UHS (Ubuntu Home Server) that mirrors WHS' functionality? Make it a detailed walkthough so that newbies can do it.  Has someone already done that?  I didn't find anything Googling; maybe I'm looking for the wrong thing.

Or better yet, what if someone could build a console application that provides much of the one-stop shopping features of WHS.  (Maybe someone's already done it!  If so, let's generate some buzz around their work.)  From this console, you set up anything that you need for your UHS, and the console will automagically configure Samba, Apache, streaming server, imaging software, or whatever else for you.  You may need to build equivalents to the Windows client applications that come with WHS as well, so you can configure your Windows boxes to back up to,  stream data from, or do whatever with the UHS.  This is all well beyond my capabilites.  But it's an interesting idea for a project, isn't it?  **Has **someone already done it?

Thanks,

---

### Post by ffejrey on 2007-08-23
I think it sounds like a good idea and would like to see something like this.

---

### Post by smiggs on 2007-08-23
[http://www.ubuntuhomeserver.org/](http://www.ubuntuhomeserver.org/)

They're already had quite long threads about a concept like this in the development forums on this site, I believe they are looking at a Gutsy +1 release. If you read the specifications it sounds very promising and probably mirrors what you have there plus a little bit more.

---

### Post by gaalderman on 2007-08-24
That is **exactly** what I'm looking for.  =D>  Thanks for the pointer!

No matter what you're looking for, chances are there's someone out there in FOSSLand who's doing it or has already done it.

---

### Post by stevelasvegas on 2008-01-31
I don't think it's Ubuntu but it is Linux based. I used Windows Home Server for a couple of weeks and now I am using this [http://www.ezbluesoftware.com/](http://www.ezbluesoftware.com/)

---

### Post by volkswagner on 2008-10-01
> **smiggs said:**
> [http://www.ubuntuhomeserver.org/](http://www.ubuntuhomeserver.org/)

They're already had quite long threads about a concept like this in the development forums on this site, I believe they are looking at a Gutsy +1 release. If you read the specifications it sounds very promising and probably mirrors what you have there plus a little bit more.

Anyone know the current status of UbuntuHomeServer edition?  

It appears the site is down at the moment.  I have checked a few times in the past.  I was hoping for an alfa by now.

---

### Post by volkswagner on 2008-10-01
Well, the site is back up.  It is DEAD.  I was looking forward for a real ubuntu version.  Seems the all the Ubuntu servers have had a lot of downtime lately.

From the forums-
> 
this project is dead.

all active developers forked and created a new project "satega the openhomeserver"
satega.org

we are currently working hard for our first release.
All help is welcome.

---

### Post by chungy on 2008-10-02
Well, there's the official Ubuntu Server.  I know it doesn't have pretty GUI configuration tools or a web interface or whatever, and pretty much only comes with a web server by default (are all servers web servers? heh).  It'd be a good experience to learn how to use the software directly, especially if you'd like a job as a system administrator :)

---

### Post by oly on 2009-02-09
check out [www.ubuntuservermanager.org](www.ubuntuservermanager.org) or launchpad.net/usm, this is basically a project to create a home server based on ubuntu but has been moving along slowly due to very little interest only one person currently working on it which is me but i have been hammering away at it for over a year.

---

