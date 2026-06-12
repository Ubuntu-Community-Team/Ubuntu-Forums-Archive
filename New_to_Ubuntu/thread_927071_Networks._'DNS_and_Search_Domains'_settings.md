---
title: "Networks. 'DNS and Search Domains' settings"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by nads1978 on 2008-09-22
Hi, I have a Thinkpad T61 which I use for work with WinXP. 
For my own use I have Hardy installed on a SEPARATE hard drive, which I physically remove and swap with the WinXP one as desired.

I recently looked at some of my Hardy WIFI settings and 'DNS Server' has a number (as expected). Also My 'Search Domains' field is the web address of work. 

How is it possible for my employers settings to be on my separate HDD Linux install? Is it somehow stored on my laptop hardware?

Also if the 'Search Domains' field is the same, will the DNS Server numbers be the same.

I thought my install of Hardy allowed me to be independent of my employer - can they monitor me?

Many thanks.

---

### Post by vrangforestillinger on 2008-09-22
How are you connected to the net? Normally, both Ubuntu and Windows get these settings from a DHCP-service running on the network you connect to. If you are using the same connection with both harddrives, then they will get the same parameters.

---

### Post by nads1978 on 2008-09-22
Thanks for the response.

I connect at work with XP through Cable (cat5)

At home through the wireless router with both OS'

My main concern is that I want to be independent from work, in that anything I decide to do with my own HDD, will not be anyhow linked to work. - Don't worry I'm not up to anything dodgy, its just my companies IT policy is pretty strict! (social networks, skype, GNU etc)

---

### Post by willca on 2008-09-23
Unless you're home network is tied up with your work network then its really odd you are getting that assigned to your /etc/resolv.conf file.

Did you by chance set static IP and DNS for your Ubuntu?
If not, try flushing the network stack out.

sudo /etc/init.d/networking restart

Then check if its still the same.
cat /etc/resolv.conf

---

### Post by nads1978 on 2008-10-05
Thanks willca - worked a treat!

---

