---
title: "getting access to server behind router"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by jcr1 on 2008-06-17
Hi all,

Been setting up a home server. I am trying to set up remote access. This is working nicely within  my LAN, using apache and tightvnc java applet thingy, so via a web browser.

But I am struggling a bit with understanding all the port forwarding necessary to access this from outside over the internet.

The index.html for the remote java control within my /var/www/ folder says i am using port 5800. 

So on my router I created a 'service' called server, which listens on port 5800 to 5800. 

Then I added an inbound service to always allow 'server' to be passed to internal.ip.addy.of.my.server.

This was done following this:

[http://www.portforward.com/english/routers/port_forwarding/Netgear/DG834GT/Remote_Desktop.htm](http://www.portforward.com/english/routers/port_forwarding/Netgear/DG834GT/Remote_Desktop.htm)

I also registered with no-ip.com to get a name to go to to solve the dynamic ip problem (not sure if i set that up right either). 

So in a browser i go to [http://'myserver'.myvnc.com](http://'myserver'.myvnc.com) and it goes to the log in window for my router! Which I didnt like at all as the username and password are default... so anyone could access my router! So I deleted that no-ip thing and changed the default pass on my router!

So I guess somewhere I havent set up the correct port forwarding to forward that request onto the server to get to the /var/www/ directory.

Hope someone can help!

---

### Post by Kebabman on 2008-06-17
The first problem is that you obviously have external access to your routers control panel enabled so you will want to disable that. It has nothing to do with using no-ip so that should be fine once you disable that.

The second problem by the sounds of it is that you are listening on port 5800 but not specifying that when you attempt to connect.

Instead of going to :

[http://'myserver'.myvnc.com](http://'myserver'.myvnc.com)

You should put the port number in as well otherwise it will default to port 80:

[http://'myserver'.myvnc.com:5800](http://'myserver'.myvnc.com:5800)

This should redirect it to the correct port for your vnc.

Hope this helps.

---

### Post by jcr1 on 2008-06-17
Ah thats all very interesting, thanks for that! Will look into all that today. 

Another question, when I go to [http://'myserver'.myvnc.com:5800](http://'myserver'.myvnc.com:5800) can I add a /directory to go to another directory within /var/www/?

e.g. [http://'myserver'.myvnc.com:5800/directory](http://'myserver'.myvnc.com:5800/directory)

Many thanks.

---

### Post by Kebabman on 2008-06-17
Yes that should be fine. There is no difference running a web server on a different port except having to specify the port number inside the url.

---

### Post by jcr1 on 2008-06-17
OK, so am I understanding this right...

In my /var/www/ I dumped the tightvncjava stuff. I edited the index.html like so fromanother tutorial on here:

```
<HTML>
<TITLE>
TightVNC desktop
</TITLE>
<APPLET CODE=classes/VncViewer.class CODEBASE=classes/ WIDTH=800 HEIGHT=632>
<param name=PORT value=5800>
<param name="Open New Window" value="yes">
</APPLET>
<BR>
<A href="http://www.tightvnc.com/">TightVNC site</A>
</HTML>
```

Where it specifies the PORT number, I could put anything (that's not already in use) as long as I then specify the same number in my router to forward to the server and then put the same number after the url?

How can I find out what ports I can use and which I can't? Are there specific ports used for specific purposes, just out of custom or because they only work in certain ways?

Thanks.

---

### Post by jcr1 on 2008-06-17
Well I can't seem to get this quite right I don't think.

If I just go to my external addy i can log into my router, but if i go to my ipaddy:5800 then i just get a "Failed to Connect: Connection was refused".

Something obviously not quite right in how I am forwarding ports I would imagine...

---

### Post by Kebabman on 2008-06-17
Ah right ok. I thought you were saying your web server was running on port 5800 where it is your vnc server that is running on that port and it is an applet. You don't need to specify the port in the url as I previously stated in this case.

Your problem now is that you still have your routers control panel accessible from the outside world (WAN) which you really need to disable. When you have done that you need to forward port 80 through your router to the IP address of the machine on your network running the server.

---

### Post by lavinog on 2008-06-20
the ports should be forwarded correctly. Have you checked to see if the vncserver is setup correctly?
try accessing it from within your lan on another computer...if you get the same error then the problem is not with your router.
goto [http://'ip](http://'ip) address of server':5800

how are you setting up the java vnc server?

---

### Post by jcr1 on 2008-06-23
OK.

At one point this was working, as I got a friend over the internet to go to 'my-no-ip-addy.myvnc.com' and it worked! The java applet loaded and opened with a password. Great I thought.

Now this weekend, I went away for the weekend, and wanted to see it working for myself but it wouldn't work!

I have installed LAMP server and then in the var/www folder dropped the tightvnc java viewer stuff, edited the index.html to get it working.

This weekend it would not work. I kept getting (after a wait) a "connection timed out" error. 

What would cause a connection timed out error?

This also worked when I tried to login via a terminal using ssh.

---

### Post by jcr1 on 2008-06-23
in retrospect, this I am thinking could well be caused by not setting a static IP address on my server.

Usually on my lan, there is my laptop running before I turn the server on (because I am still playing with it) so it always gets assigned the next available addy. This weekend, I turned it on when the laptop was off, so it probably got a different IP addy, therefore port forwarding in the router would have been sending to the wrong ip address.

DOH!

I will set it to static IP address.

---

### Post by lavinog on 2008-06-23
The server needs a static ip address on your network for port forwarding to be effective.
You also should make sure that when your external ip address changes your no-ip address is updated.
There are programs you can install on your server that periodically checks your external ip address for changes and updates the dns servers for you.
here is a how to on how to do that.
[http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html]("http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html")

---

### Post by Kebabman on 2008-06-23
That being said, most modern home routers can do this automatically for you. There is quite often a setting to automatically update dyndns, no-ip etc somewhere in your routers config.

---

### Post by Joeb454 on 2008-06-23
Kebabman is right, my router (Speedtouch 7G) supports this directly, I just enter the log in name and password in the router, and what the domain is allocated to, and voila :)

(I use DynDNS if that matters :))

---

### Post by lavinog on 2008-06-24
some older linksys routers do not handle dyndns correctly which in the end causes them to be blocked. 'we intend to block all access to our site by WRT54G routers that have not been upgraded.' [http://www.dyndns.com/news/releases/service_availability_notice_for_linksys_router_owners.html]("http://www.dyndns.com/news/releases/service_availability_notice_for_linksys_router_owners.html") Of course updating the firmware fixes this problem.

here are some more reasons why using a software client could be better:
[http://www.dyndns.com/support/kb/cat_routers.html]("http://www.dyndns.com/support/kb/cat_routers.html")

---

### Post by jcr1 on 2008-06-24
Well this is odd. I have static ip on my server now. 

In work I cannot get anything out of it. I cannot ping it, nor obviously connect via vnc java (browser), vnc stand-alone viewer or putty.

Could it be my work network stopping it? But it seems the same symptoms when I tried it from my parents house, which is just normal broadband. Someone else managed to connect.

I always get a "timed out" error, 10060 on putty.

Very annoying.

Hope someone can point me to some things to check.

---

### Post by lavinog on 2008-06-24
if you are trying to connect via ssh/putty you need to setup port fowarding for port 22 (or whatever your ssh port is...22 is default)

---

### Post by jcr1 on 2008-06-24
ok home now (which helps) looks like I need to set up what you mentioned to keep my no-ip addess up to date, as it IS now different. This will explain why hopefully.

Watch this space.

Thanks for the link.

---

### Post by jcr1 on 2008-06-24
BTW port 22 is set up.

All this port forwarding for remote control...is it just incoming I need to forward in my router, as there is options to set all these ports for outgoing too?

---

### Post by jcr1 on 2008-06-24
perfect! Well at least as far as I installed no-ip on my server and configured it and instantly on my account on no-ip.com the correct ext. ip-addy updated!

Thank you!!

---

### Post by lavinog on 2008-06-24
> **jcr1 said:**
> BTW port 22 is set up.

All this port forwarding for remote control...is it just incoming I need to forward in my router, as there is options to set all these ports for outgoing too?

It is all for incoming traffic. What you are doing is setting up rules that your router uses to direct incoming network traffic...the outgoing traffic is handled by the recipients router.

---

### Post by jcr1 on 2008-06-25
ok well now I am in work, things are looking promising. When i go to no-ip address in a browser I am getting to the right page! My page is just the basic java applet and then the Tightvnclink at the bottom. This displays so I know I have things set up correctly that far.

But as I knew was going to happen, the java applet does not load here in work, as java is not enabled/installed and I do not have the permissions to do this so will not be able to use the java applet.

I am also trying to use putty (standalone) and a free standalone windows vncviewer (from realvnc) both of which are still giving me a connection timed out error! 

So I am wondering if this is just something to do with the setup of the network here in work preventing me from making the connection?

Any other options I could look at to log in from work, without the need to install software (as I can't)

---

### Post by jcr1 on 2008-06-25
reading round a bit, it may well be possible/likely that my work network administrator is blocking outgoing port 22. This is of course the port ssh wants to use. So can I config my ssh to use a different port, that my work is not likely to be blocking?

But then this doesn't explain why the vnc viewer is getting the same error listening on port 5900... unless this is another popular port to block?

Can I just use any port I want, as long as I specify it in the config, and router?

---

### Post by lavinog on 2008-06-25
did you setup port fowarding for port 5900?
It is possible that port 22 is blocked, but I dont know why...I had a router that would not allow me to setup port forwarding on port 22...it was undocumented why, but i just set it up with a different port.
Using non standard ports for personal servers is actually preferred from a security standpoint. Hackers/script kiddies will scan for the common ports used for remote access.

I should have mentioned that if you can get ssh access to the computer you can do everything through ssh including remote desktop.
this is how to access it from linux terminal
```
ssh -XC -p {port} name@host
```
It has been a while since i used putty, but you have to enable X11 Fowarding in the tunnels section of the connection properties.
save your connection
then after you login type xclock and if you see a clock on your screen it worked.
You can get the whole desktop to show, but usually it is best to learn the commandline commands to start the program you want. If you have open office installed on your server you can type openoffice and it will display on the remote computer.

Another nice thing about ssh is tunneling. I only need one ssh port forwarded to my server. through that one port I can access all of my computers.

---

### Post by jcr1 on 2008-06-25
I like the sound of what you are talking about...I had this in mind, i.e the concept of one 'path' or 'tunnel' through which my whole lan can be accessed. But I think one step at a time for now lol.

Tonight, I will reconfigure ssh to go through a different port and see if that helps (update port forward too) Does it matter what number port I use? As long as nothing else is using it...

Port 5900 is forwarded in my router... just going to my no-ip address does forward me successfully to my server... I just can't use the java client here, so that is working ok. I think port 22 must be being blocked.

Thanks again.

---

