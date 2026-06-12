---
title: "Samba server and Apache Server"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-09-02
Hello all,
I have just recently started working with Ubuntu as a LAMP server and just this past weekend installed KDE on top of Hardy on a stand alone machine that is networked to my other Windows boxes.  I am trying to figure out how to get files from my Windows XP box in particular web development files over to the Kubuntu LAMP server.  I am now reading about SAMBA server just wondering has anyone had any conflicts with the  Apache server or should they co-exist?  Is Samba the best way to link the 2 machines?  

Thanks in advance,

---

### Post by halitech on 2008-09-02
SAMBA is simply for sharing files on a network, Apache is for serving webpages and both use different ports so there won't be any conflict at all.

If you are using Windows and Ubuntu then either SAMBA or FTP is the only way to go

---

### Post by jamesrfla on 2008-09-02
My area of expertise :) Samba is a file server to share files over your network. Apache2 is a web server. You would use apache2 to host a internet web site or a external web site. If you want to share files outside your network other than just sharing them inside your network let us know and we will give you instructions.

---

### Post by JKHinton CPBD on 2008-09-02
Thanks Halitech and Jamesrfla, for the respones to my post.

Well right now I am just trying to pass files at home from XP to Kubuntu on my local network.  If I can get my existing web development files over to the Kubuntu box and have it working under LocalHost my long term plan is to carry this Kubuntu box to my office and set it up as a web server for a small company which will not be having a lot of traffic.  Then if all goes well I plan to build another Kubuntu box for my home and then will probably want to access the office system remotely about 45 miles over the internet.  What I'm hearing both of you say is Samba will be a good choice for this and will not interfere with my Apache Web Server that I am trying to set up?

Thanks to folks like you, this forum is the best.

---

### Post by jamesrfla on 2008-09-02
Thanks. This is the best Linux forum out there. I run apache2 and samba on my Ubuntu desktop and I don't have any problems. Samba just acts as my file server and my apache2 acts as my web site inside my network and outside my network. If you want it can just be inside your network. If you have any other questions just ask.

---

### Post by halitech on 2008-09-02
> **JKHinton CPBD said:**
> Thanks Halitech and Jamesrfla, for the respones to my post.

Well right now I am just trying to pass files at home from XP to Kubuntu on my local network.  If I can get my existing web development files over to the Kubuntu box and have it working under LocalHost my long term plan is to carry this Kubuntu box to my office and set it up as a web server for a small company which will not be having a lot of traffic.  Then if all goes well I plan to build another Kubuntu box for my home and then will probably want to access the office system remotely about 45 miles over the internet.  What I'm hearing both of you say is Samba will be a good choice for this and will not interfere with my Apache Web Server that I am trying to set up?

Thanks to folks like you, this forum is the best.

you have it half right :) If you move the kubuntu box to your office, you'll need a little more setup then just samba and apache to access it from home. You might be able to use Samba to access the drives remotely but for that I would probably go with an ftp server (there are a few in the repos that work well) and to remotely control it you will probably need something like vnc. All of these run on different ports so there won't be any conflict if you do install all of them.

---

### Post by brentoboy on 2008-09-02
A word of security caution.

First off, sharing /var/www (or whatever your site root folder happens to be) is a wonderful idea.  You can then edit things across the network without even having a local copy if you want to.  This is great while you are building the site.

When you are done (before you take it elsewhere), you should remove samba altogether, or at the very least, stop sharing /var/www.  You wont be able to get to it easily via samba anyway once it is on another network.

I would say that setting up FTP would help you, but chances are, even that will be quite difficult as a way of maintaining the site.  The end user is very likely to be on a private lan behind a firewall/router. you will need to be able to poke a hole in their firewall and forward the FTP traffic to your internal server.  Which means you need to set up a static ip address inside their lan, and (hope) they have a static IP address from their service provider.  All of these things are a mess unless you know your stuff and are aware of what could go wrong.

The easiest way might be to turn off samba when you take it out, and then, when you want to update it, go on site, and turn samba back on, and then copy over your files again, and then turn it back off.

Anyway, adding samba on an apache server is not a bad thing at all.

---

