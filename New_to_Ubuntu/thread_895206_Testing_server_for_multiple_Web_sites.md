---
title: "Testing server for multiple Web sites"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-08-20
Hello~

I am using LAMP, ProFTPd, etc., as a testing server for the occasional Web site we’re asked to build/redesign. The design work itself is done via Dreamweaver on a Mac and PC, with the “local” files being stored on the Linux box (it’s also acting as our home office file server). 

I have it up and running with *one* web site, but the only way I can get relative links to work is to have the site located at the root of /var/www. 

Where should I look/what should I read about configuring Apache to allow me to use/assign subfolders to different sites? (Sorry I don’t know the terminology at this level—hence why I’m having a hard time finding the solution on my own.) That is, I’d like to set things up so that testing files are located in var/www/site1, var/www/site2, var/www/site3, etc., so that when I click a link on a page I’m testing it uses those paths for the tested site. 

Is this where a DNS server comes in? For an internal network, how does one approach such a thing? Or am I barking up the wrong tree?

I’m slowly learning Webmin, if that makes a difference, but if direct editing of config files or a different method is better, I’m willing to learn. 

Thanks, 

Rhythm

---

### Post by tamoneya on 2008-08-20
I think if we just clear up the terminology it will get you pointed in the right direction.  

What you need is called virtual hosts.  Ive played with it a little and it worked great.  Here is the guide i used: [http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)

---

### Post by Rhythmdvl on 2008-08-20
Wow, thanks -- that's exactly the guidance I was looking for! It's always much easier when you know what to look for, isn't it?

---

### Post by Gregmond on 2008-08-20
I had been meaning to look up how to do this for myself. Thanks for saving me lots of effort.

---

