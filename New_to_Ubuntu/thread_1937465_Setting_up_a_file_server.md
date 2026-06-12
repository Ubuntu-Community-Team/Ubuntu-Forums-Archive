---
title: "Setting up a file server"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by Socinus on 2012-03-07
I have a spare CPU and I'm looking into setting it up as a file server with Ubuntu attached to my main desktop as well as running the BOINC client. Is there a guide on how to do this anywhere and is going to be a problem that I dont have another monitor to attach to this new CPU?

---

### Post by jerome1232 on 2012-03-07
> **Socinus said:**
> I have a spare CPU and I'm looking into setting it up as a file server with Ubuntu attached to my main desktop as well as running the BOINC client. Is there a guide on how to do this anywhere and is going to be a problem that I dont have another monitor to attach to this new CPU?

Yes and no.


For the initial install of Ubuntu server edition (cli only by default), you will need a monitor. Set it up with ssh and a static ip and then you'll be able to ssh into it from your desktop, no monitor required thereafter (my little home server is crammed into a cupboard) During the installation you are asked what tasks the server is for, openssh and samba file server are two options you will want to check, that will install openssh and samba.

What clients is it going to be serving files to, Windows? Mac? Linux? mixed?

---

### Post by Socinus on 2012-03-07
> **jerome1232 said:**
> Yes and no.
 
 
For the initial install of Ubuntu server edition (cli only by default), you will need a monitor. Set it up with ssh and a static ip and then you'll be able to ssh into it from your desktop, no monitor required thereafter (my little home server is crammed into a cupboard) During the installation you are asked what tasks the server is for, openssh and samba file server are two options you will want to check, that will install openssh and samba.
Can you elaborate more on what SSH is?
 
> What clients is it going to be serving files to, Windows? Mac? Linux? mixed?
Mixed, a Windows XP (eventually Windows 7) desktop and to a Ubuntu laptop.
 
How do I actually connect the other machines to this CPU? Wirelessly? Ethernet cables?

---

### Post by jerome1232 on 2012-03-07
It stands for Secure Shell

[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

Essentially it's a way to remotely control the computer. A great way to administer a headless server (no keyboard or monitor attached) just beware, this is a service which allows remote administration, so don't open it up to the internet (port forwarding on your router) unless you know how to properly secure it.

I would connect the server wired to your router since it's
[LIST]
[*]Less of a headache for setup
[*]Less prone to problems
[*]Less prone to problems
[*]Less prone to problems
[*]Less of a headache for setup
[/LIST]

Since you are in a mixed environment it's probably best to stick with Samba as your file server (an option in tasksel anyways). There are a ton of guides on how to setup samba hit up your favorite search engine, just make sure the guide is up to date, feel free to ask more questions if you have them!

---

### Post by matthill11 on 2012-03-08
this is also what i plan on doing when i can put another tower together. I found an interesting article on this [http://www.linuxjournal.com/node/1005985](http://www.linuxjournal.com/node/1005985)

---

### Post by jerome1232 on 2012-03-08
> **matthill11 said:**
> this is also what i plan on doing when i can put another tower together. I found an interesting article on this [http://www.linuxjournal.com/node/1005985](http://www.linuxjournal.com/node/1005985)

Like I said, check the dates on these things, Jan 17, 2008  is a bit dated to say the least.

---

### Post by Socinus on 2012-03-08
What distro would be best to use for the file server desktop? I was looking at Xubuntu or Puppy.

---

### Post by jerome1232 on 2012-03-08
My instructions were for Ubuntu Server, which is what I use, if you really want a gui you could always install one after the install, generally not done on a headless server.

---

### Post by phrak on 2012-03-08
You might also check out [FreeNAS]("http://www.freenas.org").  It has a web interface (never tried to connect from outside my home though) and ssh.  I've used it in the past.

---

### Post by kevdog on 2012-03-08
How many users are going to be using your server?  If its just you, any distribution would work.  I have Ubuntu as a server but its the regular desktop edition.  From time to time something breaks my ssh connection so I have to go over and turn the monitor on and manually log into the system to fix the problem.

---

### Post by Socinus on 2012-03-08
Can you use something like LogMeIn to make changes instead of a monitor?

---

