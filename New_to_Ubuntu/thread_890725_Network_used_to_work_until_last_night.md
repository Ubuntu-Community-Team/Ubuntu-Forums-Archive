---
title: "Network used to work until last night"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by jkraj on 2008-08-15
This has got to be an easy one, but I can't find the answer.

I have a clean install, one week old today.  Everything has been working perfectly.  However, somehow the networking borked overnight.
  
This is a wired connection. 

Everything looks normal but doesn't work.  If I run dhclient I can see the request on the server and it sets the IP.  If I manually set the IP everything looks fine but doesn't work.  "Doesn't work" meaning ssh, ping, ftp, etc... using both names and ip addresses.

I see nothing out of the ordinary with ifconfig.

It isn't the hardware, everything works fine using the live CD.

How do I reset networking or whatever I need to do to get this to work?  I don't want to reinstall.

Thanks,
jkraj

---

### Post by halitech on 2008-08-15
can you post your ifconfig info here

---

### Post by wpshooter on 2008-08-15
I think I would try doing a fscheck !!!

---

### Post by jkraj on 2008-08-15
I ran a fsck which turned up nothing.  

In order to post the ifconfig info I would have been much easier to have network access.  I know I could have saved a file, rebooted using the live cd, etc..

But, I did find the problem, although I'm still not sure why it is just now showing up.  It looks like there was a conflict somewhere between a vmnet and my networking setup.  I'll investigate it further when I get the time.  But stopping vmware allowed my network to once again function.

Yes, the vmnet was displayed in the ipconfig, the only reason I guessed at the problem.

Thank you for your help.

jkraj

---

