---
title: "Ubuntu vs CentOS"
date: 2009-09-29
forum: Recurring Discussions
---

### Post by swordfishRU on 2009-09-29
Hi all!

Now I'm looking for one enterprise distribution for servers and desktops. And I'm choosing between Ubuntu and CentOs. 
Ubuntu is the best desktop and server solution, with many installations and good support. But there is no free systems management tool - Landscape server is not open and free.
CentOs - I've never worked with it before and I can't say something about it. But for CentOs there is open source system management tool - Spacewalk.

So, what would you advise me?

---

### Post by Giblet5 on 2009-09-29
Why not use [Landscape]("http://www.ubuntu.com/news/landscape-system-management-tool")?

You can probably port Spacewalk to Ubuntu, but Spacewalk isn't very Debian-centric...

---

### Post by swordfishRU on 2009-09-30
Why? I don't wanna to use proprietary software. Now I'm thinking about binding ubuntu and puppet.

---

### Post by FunkyRes on 2009-09-30
IMHO CentOS is better for servers.
Ubuntu is better for desktops.

I think this is one of those things where you aren't going to find a distribution that does both exceptionally well because they are so different.

If installing CentOS, unless you know you need sendmail, replace it with postfix - as root

yum install postfix system-switch-mail
system-switch-mail (choose postfix)
yum remove sendmail

If you want sudo in CentOS to behave like sudo in Ubuntu, install sudo, add yourself to the wheel group, and set up the sudo config file like the ubuntu config (making sure to use wheel group).

Anyway, CentOS has a very good implementation of SELinux, which IMHO gets in the way for desktop but adds security for servers, it has LVM by default and excellent GUI for administrating LVM, etc.

The PHP is dated but you can build newer php (I have src.rpm if you need it) but otherwise it is an excellent server distribution. I think it has good ruby support in EPEL but I don't do ruby.

With respect to desktops, the desktop software in CentOS is too dated to install a lot of the modern multimedia related stuff w/o doing a lot of compiling yourself, Ubuntu is better in that respect.

That's my two cents worth.

---

