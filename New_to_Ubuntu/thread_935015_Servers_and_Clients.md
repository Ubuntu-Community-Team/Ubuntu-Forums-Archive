---
title: "Servers and Clients?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by fgn89 on 2008-10-01
Is there a server version of Ubuntu?

If there is, how do I get one?

And what actually, is the difference between a Ubuntu server and a Ubuntu client? Assuming there is a server version of Ubuntu, of course.

---

### Post by vantsochev on 2008-10-01
[http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html) 

This should help u.

:P

---

### Post by fgn89 on 2008-10-01
Oh.. I always thought Debian and Ubuntu were.. from different.. 'developers'. Thanks :P

Mhm..

Haha, but can anyone give me a general overview? Over what servers have over clients..

'cause I'm sort of debating this over with my dad. He keeps claiming I should stick with a server version of Linux, to test some functions.

I insist, that there won't be much of a difference, in terms of functionality, between servers and clients. 

What a server can do, can't a client do as well, if only not as well?

'cause, I have this problem.. 

Have asked the question(s) in other threads as well.

I just can't access a database, which is on my Linux server, shared using samba, from my windows client.

My dad insists my copy of Linux is the problem, can anyone clarify this for me?

Sorry if I'm being vague, if anyone needs more information to answer..

Thanks in advance. =>

---

### Post by superprash2003 on 2008-10-01
by database i presume you mean something mysql etc.. you need to first ensure that no firewall is blocking anything.. check your iptable rules.. also ensure that both pcs are able to ping each other..
read this for server vs desktop [http://ubuntuforums.org/showthread.php?t=225546](http://ubuntuforums.org/showthread.php?t=225546)
[http://ubuntuforums.org/showthread.php?p=5611394](http://ubuntuforums.org/showthread.php?p=5611394)

server version is basically meant only for server purposes.. uses less CPU power, comes pre installed with LAMP .

---

### Post by hyper_ch on 2008-10-01
(1) Yes, debian and ubuntu is developped individually

(2) Yes, there is a server version

(3) Yes, there are differences... main difference is, that the server version installs only a base system and no gui and that the server version has a different kernel, aimed at server tasks.

---

