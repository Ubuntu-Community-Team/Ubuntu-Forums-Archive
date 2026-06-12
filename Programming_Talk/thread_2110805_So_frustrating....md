---
title: "So frustrating..."
date: 2013-01-31
forum: Programming Talk
---

### Post by tehcavil on 2013-01-31
Ugh. webhost I paid good money for is slow. on top of that, there's no ffmpeg on the server. I'm making a video site so How am I supposed to convert the videos that users upload? And I say OK ill compile it myself but guess what theres no C compiler installed!. Then I say ok ill transfer a static binary that I downloaded but when Its on the server and I try to run it it gives me a segfault and says "fatal: kernel too old".

EDIT: apparently I lied earlier. It was early in the morning, actually the host is running "Cent OS 5.5 32 bit PAE" (seems more reasonable). In any case kernel 2.6 is apparently too old for the latest (and only) static binaries I could find online for 32 bit linux.

I thought about rolling my own server, but I really don't have the money right now, maybe if the site is somewhat successful I'll have enough money to get an my own and do whatever I want.

Question is, does anyone know how I can get ffmpeg or avconv working  with support for converting videos from any format to h.264/mp3 .mp4  videos so I can use it in my video site backend?

---

### Post by dwhitney67 on 2013-01-31
> **tehcavil said:**
> 
Turns out the host is running Red Hat 4.1.


RHEL 4 has been deprecated for a while now; there are no more security updates for it, and and its use is frowned upon because of inherent security issues.

You should choose a different OS, such as RHEL 6 or CentOS 6, or other Linux distro that is up to date.

IMO, cancel your contract with the Web Server service provider, or ask them to upgrade their OS.

---

### Post by Bucky Ball on 2013-01-31
The use of descriptive thread titles will give you a better chance of getting help. This one's generic and says nothing about your question. It can be changed by editing the first post and clicking Go Advanced.

Also posting in a Red Hat forum might help if that is what you're using.

---

### Post by ikt on 2013-01-31
> **tehcavil said:**
> working on red hat 4.1?

I'm not sure I believe they're running 4.1

[http://en.wikipedia.org/wiki/Red_Hat_Linux#Version_history](http://en.wikipedia.org/wiki/Red_Hat_Linux#Version_history)

4.1 (Vanderbilt), February 3, 1997 (Linux 2.0.27)

This is equivalent to having a server running windows NT4. (or a person saying they still run Windows 98)

Not only hilariously out of date, but if the PC is of the same era any video conversion attempts will take months to complete.

Personally I'd change webhost instantly and demand a refund.

---

### Post by dwhitney67 on 2013-01-31
> **ikt said:**
> I'm not sure I believe they're running 4.1

My office supported customers up until last year that were still supporting legacy systems that relied on RHEL4.

Just because an OS is old, does not necessarily mean that it is obsolete.  RHEL5, for instance, is still supported.

---

### Post by ikt on 2013-01-31
> **dwhitney67 said:**
> 
Just because an OS is old, does not necessarily mean that it is obsolete.  RHEL5, for instance, is still supported.

Anyone pro-actively running an OS from 1997 on production servers should be fired.

RHEL5 was released in 2007, same year as Windows Vista, not on the same level at all.

---

### Post by tgalati4 on 2013-01-31
Windows98 was much better than Windows3.  It's all relative.  But I agree, change your webhost immediately, or better yet, find an old machine and run your own server.  It's really not that difficult.

---

### Post by KdotJ on 2013-01-31
I agree with tgalati4, cancel your contract and just build your own. Its simple (and a great learning experience) and you would have full control and as much space as you want.

---

### Post by dwhitney67 on 2013-01-31
> **KdotJ said:**
> I agree with tgalati4, cancel your contract and just build your own. Its simple (and a great learning experience) and you would have full control and as much space as you want.

You guys forgot to mention... high-speed internet access is required and a business service plan is required.  A lot of ISPs do not allow personal (home) service plans to be used to host a Web Site.

The Web Site site must also be available 24x7, be updated for security patches, and seamlessly be switched over to an alternate system should the first fail due to a h/w issue.

For these reasons, many individuals or small companies, who tend to operate on a string budget, opt to use an outside vendor.

---

### Post by KdotJ on 2013-01-31
This is very true, and the OP didn't really specify their business needs
 However, in some cases the cost of all these extras make a big hit in the price you pay...

---

### Post by Zugzwang on 2013-01-31
... let's also add that the OP would also need to pay for electricity (which is expensive in some countries), proabably more than his/her shared server costs right now, and has good fire insurance that is fine with having a computer running while you are absent. They *can* sometimes catch fire after a defect on the high-voltage side.

---

### Post by MadCow108 on 2013-01-31
rh**e**l 4 is still in its extended life stage until 2015, I doubt the host is really running rh4 (=not the enterprise variant)
so it is old but not unusual to still be in production use.

if you want full control you can get a cloud instance from amazon, hp, rackspace or whatever other services there are. You usually have root rights on these and can run various operating systems including ubuntu.
These have the advantage that you can pull up a high cpu power instance on demand and scale down to cheaper instances when you don't need to convert videos.

---

### Post by tehcavil on 2013-01-31
Specifically, I need to know where I can find a 32-bit statically compiled ffmpeg binary with x264/lame/h.264 built in that works on kernel 2.6.18.

---

### Post by SeijiSensei on 2013-01-31
In the RedHat world, [rpmfind.net]("http://rpmfind.net/linux/rpm2html/search.php?query=ffmpeg&submit=Search") is your friend.  

In general, packages like ffmpeg which may include software that might run afoul of patents or copyrights are not distributed directly from RedHat or CentOS.  There are third-party repositories like ATrpms or RPMfusion that provide these packages.  It's the same situation as the "restricted-extras" for Ubuntu.

---

