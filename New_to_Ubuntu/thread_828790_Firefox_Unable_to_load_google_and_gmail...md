---
title: "Firefox: Unable to load google and gmail.."
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Nhira on 2008-06-14
Hello! :3

I used to have Ubuntu 7.4 but 'cause of a problem I had to format my hard disk [without back-up.. ] so yesterday night I install Ubuntu 8.4
It took me some time to set up my settings but at last, everything was perfect. Until today.
I tried to get access to my gmail account and use google but I got the following errors;

-Firefox can't find the server at mail.google.com.
-Firefox can't find the server at [www.google.com](www.google.com).

I've check my DNS and network setting, and I don't use any firewall or proxy.
Also, the second time I tried to open gmail I took the following error;
-Error code: ssl_error_bad_cert_domain

But.. after some time I was able to access my mail and after two minutes I took the same errors again..

Anyone knows what's happening? ](*,)

-N.

---

### Post by alienexplorers on 2008-06-14
Have you tried to ping [www.google.com](www.google.com)....  If you can ping it you should be able to load it since it means the site is not down.  If you can't load it then try reinstalling firefox 3.0....  I have tried both sites and they work perfectly.  Are you running any add-ons in firefox?

---

### Post by lisati on 2008-06-14
There have been reports that Google hasn't been working too well in some parts of the world - see here: [http://ubuntuforums.org/showthread.php?t=828771](http://ubuntuforums.org/showthread.php?t=828771)

Good luck!

---

### Post by Nhira on 2008-06-14
alienexplorers thanks for your reply!
I ping it and I still had the same problem.. but now it's working fine. Gmail, google, gtalk et.c. are loading without any problem or delay.
The only add0n I have is Interclue 1.5.5

@Lisati
Yes, it wasn't only me!
Thanks for your reply.
At least now it's working perfectly :>

---

### Post by Tigrillo on 2008-06-15
I had the same problem. I was using a manual proxy configuration and after checking:

Edit-Preferences-Advanced-Network-Settings-Manual proxy configuration-Use this proxy server for all protocols

it finally worked.

I hope this helps

---

### Post by Nhira on 2008-06-15
> **Tigrillo said:**
> I had the same problem. I was using a manual proxy configuration and after checking:

Edit-Preferences-Advanced-Network-Settings-Manual proxy configuration-Use this proxy server for all protocols

it finally worked.

I hope this helps

I'll try it.. Today, google refused to load again.. :(

---

### Post by cariboo on 2008-06-15
If you can access everything else but google, wouldn't that lead you to believe that the problem is with google and not your computer? no sense trying to fix a problem that isn't yours.

Jim

---

### Post by Nhira on 2008-06-15
according to this thread [http://ubuntuforums.org/showthread.php?t=828771](http://ubuntuforums.org/showthread.php?t=828771) , google and its services are going on and off. Which is really annoying..
Despite that, as I said, I'm also taking strange sll_errors, so i'll do my last try to see if it's something with my computer and if not, i'll quit ttrying.
Yesh, I thought the same as you Jim but if one in a million the problem is with my computer, i'd love to solve it.
Is kinda annoying when you cannot access your mail and you're waiting for an improtant one.. :|

-N.

---

### Post by Xtian_1028 on 2010-06-22
Hello!

I am also having trouble with browsing the web using firefox. When I type in yahoo.com, I get the screen showing that the webpage is being loaded, but it stays like that for all eternity.

According to some posts, there was a relation to the proxy settings of the GNOME. maybe you guys can help me configure that settings?

Thanks! 
Press **ENTER** to look up in Wiktionary or **CTRL+ENTER** to look up in Wikipedia

---

