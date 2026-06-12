---
title: "Geting Putty to work?"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by melbs on 2008-08-28
I am able to use Putty on this lap top computer and SSH into my desktop computer however when I am on my work computer or another computer I can't seem to log in. I do everything the same. Does anything else need to be installed? Keys or something? I also have Virtual Box program on this lap top, if that has anything to do with it. Thanks.

---

### Post by KevinD_Atl on 2008-08-28
[FONT="Tahoma"]If you have a router in between, you will need to forward your ports through your router. If your IP is say 192.168.1.101 then forward port 22 to that IP address selecting TCP protocol. [/FONT]

---

### Post by melbs on 2008-08-28
Okay, this is going to be a really really stupid question but we are in beginner talk, right?

I am SSHing into my desktop computer by using either Putty or Virtual Box and using ssh 192.168.1.101 in command line. It works. Is that my desktop computer IP or does that only work because my lap top and my desktop computer are on the same router (wireless)?

I thought 192.168.1.101 was my desktop computer IP and I could SSH into it from any other computer wherever..but since you used it as an example I am thinking that is just a made up one people use for examples?

I thought I was understanding the SSH a little better but now I've taken a few steps back! I am thinking the only reason why I was successful at connecting to my desktop computer is because both the computers are using the same router. Any help for a confused girl? :) 

Sorry, I've been trying to google and search this stuff before I ask because I have been having so many questions but I'm not getting many answers. Thanks.

---

### Post by ztirffritz on 2008-08-28
Often wireless routers have DHCP enabled.  This means that the IP Address of your computers may change occasionally, so perhaps your IP address that you're using is not correct any more.  When you use SSH the command from the CLI usually looks like:

ssh [email]username@192.168.1.xxx[/email] 

where 'xxx' is the part of your IP address that might be changing.  'username' is the name of the user on the remote machine that you want to connect as.  Verify the IP address of the remote machine that you are connecting to and try again.

---

### Post by melbs on 2008-08-28
I am able to connect using Putty and Virtual Box right now with ssh 192.168.1.101 .. then it asks for a password, it works.

What I' confused about is if that is really my IP address? People use it as an example IP so I don't think it's my "Real" IP address.

When I am on other computers, other than my lap top, I can't connect but I use the same IP now and it works on my lap top.


EDIT: Okay, I have tried searching some more and it looks like the IP 192.168.1.101 is assigned to my computer because of my router.

Questions - 

1.) Am I able to SSH into my computer only because the computer I'm on is on the same router?
2.) ..this is going to be stupid :( .....am I able to SSH into my desktop computer from computers anywhere (not on that router or network) or will that not work? If I can connect to my computer at home via SSH how do I do that? Do I need to use a different IP?


Thanks.

---

### Post by kindofabuzz on 2008-08-28
> **melbs said:**
> I am able to connect using Putty and Virtual Box right now with ssh 192.168.1.101 .. then it asks for a password, it works.

What I' confused about is if that is really my IP address? People use it as an example IP so I don't think it's my "Real" IP address.

When I am on other computers, other than my lap top, I can't connect but I use the same IP now and it works on my lap top.

Yeah if you're trying to connect frm a computer not on your local network of course 192.168.1.101 isn't going to work.  You have to have port 80 open and forwarded to the computer you want to connect to.

---

### Post by melbs on 2008-08-28
"You have to have port 80 open and forwarded to the computer you want to connect to."

Is that done on the computer I'm currently on or the I'm SSHing into? Where is this done?

---

### Post by juanoleso on 2008-08-28
You would have to setup the port forward on the router and if you have a firewall open the port on that as well.  Try this website

[[COLOR="Blue"]http://portforward.com/english/routers/port_forwarding/routerindex.htm[/COLOR]]("http://portforward.com/english/routers/port_forwarding/routerindex.htm")

Select your router from the list.  It might be able to help you setup the port forward for ssh from outside your router.  Your router will also tell you what your (it's) outside IP address is.  That address is what you will use if you are trying to connect from somewhere not inside your network.  If you haven't "purchased" an IP address from your ISP then it will most likely change periodically.  Thats another problem.

[[COLOR="Blue"]This tutorial[/COLOR]]("http://ubuntuforums.org/showthread.php?t=383053") starting at number 7(the whole tutorial really applies here, though) will help with that.

---

### Post by melbs on 2008-08-28
So it IS possible to connect to my computer from a remote computer not on the same network - I just have to set some options and things on my router. For a second I thought maybe I had to do something with a server or "putting" my computer on the Internet - was a bit confused.


Are the changes I have to do (port forwarding things) just on my router? Is there anything I have to do, set or install on the computer I want to SSH into or the computer I am using to SSH?


I'm pretty sure I found the public IP address for my computer. Thanks for the links.

---

### Post by yawnzzzz on 2009-03-03
Here's kind of an overview.

When you're connected to the internet using a router, then the router is really the only thing that has an ip address to the outside world.  So you need to determine that ip address.

When you're connected to your router, click this link:
[http://www.ip-adress.com/](http://www.ip-adress.com/)

It will tell you your 'public' IP address.  This is the same for every computer connected to your router, and this is the IP address that you'll need to SSH into when you're not at home.

Now, the 192.168.1.101 is the address of your computer on your network.  It's called a 'private' IP address. It only lets computers on your network communicate.  If you see 192.168.X.XXX, then it's a private address.

When you SSH in to that public IP address, your router will be confused on what computer on your network that you want to connect to.  So, how this is handled is thru port forwarding.  For example with SSH, the default port is 22.

To set this up, you need to connect to your router.  My guess is that the 'private' ip address of your router will be 192.168.1.1.  If you type that into a web browser, you'll likely see a screen asking for a username and password.  You can search online to find the defaults for your router if you've never changed them.  For example, my Linksys router defaulted to blank for username and 'admin' for the password.  Once you've connected, look for an area called port forwarding.  It will likely ask for a few bits of information.  Probably something like a name (which will just be used so you can remember what it was for), a range of ports, and an IP address.  It also might have a checkbox to enable/disable.  So, for the name, you can type SSH, for the ports you'd use 22-22, for the IP address you'd use 192.168.1.101, and if there's an enable checkbox, then you'd want to make sure it's checked.

Now that all of that's set-up, you can type your public ip address into your SSH client along with port 22 and it will find your computer.  The public IP address points it at your router.  Then the router looks at port 22 to see if it's pointed at a computer on the network.  It is, so it sends it to that ip address (192.168.1.101) which is the computer you've been looking for.

---

