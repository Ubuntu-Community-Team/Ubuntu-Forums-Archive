---
title: "bittornado yellow light"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by shayvasa on 2008-05-07
hi, i downloaded bittornado and its downloading really slow, itrs also showing a yellow light in the top right corner which im guessing its because im using a router. any1 has any ideas on how to get the green light to make the downloads go faster?

---

### Post by SunnyRabbiera on 2008-05-07
you can try different speeds, its what I do.

---

### Post by shayvasa on 2008-05-07
how do i do that?

---

### Post by SunnyRabbiera on 2008-05-07
well you see that button that says "settings for" next to it?
that is a pulldown menu with various speeds in it, by default its "automatic" but you can change it to whatever you wish.
also remember that torrents are only as good as how many peers/seeds are availible at the time, it can be a real crapshoot.

---

### Post by tjwoosta on 2008-05-07
you can go to options and turn the yellow light off (so it forces a green light)

the reason for the light is probably because of your router or a firewall 
(i also get one) 
but there really isnt anyway to make things go faster without sacrificing security 

infact i dont know why they even make the yellow light, because most users will have firewalls or routers

with other bittorrent clients like (for example) Transmission it doesnt even mention anything about my firewall or router and i get soem pretty fast connections

---

### Post by shayvasa on 2008-05-07
ok ill do that thanx, do u know of a good download manager? just in case i need to download from firefox

---

### Post by Delever on 2008-05-07
If you own the router, and it has stable/static IP address visible from outside, you can redirect/open specific port to point to your computer. You need to make your computer to use local static IP address, not roaming mode. Then in options of your favourite torrent program, select port to use for incomming connections.

I tried to use usual words for doing that so you can do futher searches how to do it. If you need more information, or some help how to find information about specific things, just ask.

---

### Post by shayvasa on 2008-05-07
delever i dont know if i have static ip. how do i check? and if i have i didnt quite follow what to do next

---

### Post by Delever on 2008-05-07
First of all, is that router yours, and do you know how to connect to it to configure?

---

### Post by shayvasa on 2008-05-07
yes its mine, and  think i need to enter [http://192.168.X.XXX](http://192.168.X.XXX) dont know whats in the X. btw i have a CNet CWR-854V

---

### Post by Delever on 2008-05-07
Ok. Found your router screenshots [there]("http://portforward.com/english/routers/port_forwarding/CNET/CWR-854/SlingBox.htm"), so I can help.

You need to enable access just for one program, using single port. It is not a security threat as long as that program does not have vulnerabilities.

Say we will use port 54320 for incomming connections.

"Open a web browser like internet explorer or Netscape. Enter the ip address of your router in the address bar of your browser. In the picture above the address bar has [http://www.google.com](http://www.google.com) in it. Just replace all of that with the ip address of your router. By default the ip address should be set to 192.168.62.1." (it was 192.168.1.254)

"You should see a box prompting you for your username and password. Enter your username and password now. By default the username is admin, and the password is 1234. Click the Ok button to log in to your router. " (password/username or both could be blank)

"Click the Advanced Setup link near the left of the page."

[http://portforward.com/english/routers/port_forwarding/CNET/CWR-854/CWR-8543.jpg](http://portforward.com/english/routers/port_forwarding/CNET/CWR-854/CWR-8543.jpg)

"Click the Filters link near the top of the page."

[http://portforward.com/english/routers/port_forwarding/CNET/CWR-854/CWR-8544.jpg](http://portforward.com/english/routers/port_forwarding/CNET/CWR-854/CWR-8544.jpg)

Using this page, find port range which includes 54320. I can't know where or what range it would be, you will need to make apropriate adjustments yourself. Say, 54320 is in range **50000-60000 "Outbound"**, "TCP". Change it to **50000-54319 "Outbound", "TCP"**. Add new filter with range **54320-54320 "Both", "TCP"**. This is your actual port with allowed traffic to both sides. Add another filter range to cover upper interval: **54321-60000 "Outbound", "TCP"**.

"Click the Virtual Servers link near the top of the page."

[http://portforward.com/english/routers/port_forwarding/CNET/CWR-854/CWR-8543.jpg](http://portforward.com/english/routers/port_forwarding/CNET/CWR-854/CWR-8543.jpg)

Change one line to such values:
Service: "Torrent" (any name, without quotes)
Public IP Address: don't change
Public Port: 54320
Private Port: 54320
Protocol: TCP
Private IP address: 192.168.1.1 (i have chosen "1" myself. This will be your computer address. "254" is your router address)

Apply settings.

I see "Routing" tab in router settings. I don't know what exactly is in it (obviosly), so you yourself have to find where DHCP server (thing that assigns IP addresses automatically) settings are, and find what IP range is used by it. You have to make it exclude 192.168.1.1 address. If it starts with 192.168.1.1, change it to 192.168.1.2.

Next step - change your computer address from dynamic to static.
System -> administration -> network -> Unlock

Select your wireless connection, click "Properties" (if you don't know which one of connections listed there is wireless, you can find by doing following steps to every one which has roaming mode enabled and reverting back if it does not work)

Uncheck "Enable roaming mode" (if internet stops working, just enable it again)

Configuration: Static IP address
IP address: 192.168.1.1 (the one we chosen)
Subnet mask: 255.255.255.0
Gateway address: 192.168.1.254 (router address)

Click OK. Open DNS tab in Network Settings dialog. DNS is responsible of actual browsing on internet (simplified explanation). There should be one or two addreses listed. If not, enter them manually from your router "Routing" configuration page. It should have DNS addreses too.

Close, and check if internet is working. If you did everything right, it should work. If it is not working, go to Network settings again, and enable roaming mode.

Now, open your torrent program. I will use Transmission as example. Find "Incomming TCP port" field in preferences, and change it to 54320.

If any bit of this seems too complicated or you don't understand it enough, don't do it, or ask more :).

---

### Post by shayvasa on 2008-05-07
thanx for the turorial but i cant manage to get into [http://192.168.62.1](http://192.168.62.1) so i cant advance

---

### Post by Delever on 2008-05-07
192.168.1.1

192.168.1.255

192.168.1.254

---

### Post by shayvasa on 2008-05-07
ok its 192.168.1.254 but i dont know what the username and pass is, and its not admin and 1234

---

### Post by Delever on 2008-05-07
Try entering blank. I will modify tutorial for you router address soon.

Done.

---

### Post by shayvasa on 2008-05-07
didint work blank

---

### Post by Delever on 2008-05-07
Ok, so it stops here. If you have your router manual somewhere, check what default password is. If it still does not work, it means that someone who configured router did not want anyone else to access it.

---

### Post by shayvasa on 2008-05-07
ok thax, ill try to figure out whats the pass, thanx for everything

---

