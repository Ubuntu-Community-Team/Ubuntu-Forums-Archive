---
title: "What am I missing here?  (wireless problem)"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by markc7 on 2008-04-30
Ok, I'm probably missing something really obvious here, but I was wondering if someone could help me out.  I got my new laptop today, a Dell Inspiron 1525.  So far everything looks good.  I can see my neighbour's wireless, and when I try to access it I get the "Network Key Required" box, so I think my wireless card is working properly.  

So then I went to the public library and try to connect to their network (which, unlike my neighbour's wireless, I have permission to access).  The applet actually shows a connection being made, and it tells me that it's got a strong connection.  Now here's the problem.  At this point the network should request a username and password from me, but it doesn't.  When I start up Firefox, the status bar tells me that it's searching for, connecting to, then waiting for the website.  But nothing ever comes up.  I have done everything mentioned on the [library  website]("http://www.biblioottawalibrary.ca/explore/virtual/wireless/wireless_e.html") (disabled pop-up blockers, set up my system up for DHCP), but to no avail.

So basically I can make the connection but don't have permission to use the network because it doesn't ask me for my password.  :confused:  How do I get the network to ask me for permission?  Am I asking a really boneheaded question here? :oops:

---

### Post by Monicker on 2008-04-30
Did you verify whether or not you actually got an ip address?

The next time you are there. Run these commands

```
sudo ifconfig
sudo iwconfig
```


If dhcp was successful, you should have an ip address from the library's dhcp server and iwconfig should show that your are associated to one of their access points.

---

### Post by markc7 on 2008-04-30
Yep, I got the IP address by clicking on "Connection Information".  Does that give the same information as the commands you mentioned?

---

### Post by markc7 on 2008-05-01
Does Ubuntu have some kind of popup blocker that I might have to disable?  What's confusing me is that the website explains that users need to turn off their browser's popup blockers.  That leads me to suspect that the network is using something other than the standard wireless password system (which, as evidenced by my neighbour's network, is working fine for me) and that Ubuntu is maybe blocking whatever is trying to come up to request my username/password.

---

