---
title: "I am unable to view my web pages online"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by Neffness on 2013-06-30
I have followed a tutorial online about setting up a "perfect" server. I have got really far and completed almost all the tasks with no issues. I purchased a domain for my b-day and wanted to play around with it a bit. Using my domain name for SSH I am successfully able to connect to my server from my home notwork or from outside of my home network. However, I am stumped on the matter of the DNS server. It does not matter what I do, for some reason I can not get a successful dig out of my domain. I can ping it, everything matches up how it should according to the tutorial. I can even get a "IT WORKS!" if I go to the IP address, but if a friend goes to my domain outside of my network he is taken directly to a godaddy parking lot.

After some research I found that my port 80 may not be forwarding correctly. My server says its listening on port 80, but all port sniffers online state that it is in fact closed. I'm really at the point where I have no choice but to request help on forums. Nothing I do seems to matter as far as port forwarding goes. I have even disconnected all but 1 PC from the network in an attempt to free up anything that might be using port 80.

Any insight would be most helpful. I would have posted logs to review, you will have to forgive me as I am not sure which logs would be most helpful in this situation. Thanks in advance!

---

### Post by MidnightGrey on 2013-06-30
Does GoDaddy have a support forum of some kind? (i mean you are a paying customer after all).
I'm not sure what part of this issue relates to ubuntu.

---

### Post by sanderj on 2013-06-30
You have to separate two things:
1) is your webserver running and reachable based on it's IP address?
2) is your www.<domain>.com pointing to that IP address

Don't mix it.

---

### Post by Cheesemill on 2013-06-30
Some ISP's block port 80 (and some other ports) completely to stop people running servers from their home internet connections, you'll find that it's against the ToS for a lot of residential broadband connections.

Check with your ISP to see if they are blocking port 80.

---

### Post by buzzingrobot on 2013-06-30
It's unclear if you can ping or reach the site via its domain names as well as it IP number.

If you can't reach the site via the domain name, it's likely an issue with the DNS setup.  It might be as simple as the DNS changes haven't had time to percolate around the net.  Sometimes, this can take several hours or more. 

If *you* can reach it via the domain name but your friend can't, I'd wait overnight just to give the DNS change time to make its way to the nameservers your friend happens to use. If that's still not working, I'd double check my DNS setup. Your registrar and your host are the places to look for assistance.

---

### Post by fosterD on 2013-07-01
It seems to me that you haven't configured the router to forward port 80 dest packpages to your web server
Are you using external IP address?
Try to access your website from outside by your external IP address (http://<external-ip-addres>:80)

---

### Post by sanderj on 2013-07-01
Five followups, no reaction from the OP ... so I'll unsubsribe.

---

### Post by zero2xiii on 2013-07-01
> **sanderj said:**
> Five followups, no reaction from the OP ... so I'll unsubsribe.

This is really anoying on the forums these days, and the IRC are really annoying in their own right.

Anyway, just for the archive @OP. Make sure your ROUTER forwards the external traffic correctly to the internal ip:port. See port forwarding for you specific router.

Cheers

---

