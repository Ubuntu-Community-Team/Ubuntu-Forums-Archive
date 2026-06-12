---
title: "2 problems setting up LAMP server"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-08-28
alright the first would be how do I get my router to forward to my computer when my ip address is entered? I'm using a netgear. the second would be how do I delete and add files to my servers directory? it doesn't show the option to delete or to make new folders and documents. any help will be greatly appreciated! 

thank you

---

### Post by stoneybroke on 2008-08-29
You have not said if your server is on a network or not mine is but I use a different router than you do although if you have the option in your router for Port Forwarding set up port forwarding to your server's IP address (hopefully the IP address of your server is static eg 192.168.0.100) 

Here is my configuration settings from my router.


Create the port forwarding rules to allow certain applications or server software to work on your computers if the Internet connection uses NAT.
		
  	Application Name 	External Packet 	Internal Host 	Delete 	 
IP Address 	Protocol 	Port 	IP Address 	Port
  	Secure Web Server 	ALL 	TCP 	443 	192.168.0.100 	443 		 
  	Web Server 	ALL 	TCP 	80 	192.168.0.100 	80 		 
  	FTP Server 	ALL 	TCP 	21 	192.168.0.100 	21


As to your second question you might have to be a root user to add/remove directories. Or poss use a FTP program like gftp.

Hope that helps.

---

### Post by indytim on 2008-08-29
Set the owner and group of /var/www to your login id.  That will enable updates to the directories therein.  By default it's set to root.

IndyTim

---

### Post by RadiationHazard on 2008-08-29
I'm the only user on this computer. it's my personal home computer. and I tried the ip for my router and that didn't work...:(


edit: i just figured out my ip. it's 192.168.1.1 so I'm going to try to do the router settings like you stated.


Edit 2: when I click the port forwarding this is what comes up?(look at screen shot)

---

### Post by stoneybroke on 2008-08-29
Yep thats the configuration you need on your router to create a static IP address for your servers if your ISP gives you a dynamic IP address when you connect to the internet it will mean that no one will be able to connect to you when your router is turned off and on again as your ISP IP address will change, you can check your internet IP address here

[http://whatismyipaddress.com/](http://whatismyipaddress.com/)

then turn off your router for 1/2 hour or so and try again if your IP has changed then your ISP is giving you a dynamic IP address every time you connect so if you want a free static IP address go here,

[http://www.dyndns.com](http://www.dyndns.com)

Read everything there and don't forget you need to download a small program that will keep checking your ISP and your computers IP address for a static IP address to keep working.

If you need more info just ask ok.

---

### Post by RadiationHazard on 2008-08-31
those router settings can't be right because when I put in my ip nothing happens...=[

---

### Post by stoneybroke on 2008-08-31
Can you tell me what kind of a server you are setting up? if its a web server and you have installed the Ubuntu Server edition you have a default web page already installed if everything is working entering [http://localhost/](http://localhost/) or just localhost or 127.0.0.1 or http://<your ip address> e.g. [http://192.168.0.100](http://192.168.0.100) in your browser should show you this,

It works!

If you have set up a FTP server entering [ftp://localhost/](ftp://localhost/) or ftp://<your ip address> will show your ftp directory contents.

You should also make sure that your computer has a static address (not using DHCP) then use port forwarding to point to that address in your router.

You could also look at this how to [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

That might help you as well.

---

### Post by Iowan on 2008-08-31
A [similar thread]("http://ubuntuforums.org/showthread.php?t=895785") you might check.

---

### Post by tommynz1975 on 2008-08-31
other ways to see your ip address are

[http://my-i-p.com]("http://my-i-p.com/")  and you can see some information about your self including a map to show where they think you are

---

