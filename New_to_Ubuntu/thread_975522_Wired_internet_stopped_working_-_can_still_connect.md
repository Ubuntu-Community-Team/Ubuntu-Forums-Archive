---
title: "Wired internet stopped working - can still connect to router"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by randalotto on 2008-11-08
Out of nowhere, my wired internet stopped working.

I am hooked up to a router, which is still working fine with every computer that is hooked up to it via wireless.

Also, I can still connect to the router and to other computers on the network. The only thing I can't do is access the internet.

I've restarted everything, tried switching to DHCP instead of the static IP I use (when I tried that, I couldn't even connect to the router anymore...)

I have also verified that my laptop can connect to the internet via a wired connection through the router. I have no idea what to do. Any advice?

---

### Post by cmnorton on 2008-11-08
There is a lot of information here. 

If your connected via DSL, shutdown your modem for at least one minute. 

Concentrate on making sure your wireless router can provide addresses, static or otherwise, to your clients and that each client can connect and all can stay connected simultaneously. Each client should be able to access the router's config using http. That would be a good router connectivity test.

This could be due to the address range you've configured in your router config or something else.

If wired does not work and wireless does, it could be hardware or the position in your switch.

---

### Post by randalotto on 2008-11-08
Like I said, the wired connection worked when i hooked up my laptop.

I tried pulling up the router config page on several computers at once, and it seemed to work. Also, my three roommates don't seem to have any problem connecting simultaneously.

I feel like it has to be something with my ubuntu computer, but I don't know what - I didn't change any settings that I know of. It just suddenly stopped working.

---

### Post by Witling on 2008-11-08
Do you use an email engine as well as a browser? Are both down?

---

### Post by randalotto on 2008-11-08
Nothing is working. Email is down, messaging, etc... No internet for me :(

---

### Post by cmnorton on 2008-11-08
> **randalotto said:**
> Like I said, the wired connection worked when i hooked up my laptop.

I tried pulling up the router config page on several computers at once, and it seemed to work. Also, my three roommates don't seem to have any problem connecting simultaneously.

I feel like it has to be something with my ubuntu computer, but I don't know what - I didn't change any settings that I know of. It just suddenly stopped working.

How many people are using this router?

If many clients are simultaneously connected through this router and you had a static connection before, it sounds like someone got your ip address. You'd need to set to DHCP, and then reboot, or run dhclient as sudo. Like I said, try connectivity to the router. If you have to, use a roomate's good connection and check your config. How many connections can be granted, and can your DSL handle that many. Maybe I'm offbase, but I think these are good things to check.

---

### Post by randalotto on 2008-11-08
Well, I'm pretty confident that no other computer got the IP address. I have it set up as a media server, and I can still connect to it on my local network. I'll give your suggestions a shot though - couldn't hurt...

---

### Post by louieb on 2008-11-08
> **randalotto said:**
> ..and I can still connect to it on my local network. ... 
sound like a DNS problem  What does that show. Try making your router the primary and secondary DNS server. 

Also something else to check your router may have the ability to reserve an IP address based on a computers MAC  address. If so then you can set the computer to use DHCP and let the router give it the same address every time.

---

### Post by randalotto on 2008-11-08
I tried cmnorton's advice, and still have no internet... I really don't get why this just started out of nowhere.


EDIT: I changed the settings to "Automatic DHCP (Addresses Only)" and changed the DNS to my router's IP. Voila - internet restored.

Thank you for the help!

---

### Post by randalotto on 2008-11-08
Turns out my enthusiasm was short lived. It worked for a while, then I had to keep running sudo dhclient every 10 minutes or so to get it to work at all. 

Now, it's back to not working at all, no matter what I try...

---

### Post by randalotto on 2008-11-08
Another wrinkle:

If I run XP under VMwWare, I can connect just fine...

What's going on with my computer?

---

### Post by ExBuM on 2008-11-10
I'm having the exact same issue as you. Mine just began as I went back to Ubuntu from XP

---

### Post by randalotto on 2008-11-12
My internet worked for a while, then the same old problems returned. Does anyone have any new advice?

---

### Post by louieb on 2008-11-13
Just out of curiosity try getting an IP address ```
sudo dhclient
```and look at how long the lease is for at the end you will see something like this.
> DHCPACK of 10.0.0.7 from 10.0.0.1
bound to 10.0.0.7 -- renewal in 920860631 seconds.


Don't really thing that is a problem since you can still see the other computer on the network.

---

### Post by sol87 on 2008-11-23
Im having this same exact problem too the device i would usually use to connect with was greyed out and it would only let me connect to Auto Eth0

I can connect to my linksys router and to other computers on my network but no internet, its been like this for like a week

Im not sure if i can connect with windows in virtual box but im using the live cd right now

Sorry to bring up a week old thread but i really dont want to go back to windows

---

### Post by sol87 on 2008-11-23
oh and im using Ubuntu 8.10 its about a week out of date though, my internet cord is plugged into the the internet slot on my mother board

---

### Post by sol87 on 2008-11-23
Should i report this as a bug or something?

---

### Post by sol87 on 2008-11-23
sorry but i have to bump this

---

### Post by poopteam on 2008-11-23
I don't know if you are having the same problem but I had a very similar issue.  The cause seemed to be stemming from the dchp client.  The following site has the info.

[http://propellerheadadmin.com/linux-administration/wired-networking-problem-on-a-fresh-ubuntu-810-install](http://propellerheadadmin.com/linux-administration/wired-networking-problem-on-a-fresh-ubuntu-810-install)

-pt

---

### Post by sol87 on 2008-11-23
thanks for replying but the output of "$sudo /etc/init.d/networking restart" was totally different than what that site showed, but i removed "interface-mtu" anyways to see if it would do anything but it did nothing



[IMG]http://i57.photobucket.com/albums/g233/sol8712/Screenshot.png[/IMG]

I used to connect with the nForce2 ethernet controller (its built into my motherbored) but for whatever reason it went gray and i can  only connect to my local network with auto eth0 and the other one

---

### Post by sol87 on 2008-11-25
*bumping again. is there no help for me?

---

### Post by sol87 on 2008-11-25
Ok so I just figured out that I can connect to websites and stuff if I type in the ip address

Strange...
Still no clue what's happening. Anyone help???

---

### Post by randy78 on 2008-11-25
Sounds like the DNS server you are using is down

Use these: 208.67.222.222 and 208.67.220.220

Those are the addresses for OpenDNS

---

### Post by sol87 on 2008-11-25
ok thanks. This is a noobnish question but where do I put them

---

### Post by randy78 on 2008-11-25
Here's how you do it within Ubuntu... if the problem is related to your router's DNS entries, you'll have to consult your user manual.
In a terminal, type:
```
 gksudo gedit /etc/resolv.conf 
#Replace the nameserver entries with: 
208.67.222.222
208.67.220.220

```
Save the file and then issue this command in a terminal:
```
sudo /etc/init.d/networking restart
```

---

### Post by sol87 on 2008-11-25
i dont have a resolv.conf on my computer i have a folder called resolvconf and a file called resolv.conf.tmp but when i edit that and restart it undos my changes

---

### Post by randy78 on 2008-11-25
What are the entries next to 'nameserver' after it resets?

---

### Post by handydan918 on 2008-11-25
Try putting those opendns ip's in your router. Your router is serving the lan as a dns server, but getting it's info from some external source, probably your ISP. Changing your router settings to the opendns ip's provided above may do the trick.

---

