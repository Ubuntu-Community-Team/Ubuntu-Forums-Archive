---
title: "lftp problem"
date: 2007-04-29
forum: Programming Talk
---

### Post by mesh2005 on 2007-04-29
I have three websites, I can connect successfully to two of them using lftp. I can connect to the third website but I can't ls or issue any FTP command, it goes forever after I press enter and no response is returned. 
I use Ubuntu Dapper 64-bit edition

---

### Post by amo-ej1 on 2007-04-30
contact the administrator ;-)

or try a more straightforward ftp client like 'ftp'  this will give you a bit more verbosity which hopefully allows you do diagnose the problem

---

### Post by mesh2005 on 2007-05-01
thank you, I used FTP and wget. FTP works fine on for this domain, I have another question: I used to issue the comman lftp -c 'command', is there any way to pass a command using ftp without the interactive shell?

---

### Post by cwaldbieser on 2007-05-01
> **mesh2005 said:**
> thank you, I used FTP and wget. FTP works fine on for this domain, I have another question: I used to issue the comman lftp -c 'command', is there any way to pass a command using ftp without the interactive shell?

I am not sure you can pass commands to "ftp" other than using a program like "expect".  You might be able to use a program like "curl" depending on what you want to do.  Python has the module "ftplib" (standard library section 11.7.1) that pretty much lets you perform the standard command set.  Other scripting languages and tools are widely available.

---

