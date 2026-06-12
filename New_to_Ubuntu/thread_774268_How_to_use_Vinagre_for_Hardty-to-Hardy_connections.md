---
title: "How to use Vinagre for Hardty-to-Hardy connections"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by quesyducky on 2008-04-29
8.04 came out, and I officially am making my Ubuntu my all time desktop OS, but I need to be able to remotely manage my torrents, as well as shuffle some files around every so often (I dont want to use uTorrent webui, and often leave homework on my desktop that I want to access from other computers, mainly my laptop)

So, I can connect to my desktop locally (with Vinagre), but am unsure of how to do this from behind my linksys router/comcast connection. Will this be a problem? Will I need a static IP, or something like DynDNS?

Thank you very very much!

---

### Post by Monicker on 2008-04-29
> **quesyducky said:**
> 8.04 came out, and I officially am making my Ubuntu my all time desktop OS, but I need to be able to remotely manage my torrents, as well as shuffle some files around every so often (I dont want to use uTorrent webui, and often leave homework on my desktop that I want to access from other computers, mainly my laptop)

So, I can connect to my desktop locally (with Vinagre), but am unsure of how to do this from behind my linksys router/comcast connection. Will this be a problem? Will I need a static IP, or something like DynDNS?

Thank you very very much!

A dynamic dns service, along with port forwarding at the router, should work.  That is how I ssh into my home machine.  If you go that route I would suggest a STRONG password be required to connect to the vnc session on your desktop.  You would set that in System -> Preferences -> Remote Desktop.

---

### Post by encompass on 2008-04-29
Yes you ahve to setup your firewall to let your computers be exposed to the internet.  And vnc connections are not recommended way to do that.  if your going to use vnc you need to tunnel it threw ssh.  And that is beyond the scope of what I am telling you.
You could easily setup an ssh connection and you can administer your system from there... even do it very securely and mount the computers data on other computers easily.  That is how I would recommend it, as it's so much more secure.  Otherwise, you need to open one computer up to the internet.  You don't need to get dyndns... but it is helpful.  Just in case your IP changes often.

---

### Post by Monicker on 2008-04-29
> **encompass said:**
> Yes you ahve to setup your firewall to let your computers be exposed to the internet.  And vnc connections are not recommended way to do that.  if your going to use vnc you need to tunnel it threw ssh.  And that is beyond the scope of what I am telling you.
You could easily setup an ssh connection and you can administer your system from there... even do it very securely and mount the computers data on other computers easily.  That is how I would recommend it, as it's so much more secure.  Otherwise, you need to open one computer up to the internet.  You don't need to get dyndns... but it is helpful.  Just in case your IP changes often.

I was being lazy, and didn't consider the ssh tunneling. :)

Its actually fairly easy.  If you are connecting from another linux machine you can do the following:
```

ssh -L 5900:localhost:5900 username@examle.dyndns.org
```

That would open a local port of 5900 which is tunneled to the remote machine (example.dyndns.org) at port 5900.

Then you can do:

```
vncviewer localhost:0
```

...to use the tunnel and connect to the remote vnc server.  Putty and other windows gui apps also support ssh port forwarding.  For the port forwarding at the router, you only need to forward the ssh port (22 by default).

---

### Post by nousefreak on 2008-05-13
When i run:
```
ssh -L 5900:localhost:5900 username@dest-ip
```
i get:
```
ssh: dest-ip: Name or service not known
```

but when i just ssh connect it works fine
```
ssh username@dest-ip
```
this works just fine

Can someone tell me what is wrong

---

### Post by chocobanana on 2008-10-03
Hi there

Perhaps someone could confirm what happens if you set the Remote Desktop preferences to Require Encryption in the Advanced tab... 

Will it use SSH or any other reliable form of encryption?

Thanks!

---

### Post by flyingsliverfin on 2009-08-30
seems like im even worse at this than u guys... 

i though u could only connect to a ssh server with ip adresses (like xx.xx.xx.xx) 

whats localholst and localhost 5900?
whats dyndns?


heres what ive understood (i think): i can connect with ssh to another remote computer, and when im on the remote computer run vnc and vnc will somehow connect to my computer through the already established ssh link?/?
that doesnt seem too right....

---

