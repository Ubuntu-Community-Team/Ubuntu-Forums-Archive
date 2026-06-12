---
title: "Trying to install Xfire for Pidgin"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Ihr Todeswunsch on 2008-06-30
Hello everyone. 

As you may be able to tell, I'm very new to Linux/Ubuntu. I've just started it about 3 days ago, and I'm liking it a lot. And I'm also very excited to become a part of the Linux/Ubuntu Community. I've ran into a lot of issues, but from reading around on this forum and others, I've discovered ways to fix most of my issues.

However, I can't seem to work my way around this one. I've been trying to install an xfire plugin for Pidgin, and it isn't really working. I've tried many things such as .deb's from this site: 
[http://gfire.sourceforge.net/snapshots/](http://gfire.sourceforge.net/snapshots/)

But I keep getting the same error: Error: Wrong Architecture "i386"

So therefore, I can't install those packages.

I've also tried the tar.gz's from there. This is what I do.

I get it from my desktop, so I type it: cd /home/ihrtodeswunsch/Desktop
Then I type tar xvfz gaim-xfire-0.6.1~20071109.tar.gz

Then I do: cd ./gaim-xfire-0.6.1~20071109
Then: sudo ./configure

It goes through a list of stuff, before I get a glib-2.0 error. So then I got the right package. (I forgot what it was called, gtklib-2.0-dev or something)

Anyways, that seemed to solve that problem. But now, I get the error when I try to do it: No Package "gaim" found. 

I've read some other posts on this website, that stated that it would still work okay if I just tried to do this, but obviously it isn't working. And from all of the other stuff that I've tried, I'm surprised that I haven't broken Ubuntu. 

P.S. I also tried using the gfire things from this website: 
[http://edhewitt.co.uk/gfire/?page_id=3/](http://edhewitt.co.uk/gfire/?page_id=3/) 

However, I get the same architecture error.

---

### Post by Ihr Todeswunsch on 2008-07-01
Ok, now I tried again from that last website that I posted in the Post Script. 

And I got a tar.gz from there, however... now when I'm done extracting it, and I got to do the sudo ./configure; I now get a No Package "Pidgin" found. Any ideas on how to resolve this issue? I think it's more workable now since I'm using pidgin.

---

### Post by Ihr Todeswunsch on 2008-07-01
Okay, so I updated pidgin again, and it seemed to have work this time. I ended up compiling it, then when I ran it: sudo make install 

Followed by make clean.  

So it seems to have installed, with no errors. However, now... I don't know how to make the plugin work in Pidgin. Otherwise, I've solved the problem, and I've figured it out, and completed what I asked for on here: To get it installed.

Thanks anyways for the help.

---

### Post by tjwoosta on 2008-07-01
> But I keep getting the same error: Error: Wrong Architecture "i386"

what this is saying is that you are trying to use the 32bit version on a 64bit machine

just use the 64 version and it should work
> However, now... I don't know how to make the plugin work in Pidgin

after installing the plugin you should automatically see xfire in the list of clients to use

---

### Post by ACE195 on 2008-11-01
i have this same problem but i dont have a 64bit system

i have a 32bit one i think how do I fix this?

---

