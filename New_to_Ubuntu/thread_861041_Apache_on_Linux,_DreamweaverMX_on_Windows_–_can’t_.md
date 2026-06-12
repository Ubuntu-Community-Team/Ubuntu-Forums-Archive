---
title: "Apache on Linux, DreamweaverMX on Windows – can’t connect"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-07-16
I have Ubuntu Server with LAMP installed and ostensibly running. Among other things, I want to use it as a testing server for Web pages. That is, when I make changes to a Web page in Dreamweaver (running on a Windows box), I’d like to test/preview it via the LAN on the Linux box. 

On the Linux box, I was able to define a new Apache site and create a small HTML file in the directory I created. I can see the page if I browse to it from Windows. I get to the page by putting the Linux box’s IP address into the address bar (I have it assigned as a static IP). 

But when I try and define the site in Dreamweaver, I’m at a loss. Unfortunately, none of the tutorials I’ve found deal with Dreamweaver on one platform and Apache on another. 

If I select Access:Local/Network, I can browse for the testing server folder, but I can’t see it. If I change access to FTP, can enter the IP address of the Linux and the host directory, but I get a generic “An FTP error has occurred – cannot make connection to host. The server 192.168.1.108 is not responding.” 

If it makes a difference, I was able to get SAMBA up and running, get Windows to map/assign a drive letter, and save/read files saved there from both machines. I mention this to note that on at least one level I am able to get the two machines to play nicely together. (Or maybe I’m mentioning it because I’m damn proud to have gotten that to work. Small victory, perhaps, but it took me a lot of reading. Boy am I new at this!). 

Though I’ve read numerous pages and skimmed countless others, I’m sure this is such a basic issue that I just overlooked the right tutorial. Would you care to give me a bit of guidance/link?

Thanks, 

Rhythm

---

### Post by benfindlay on 2008-07-16
You will need to install an ftp server, such as vsftp or proftpd to allow ftp access. Then you will need to configure the ftp server to allow access to the directory you want to put the website in. I'd recommend installing proftpd personally. I would also recommend you look at installing webmin and virtualmin on your lamp server as these allow the servers to be administered via a web browser as well as the command line. I know of at least one web design/hosting company in my local area that use this setup to upload dreamweaver designed websites to their lamp servers. Since they host multiple websites for companies, they use webmin and virtualmin to facilitate this process.

Hope this helps!

---

### Post by arkara on 2008-07-16
This one is exactly beginners talk should it be here?

---

### Post by benfindlay on 2008-07-16
> **arkara said:**
> This one is exactly beginners talk should it be here?

Well if the moderators want to move it, then they will. Until then, as a member of the Absolute Beginners Team, I'll try to help anyone that posts here!

---

### Post by Rhythmdvl on 2008-07-16
Thanks **benfindlay** for the quick reply—and the direction. Looking at it it’s painfully obvious where I went wrong! I’ve been doing a *lot* of barking up the wrong tree, but hopefully what I found will help out later on. Again, thanks.

**arkara**, I’m not sure what you mean by “This one is exactly beginners talk should it be here?” I’m not trying to be obtuse—I’m really not sure what you mean. Are you saying I posted to the wrong forum? I figured since I’d only been at it for four or five days now, this was the right place to put my post. I’m too new to get the general etiquette of these boards, so please accept my apology if this should have gone somewhere else. If you have the inkling to tell me where and why, I’ll be much obliged (and I’m sure the moderator’s will appreciate it too). Again, no sarcasm or whatnot intended, since as it looks like I’ll be on this board for a while, I’d like to start off on the right footing.

---

### Post by benfindlay on 2008-07-16
Just a thought, if you do opt for the webmin/virtualmin approach, I'd recommend installing proftpd manually via synaptic/terminal rather than using webmin to do it for you. It has always given me problems when I have used webmin to automate it. I think its to do with the fact that proftpd needs to ask you some questions and presents you with a menu system to select options; webmin doesn't (or isn't able) to provide this to you. Once installed however, webmin makes administration of proftpd extremely easy!

And with regards to where to post, I've been using this forum for nearly 2 years and still consider myself an absolute beginner! Also, most of my posts go in the absolute beginners forum as they seem to get more responses than when you post them elsewhere!

Hope this helps!

---

### Post by Rhythmdvl on 2008-07-16
Ok then ... one step at a time. I used apt-get to install proftp and gproftpd (that's actually the only way I know how to install things so far) before your last post. I'm now going to spend a bit of time reading proftpd.org and [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) ... one step at a time :)

Thanks again!

---

### Post by benfindlay on 2008-07-16
Yes, and for help with installing webmin, go [here]("http://ubuntuforums.org/showthread.php?t=7507")

Hope this helps!

---

