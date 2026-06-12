---
title: "Seeking Opinion About Best Server Practice"
date: 2008-06-09
forum: Philippine Team
---

### Post by jeffimperial on 2008-06-09
Hey all! I'd love to hear your opinion about this...

I'm not a big fan of the CLI. Don't get me wrong. I've seen how helpful it can be. But I just haven't the diligence to learn the commands every time I need to do something new. 

Which of the following do you think is better?
[LIST=1]
[*]Ubuntu Server, then install the a window system
[*]Xubuntu, then install LAMP
[*]Server with GUI **TOTALLY A NO-NO** due to security risk
[/LIST]

I currently have Apache2 running on my Home PC. It's a fairly new machine, but the Site goes with my Shut Down. A lower consumption machine with minimal resources would do a much better job as a dedicated server than my current setup.

---

### Post by az on 2008-06-09
> **jeffimperial said:**
> Hey all! I'd love to hear your opinion about this...

I'm not a big fan of the CLI. Don't get me wrong. I've seen how helpful it can be. But I just haven't the diligence to learn the commands every time I need to do something new. 

Which of the following do you think is better?
[LIST=1]
[*]Ubuntu Server, then install the a window system
[*]Xubuntu, then install LAMP
[*]Server with GUI **TOTALLY A NO-NO** due to security risk
[/LIST]

I currently have Apache2 running on my Home PC. It's a fairly new machine, but the Site goes with my Shut Down. A lower consumption machine with minimal resources would do a much better job as a dedicated server than my current setup.

Installing the server, then the desktop used to install the server kernel and that may not play well with your desktop hardware.  Some things like your mouse or keyboard may not work as you would expect, but they would work fine using the desktop kernel.  I think it would be simpler to just install the desktop and then add the LAMP packages after that.

Whether it is a security risk or not is up to you.  Are you going to be hosting a blog or some other web application that is not-so-mission-critical?  What's at stake?  Your reputation as a sysadmin or thousands of credit card numbers?  

For an informal website with no critical information that anyone would want on it, the GUI wouldn't bother me so much.  It I was put in charge of running a mission-critical cannot-be-hacked corporate database server, then I would avoid the GUI packages.

---

### Post by loell on 2008-06-09
for me, server with a window manager will do.

also to reduce power consumption, it may be better using thumb drive instead of full blown hard disk. :grin:

---

### Post by jmazaredo on 2008-06-09
D rin ako ganun kagaling sa cli.
When I install a server i use the desktop CD of ubuntu or other linux that has a desktop environment. then just add up the server applications and then use webmin. After all are working, I disable the auto start of the window manager.

I just use the startx command whenever I want to use the window

---

### Post by jsgotangco on 2008-06-09
This is how I usually set it up:

[LIST=1]
[*]A development machine with all the stuff I need, even with X
[*]A staging machine with no X (only CLI) where I can deploy test code
[*]A production machine similar to staging but with very restricted access
[/LIST]

Do you really need 3 physical machines for such? No. You can utilize virtual machines if needed. Why 3 stages? It's the best practice to do when developing. If you found bad code in staging, then you wouldn't deploy it to production. If something in production went bad, you can rollback to a previous version that is perhaps in staging or in a VCS.

Servers especially in production should always have clean states - not just X but with unused services

---

### Post by Nessa on 2008-06-09
Huh? Ganun ba ka threatening ang risk kapag may GUI?

---

### Post by jeffimperial on 2008-06-09
> **Nessa said:**
> Huh? Ganun ba ka threatening ang risk kapag may GUI?
Sa mga nababasa kong posts (ubuntuforums.org and several others), "most malicious attacks are inserted in client scripts". Pero sabi naman ng iba "GUI security risks in modern window managers are mostly dead" because they don't allow remote connections [by default or at your option] anymore, and that they receive security patches much more often than back in the years - this is especially true for Linux-based systems. Di ko na mahanap kung san ko 'to napag-kukuha kaya walang links. Hehe.

Anyways, paano naman sa tingin nyo kung halimbawa, install ako ng Fluxbuntu then just add the server packages? Parang it makes more sense as far as the performance argument is concerned.

---

### Post by loell on 2008-06-09
> **jeffimperial said:**
> 
Anyways, paano naman sa tingin nyo kung halimbawa, install ako ng Fluxbuntu then just add the server packages? Parang it makes more sense as far as the performance argument is concerned.

yeah, that setup will do just fine ;)

if I understand it correctly this is just a personal website, right? 

to offload your cost  on your electricity and would like to have a capacity of 5 million pageviews per month, at absolutely no cost.

perhaps one of these days, you might like to try [Google app engine]("http://appengine.google.com") :)

---

### Post by jsgotangco on 2008-06-10
> **jeffimperial said:**
> Sa mga nababasa kong posts (ubuntuforums.org and several others), "most malicious attacks are inserted in client scripts". Pero sabi naman ng iba "GUI security risks in modern window managers are mostly dead" because they don't allow remote connections [by default or at your option] anymore, and that they receive security patches much more often than back in the years - this is especially true for Linux-based systems. Di ko na mahanap kung san ko 'to napag-kukuha kaya walang links. Hehe.

Anyways, paano naman sa tingin nyo kung halimbawa, install ako ng Fluxbuntu then just add the server packages? Parang it makes more sense as far as the performance argument is concerned.

Be that as it may, most nix services are running without a graphical environment, so it doesn't make sense to have one on a server unless you're not really using it as a serious server, but more of a hobby server. Also, general practice for nix servers is to be headless and administered remotely. And besides, the knowledge helps.

---

### Post by jeffimperial on 2008-06-10
> **jsgotangco said:**
> ...most nix services are running without a graphical environment...general practice for nix servers is to be headless and administered remotely.
Why is this so? I still don't get it. If there isn't or minimal threat, and if one has iptables setup properly and it doesn't have that big a performance issue, then why?
> **jsgotangco said:**
> And besides, the knowledge helps.
I agree. I guess I'll have to learn at least basic CLI if I want to set up my own Web server using the famous Apache on Linux, then use Webmin or phpMyAdmin or something to administer it via my network or the Net.

---

### Post by jsgotangco on 2008-06-10
> **jeffimperial said:**
> Why is this so? I still don't get it. If there isn't or minimal threat, and if one has iptables setup properly and it doesn't have that big a performance issue, then why?

The simplest of setups are the most practical to manage. Hence, a server with simple configurations are bound to be less prone to human errors as well as direct management. For a single server setup, it may not require very strict guidelines, but if you're in a position to manage multiple servers, then you have to reconsider. 

X was designed for the network in mind, but you don't want to introduce any reason for outsiders to try to get it, even if you have set all your routing, iptables, firewalls, and whatever security appliance/software you have, etc. 

Unless you are using IIS, your Apache installation only requires 2 things to be able to manage it: a remote connection and an editor. Same with Samba, NFS, Sendmail, Postfix, etc., etc.

---

### Post by jeffimperial on 2008-06-11
Oh so that's why. Thanks for clarifying, Kuya Jerome!

And thank you all for your comments and replies. I have just officially decided that, though a little more tedious than I first imagined, I will set up my home Web server **without** a GUI. Thanks again!

---

