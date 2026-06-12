---
title: "Best way to download files from internet using bash"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by Anton_Sack on 2013-09-19
Hi there,

I am currently installing my ubuntu server (13.04). Doing so, I need to download several drivers from the internet using bash. I know that I could use wget but depending on the target urls it might be pretty horrible to type in the complete link. How do you guys do this?

Cheers

---

### Post by Lars Noodén on 2013-09-19
[wget](http://manpages.ubuntu.com/manpages/raring/en/man1/wget.1.html) would definitely be the way to grab files from the web using a script.  Another option would be to install [curl](http://manpages.ubuntu.com/manpages/quantal/en/man1/curl.1.html) but the syntax is not going to be that different.  If you have a problem with URLs in wget you will have the same problem with curl.  Can't you just cut and past the URL into the terminal?  That usually works for me though for some links I have to wrap them in quotes ""

---

### Post by buzzingrobot on 2013-09-19
If the servers offers FTP, the ncftp client is still around.  Kind of a command line browser interface.

I *think* a text-based browser like lynx can handle downloads, too. (Would be handy to have on a server, too.)

But, for just a one-off download of several files, I'd just use wget.

---

### Post by newb85 on 2013-09-19
Are you ssh-ing into the server, or working on the machine itself?

---

### Post by 3rdalbum on 2013-09-19
There are text-mode browsers available. W3M, Links2 (which can run in graphical mode without X, just start it with the -g parameter) and eLinks are good options and should work fine for the purpose of browsing around to a driver download page, and then downloading a driver.

---

### Post by Lars Noodén on 2013-09-19
> **buzzingrobot said:**
> If the servers offers FTP, the ncftp client is still around.  Kind of a command line browser interface.

I *think* a text-based browser like lynx can handle downloads, too. (Would be handy to have on a server, too.)

But, for just a one-off download of several files, I'd just use wget.

[lynx ](http://manpages.ubuntu.com/manpages/raring/en/man1/lynx.1.html) is also a great choice.  It does downloads, too, of course.  But it's also good for browsing through other web pages to get to the link you need to download.

---

