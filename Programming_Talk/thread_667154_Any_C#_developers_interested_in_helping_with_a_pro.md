---
title: "Any C# developers interested in helping with a project?"
date: 2008-01-14
forum: Programming Talk
---

### Post by st4rdr1ft3r on 2008-01-14
I'm starting to write a server administration application, using c#. It'll be cross platform (linux/windows/bsd) and the basis behind the idea is using addins as controller modules and certain layers of abstraction.

For example, you have an abstraction layer that implements the idea of a website so you can provide the application with some basic information (domain name, root directory, etc.) and it'll then hand this information onto the loaded controller for the web server which can then setup this website.

It'll run as a daemon which listens for xml to be sent to it for commands, which it then passes onto the appropriate controllers and they build up the return xml, which will allow eventually for a central daemon automate a group of servers by sending xml, or allow clients that connect to the daemons to get as indepth as they wish (only view websites, or descend into the actual server controller).

If anyones interested then let me know.

---

### Post by pmasiar on 2008-01-14
You would get better response if you mentioned what other open source and/or proprietary source experience you have. If this is your first serious project, I would strongly recommend first contributing to any existing project, to build credibility and gain skills.

---

### Post by st4rdr1ft3r on 2008-01-14
Well, I work as a software developer (recently looking after the network, firewalls, phone systems has been added to my task list also) but most of that code is simply in-house. I've done a (minute really) small amount on mono, main thing was adding application restarts for .NET 2 websites when App_Code files are modified. Messed about a little with elisa media centre. Nothing major.

I'm going to be working on this project anyway on company time as an aim to get infrastructure here more automated that it currently is, with management in a central point (well, 2 central points for failover).

---

### Post by achron on 2008-01-14
You might want to review your company's policy on the software you're looking to develop.  Every company I've worked for has a "Developed using our time or our hardware means we own it" kind of policy.

You'll still be able to find assistance with questions or issues here in the forums I'm sure, but I'd think anyone who might contribute in a serious manner would want the product to remain "open sourced" and not subject to future haggling by the legal eagles...

It sounds interesting, but is definitely outside my bailywick.

---

### Post by st4rdr1ft3r on 2008-01-14
I have an opensource friendly technical director and I demanded that this would be opensource, as I knew he would agree, so no worry there about it not being oss.

---

### Post by st4rdr1ft3r on 2008-01-31
If anyone is interested in looking at progress it is hosted in my svn, can browse it through:

[http://svn.digitalnetworks.co.uk/trunk/dryad/Dryad/](http://svn.digitalnetworks.co.uk/trunk/dryad/Dryad/)

Most of the work I've done so far has been in the Web and Dns controllers.

---

### Post by cprofitt on 2008-01-31
I will keep tabs on it, but I have not gotten in to the network aspects of C# yet.. my focus has been on database applications.

---

