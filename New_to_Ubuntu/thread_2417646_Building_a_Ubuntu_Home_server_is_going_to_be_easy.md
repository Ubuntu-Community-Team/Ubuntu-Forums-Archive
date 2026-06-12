---
title: "Building a Ubuntu Home server is going to be easy"
date: 2019-04-25
forum: New to Ubuntu
---

### Post by elingdreamer on 2019-04-25
Building a Ubuntu Home server is going to be easy or so I thought. 

So, I am trying to build a private server for personal cloud/Plex/web/compute server for home use. I repurpose an Acer m1930 PC with upgraded ram and processor and installed Ubuntu 18.10. I then managed to got docker working with Apache/mariadb/next cloud working. So far so good. I tested all this using a few laptop running Windows and Ubuntu using chrome and going to the host ip and the services's respective ports. Great!!

Now a web and cloud server needs to be able to be reach from outside my house right? So my I begin messing with the router. I done the necessary port forwarding, ddns routing to my public , obtaining a domain and cnaming to the ddns service and and finally allow traffic to the ports that I would be using .After everything was configured correctly I begin testing my setup. And here is where my problem begin . I try typing my cloud.mydomain.com , no luck . I double check the ports , triple check the IP and quadruple check the ports. Still cant find any fault. So I bootup my raspberry pi and made a simple Apache test site to verify my setup and it surprisingly works. I thought it would be the firewalls problem so I turn it disabled it completely . Still no luck . I tried flushing the iptable which messed up my the whole firewall setting so I decided I need a fresh start which mean a fresh reinstall of Ubuntu. 

Repeated all the steps except the messing up the firewall part (don't use, "sudo iptables -F" you will regret it) and still no luck. I thought it might be because of 18.10 not being stable enough for this kind of simple operation . So i went 18.04 and try things again to no one's surprise it still don't work. 

All this while the machine is located in my room the router is located in the living room so wifi is the only cheap way with needing to install fancy Ethernet cable to wire things up. So I finally gave in and move the PC and everything need to the living and setting up. My prayers was answer when I say the default Apache html page thought the domain name that I purchased. 
We finally arrived at this point ,where I know that my server is working and some what pin point the problem to the wifi setup. 

Incoming request to the server via WiFi seem block by something on the server. I also disabled the ufw to make sure it's not the firewall. Anyone have any idea what of problem am I facing ? 

I want to PC in my room so I really wish anyone help me with this. 

Thank you for wasting 5 min of your time reading the first 2/3 unimportant ramble of word.

---

### Post by Tadaen_Sylvermane on 2019-04-25
One of 2 things is happening here.

You didn't mention the part where you got hold of your ISP and asked them to open the proper ports. Most home internet connections will keep those ports closed for this exact reason. They may be open on your personal router, but not the ISP stuff. You need them to open the ports on their end. They will most likely demand that you upgrade to a business class line if you want this feature.

Other possibility. At my church we have security cameras with a web interface to view. We have a business class static ip with ability to open ports. However I have to use 2 different addresses to access the system. Our public IP + port won't work if I'm inside on the local lan. Only at another location. So I have to use the local ip to view when I'm there, and the public ip when I'm not. I can't explain why this is, I just know it is an issue.

*EDIT* A sidenote. Server is meant to be long term stable. Means less screwing around with it. Stick with 18.04. 5 years of support or between upgrades beats every 6 months.

---

### Post by elingdreamer on 2019-04-25
Yup i requested that from them and they did open the port. Like I said earlier I verified that using a raspberry pi test server which I am able to connect from outside of the local network. I also verified that my portfowarding works.

---

### Post by TheFu on 2019-04-25
Stay LTS release for any server, unless there is a specific bleeding-edge-hardware reason. Agreed.
Avoid wifi on any server. It is a bad idea for many reasons.  Powerline networking would be better than wifi, just be prepared for only 10% of the advertised speeds from the box - sorta like wifi.

If you insist on using wifi, look for power management and automatic shutdown of the networking.

Stock nextcloud will run fine on a raspberry pi, BTW. If you plan to get another Pi, there are better alternatives, perhaps 2x faster with GigE and USB3 and SATA for a little more money.

If only you will be accessing the nextcloud instance, might I strongly suggest not having that machine open to the internet?  Use either a VPN or SOCKS proxy over ssh to gain access. Which is easier depends on the client(s) used.  A linux laptop can use the ssh-SOCKS proxy much easier.  Pretty much all the other clients are better with a full VPN.  Both VPN and ssh effectively become network authentication, so only "good guys" get to have access.  Securing any php webapp is a difficult thing.  It is a non-trivial problem.

BTW, plex works without any plex account from anywhere in the world with either the VPN or ssh SOCKS proxy. Just use the web interface.

I've had 3 IPs and none of them minded or blocked little personal websites.  The did block in/out port 25 SMTP and inbound port 20-21 FTP traffic.

There are security reasons to block accessing the public IP from inside the LAN. Google will explain why that is useful for 99% of the world. It is usually a setting in the WAN router, assuming you have control over it.

I'm not a fan of prebuild docker things from people I don't trust. Please be very careful using those.  [https://techbeacon.com/security/hackers-love-docker-container-catastrophe-3-2-1](https://techbeacon.com/security/hackers-love-docker-container-catastrophe-3-2-1)

---

### Post by elingdreamer on 2019-04-26
Thank you for the advice you given  , i am thinking just loading up LTS and moving the system next to the router. i will so be looking into ssh sock and other stuff you mention .

---

### Post by TheFu on 2019-04-26
"ssh SOCKS proxy" - this is a way for all TCP traffic from a web browser to be sent through an ssh tunnel to another machine.  I've posted my scripts for this in these forums a few times. The browser must be configured for it. Usually that is in the network settings of the browser.  The client machine has to have made the ssh-tunnel connection with specific params and the server has to be up.  The ssh-server doesn't need any special settings that I recall.  If you can ssh in, then you can run an ssh-tunnel in too.

---

