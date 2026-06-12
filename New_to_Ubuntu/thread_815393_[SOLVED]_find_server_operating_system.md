---
title: "[SOLVED] find server operating system"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-06-01
hey,

how can I find out what operating system a specific site is using?

is there a command or service that I can use to find out?

thanks

---

### Post by sayakb on 2008-06-01
Try to access the server through [ftp://IP.ADD.RE.SS](ftp://IP.ADD.RE.SS) of the server. If you enter a Unix like architecture, then you can say it's not Windows :)
FTP works if the port 21 of the remote server is open.

---

### Post by newbuntuxx on 2008-06-01
I did, and it prompted me to enter a  user name a password. so i entered gibberish, then it took me to a white blank page, and it didn't say anything about the server's architecture.

---

### Post by Wicca on 2008-06-01
Hi,

Visit [http://www.netcraft.com]("http://www.netcraft.com"). You can do a query there.

For instance, check download.microsoft.com. Fun!:popcorn:

---

### Post by sayakb on 2008-06-01
> **newbuntuxx said:**
> I did, and it prompted me to enter a  user name a password. so i entered gibberish, then it took me to a white blank page, and it didn't say anything about the server's architecture.

That means you were not provided access. Otherwise, you should have been directed to the online file/archives viewer.

---

### Post by newbuntuxx on 2008-06-01
> **Wicca said:**
> Hi,

Visit [http://www.netcraft.com]("http://www.netcraft.com"). You can do a query there.

For instance, check download.microsoft.com. Fun!:popcorn:

thanks, thats very useful. BUT, is download.microsoft.com using linux? :| Am I reading the results properly?

---

### Post by newbuntuxx on 2008-06-01
actually, its sort of confusing! 

when you enter download.microsoft.com you get the following latest results

```

Netblock Owner	IP address	OS	Web Server	Last changed
Computer Sciences Corporation CSC, Managed Services and Web Hosting 266 Second Avenue Waltham MA US 02451	4.23.54.124	Linux	Microsoft-IIS/6.0	31-May-2008
```


So, the operating system is linux, and the web server is IIS. Does that make sense? I didn't think you can install IIS on linux?

any clarification is appreciated!

---

### Post by Wicca on 2008-06-01
> **newbuntuxx said:**
> thanks, thats very useful. BUT, is download.microsoft.com using linux? :| Am I reading the results properly?

Netcraft is a serious organization and based many, many queries I did I happen to think, yes.

Besides that: It is a public secret that MS uses Linux , mainly on their NAT-routers (security? ;)) , but even some Linux servers do exist. Check 'microsoft.com' to query all of their servers.

---

### Post by Wicca on 2008-06-01
> **newbuntuxx said:**
> actually, its sort of confusing! 

when you enter download.microsoft.com you get the following latest results

```

Netblock Owner	IP address	OS	Web Server	Last changed
Computer Sciences Corporation CSC, Managed Services and Web Hosting 266 Second Avenue Waltham MA US 02451	4.23.54.124	Linux	Microsoft-IIS/6.0	31-May-2008
```


So, the operating system is linux, and the web server is IIS. Does that make sense? I didn't think you can install IIS on linux?

any clarification is appreciated!

Well I can't clarify it. But this is Microsoft and I guess a lot is possible then. If you invented and made IIS, it is not too difficult to modify an Open  Source OS to your needs to let it host your software?

Edit: Or they did find out about Wine :lolflag:

---

### Post by Wicca on 2008-06-01
I just found out why on Netcraft it seems some MS servers are running IIS on Linux.

In short: To avoid DDOS attacks they use 'caching servers' from Akamai, and these are running Linux. These respond to the OS query while the MS server itself runs IIS on Windows.

See for more information:
[http://news.netcraft.com/archives/2003/08/17/wwwmicrosoftcom_runs_linux_up_to_a_point_.html]("http://news.netcraft.com/archives/2003/08/17/wwwmicrosoftcom_runs_linux_up_to_a_point_.html")

So.... although MS doesn't run Linux on their servers, they do use a Linux-based system to protect themselves. =D>

---

### Post by cariboo on 2008-06-01
Microsoft uses Akamai to host their downloadable files. Akami uses Linux. If you search slashdot.org you should be able to find out all you want to know.

Jim

---

### Post by newbuntuxx on 2008-06-02
i see. Nonetheless, it still, in a way, shows M$'s incompetence; having to rely on Akamai's linux servers.

---

