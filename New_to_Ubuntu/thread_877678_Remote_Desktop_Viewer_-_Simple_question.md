---
title: "Remote Desktop Viewer - Simple question"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by crjackson on 2008-08-02
I recently setup a system with Hardy for a friend.  He lives about 2 hours away.  He would like for me to connect to his machine for assistance.  Before I sent his computer home with him, I went to the remote desktop preferences and enabled his computer receive connections and I password protected it.

I know how to connect to other computers in MY house using the find function of the viewer.  How do I connect to his machine located outside of my network?

Do I simply enter his ip address into the "HOST:" block of the viewer prompt?

He is connected directly to a DSL modem, and is not running a firewall at this time.

Thanks

---

### Post by lisati on 2008-08-02
One thing to be aware of is that if his ISP uses DHCP, his IP address might change from time to time, especially if he resets his router.

---

### Post by crjackson on 2008-08-02
> **lisati said:**
> One thing to be aware of is that if his ISP uses DHCP, his IP address might change from time to time, especially if he resets his router.

Yes I know, but do I just enter in the ip address in the HOST: box?

---

### Post by crjackson on 2008-08-02
I can't ever seem to get an answer on these forums anymore.  Is this so complicated.  Of course I plugged in the IP in question and it didn't work.  Would someone be so kind as to explain how to do this?

---

### Post by jamesrfla on 2008-08-02
All you need to do is have remote desktop enabled and have a VNC veiwer on the client computer and a IP address(ex.192.168.1.4). If you are doing remote desktop out side your network (on the internet) then you need to port forward port 5900. Then find your work ip address and give it to the guy you are helping.

---

### Post by crjackson on 2008-08-02
> **jamesrfla said:**
> All you need to do is have remote desktop enabled and have a VNC veiwer on the client computer and a IP address(ex.192.168.1.4). If you are doing remote desktop out side your network (on the internet) then you need to port forward port 5900. Then find your work ip address and give it to the guy you are helping.

It's enabled on his computer and I have his ip address but I'm getting nothing.  I guess it has something to do with port forwarding 5900.  I'm not exactly sure how to go about doing that.  I have a Linksys router and I know where to find the port forwarding section, but I don't know how to make it work.

Here is a screen shot.  I made the port range from 5900 to 5910 and clicked save the changes.  It tells me it saved them, but when I tell it to continue and view the chart again, my settings are gone.

How can I make this work?  Here is a screen shot of what I'm looking at.

---

### Post by crjackson on 2008-08-02
Okay, never mind about getting the settings to stick.  I figured that out but it's still now working.  I'm going to get him on the telephone in a little bit and have him double check his settings.  I think we're getting closer.

---

### Post by jamesrfla on 2008-08-03
All you need to do is put what ever you want for application. For the range just put 5900 and 5900. By default remote desktop uses port 5900. You don't need to make a range from 5900 to 5910. You are just letting more people into your network. If you want for added security change to default port number to 5902 or 5909. You would need to make these changes in System>Preferences>Remote desktop on the secound tab. Check the box to use alternate port number and change it to something other than 5900. Then make the port changes in your linksys router. Then when the guy connects you have to connect differently (ex.<world ip address>:<new port numer>. This is optional so you don't have to do it. Now back to the router pages once you put the port ranges in like 5900 to 5900 or 5904 to 5904 leave the protocol at both. I am not sure if it uses UDP port 5900 or TCP port 5900 so just leave it. Then put the ip address of your Ubuntu computer you are trying to remote out of in that box. Then hit the check mark enable and save settings and it should work unless your ISP doesn't allow it and then you either have to pay more or make some changes in your modem.

---

### Post by crjackson on 2008-08-03
> **jamesrfla said:**
> All you need to do is put what ever you want for application. For the range just put 5900 and 5900. By default remote desktop uses port 5900. You don't need to make a range from 5900 to 5910. You are just letting more people into your network. If you want for added security change to default port number to 5902 or 5909. You would need to make these changes in System>Preferences>Remote desktop on the secound tab. Check the box to use alternate port number and change it to something other than 5900. Then make the port changes in your linksys router. Then when the guy connects you have to connect differently (ex.<world ip address>:<new port numer>. This is optional so you don't have to do it. Now back to the router pages once you put the port ranges in like 5900 to 5900 or 5904 to 5904 leave the protocol at both. I am not sure if it uses UDP port 5900 or TCP port 5900 so just leave it. Then put the ip address of your Ubuntu computer you are trying to remote out of in that box. Then hit the check mark enable and save settings and it should work unless your ISP doesn't allow it and then you either have to pay more or make some changes in your modem.

Thank you very much, this is the information I need.  I haven't been able to contact him and give it a shot today, but I'm sure it will work with the provided information unless blocked by his isp.

---

### Post by crjackson on 2010-08-24
2 years later and I'm still trying to get this working....

I understand that I need to configure port forwarding on my router so that I can call out to the remote client on port 5900.  I've done that.


Other than configuring the the client (remote machine) to enable outside connections (via: System>Preferences>Remote Desktop), is there any other configuration settings to do on his (Remote) machine?

The remote machine is using a router but not any kind of firewall. Do i simply use the world ip address and the port number to connect?  Does his router need port forwarding or other configuration to receive connections outside of his local network?

Thanks for any help.

---

### Post by silverglade00 on 2010-08-24
One thing that will make both your lives a lot simpler would be to use [Teamviewer]("http://www.teamviewer.com"). It is free (as in money) for personal use, but not free as in open source. They have a Linux version now and it works very well, even passing through firewalls and everything. It is password protected. You can set it to have a permanent connection ready with the same password, or you can have it dynamically generate a new password everytime he fires up Teamviewer. In that case, he will have to communicate the new password to you some other way.

---

### Post by crjackson on 2010-08-24
> **silverglade00 said:**
> One thing that will make both your lives a lot simpler would be to use [Teamviewer]("http://www.teamviewer.com"). It is free (as in money) for personal use, but not free as in open source. They have a Linux version now and it works very well, even passing through firewalls and everything. It is password protected. You can set it to have a permanent connection ready with the same password, or you can have it dynamically generate a new password everytime he fires up Teamviewer. In that case, he will have to communicate the new password to you some other way.

Well, I'd love to give it a try but it won't complete the install on my system.  Also it's not a native Linux version, it's a windows program packaged for use with WINE.  If I can ever get the other solution to work I'd rather stick with an all Linux application.

---

### Post by carlorub on 2010-08-30
I just Downloaded Teamviewer, and it is great. Really. The only problem for Me, is the image quality... Is there something to do about it?

---

