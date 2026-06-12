---
title: "&quot;cannot determine ethernet address for proxy ARP&quot;"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Nortikal on 2008-08-26
I am having trouble with my internet connection. When I boot my computer the connection is automatically established as I have specified through the sudo pppoeconf procedure. However when I open firefox, it says connecting to google.co.uk but the status bar is blank and nothing happens.
When I enter plog in the terminal I get this:

me-desktop pppd: 
pppd 2.4.4 started by root vid0
using interface ppp0
connect: ppp0 <--> eth0
peer from calling number 00:07:BA:91:31:EE authorized
Cannot determine ethernet address for proxy ARP
local IP address 10.255.12.99
remote IP address 10.250.1.9
primary DNS address 81.91.192.254
secondary DNS address 81.91.192.254

A connection has been established because when I put sudo poff into the terminal I get eg:

me-desktop pppd:
Terminating on signal 15
connect time 117.0 minutes
sent 12133 bytes received 3248 bytes

Which shows I've been connected but when I open firefox I get a blank screen and nothing else. Eventually getting a firefox session timed out thingy.

I think the "cannot determine ethernet address for proxy ARP" is the culprit I've never seen it before - until I've been having these problems.

Any assistance will be really appreciated

---

### Post by nicedude on 2008-08-26
A question that the answer of will help anyone who tries to help you.

Did you have this connection working in Ubuntu with your pppoe config setup and then it stopped working or is this your first attempt?


Also try a simple ping when you think it is connected and see what you get, here is one that should work fine to see if you are actually connected or not.

ping -c 3 [www.google.com](www.google.com)


If this is successful then you have a valid connection but if not then I think your not really connected and authenticated but instead have an incorrect setting in your pppoe configs file. If this is so try looking at your ISP's website and see what they say about their pppoe login procedure or if you can find others via google search asking about ubuntu or Linux in conjunction with this ISP.

---

### Post by nicedude on 2008-08-26
I don't think you have a connection as your remote IP is a private network address not one I would expect to see, like one that belongs to your ISP. This might mean that your ISP is not giving you an address as PPPOE hasn't actually taken place correctly, I recommend everyone to just buy a $40 router and let it handle all your PPPOE login stuff as that is good extra security as well.

---

### Post by ilrudie on 2008-08-26
Could also simply be a dns lookup issue.  Try going to 74.125.47.103 in your browser.
If that works and you get google then your dns is messed up.

---

### Post by Nortikal on 2008-08-28
> **nicedude said:**
> A question that the answer of will help anyone who tries to help you.

Did you have this connection working in Ubuntu with your pppoe config setup and then it stopped working or is this your first attempt?


Also try a simple ping when you think it is connected and see what you get, here is one that should work fine to see if you are actually connected or not.

ping -c 3 [www.google.com](www.google.com)


If this is successful then you have a valid connection but if not then I think your not really connected and authenticated but instead have an incorrect setting in your pppoe configs file. If this is so try looking at your ISP's website and see what they say about their pppoe login procedure or if you can find others via google search asking about ubuntu or Linux in conjunction with this ISP.


Thanks for your reply. I am a complete ubuntu beginner: what is this ping -c 3all about? What do I do? I just googled it....But what next...?
I was using this pppoe config setup on ubuntu for a few months; all well and good. But my isp suspended my account over a late payment; and then when they reactivated my account; the above problem occured! And of course they don't offer support for linux systems.

---

### Post by nicedude on 2008-08-28
Ok then if it once worked and after a shutoff once you got your internet turned back on and it doesn't then this is a PPPOE configuration problem. I cannot be much help in this as even though I have a PPPOE DSL based internet I have never used PPPOE config at all since I have 5 PC's in my house and therefore use a simple $40 router to do all my PPPOE login work and then anything I plug into the router has instant internet access, this is the best solution I know of since it is a big boost to your internet security and if you buy the router then you control the router and therefore the ISP can't mess with any PC so connected. I remember back in the early days of DSL & Cable modems in the USA when they gave you Windows software you had to install to get setup, but nowadays everyone with good knowledge of these things uses a router since then it doesn't matter what ISP you use or what OS's they give support for since routers work with all OS's.

You may also have a IP address that you can log into your DSL modem with and configure it, I do and I could if I wanted to configure my PPPOE login there. If you want to PM me with the following info I will try to figure out whether you can do the same, but don't post it here send it in a PM so I might see it quicker.

Please tell me what country you are in and who your ISP is. Also tell me your DSL modems model number and brand. Armed with that info I can try to lookup what your options are. But I stress once again that if $40US is not allot of money to you that you should purchase a netgear or linksys basic router ( I suggest newegg.com for good deals and service ), since with a simple router you can forget about having to use PPPOE config to use the internet and get better security to boot. A router is the best investment anyone can make for internet connection purposes and general security. If you do get a router I would be glad to help by giving tips on how you should configure it.

PS and ping is a command to use at the command line in a terminal, it sends data to a target address and tells you if the info made it there. Sometimes it is a better test than whether your webbrowser works since it is a much more simple operation and if you are connected to the internet correctly the ping will work and if it doesn't your not. It also can tell you what sort of millisecond response time your network has at various destinations of the data's journey, allowing you to troubleshoot where a slowdown is occurring. Also the other guy who said this could be a DNS problem could be right as well so if you do the following 2 ping commands this would allow you to eliminate that possibility from the equation. The -c 3 means send 3 ping packets FYI.

THIS ONE WILL PING GOOGLE BY DNS NAMED ADDRESS
ping -c 3 [www.google.com]("http://www.google.com")

THIS ONE WILL PING GOOGLE BY IP ADDRESS
ping -c 3 74.125.47.103

If both work then you are connected and this is some weird browser problem ( not going to be the case but is still a 1 in a million )

If first one fails and second one is successful then you have a Internet connection but your DNS is screwed up.

If both fail then you are not getting connected correctly via PPPOE and that is your problem. I think this will be the case but I can't say for sure until you try these, please let me know what one of the scenarios is your situation. To open a terminal to paste these commands into look at top menu bar -> Applications -> Accessories -> Terminal

Please PM me all the info I asked for and the outcome of those ping commands and I will try to help you fix it ( to send PM just click on my name and select "send private message" )


nicedude

---

### Post by lenci on 2008-11-03
I have exactly the same problem. I can ping and browse sites only by their IP address. If I know the IP address, I can ping/browse them, otherwise not. It seems, like someone of you has already said, that my dns is screwed up, what to do with it? There are two entries (nameservers, no search) in my resolv.conf, this seems to be allright, as far as I remember (I'm on a different machine now) I also do have /etc/hosts file with correct entries.
I'm desperate about what is wrong, I have no idea what to do. Maybe something could have gone wrong when I upgraded from Hardy to Intrepid, couldn't it?
I use ppp connection (pppoe), I also found the message 'cannot determine ethernet address for proxy ARP' in syslog (or plog) from pppd, I have never had this problem before...
Please help me...
thanks

---

### Post by lenci on 2008-11-07
oh, forget it, I've already solved my problem...interesting, a week ago there were entries in my resolv.conf and it did not work...now there were no entries, so I added nameservers (the same as there were a week ago) and now it works, great:)

---

