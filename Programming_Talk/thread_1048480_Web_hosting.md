---
title: "Web hosting"
date: 2009-01-23
forum: Programming Talk
---

### Post by PaulM1985 on 2009-01-23
Hi

This is something I know nothing about so apologies if it is really basic.

I want to be able to host internet files on one computer and view them from another using the internet.

I have downloaded and installed apache tomcat from the website, on to my laptop, got it running (I think) and I am able to see the example pages that come with it using the [http://localhost:8080/](http://localhost:8080/).  Am I able to type something in the address bar in a web browser on a different computer so I can see these files on my laptop?  Am I some of the way there?

Any advice would be greatly appreciated.

Paul

---

### Post by curvedinfinity on 2009-01-23
Heya,
First, if you run a NAT Router of some kind, you'll have to set it up so it forwards port 80 or 8080 to your PC. Then you can access that computer through your internet IP address, which is assigned by your ISP to your router. This is a different address from the subnet IP address assigned to your computer by your router.

You can find out what your internet address is with an address-echoing website like [http://www.ipchicken.com](http://www.ipchicken.com)

---

### Post by PaulM1985 on 2009-01-23
Hi

I think I have figured it out.  Thanks for the help.  I am having trouble with my BT router allowing it through so I will ring them up and get them to sort me out.

Thanks again.

Paul

---

### Post by Mud.Knee.Havoc on 2009-01-23
> **PaulM1985 said:**
> 
Am I able to type something in the address bar in a web browser on a different computer so I can see these files on my laptop?  Am I some of the way there?


Paul, if I am understanding you correctly, there are a couple things that you'll need to do.  You already have apache running on your local machine - this is a good start!

The first is sign up with dyndns.org.  This is a free service that allows you to assign a static name to your computer, which probably has a dynamic IP.  This way, you can just surf to, for example, pauls-computer.dyndns.org and no matter what IP your computer is using, it will point at your computer.  This requires the use of ddclient (or a similar program - some routers are dyndns compatible, as well) which makes sure that dyndns.org always knows what IP address is assigned to you.

Once this is up and running, you'll need to open ports in your firewall (your router is often a hardware firewall).  If you want to host a website, this usually means port 80.  Although it seems that you've already got it to run at port 8080, so you'll need to either change this to 80 or keep remembering to specify :8080 every time you want to get there.  

Now, if I'm browsing the web somewhere, I don't need for you to be sitting at your computer to tell me what your current IP address is, I just put pauls-computer.dyndns.org(:8080) into my browser and I'll see your website.

This can be used with other services.  You may want to run an ssh server, which will let you log into your machine remotely, for example.  Now you'll be able to ssh into (another example) [email]paul@pauls-computer.dyndns.org[/email] from anywhere in the world.

Before actually setting up anything like this, make sure to search the forum (or just google) for some tips.  Especially with ssh, there are a lot of things that you can do to increase security (use a non-default port, etc).

I'm assuming that BT is British Telecom (you *did* say you'll "ring" them and not "call" them, so I'm pretty confident you're British). :)  Watch out - a lot of ISPs don't want you to run a server and often explicitly state in the terms of service that you cannot do so.  You still can, as long as you have very little traffic going to your site, and *hopefully* they won't find out.  

In Canada, the major ISPs won't allow it, so that was one reason why I chose a smaller provider.

EDIT: I forgot to mention - it's important to google something like 'ubuntu ddclient' for instructions on setting up ddclient.  It's quite easy, but there is some initial configuration that must be done.

---

