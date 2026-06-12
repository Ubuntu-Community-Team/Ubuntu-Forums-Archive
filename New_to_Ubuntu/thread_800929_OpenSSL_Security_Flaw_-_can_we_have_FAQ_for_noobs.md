---
title: "OpenSSL Security Flaw - can we have FAQ for noobs?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-05-20
Relating to this news story:

[http://www.security.itproportal.com/articles/2008/05/20/security-firm-confirms-serious-ubuntudebian-security-flaw/](http://www.security.itproportal.com/articles/2008/05/20/security-firm-confirms-serious-ubuntudebian-security-flaw/)


One of the reasons I want to switch to Linux is the lessened risk of spyware/viruses.

Is this security issues something we should worry about?


.

---

### Post by Joeb454 on 2008-05-20
Not really no. It's been fixed, that's all there is to it.

Please read the announcement (at the top of the forum main page - it's in blue) for more details :)

And for "noobs" most are unlikely to be using SSH for anything anyway ;)

---

### Post by neurostu on 2008-05-20
In order for your machine to be vulnerable you needed to have installed: openssh-server
openssh-server allows inbound connections to your machine over the ssh protocol. If you don't have this installed then any inbound connections will be ignored. 

> 
One of the reasons I want to switch to Linux is the lessened risk of spyware/viruses.


So the security issue was not an issue with linux, rather it was an issue with the ssh program.  This would be blaming windows for a security problem in Firefox.  Granted linux is great and has a lot of security features that make it more difficult to exploit, but if you are running bad code or have a malicious program installed the OS can only do so much to protect you. Ensuring that your machine is secure also depends on running well written programs, not just the OS.

Now i know that it is a little bit more complicated then that but for a noob the analogy should hold up just fine.

---

### Post by Sealbhach on 2008-05-20
Ok, thanks.

Sorry, I didn't see that blue bar.

So if I have any of:

Ubuntu 7.04: libssl0.9.8 0.9.8c-4ubuntu0.3
Ubuntu 7.10: libssl0.9.8 0.9.8e-5ubuntu3.2
Ubuntu 8.04 LTS: libssl0.9.8 0.9.8g-4ubuntu3.1 

Then the problem is already fixed?

.

---

### Post by vexorian on 2008-05-20
A security firm confirmed a serious security bug in debian, weeks after it was announced by ubuntu and debian people themselves, and also 1.5 weeks after it was fixed?

---

### Post by Joeb454 on 2008-05-20
It depends, what version of Ubuntu are you running?

If you have installed all available updates, then you should be fine :)

---

### Post by neurostu on 2008-05-20
Yes are running a newer version of ubuntu then the problem got patched via automatic updates.

I also mis-spoke, a computer was only vulnerable (without the updates) if it was enabled to allow people to connect to the machine via ssh-keys.

---

### Post by Joeb454 on 2008-05-20
If you run your own server, then check that (just to make sure) as I did, though for most home users, it really shouldn't be that much of a problem, as most won't use SSH.

---

### Post by muteXe on 2008-05-20
I was going to start playing around with ssh tonight, i don't think i will yet.

---

### Post by vexorian on 2008-05-20
> **muteXe said:**
> I was going to start playing around with ssh tonight, i don't think i will yet.
The bug has been fixed some days ago already, just download the update, if your update-manager isn't in red exclamation mark mode, chances are you already got the update...

---

### Post by Joeb454 on 2008-05-20
I'm with vexorian, I've been SSHing in and out of my server many times (website maintenance and IRC bot maintenance :p)

---

### Post by muteXe on 2008-05-20
okay :)

---

### Post by bartcramer on 2008-05-20
One addendum: I think that using https websites had also become less secure. I received ssh updates on both Hardy and Gutsy, and I suppose that they upgraded earlier versions as well. 

To the OP: using Ubuntu (or Linux/FreeBSD/MacOS in general) still has an enormous security benefit for you. Do it :)

---

### Post by neurostu on 2008-05-20
One more thing, openssh-server by default allows for inbound connections to connect with ssh-keys. Even with this option enabled you are not necessarily vulnerable. You need to have a public key added to your .ssh/authorized_keys file.  If you haven't ever messed with SSH Keys before then don't worry you're not at risk.

Most people don't use SSH Keys although they are a great way of accessing systems securely and quickly.

---

