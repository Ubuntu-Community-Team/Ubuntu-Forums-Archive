---
title: "another PHP ide holy grail"
date: 2008-06-19
forum: Programming Talk
---

### Post by bodselecta on 2008-06-19
Hi, I know that this has been posted a few times and I've googled numerous sites and looked through these forums, but I'm still really trying to find an excellent commercial and home ide/debugger for PHP. The ubuntu php eclipse page doesn't document remote debugging local sites.

For work, we're just about to install php in our stack and it's a pretty big company but missing a proper 'web' language compared to java etc. 
I'm developing on win xp and the servers are all AIX so I'm trying to find a reliable all in one ide/debugger with source control and code completion. We use myeclipse at work and I'd briefly tried out the php plugin but didn't have great success debugging local apache sites, though was straight forward running a php script. 
Maybe I didn't understand how the debug process properly worked, it seemed that you have to map an apache host or directory directive to the location of the files in your eclipse workspace project directory, or create your eclipse work folders in apache's htdocs, and both seemed a bit messy as there'd be lots of extra files directories lying around (for example cvs folders/files, project files etc) 
We'd have money to spend on licenses so I'd appreciate any advice both for software and how best to work.

From home I've just gotten into ubuntu, really enjoying it and have apache, mysql, php, tomcat, eclipse and jboss all installed, they've been installed separately and I didn't want to use the xampp package.
I prefer starting and controlling the servers separately and using the command line. I'm used to stop/starting tomcat/jboss from eclipse but not mysql and apache, I suppose I'm used to working in distributed environments.  
The xampp (and apache and mysql) preferences are part of the PHP External tools preferences in eclipse and wondered whether xampp has to be used if wanting to debug in eclipse on ubuntu or if you can startup everything on its own and still debug?
Any ideas or tips would be really welcome.
Cheers

---

### Post by jsmiith on 2008-06-19
I use komodo edit for most of my web scripting. It has excellent code intelligence and lots of other little things that make an ide great. I believe that komodo ide( not open source, cost ~ $299 ) has support for debuggers such as xdebug and for source code control.

---

### Post by bodselecta on 2008-06-20
thanks jsmith...
i've used the free komodo for perl before and thought it was actually pretty good. 
Is debugging remote php through apache straight forward?

To be honest I probably would prefer to go down the myeclipse route with pdt but haven't seen what it's debugging capabilities are like

---

### Post by xlinuks on 2008-06-20
> **bodselecta said:**
> thanks jsmith...
i've used the free komodo for perl before and thought it was actually pretty good. 
Is debugging remote php through apache straight forward?

To be honest I probably would prefer to go down the myeclipse route with pdt but haven't seen what it's debugging capabilities are like

By now we have NetBeans 6.1, the next release will be 6.5 . Sun is working hardly on bringing the best support for PHP on NetBeans which will probably be released later this years. They are even planning to have a separate download for NetBeans bundled with PHP support out of the box. Among other things "NetBeans 6.5 will include editing and debugging support for PHP, JavaScript (client & server), Ruby, and Groovy."

---

