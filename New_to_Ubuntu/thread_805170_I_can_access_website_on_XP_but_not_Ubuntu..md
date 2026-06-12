---
title: "I can access website on XP but not Ubuntu."
date: 2008-05-23
forum: New to Ubuntu
---

### Post by luke949 on 2008-05-23
Hi!

  I can connect to a certain page on Windows XP with firefox, but when I try to connect to the same page through Ubuntu with Firefox, I get a Failed to Connect error. The website I am trying to access is: [http://www.playrequiem.com/index.aspx](http://www.playrequiem.com/index.aspx) 

Please see if this website works for any of you because it isn't working for me. 
Thanks everyone!

Also, for some reason I can access the website using a proxy server, but not by going directly there.

---

### Post by alzie on 2008-05-23
Seems to be there for me.  Hardy Heron using FF 3.0b5

---

### Post by ByteJuggler on 2008-05-23
> **luke949 said:**
> Hi!

  I can connect to a certain page on Windows XP with firefox, but when I try to connect to the same page through Ubuntu with Firefox, I get a Failed to Connect error. The website I am trying to access is: [http://www.playrequiem.com/index.aspx](http://www.playrequiem.com/index.aspx) 

Please see if this website works for any of you because it isn't working for me. 
Thanks everyone!

Also, for some reason I can access the website using a proxy server, but not by going directly there.

Works fine for me.  As for it working via proxy - is this on XP or Ubuntu?  Can you ping the site?

---

### Post by luke949 on 2008-05-23
> **ByteJuggler said:**
> Works fine for me.  As for it working via proxy - is this on XP or Ubuntu?  Can you ping the site?

I can access the site through a proxy on Ubuntu. I'm also not sure how to ping a site, could you please explain for me? Thank you.

---

### Post by Samhain13 on 2008-05-23
The site is working for me too.
Same spec as alzie.

---

### Post by linuxisgoed on 2011-03-30
For some reason I cannot access "my.unisa.ac.za" when I use firefox in Ubuntu in 10.10 but when I duel boot xp on the same machine I can access it also using firefox. I can access any other sites on ubuntu including this forum but when I try the link above it says 
Unable to connect 
Firefox can't establish a connection to the server at my.unisa.ac.za.
I have tried using chromium web browser but get the same message 

I have no reason to believe the site is down as I can access it via a proxy, when I ping it I get :  Destination Port Unreachable 

I have not manually set up any firewall and no website are being blocked via the settings on my router.

any suggestions?

---

### Post by ByteJuggler on 2011-03-30
Assuming you're using an ethernet connection and not wireless, try this:

1.) Open a terminal.
2.) Enter:
sudo ifconfig eth0 mtu 1400

Enter your password when prompted.  This command makes the "Maximum Transfer Unit" smaller -- some routers drop oversized packets and this sometimes surfaces as sites not being accessible even when others are.

Let me know if this works.

---

### Post by lz1dsb on 2011-03-30
> **luke949 said:**
> I can access the site through a proxy on Ubuntu. I'm also not sure how to ping a site, could you please explain for me? Thank you.
You can ping a site by opening a command prompt and there you should type:
ping <site's address>
So with this the system will first try to resolve the fqdn(fully qualified domain name) into an IP address and after that (assuming that your DNS service is working) will try to actually sent an ICMP echo request message. I'm not on a Linux console right now, so I can't send a sample output.


Cheers

---

### Post by lz1dsb on 2011-03-30
> **ByteJuggler said:**
> Assuming you're using an ethernet connection and not wireless, try this:

1.) Open a terminal.
2.) Enter:
sudo ifconfig eth0 mtu 1400

Enter your password when prompted.  This command makes the "Maximum Transfer Unit" smaller -- some routers drop oversized packets and this sometimes surfaces as sites not being accessible even when others are.

Let me know if this works.
That's a pretty good suggestion but how does that explain that it's working for him from Windows? That would be quite interesting for me...

Cheers

---

### Post by beew on 2011-03-30
> **luke949 said:**
> Hi!

  I can connect to a certain page on Windows XP with firefox, but when I try to connect to the same page through Ubuntu with Firefox, I get a Failed to Connect error. The website I am trying to access is: [http://www.playrequiem.com/index.aspx](http://www.playrequiem.com/index.aspx) 

Please see if this website works for any of you because it isn't working for me. 
Thanks everyone!

Also, for some reason I can access the website using a proxy server, but not by going directly there.

No prob for me. Using firefox4 on Ubuntu 10.10. **Edited: **Tried going there with Opera, can still access it but a window pops up saying that the site's security certificate has expired, don't know if that has to do with anything.


> **linuxisgoed said:**
> For some reason I cannot access  "my.unisa.ac.za" when I use firefox in Ubuntu in 10.10 but when I duel  boot xp on the same machine I can access it also using firefox. I can  access any other sites on ubuntu including this forum ?

Also works for me.

---

### Post by linuxisgoed on 2011-03-30
I figured out my mistake.  I have completely forgotten I have ipBlock set up to automatically start when Ubuntu starts. It was set to block the incoming requested from ip address that originate from universities. The website I was trying to view is obviously on that list so simply right clicking the blocked address in the log and selecting 'permanently allow' has sorted out the problem - now I can get back to my studies :)

For those interested ipBlock works great, it works so well you don't even realise it's there until it blocks something it's not suppose to.  
Thanks to all who made suggestions

---

### Post by ashhab2010 on 2011-03-30
I had no trouble with [url http://www.playrequiem.com/index.aspx[/url]. However, you should keep in mind that there are some sites that are Windows only. For example, Pepsi has a site that cannot be viewed in anything but Windows. [http://ubuntuforums.org/showthread.php?t=1476299](http://ubuntuforums.org/showthread.php?t=1476299)

Try using opera...... or you can find many web browsers in the Ubuntu Software Center. Although, if you aren't able to visit some sites, you should find out why. May be there's some security configuration preventing the browser to display specific sites.

Kind regards!

---

### Post by lz1dsb on 2011-03-31
It always amazes me that there are still companies making sites that are "windows only". That was not the original idea behind HTML, wasn't it? The whole point of making a site is for it to be viewable (in the best case scenario) on all platforms...

---

### Post by ByteJuggler on 2011-03-31
> **lz1dsb said:**
> That's a pretty good suggestion but how does that explain that it's working for him from Windows? That would be quite interesting for me...

Cheers

Because Windows might be using a smaller MTU size?

---

