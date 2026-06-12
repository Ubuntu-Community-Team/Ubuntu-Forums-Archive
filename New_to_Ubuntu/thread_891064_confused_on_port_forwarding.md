---
title: "confused on port forwarding"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by paker on 2008-08-15
How do I code "allow port number 9876 to Transmission"? I searched and found several posts on port forwarding. As instructed,

I opened Firestarter > Add Rule > Allow Serivce. Didnt find Transmission in the Name section. Deluge was not listed. Closest was BitTorrent. I chose BitTorrent. Number 6881 automatically popped up in Port. Everyone said not to use it. If I entered 9876, Name field changed to Unknown.

I am not sure if I missed something or those who were giving instructions were just giving theoretical instructions.

---

### Post by estyles on 2008-08-15
You shouldn't need to modify ufw or firestarter, unless you've previously set them up to block ports.  Assuming you haven't, any ports should be available for transmission.

If your ports have been open and then close, I think that means that your IP is changing?  I.e. you get a lease from your router on a particular IP and it expires, at which time your router gives you a different IP.  Can you confirm if this is true?  (I can't give you a simple command to check your ip, but I'm sure one exists - maybe someone else can post, or else do some searching on that... personally, I have conky running at all times so if my ip changes, I see it immediately.)

If that's true, then there should be a way to fix that in your router settings.  In my netgear router, there is a section under DHCP for "IP Reservations".  I simply enter my MAC Address (actually, there's a nifty interface to capture a currently connected MAC), and tell it to reserve a particular IP for my machine, then use that IP for the port forwarding.  I do not know if there is a way to do that on your router - poke around in the settings and see if you can find it.

If not, I don't see why it wouldn't work for you to make the Network Manager use a static IP, but I've never tried that, so I don't know.

---

### Post by paker on 2008-08-15
> **estyles said:**
> You shouldn't need to modify ufw or firestarter, unless you've previously set them up to block ports.  Assuming you haven't, any ports should be available for transmission.

[B]Yes, Transmission works whether Incoming TCP Port is Open or Closed. But when Closed, downloading speed stays 80 KB/s. When Open, it goes up  200-400 KB/s range. I asked about this here and people said I should forward port to Transmission. That's how I got into this.:( 

No, I haven't blocked any port. To be honest with you, I don't even know what opening/closing port is. My only goal is to increase downloading speed.[/B]

If your ports have been open and then close, I think that means that your IP is changing?  I.e. you get a lease from your router on a particular IP and it expires, at which time your router gives you a different IP.  Can you confirm if this is true?  (I can't give you a simple command to check your ip, but I'm sure one exists - maybe someone else can post, or else do some searching on that... personally, I have conky running at all times so if my ip changes, I see it immediately.)

**I am on cable. I know I have a static external (?) ip. I am not leasing router.**

If that's true, then there should be a way to fix that in your router settings.  In my netgear router, there is a section under DHCP for "IP Reservations".  I simply enter my MAC Address (actually, there's a nifty interface to capture a currently connected MAC), and tell it to reserve a particular IP for my machine, then use that IP for the port forwarding.  I do not know if there is a way to do that on your router - poke around in the settings and see if you can find it.

**I will look into this.**

If not, I don't see why it wouldn't work for you to make the Network Manager use a static IP, but I've never tried that, so I don't know.

[B]If what you mean is System > Administration > Network > uncheck Enable Roaming and enter ip address,
I tried it. After it, I couldn't get on internet at all. [/B]

I will post back after "ip address reservation in DHCP"

---

### Post by nicedude on 2008-08-15
I would suggest you try guarddog instead of firestarter, for a windows convert like me it just seemed easier to configure and has an easy to find place to open ports up, as well as it is simple to save your configuration when you get it all set up and transfer the same settings to other computers :-)

---

### Post by jerome1232 on 2008-08-15
are you behind a router or are you connected directly to a modem.


If you are behind a router they actually have NAT enabled which effectively blocks all ports for every computer connected to that router. You will need to open the port in your router first. Ubuntu doesn't have any services by default that lisetn for connections so a host based firewall is really not needed. Firestarter is a dead project.

If you are directly connected to a modem and your a little paranoid or want to protect against configuration mistakes on your part a firewall may be in order. UFW is a much better frontend to iptables then firestarter is and it's installed by default. I've heard guardog is a good program but haven't used it.

using ufw is very easy it is command line based (there is gufw which has a gui but I have no experience with it)
If you wanted to ditch firestarter I would suggest doing this:

baciscally this removes firestarter purges iptables, then configures ufw and allows incoming connections on port 51413, then enables logging of rejected connections and finally enables ufw

note: If you are behind a router you will still need to forward port 51413 unless the router is upnp enabled, then transmission can automatically forward the port on it's own.

```
sudo apt-get remove --purge firestarter
sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo ufw default deny
sudo ufw allow 51413
sudo ufw logging on
sudo ufw enable
```

---

### Post by paker on 2008-08-16
**note: If you are behind a router you will still need to forward port 51413 unless the router is upnp enabled, then transmission can automatically forward the port on it's own.**
1) Yes, I have a router behind cable modem. I suppose I shouldn't do the sudo commands.
2) I assume Transmission uses 51413? 
3) How do I implement "you still need to forward port 51413"?
4) I don't know if my 5 year old d-link router is upnp enabled. But when I open Transmission and enter port # 51413, the port appears closed. Is this an indication that my router is NOT upnp enabled?

