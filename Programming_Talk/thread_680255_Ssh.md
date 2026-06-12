---
title: "Ssh"
date: 2008-01-27
forum: Programming Talk
---

### Post by sdmike on 2008-01-27
At my work I can't download any programs so I can SSH into my home computer to work on anything.

Is there a way I can use a website that allows you to SSH on it?

---

### Post by Nano Geek on 2008-01-27
Do you mean connect to a website through your home computer?

If so just run ssh using** -x** and once connected to your sshed computer, run **firefox <website_name>** and you'll connect through your home computer to the site.

---

### Post by Joeb454 on 2008-01-27
asjd, I believe he means is there a website that allows you to SSH into a remote PC.

Such as [www.mibbit.com]("http://www.mibbit.com") which allows you to connect to IRC servers without having an IRC client

EDIT: As far as I'm aware there is no such website, I think it would be too insecure. Though I can't be certain.

---

### Post by Acglaphotis on 2008-01-27
I think he meant that he wants to use ssh through a browser. I don't know how to do this except for a VNC java applet.

---

### Post by Nano Geek on 2008-01-27
I guess you two are right.

And I agree that you shouldn't try to use a website to ssh. 
For all you know, they could be recording everything you type.

---

### Post by stroyan on 2008-01-27
If your home system is running ubuntu and you are willing to run a web server on it, then you could use the 'jta' package which provides an ssh capable terminal as a java applet.  You would then visit a link on your web site and run a java applet in a local web browser that makes a secure ssh connection to your system.

---

### Post by Joeb454 on 2008-01-28
True that could work, though it might be a bit complicated just to SSH into your own PC, though if you really need to I guess that'd be a fairly decent way...mainly because you'd know the website was your own

---

### Post by Lux Perpetua on 2008-01-28
In the absence of an SSH client on the local machine, that seems like a pretty good way...

---

### Post by FaBi3ttO on 2008-01-28
Otherwise you can configure your home ssh server to listen on port 80, then follow this guide to bypass the firewall
[http://www.mtu.net/~engstrom/ssh-proxy.php]("http://www.mtu.net/~engstrom/ssh-proxy.php")

My 2 cents,

---

