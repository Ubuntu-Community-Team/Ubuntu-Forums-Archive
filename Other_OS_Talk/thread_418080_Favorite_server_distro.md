---
title: "Favorite server distro"
date: 2007-04-22
forum: Other OS Talk
---

### Post by jinx099 on 2007-04-22
I have a headless server sitting in my closet primarily acting as a fileserver, but I also run VMware, VNC and some other stuff on it.  It is currently running openSUSE 10.2 but I want to load a new OS on it as I don't really like suse much anymore.  Yast is nice, but the package manager is overly complex, and seems a bit slow.

So here is what I'm considering loading on it next.

-Ubuntu 7.04 server
-Debian etch
-FreeBSD
-CentOS 5
-others?

The performance for VMware supposdley in Ubuntu 7.04 sounds interesting.  Is that an ubuntu only thing, or do other distros utilize that?  Or is it something built in to the 2.6.20 kernel?  Also, KVM seems interesting, but I havent gotten to get it working very well on my desktop.  Also, does KVM only work with virtualization processors?  

Debian Etch should be a great stable server, but I fear it would get outdated quickly.

FreeBSD would be cool, but last time I checked, VMware server wont run on it.  A plus for it would be I could use ZFS.

Centos 5 based on RHEL5 would be pretty cool, althought last time I tried it it seemed nearly identical to Fedora Core 6.  Fedora Core 6 has a serious bug in it that does not allow me to install on my server (I tried).

Also, I want to use Xen, but I've not had much luck using it in the past.  Which distro would you recommend for Xen?  What distro would you run on a home server and why?

---

### Post by heimo on 2007-04-22
> **jinx099 said:**
> 
Also, I want to use Xen, but I've not had much luck using it in the past.  Which distro would you recommend for Xen?  What distro would you run on a home server and why?

Of course there's lot of subjectivity when talking about distros. I'd be familiar with Debian, and as Etch is fresh, it's very tempting choice. I might even use it on my desktop. Currently, I'm using Ubuntu 7.04 on my desktop and running several Ubuntu 7.04 servers, couple Apaches, imap, smtp etc, on it using Xen. It was easy to setup (at least with Ubuntu clients), runs very smoothly and in my use (low load) is very fast. So that's my recommendation, but I have no doubt that there's other combinations that'll work equally well. However, I'd stay away from VMware, free virtualization software is definitely the way to go.

---

### Post by chatuser on 2007-04-22
If you know how about Ubuntu administration then use Ubuntu Server or Debian.

If you gonna use several server applications (Apache, MySQL, PHP, ...) I prefer Debian by now, it is very similar to Ubuntu, of course.

After some years, if Ubuntu demonstrates it stability for servers, perhaps it becomes a real alternative. For many people Ubuntu Server is a real alternative today.

---

### Post by zaratustra on 2007-04-22
> **jinx099 said:**
> 
The performance for VMware supposdley in Ubuntu 7.04 sounds interesting.Performance of VMware sounds intresting in any distro... I don't try to say something against ubuntu, I say that VMware is awsome. 
If you really want to be safe, try Free or even maybe OpenBSD(if you aren't geek and don't like idea of partitioning disk in sectors using your calculator, don't use it:-), but if it's that your home server, debian would do the buisness. Don't worry, you won't get outdated... You shouldn't really care much about that, if you want to set it up to work and then just use it without touching it any more... But if you are Indiana Jones type and you want cutting edge, put gentoo on it:)  And there is always good old slackware
Don't forget that I recommended you distros which you can customize installation not to install X and other stuff you can't use unless you have head:-) geez, I sound like a Clint Eastwood:-)

---

### Post by Pobega on 2007-04-22
Ubuntu is a little too unstable in my opinion for a server, and using LTS defeats the purpose; Debian's new stable release (Etch) is more up to date than Dapper is, so it's probably your best bet at this point in time.

Debian is amazingly stable, and I would recommend it to anyone else.

Me personally, I use FreeBSD. I love Debian, but I like learning about different distributions/operating systems more. So on my desktop (Which I use mostly as a server/slave, for compiling things and the like) I run FreeBSD, and I SSH into it from my laptop to take care of business once in a while. Ports isn't the best package manager ever, but it's very interesting to learn and work with. I just wish I could find a way around the nCurses menus messing with my compile time!

---

### Post by gnomeuser on 2007-04-22
Depending on the deployment, if I was putting up a company server that needed available tech support I'd go with Red Hat Enterprise Linux - I know the system well and it has always served my purpose nicely.

For a home server I have a strong preference for Fedora or CentOS both have decent support and update cycles, if I don't mind a 13 month upgrade cycle then Fedora gives me the newest versions and excellent security - if I need a bit longer cycle then CentOS being a recompile of RHEL has a 7 year support cycle and new versions come out every 2 years with a smooth upgrade path.

So it all depends on your use case, I'd probably favor a CentOS especially since Fedora is filling the hole in terms of natively compiled and supported applications with the EPEL project. Additionally you can run any program certified for RHEL on CentOS.

---

### Post by kerry_s on 2007-04-22
I would go for debian, with debian you can use packages from testing, unstable and experimental with out having to up grade your whole system. Just remember to set your default to stable(etch) in apt. You can always stay up to date with just the apps you want and if the upgrade goes wrong you have the option to down grade back to the previous version.

I used this 1 -> [http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r0-i386-netinst.iso](http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r0-i386-netinst.iso)
for a custom build, it allows you to select what you want, i don't select anything to get a minimal install. Use " installgui " if you want the pretty installer otherwise just press enter.

---

### Post by dca on 2007-04-23
I have not had one issue w/ 6.06LTS on the server...  BUT, I will also throw in CentOS5...  Very impressed with that one...

---

### Post by plb on 2007-04-23
Debian etch.

---

### Post by jinx099 on 2007-04-23
So nobody recommends I install Fesity on my server?  I will probably go with Debian etch as recommended and try to figure out Xen.  Anyone have a good Xen on Etch howto?

---

### Post by kerry_s on 2007-04-23
> **jinx099 said:**
> So nobody recommends I install Fesity on my server?  I will probably go with Debian etch as recommended and try to figure out Xen.  Anyone have a good Xen on Etch howto?

Try browsing here, i remember seeing it-> [http://forums.debian.net/viewforum.php?f=16&sid=a319b4d46fee042e4308b339e4220e42](http://forums.debian.net/viewforum.php?f=16&sid=a319b4d46fee042e4308b339e4220e42)
i'm just to tired to look through all the threads.

---

### Post by Pobega on 2007-04-23
> **jinx099 said:**
> So nobody recommends I install Fesity on my server?  I will probably go with Debian etch as recommended and try to figure out Xen.  Anyone have a good Xen on Etch howto?

Honestly, I would never recommend Ubuntu for a server platform, even with Dapper's long time support. Ubuntu is stable enough for home use, but nowhere near stable enough for server use; If you want a server go with a distro that specializes in servers, like Debian or a BSD.

---

