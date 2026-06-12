---
title: "VPN questions."
date: 2015-11-11
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-11-11
Still learning stuff.  :KS

I intend on using OpenVPN on my server so to access Owncloud content over the internet.  I wont move to hasty down that path until I fully understand how vulnerable I might be making myself.  Perhaps someone can enlighten me a bit.

The other area I'd like to explore, and perhaps gain some understanding, is 3rd party VPN solutions and the purpose.

I understand I can install and implement OpenVPN on my own server so to access my resources over the internet, so, what is the value-add of a 3rd party subscription based VPN service providing me?  Is it mainly used just to mask my geography from various services?  i.e. Netflix regional restrictions, etc?  

I'm looking for a basic understanding of these VPN elements...  Hopefully someone can shed a little light on the subject for me.

---

### Post by TheFu on 2015-11-11
An  external VPN provider is desireable if you don't trust your ISP, if they may watch your connections (and you rather they didn't) or if you want the location you appear to be somewhere else in the world, or just across town.

For example,  AT&T is rolling out 1Gbps service, but they want their customers to agree for ALL their traffic to be watched and sold to marketing companies. People want the speed, but not the lack of privacy, so they get a VPN. The VPN provider might be doing the same thing, who knows?

The purpose to run your own VPN is for secure, remote, access to your LAN from anywhere in the world.  If you have a need to have all traffic, always, from every remote location you might be, go back to yuor home before heading back out onto the internet, then this is a good solution.  You've probably heard to never use any public wifi without a VPN? This is one of the solutions to that. It is probably the easiest, yet secure method available to smartphone users as well.  When properly configured, only 1 UDP port needs to be opened. Since OpenVPN uses pre-share 4K keys for authentication, the risks from attackers is minimal, unless  they hack your client and steal the keys.  The "evil maid" attack is real for all your devices.

If you need more basic knowledge, read the wikipedia article.  Oh ... and if you plan to do this, you'll want your internal LAN IPs to be something non-standard.   Definitely avoid 192.168.0.0/24 and 192.168.1.0/24 since those are commonly used at free-wifi locations.  Think of all the wifi networks you've been on - you want the internal LAN to be something other than those.  172.26.x.x/24  should be good or any of the higher 192.168.30+.0/24 addresses.

If you don't have a smartphone or non-technical  people who also need remote access to the HOME network, then you can use ssh as an easier solution. Setting up ssh is about 10x easier and it can do almost everything openVPN can do with a little smarts.

---

### Post by eddiefiggie on 2015-11-11
You sir, are most excellent!

Thanks for taking the time to reply in such detail.  VERY helpful.

---

### Post by TheFu on 2015-11-11
You might  want to leave this **unsolved** to get a few more perspectives - 3-7 days.  It is unlikely I covered all the important aspects. Plus I see a few missing letters above  -  my cheap chromebook keyboard has been dropping letters the last few weeks and I don't always  catch the issues.

---

