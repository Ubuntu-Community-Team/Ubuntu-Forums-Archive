---
title: "Hard to describe PHP issues."
date: 2008-09-26
forum: New to Ubuntu
---

### Post by fatgeek on 2008-09-26
I'm trying to setup and run [RUTV]("http://linux.softpedia.com/get/Office/News-Diary/RUTV-40155.shtml") and I'm having some issues.  It requires PHP be installed.  It also requires CURL, PDO, XMLRPC, DOM.  I was able to add PHP and I think I installed the modules correctly.  

When I try and run the script, or any other PHP for that matter, I get the following error:

```
PHP Fatal error:  PDO: driver sqlite2 requires PDO API version 20060511; this is PDO version 20060409 in Unknown on line 0
PHP Fatal error:  Unable to start SQLite module in Unknown on line 0

```

The version I have installed seems to be up to date and the requested version is from 2006.  Something here is simply not making sense to me.  Any help would be appreciated.

---

### Post by Peter09 on 2008-09-26
There are two version of PHP, one is designed to run from the command line and command line scripts, the other is designed to be run within a web environment, with apache for instance. Which one do you want, and which one have you got. Go check in synaptic :)

---

### Post by fatgeek on 2008-09-26
I wasn't aware of that.  How would I tell the difference?

---

### Post by Peter09 on 2008-09-26
In synaptic do a search on php5, you can see all the additional modules there. php5-cli is the command line interpreter.

---

### Post by fatgeek on 2008-09-26
Yeah, I already had it installed.

---

