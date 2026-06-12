---
title: "PHP SSH Client"
date: 2006-02-28
forum: Programming Talk
---

### Post by anaoum on 2006-02-28
Hello,

Does anybody know of a SSH client that is written in php?

thankyou

---

### Post by anaoum on 2006-03-01
anyone?

---

### Post by celloandy on 2006-03-01
Why would anyone do this?  PHP is primarily a server-side web application language, and is designed primarily to generate content to be output by a webserver to a browser.  While it's possible to write command-line apps in PHP, the language is certainly not designed for this purpose, and there would be better languages to use to do this.  Furthermore, PHP's interpreted, high-level language makes it less than ideal for the math operations involved in encrypting and decrypting data.  Perhaps I'm misunderstanding what it is that you want, but I would be very surprised that anyone would invest the effort to implement a full-scale SSH client in PHP.  There's simply no advantage to using this language for this particular task.

Andrew

---

### Post by harisund on 2006-03-01
What is it that you are looking for exactly? If you are simply looking for a SSH Client, you can find free ones for every operating system. 

Why the preference towards PHP alone? Any particular reason?

---

### Post by ger.kirill on 2008-12-07
You can get pure-php implemented ssh client at phpclasses.org - [http://www.phpclasses.org/browse/package/2477.html](http://www.phpclasses.org/browse/package/2477.html)

---

### Post by nevergolden on 2009-02-17
> **ger.kirill said:**
> You can get pure-php implemented ssh client at phpclasses.org - [http://www.phpclasses.org/browse/package/2477.html](http://www.phpclasses.org/browse/package/2477.html)

looking at the comments on that site...

[http://phpseclib.sourceforge.net/](http://phpseclib.sourceforge.net/)

seems to be better. supports ssh1 and ssh2 whereas the one you linked to only supports ssh1.

---

### Post by goldencontact on 2012-04-16
Hi,

I am also experiencing this issue, even this much later in time. To be specific, the issue that I am experiencing is that I am sitting at a desk of a company who have blocked port 22 outgoing (not a Net Cafe), a Server Management company. 

I need to SSH into my server.

So, what I need, is a Web Based (The part I believe wasn't clear) PHP/HTML/JS etc app that's running on Port 80/443, so I can still log in and run things on my web server. 

I have so far found:

Nix's Web Based SSH Manager
Shell in a box 

Both can be googled, the second is hosted on Google Code. Im a little surprised there arent more of these. Obviously this could be a securtiy risk, but a) so can a lot of things b) I need to work and c) a vague url hidden behind an apache login with some way to monitor login attempts (which I've never tried but is probably possible) will probably go most of the way to being mostly secure.

I'm getting my sysadmin to install both now, and I'll let you know in an hour or two if my server gets stolen as a result, or if I fall in love with a new Web App

From Golden

---

### Post by dwhitney67 on 2012-04-16
> **goldencontact said:**
> 
I need to SSH into my server.


Have you tried [FireSSH]("https://addons.mozilla.org/en-US/firefox/addon/firessh/?src=ss"), which is an addon for Firefox (err, Mozilla)?

---

### Post by goldencontact on 2012-04-17
Hi buddy thanks for the response, but here's what I mean:

I have a Terminal on my laptop. The reason I cannot use it, is that the Company I am contracting in has blocked outbound connections destined for port 22 from the network. 

Its super secure here.

So, Firessh would'nt work in this situation, as 1) I would have to configure the SSH server to serve on port 80 meaning I cant serve web pages on that port and 2) Im not sure (but i didnt check) if you can configure firessh to try to connect to a non-standard port.

But, outgoing connections going to port 80 are allowed on the assumption that they are going to a website.

So, I have tried a couple of Web Based clients (That run on the same box as the server, and are browser accessible on port 80/443)

The best one (I have found so far, in my opinion) is Ajaxterm .  Its great. I used it on Centos, which took 20 minutes to install, but i think its in the Ubuntu Repo, which makes it even quicker on 'buntu (which I have on my laptop).

Serves my purpose perfectly.

---

### Post by dharmavir on 2012-04-17
> **anaoum said:**
> Hello,

Does anybody know of a SSH client that is written in php?

thankyou

I think what you are looking for is GateOne:
[http://liftoffsoftware.com/Products/GateOne](http://liftoffsoftware.com/Products/GateOne)

Good luck. 
:-):popcorn:

---

### Post by riskable on 2012-04-29
Hi there, I'm the author of Gate One.  I thought I'd chime in and say that Gate One isn't written in PHP...  It is written in Python.  Having said that, it shouldn't matter from the perspective of this thread.  You can run it on port 443 (the default) just about anywhere and then SSH to whatever you want from there.

Since Gate One is its own web server there's no need for Apache + PHP at all.  Just start it up and you're good to go.

I'd be happy to answer any questions if you have any :D

---

### Post by SeijiSensei on 2012-04-29
Why can't you just configure your server's SSH daemon to listen on some other port besides 22?  Just edit /etc/ssh/sshd_config and change the "Port 22" declaration to some arbitrary high port like "Port 22222".  Then on your client, just run "ssh -p 22222 user@yourserver" to connect.

You'll obviously have to make sure that any firewall on your server's end is configured to accept TCP traffic on port 22222, or whichever port you choose.

---

### Post by CharlesA on 2012-04-29
> **goldencontact said:**
> Hi buddy thanks for the response, but here's what I mean:

I have a Terminal on my laptop. The reason I cannot use it, is that the Company I am contracting in has blocked outbound connections destined for port 22 from the network. 

Its super secure here.

You might want to note that we do not support bypassing any network security measures that are in place. You will have to talk to your IT department to get the matter resolved.

Closed.

---

