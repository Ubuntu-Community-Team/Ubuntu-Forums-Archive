---
title: "How would you go about becoming a Linux Administator?"
date: 2011-09-11
forum: Programming Talk
---

### Post by x-D on 2011-09-11
Hey, I was just wondering, I was thinking that maybe a career path I might to go down the lines of would be becoming a Linux Administrator.

Does anyone here know what I should learn/ be able to do to become one. I am decent with bash and know my way around Python, so if anyone can lead me to anything, I would be very grateful.

Also, could someone show me some syntax or something, of a time when Python is actually useful to Admins, because I have heard it can be, but am unsure of when this is likely to be of use.

Thanks in advance,

x-D :guitar:

---

### Post by dwhitney67 on 2011-09-11
Consider getting a certification... [http://www.redhat.com/certification/rhce/](http://www.redhat.com/certification/rhce/)

---

### Post by Senesence on 2011-09-11
Find someone who can help you get your foot in the door (an entry level support gig ... I realize that this is easier said than done, especially in this economic environment, but experience is still essential).

The fact that you know bash and python matter, but ultimately, it's all about being able to support the kind of software that is actually used in one company or another.

So, whatever software is actually used in company X for its day to day activities, learn that, all the problems that can happen with that, and how to fix them.

Some common systems that are used in sys admin circles:

Nagios.
Puppet.
OpenLDAP.

Knowing those should generally help.

Although, before you buckle down and invest a serious swath of your time/energy to study those, and other systems, you might want to think about what the market will look like for system administrators a few years down the line.

There are many companies, google being the most prominent, which are offering "cloud services", where a lot of things that were previously done by system admins are now being done "in the cloud", automatically (Chrome OS is definitely not something a "super user" would even consider , but for most people, who tend to live in the browser, it's definitely the future).

Everything is moving to the web, and therefore "the cloud" - so, since you already know Python, you might want to think about learning Google App Engine, or some other "cloud service api".

---

### Post by x-D on 2011-09-11
> **Senesence said:**
> Find someone who can help you get your foot in the door (an entry level support gig ... I realize that this is easier said than done, especially in this economic environment, but experience is still essential).

The fact that you know bash and python matter, but ultimately, it's all about being able to support the kind of software that is actually used in one company or another.

So, whatever software is actually used in company X for its day to day activities, learn that, all the problems that can happen with that, and how to fix them.

Some common systems that are used in sys admin circles:

Nagios.
Puppet.
OpenLDAP.

Knowing those should generally help.

Although, before you buckle down and invest a serious swath of your time/energy to study those, and other systems, you might want to think about what the market will look like for system administrators a few years down the line.

There are many companies, google being the most prominent, which are offering "cloud services", where a lot of things that were previously done by system admins are now being done "in the cloud", automatically (Chrome OS is definitely not something a "super user" would even consider , but for most people, who tend to live in the browser, it's definitely the future).

Everything is moving to the web, and therefore "the cloud" - so, since you already know Python, you might want to think about learning Google App Engine, or some other "cloud service api".

Hello, and thank you for the replies you two. To be honest I don't like this Cloud Stuff, but do you really think that this is the way forwards? And how can Python be used in Administration, to me it's like a general purpose language, in ways.

---

### Post by WitchCraft on 2011-09-11
> **x-D said:**
> Hey, I was just wondering, I was thinking that maybe a career path I might to go down the lines of would be becoming a Linux Administrator.

Does anyone here know what I should learn/ be able to do to become one. I am decent with bash and know my way around Python, so if anyone can lead me to anything, I would be very grateful.

Also, could someone show me some syntax or something, of a time when Python is actually useful to Admins, because I have heard it can be, but am unsure of when this is likely to be of use.

Thanks in advance,

x-D :guitar:

Start with administering your own server.
```

intranet file server with LDAP
smb server (experiment with windows shares)
printer server (CUPS, experiment with both Windows and Linux)
saned (network scanning)
ssh / sshfs (remote administration)
www server with PHP / Java / mono / Python-Django
mailserver / with LDAP
DNS server (bind9 DLZ with PostGre/MySQL)
permission management
database management
intrusion detection

- backup tools:
rsync
bacula

- database backup and restore utilities

```

and learn PERL, the traditional Linux/Unix admin scripting language


Perhaps you might want to get a certificate as SQL database administrator instead ;-)
Oracle, MySQL or MS-SQL are the big players, also starrings are Sybase, DB2, SAP/R3 .

My tip would be to learn to be an Oracle or MySQL DB admin, because that way you're independent of what happens in the future to Windows/Microsoft and/or Linux.

---

### Post by x-D on 2011-09-11
> **WitchCraft said:**
> Start with administering your own server.
```

intranet file server with LDAP
smb server (experiment with windows shares)
printer server (CUPS, experiment with both Windows and Linux)
saned (network scanning)
ssh / sshfs (remote administration)
www server with PHP / Java / mono / Python-Django
mailserver / with LDAP
DNS server (bind9 DLZ with PostGre/MySQL)
permission management
database management
intrusion detection

- backup tools:
rsync
bacula

- database backup and restore utilities

```and learn PERL, the traditional Linux/Unix admin scripting language


Perhaps you might want to get a certificate as SQL database administrator instead ;-)
Oracle, MySQL or MS-SQL are the big players, also starrings are Sybase, DB2, SAP/R3 .

My tip would be Oracle or MySQL DB admin, because that way you're independent of what happens in the future to Windows/Microsoft and/or Linux.

I don't know really, I mean, I guess I'd like to do either the more traditional Administration, or the SQL-type Administration. What are the pros and cons of each one. And that code that you put in your last post? Was that even code :lolflag:?

Cheers,

x-D :guitar:

---

### Post by Senesence on 2011-09-11
> **x-D said:**
> Hello, and thank you for the replies you two. To be honest I don't like this Cloud Stuff, but do you really think that this is the way forwards? And how can Python be used in Administration, to me it's like a general purpose language, in ways.

Yea, "Cloud Stuff" is not my favorite thing either; I like to have local resources that I can use whenever I want, however I want - there are also personal privacy issues to consider.

However, I think that businesses would prefer to further commoditize IT, to the point where they can just buy it as a service from some central distributor.

In 90% of the cases, buying Chromebooks for all your employees, and connecting them to a set of reliable google services is a lot cheaper than buying full fledged laptops, and building a local infrastructure that someone will actually have to maintain.

That's just the business perspective. So, yea, I think things are generally moving in that direction.

Regarding Python in the sys-admin world, or any other "general-purpose" language:

It's mostly just used as an automation tool - so, you have a command that you want to run on different machines, with slightly different parameters that depend on the state of some other system -> A Python script is probably a good fit there.

If you have to convert data from one format to another, that too is something that you could probably do with a small python program.

Stuff like that, I would think.

---

### Post by x-D on 2011-09-11
> **Senesence said:**
> Yea, "Cloud Stuff" is not my favorite thing either; I like to have local resources that I can use whenever I want, however I want - there are also personal privacy issues to consider.

However, I think that businesses would prefer to further commoditize IT, to the point where they can just buy it as a service from some central distributor.

In 90% of the cases, buying Chromebooks for all your employees, and connecting them to a set of reliable google services is a lot cheaper than buying full fledged laptops, and building a local infrastructure that someone will actually have to maintain.

That's just the business perspective. So, yea, I think things are generally moving in that direction.

Regarding Python in the sys-admin world, or any other "general-purpose" language:

It's mostly just used as an automation tool - so, you have a command that you want to run on different machines, with slightly different parameters that depend on the state of some other system -> A Python script is probably a good fit there.

If you have to convert data from one format to another, that too is something that you could probably do with a small python program.

Stuff like that, I would think.

Thanks for the ideas here, everybody. So it seems, if I really want to do this, then I would need to learn Perl. Bearing in mind, I've heard of Perl, but have no idea on any Syntax etc, what do I need? Is it a dynamic language, if so, then where can the interpreter be obtained from? Also, does anyone know of any good resources.

Thanks again, for your help and time!

---

### Post by WitchCraft on 2011-09-12
> **x-D said:**
> Thanks for the ideas here, everybody. So it seems, if I really want to do this, then I would need to learn Perl. Bearing in mind, I've heard of Perl, but have no idea on any Syntax etc, what do I need? Is it a dynamic language, if so, then where can the interpreter be obtained from? Also, does anyone know of any good resources.

Thanks again, for your help and time!

You need to search google for the words perl and tutorial.

---

### Post by juancarlospaco on 2011-09-12
On some things Admins still have some resistence to new things,
for example i prefer Zenoss Core instead of Nagios, i prefer Python instead of Perl,
i replaced Puppet with Fabric (but that one is a Python thingy),
if  i have to make a non-X.org UI for my scripts i use HTML5 instead of NCurses.

---

### Post by JupiterV2 on 2011-09-13
I've seen no mention of Tcl/Tk. Does it get used for sysadmin any more?

---

### Post by juancarlospaco on 2011-09-13
I used Tk, but it gets superseeded by HTML5, for me...

---