**Ubuntu doesn't have any services by default that lisetn for connections so a host based firewall is really not needed.**
This is Greek to me. My bad. (What is HOST? What is LISTENING FOR CONNECTIONS?)

---

### Post by jerome1232 on 2008-08-16
it really depends on your router, get the model number off of it and do a google search for <model#> port forwarding

this may be of use as well [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

edit: sorry I didn't notice your other questions, basically a computer is a host.
Host based firewall means a firewall that's installed on the computer. 

I guess I'll use a web server as an example

when you try to goto [www.google.com](www.google.com) you send a request to view the page on port 80, google's server is always listening for connections on port 80 and acts on them when it see's them, in your case it will allow you to view html content.

If there are no services listening, there's nothing to attempt to connect to and exploit or hack, thus no need for a firewall to block those incoming connections.

I hope my description helps

---

### Post by paker on 2008-08-16
1) I googled and found my DI-604 is upnp enabled, and in order not to use the functionality, I must disable it. Since I didn't to any disabling, it must still be upnp enabled.

2) I already knew about the link portforward.com, and set up my rounter with various port numbers. But still in Transmission, the port numbers are closed. I just tried 51413, and it is closed in Transmission.

My goal is to increase downloading speed in Transmission. When Incoming TCP Port is open, downloading speed goes up to several hundred KB/s. When closed, 80 KB/s. My line can download up to 1 MBytes/s.

How can I achieve my goal?
I am assuming I can do that by getting an open TCP port to Transmission. Is this correct?

---

### Post by jerome1232 on 2008-08-16
Then do all of the steps up to the ufw stuff, that turns off firestarter and flushes iptables of the rules firestarter put in there. 

And yes transmission by default uses 51413 you can change it to whatever you want though.

---

### Post by cariboo on 2008-08-16
A good way to check which ports you have open to the world, go here:

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Just enter the port numbers of the ports you have forwarded.

Jim

---

### Post by nicedude on 2008-08-16
I would suggest you try Azureus bit torrent client instead of transmision ( transmissions are car parts right? ). It has settings for everything ( like limiting upload speeds on a per torrent basis ) and I can max out my connection easily depending on where I am downloading from.

Remember that even the best BT client set up perfectly on a killer cable modem won't do squat if the people seeding it are not there or are flooded with leechers, so go get a few private torrent accounts. A good test though is to download something that is both legal and has plenty of seeders, like an Ubuntu torrent :-)

Hope this helps

---

### Post by macvr on 2008-08-16
if the port has closed again- it is not transmission's fault
so no matter if u shift to deluge u might have same prob
re-check all steps u have taken to open ports[pretty sure that its something u have missed there]

have u rebooted after the port was open? check what ur ip is now

make sure u have reserved ur IP in ur Dlink router

---

### Post by jerome1232 on 2008-08-16
> **nicedude said:**
> I would suggest you try Azureus bit torrent client instead of transmision ( transmissions are car parts right? ). It has settings for everything ( like limiting upload speeds on a per torrent basis ) and I can max out my connection easily depending on where I am downloading from.

Remember that even the best BT client set up perfectly on a killer cable modem won't do squat if the people seeding it are not there or are flooded with leechers, so go get a few private torrent accounts. A good test though is to download something that is both legal and has plenty of seeders, like an Ubuntu torrent :-)

Hope this helps

You can do that all that stuff in transmission too, I just like it because you can ignore unencrypted peers which means my isp can't tell it's a torrent and limit my bandwidth as some do.

edit: I think azureus can do that too

---

### Post by macvr on 2008-08-16
> **jerome1232 said:**
> You can do that all that stuff in transmission too, I just like it because you can ignore unencrypted peers which means my isp can't tell it's a torrent and limit my bandwidth as some do.

i have used azureus and transmission too but transmission has a lot lesser options and azureus is too heavy on the system

but _parker's problem is not cause of the client_, any client he uses he'll have same port problem if not forwarded properly[COLOR="DarkRed"][believe me i have been down this road trying all clients in XP till i got to realize how to CORRECTLY forward ports][/COLOR]

---

### Post by nicedude on 2008-08-16
Azureus has settings for how to handle encrypted peers as well, and by direction. As in you can allow unencrypted incoming but not outgoing which is a plus in my book. TO ALL THAT READ THIS IN THE USA - YOU CAN ONLY BE SUED FOR UPLOADING NOT DOWNLOADING. The media will never say that as they always say sued for "downloading" and this is a lie. Just thought I should share that as almost no-one I know ever understands that simple thing. 

Sorry to hear your ISP uses throttling, that is BS technology. But if you use Private torrent sites and SSL encryption it shouldn't be a problem as they won't be able to see what the hell your doing ( outside of the NSA of course who can break that key like I break a WEP key :-) )

---

### Post by jerome1232 on 2008-08-16
Yeah I've heard azereus (spelling?) is very full featured, I just meant torrent by torrent throttling, I will have to try it out sometime, I just don't torrent much other than distro iso's so haven't needed the feature set.

@OP, have you checked to make sure your router does actually have upnp turned on by default? In my mind it's a security hole and I could see why it wouldn't be on by default. (mean any program on my computer can just say hey open me a port)

---

