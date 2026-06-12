---
title: "Remote Login??"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by KingTermite on 2008-07-01
I've searched through many threads and tutorials and thought this would be a common problem/question, but I'm not finding the exact answer I need.

This Ubuntu (7.10) pc needs to now be accessed by another user (I added as an admin). He needs to remote login to this computer, securely from his work desktop computer **(Windows OS)**.

I enabled the remote desktop and tested it out. It only seems to work if somebody is already logged in and you "take over" the control of the window. I need to be able to get to computer and login with his own session.

What do I need to enable/install for that? And what is the easiest/best thing for him to use as the client to access this machine?

---

### Post by benfindlay on 2008-07-01
Try this guide: [http://ubuntuforums.org/showthread.php?t=122402]("http://ubuntuforums.org/showthread.php?t=122402")

He'll need to remember to log out when finished though, as the session stays active unless you log out.
The connection tunnels through SSH, so its ultra secure. He can use putty as a free SSH client on windows, along with the stand alone tight vnc exe to remote connect to your machine.

Hope this helps!

---

### Post by KingTermite on 2008-07-01
Cool...thanks. Trying out now.

---

### Post by Inxsible on 2008-07-01
you might also want to have a look at NXServer....which IMO, is much faster than VNC.

And you can NX over SSH too...so its secure as well.

---

### Post by cariboo on 2008-07-01
If you want to view the remote desktop in windows you can use vncviewer or one of it's derivatives to accomplish this.

Jim

---

### Post by KingTermite on 2008-07-01
> **cariboo907 said:**
> If you want to view the remote desktop in windows you can use vncviewer or one of it's derivatives to accomplish this.

Jim
No...that was one of the original problems. I don't want to just view an existing desktop, I want to be able to login remotely and use the computer.

I tried the first solution provided and installed putty on my computer here (my windows/work one). It won't connect ("connection refused"). Do I have to specify a certain port? Not specify a port (defaulted to 22)? Open up the port on the computer? How do I connect?

---

### Post by KingTermite on 2008-07-01
Putty also seems to only be a terminal client. Can the remote user do normal xhost login and be able to run any of the graphical programs? Or will it be terminal only? I'd like him to have ability to run apps too.

---

### Post by Inxsible on 2008-07-01
> **KingTermite said:**
> No...that was one of the original problems. I don't want to just view an existing desktop, I want to be able to login remotely and use the computer.

I tried the first solution provided and installed putty on my computer here (my windows/work one). It won't connect ("connection refused"). Do I have to specify a certain port? Not specify a port (defaulted to 22)? Open up the port on the computer? How do I connect?You will also have to open the port (22 or any other you chose) in the firewall. you can use firestarter to do that. You will also have to forward that port in your router if you use one.

> **KingTermite said:**
> Putty also seems to only be a terminal client. Can the remote user do normal xhost login and be able to run any of the graphical programs? Or will it be terminal only? I'd like him to have ability to run apps too.As I already mentioned, NX is a way to login remotely and use the computer. It also gives you a much better graphical usage than VNC, IMO.

Having said that, PuTTY can also forward X, provided you have setup your sshd_config correctly.

---

### Post by KingTermite on 2008-07-01
I looked at NX (or rather tried to). I can't even get to web page because apparently our IT department thinks its a site we don't need to be going to. :confused:  Yea! IT keeps me from doing legit work AGAIN.

It looks like I'll have to stick with Putty. How can I open port? I didn't install any firewall, and its not installed by default, is it (7.10)? Shouldn't all ports be open then?

---

### Post by KingTermite on 2008-07-01
Also should mention that when I tried that tutorial, I attempted the local test with the "vncviewer localhost:1" command and it seemed to get in to an infinite loop of opening vnc sessions. Is that a problem?

---

### Post by benfindlay on 2008-07-02
With vnc installed you run your X applications through a tunnel in putty. Go to the SSH>Tunnels section and enter 5900 as the source port and 127.0.0.1:5901 into the destination port and click to add it. Don't forget to click save on the session page so you don't have to do this every time!

Then once you have logged into SSH, you launch your vnc client and put 127.0.0.1 ad the address!

I'm not sure about NX as I've never used it, but I would imaging you point it at the localhost (127.0.0.1) address like you do with vnc

Hope this helps!

---

### Post by Inxsible on 2008-07-02
> **KingTermite said:**
> I looked at NX (or rather tried to). I can't even get to web page because apparently our IT department thinks its a site we don't need to be going to. :confused:  Yea! IT keeps me from doing legit work AGAIN.

It looks like I'll have to stick with Putty. How can I open port? I didn't install any firewall, and its not installed by default, is it (7.10)? Shouldn't all ports be open then?Ubuntu comes with a default firewall called iptables and IIRC, everything is blocked. So you will need Firestarter to open the ports you are interested in. You also need to forward the ports in your router - if you use one.

---

### Post by wootah on 2008-07-02
> **Inxsible said:**
> Ubuntu comes with a default firewall called iptables and IIRC, everything is blocked. So you will need Firestarter to open the ports you are interested in. You also need to forward the ports in your router - if you use one.

Uncomplicated FireWall -> ufw

It has been added in Hardy. Check it out. From a small tutorial ([http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)):
> 
**Install UFW in Ubuntu** Currently this firewall package is available in Ubuntu 8.04
 sudo apt-get install ufw
 This will complete the installation
 

Turn firewall on and off (&#8217;disable&#8217; is default ACCEPT)
 # ufw enable|disable
 

Toggle logging
 # ufw logging on|off
 

Set the default policy (ie &#8220;mostly open&#8221; vs &#8220;mostly closed&#8221;)
 # ufw default allow|deny
 

Accept or drop incoming packets to (can see what services are available with &#8217;status&#8217; (see below)). can be specified via service name in /etc/services, &#8216;protocol:port&#8217;, or via package meta-data. &#8216;allow&#8217; adds service entry to /etc/ufw/maps and &#8216;deny&#8217; removes service entry from /etc/ufw/maps. Basic syntax:
 # ufw allow|deny [service]
 

Display status of firewall and ports in the listening state, referencing /var/lib/ufw/maps. Numbers in parenthesis are not displayed to user
 # ufw status
 
**UFW Examples**
 Allow port 53
 $ sudo ufw allow 53
 

Delete Allow port 53
 $ sudo ufw delete allow 53
 

Allow port 80
 $ sudo ufw allow 80/tcp
 

Delete Allow port 80
 $ sudo ufw delete allow 80/tcp
 

Allow port smtp
 $ sudo ufw allow smtp
 

Delete Allow port smtp
 $ sudo ufw delete allow smtp


 Allow fro Particular IP
 $ sudo ufw allow from 192.168.254.254


 Delete the above rule
 $ sudo ufw delete allow from 192.168.254.254



---

### Post by KingTermite on 2008-07-02
Still nothing working right.

It seems port is 5901,right? I run the "netstat -taupn" command it shows 5901 is listening, so I shouldn't have to worry about firewalls and opening ports, right?

I set Putty as benfindlay mentioned, but it still does not connect. Can't seem to get Putty to connect at all.

I can VNC in just fine, but that just lets me see my already open desktop. I want to be able to get there and "log in".

---

