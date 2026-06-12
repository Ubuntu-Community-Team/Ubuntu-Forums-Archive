---
title: "LAMP Appliance Help"
date: 2008-01-28
forum: Programming Talk
---

### Post by Thund3rstruck on 2008-01-28
Hi all,

I'd like to play around with potentially converting some of my ASP.NET/C# web applications (such as [MP3 CMS]("http://www.nealosis.com")) into PHP/Python but I really don't want to have to build out a new server and go through the LAMP installation hassles. Does anyone know of a pre-built, pre-configured VMWare appliance that I can use for this purpose? If the conversion bears fruit I'll consider standing up a dedicated LAMP but I just can't justify all the expense (time) otherwise to move from Win2003 Server. 

There is an appliance on VMWare's site but it's of an old Ubuntu distro. 

Thanks..

---

### Post by Tuna-Fish on 2008-01-28
Umm... the time it takes to set up a server to run php on ubuntu: way less than it took you to write that post.

sudo tasksel install lamp-server

document root is at /var/www

have fun...

---

### Post by pmasiar on 2008-01-28
You may want take a look on TurboGears or Django. I know for sure TG comes with development server (good also for light serving) which is much simpler than Apache. Django likely has the same, I just don't use it.

Also, [http://en.wikipedia.org/wiki/Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) design pattern is great improvement over ASP, comes with both TG and Dj, make sure you use it.

Follow TG demo, you will build simple wiki in less than hour, including download.

---

### Post by Thund3rstruck on 2008-01-29
> **Tuna-Fish said:**
> Umm... the time it takes to set up a server to run php on ubuntu: way less than it took you to write that post..

Really? The last time I tried to set up a LAMP server (a few years ago) it was an endless pit of hell with failed dependencies, MySql configuration errors, and no documentation what so ever. After 2 days I tossed my hands up in the air and went back to IIS & ASPNET. 

I sure hope you're right.

---

### Post by pmasiar on 2008-01-29
apt/synaptic solves all dependencies for you, in my experience. Ubuntu app stack is simpler to install that Windows.

---

### Post by Tuna-Fish on 2008-01-29
> **Thund3rstruck said:**
> Really? The last time I tried to set up a LAMP server (a few years ago) it was an endless pit of hell with failed dependencies, MySql configuration errors, and no documentation what so ever. After 2 days I tossed my hands up in the air and went back to IIS & ASPNET. 

I sure hope you're right.

You didn't get it.
```

terminal:
sudo tasksel install lamp-server

```
was it. In addition to that, you are asked for a mysql root password. no other mandatory configuration. It's up and tunning in 15 mins or less, with sensible defaults and your machine serving the apache test page at port 80.

Don't you just love debian and apt?

---

### Post by Thund3rstruck on 2008-01-30
> **Tuna-Fish said:**
> You didn't get it.
```

terminal:
sudo tasksel install lamp-server

```

Don't you just love debian and apt?

No, no.. I've got it and you're right it was exceptionally simple. I'm glad to see this has been worked on in the last few years.

---

