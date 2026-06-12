---
title: "What Does Networking Do?"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-07-31
I have installed LAMP via Syn. Pkg. Mgr. When restarted Apache2 I see an error msg. in the terminal and on trying to resolve that problem by reading previous posts and pages, I find I am too ignorant of what needs doing.

From what I have learned I need to point the Apache2 server (hereafter server) to (by way of example)

example.com

The error message refers to line 237 in apache2.conf file. Line 237 is:

# Include the virtual host configurations:
Include sites-enabled/

These are the advantages I hope to have by LAMP.

1 - to run VnStat in a gui to see bandwidth usage on this network of 3 (wifi connected) computers.

2 - to serve a 100kilobyte .mp3 file to a weblog (blogger.com)

3 - to have a MythTV media center

Does LAMP do all this, as long as VnStat, and MythTV is installed? is the "Include sites-enabled/" to read (for example)

unidentifiedparty.com

or

[www.unidentifiedparty.com](www.unidentifiedparty.com)

or

[http://www.unidentifiedparty.com](http://www.unidentifiedparty.com)

and I'm lost as to what to ask about a gui for VnStat as I'm looking at my computer's network bandwidth usage and not a device or network outside this one. So:

vnstat.com 

and as above iterations?

LASTLY: I would like to begin by getting VnStat running. The other parts can wait. If I can understand the "single default virtual host" I can move on to adding more. Trying to post intelligent questions, when I have no idea of what I'm doing is the reason that this post is in Absolute Beginner's Section, as I thought about putting it in Networking.

---

### Post by TheFu on 2013-07-31
You'll get there, but some basic knowledge seems to be missing.

[http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) can help a little. Hopefully that is clear enough to get you started.
I don't know anything at all about the specific programs you've listed like VnStat, sorry. Never heard of it. My router tracks connection information for every device on the LAN, not just 1 computer. 

A basic understanding of networking will be needed too, but DNS, registrars and IP addressing basic understanding are more important at this point.

---

### Post by Mark_in_Hollywood on 2013-07-31
I had a look at the 'blog and thanks for that. I have purchased a .com. And [http://www.unidentifiedparty.com/]("http://www.unidentifiedparty.com/") is up on the 'net. Let me try this another way. I want a working LAMP configuration. Currently Apache2 is giving errors. Two actually. The first I wrote about above, in this post, the 2nd is about a missing </VirtualHost> being missing. I'm trying to learn and fix this one problem at a time. I've learned that the apache2 "example.com" filled. I am now trying to understand what I must change within that file to make it work for my particular applications. Can you point me to a page or two for a beginner?

---

### Post by TheFu on 2013-07-31
[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp) can help.
I'm not convinced that the guide creates a secure server when everything is done, however.

LAMP only provides the base stack, not any specific applications and definitely NOT MythTV which is completely unrelated to LAMP.  I suppose the MySQL install could be used for both MythTV needs and whatever web-applications you need.  Be certain to use a different DB if you do that.

If your PC has enough CPU and RAM, it might be a good idea to look into virtualization to split drastically different programs up.  This can be very important for internet facing applications like most web-apps want for security reasons.  MythTV doesn't need to be internet facing at all and probably needs to be closer to the computer hardware - depending on the tuner card you have.  I run a TV recording virtual machine, thanks to a network-based tuner device that doesn't use PCI slots to any PC here.

And just for clarification - a web "virtual host" is different from a "virtual machine." Completely different technologies.

---

