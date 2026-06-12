---
title: "Slim down ubuntu server install after installation (on vps)"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by patrickallo on 2013-11-02
My VPS only lets me install preconfigured templates, but no custom installation.

Since I'd like to follow the [Ars Technica web Served series]("http://arstechnica.com/series/web-served/"), I'd rather just have a minimal installation with only open ssh server.

Is there a straightforward way to slim down an existing standard installation? (Or at least a good list of packages that can safely be uninstalled).

Thanks!

---

### Post by DuckHook on 2013-11-02
No straightforward subtraction method that I'm aware of. Due to the nature of dependencies, it's easy to add things, but hard to subtract. I have the same dilemma: because I like monkeying around with different distros, I install them on VMs. But distros like Knoppix install tons of bloatware that eat up disk space when all I want to do is explore the basic utilities, file structures, etc. I tried nuking the apps individually, but aside from this being a deathly boring and repetitive exercise, it was fruitless because uninstalling would often leave orphaned dependencies behind. This is because most uninstall scripts err on the side of caution and assume that the dependency libraries/apps may be used by other programs. Libraries just take up disk space, but unneeded services, modules, etc. are an attack vector for malware, never mind draining your system resources, so there's a big incentive to get rid of them. Unfortunately, there's no easy way except to painstakingly pick through them. Wish I had better news for you.

Surely, your VPS has a bare-bones or least bloated template? I can't believe that they would only offer GUI-stuffed obese templates. After all, most people run VPSes only because they want a server. If you start with their least bloated offering, it may not be that hard to back out the junk.

---

### Post by ian-weisser on 2013-11-02
It would help if you showed us some of those templates.

For example, Ubuntu Server includes the *tasksel* package and command for precisely the purpose you want.
But we don't know if any of those template include Ubuntu Server.

---

### Post by sandyd on 2013-11-02
> **patrickallo said:**
> My VPS only lets me install preconfigured templates, but no custom installation.

Since I'd like to follow the [Ars Technica web Served series]("http://arstechnica.com/series/web-served/"), I'd rather just have a minimal installation with only open ssh server.

Is there a straightforward way to slim down an existing standard installation? (Or at least a good list of packages that can safely be uninstalled).

Thanks!
If your using Ubuntu 12.04, the below should remove all the extra stuff on a _standard_ Ubuntu 12.04 OpenVZ VPS
```

apt-get purge apache2* bind9 samba*
```

The rest of the stuff takes up little memory and is not worth removing

---

### Post by DuckHook on 2013-11-02
I thought *tasksel* was just a ncurses version of a stripped-down Software Centre. Will it cleanly and thoroughly back out whole installed packages? I suspect that it suffers from the same easy-to-add hard-to-subtract problem that plain old apt suffers from, but don't really know enough about it to be sure.

I don't know which VPS service OP is using, but when I last looked into such providers, what they meant by "templates" were actual pre-built virtual disk images. You could only get the "web server + blogging template", or the "mail server/exchange template", etc. Trouble was each "template" came with DE, GUI-based admin tools, tons of fluff, cruft and bloat. Admittedly, I wasn't looking seriously, almost all of the choices were Windows-based and this was some time ago, so my knowledge is obsolete. I do recall a choice for a bare-bones system though, so don't know why OP wasn't given such a choice too.

@OP

Have you tried contacting your VPS provider directly to ask for a bare-bones image?

---

### Post by sandyd on 2013-11-02
> **DuckHook said:**
> I thought *tasksel* was just a ncurses version of a stripped-down Software Centre. Will it cleanly and thoroughly back out whole installed packages? I suspect that it suffers from the same easy-to-add hard-to-subtract problem that plain old apt suffers from, but don't really know enough about it to be sure.

I don't know which VPS service OP is using, but when I last looked into such providers, what they meant by "templates" were actual pre-built virtual disk images. You could only get the "web server + blogging template", or the "mail server/exchange template", etc. Trouble was each "template" came with DE, GUI-based admin tools, tons of fluff, cruft and bloat. Admittedly, I wasn't looking seriously, almost all of the choices were Windows-based and this was some time ago, so my knowledge is obsolete. I do recall a choice for a bare-bones system though, so don't know why OP wasn't given such a choice too.

@OP

Have you tried contacting your VPS provider directly to ask for a bare-bones image?
Most providers dont have minimal Ubuntu 12.04 images, they come with apache2, bind9 and samba installed. *some* have Debian minimal. Two that I know of have removed them in the last few months or so
[http://199.241.30.127/img/scrn/ubuntureinstalloptions.png](http://199.241.30.127/img/scrn/ubuntureinstalloptions.png)

Ask them to take Ubuntu 12.04 from [http://wiki.openvz.org/Download/template/precreated](http://wiki.openvz.org/Download/template/precreated)
If they have a too-old kernel, they will have to enter your VPS after creating it, and add this ppa -> [https://launchpad.net/~izx/+archive/ovz-libc](https://launchpad.net/~izx/+archive/ovz-libc)

---

### Post by patrickallo on 2013-11-02
@sandyd: I'm going with your suggestion of just removing apache2 bind9 and samba
I guess that should be fine, since my main concern is to get rid of apache in favour of nginx

@DuckHook: The only available bare-bones image is a minimal install of Centos 6.2

---

