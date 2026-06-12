---
title: "'Desktop' server - best platform?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by kneewax on 2008-07-02
Hi Guys,

I have been using Ubuntu for a while now on my main machine, and also have two other PCs in the home / office one of which is on vista (my wife insists!).  

I want to build a desktop server for simple tasks - mainly as a web proxy, (and Dansguardian) but also it might be useful to have a sharable local calendar.

I was planning on using Ubuntu server for this, but would rather have a x-window interface for management  - particularly as I'd like to be able to put the machine in a cupboard and VNC to it when needed.  

Does anyone have any suggestions on the best platform for this?  I am not wedded to Ubuntu for this Job, although it would make some sense, if the desktop version is up to this job, equally I am happy to give a different distro a go if necessary.

Cheers

Kneewax

---

### Post by damis648 on 2008-07-02
You can install a gui to Ubuntu server edition. When you install it, just run```
sudo apt-get install ubuntu-desktop
```

---

### Post by hyper_ch on 2008-07-02
how will a gui help you adminster the server?

---

### Post by kneewax on 2008-07-02
[Rant removed.]

Because I am a visual person, who finds GUIs intuitive and helpful.  One of the reasons the MS Server Range virtually wiped out Novell in small businesses in the UK, was its usability and Graphical Interface.  I am no fan, but the companies I used to run IT systems for went with MS everytime, because of the GUI.

---

### Post by kneewax on 2008-07-02
> **damis648 said:**
> You can install a gui to Ubuntu server edition. When you install it, just run```
sudo apt-get install ubuntu-desktop
```

OK - grand. Thanks I'll see if that works for me...

---

### Post by damis648 on 2008-07-02
> **kneewax said:**
> OK - grand. Thanks I'll see if that works for me...

Good Luck!

---

### Post by laserprinter on 2008-07-14
> **damis648 said:**
> You can install a gui to Ubuntu server edition. When you install it, just run```
sudo apt-get install ubuntu-desktop
```

Can I do 
```
sudo apt-get install ubuntu-server
```

to install server on my desktop?  I am new and happy with the desktop for my learning pleasure.   I like to run a VPN server until I get comfortable running a server.

I tried but it says could not find package!

---

### Post by hyper_ch on 2008-07-15
a server is nothing more than a computer that runs some services on it and those services use text files to be configured so a gui does not help at all for setting up a "server"

---

### Post by cariboo on 2008-07-15
I was just looking and I didn't see the server setup in synaptic, but you can use tasksel to intall the server applications. In a termial:

```
sudo tasksel
```

This brings up a text based gui select lamp server and then OK this will install the needed apps. It will seem to not be making any progress, but just give it time as it has to download all the packages. Once the packages are downloaded it will walk you through the installation. Just FYI I see that MS has started using a terminal to administer their 2008 server package.

Jim

---

