---
title: "Beginning server - dumb question #1 - network"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by squakie on 2012-12-21
So I installed the server version to an OLD, SLOW, TINY laptop I had left over from setting up my Mom and Dad - thought it might be better to play rather than just throw it away.

I have a book about Ubuntu (for 11.x, but I'm sure the server things still apply) that I'm using as a guide.  Since I'm sure I'll have more questions, I'll start with dumb question number 1:

- if I attach a spare wireless router to the ethernet port on the laptop, will I be able to set up a "short range" network that my other PCs can connect to wirelessly so I can try things out?  In other words, I'd like the server to "host", if that word can be used in this context, the network.

---

### Post by cwsnyder on 2012-12-21
You realize that when you connect wirelessly that absolutely any machine within range can connect unless you lock down the router?  Period. No exceptions.  No cookie.  You don't have to be connected to the Internet for lurkers to trash your server or any machine connected to the 'network.'

Go into your wireless router settings and set up your router to WPA-PSK/WPA2, assign a passphrase, and lock it down to specific MAC addresses if you are going to still connect a wireless network.  Connect your 'server' to the Internet connection on the router (you may need a crossover cable, I'm not sure).  You actually don't even need a router, just a wireless access point on your 'server', but then you will definitely need to set your 'server' up with router-like software to verify members of your 'network' with passphrases, MAC addresses, etc.  This is the reason your question languished for 7 hours.  There IS no simple answer to your question.  You probably need to do a LOT more reading about networks before you attempt this project.

---

### Post by SeijiSensei on 2012-12-21
Since you have a "spare" router, there must be another router on the network now.  Why not just connect the server to the existing router with an Ethernet cable?  Give the server a static address, either by a "reservation" on the router tied to its MAC address, or [configure static routing]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html") in /etc/network/interfaces on the server and assign the machine an IP address outside the range managed by the router.  For instance, configure the router's DHCP server to hand out addresses from [prefix].1-199 and put the server at [prefix].200.

If you choose to use both routers, after following all of cwsnyder's excellent advice, make sure the second router uses a unique radio channel to reduce interference.  Running [FONT="Courier New"]sudo iwlist wlan0 scan | grep 'Channel:'[/FONT] on a wifi-enabled Ubuntu machine will list the channels used by all the routers in your vicinity.

Even better, if you're just trying some experiments with the server version, turn off the radio in the second router and use only its wired Ethernet ports.  Plug in the server and a test client.  Wi-fi is convenient but not always the best approach.

---

### Post by CharlesA on 2012-12-21
> **SeijiSensei said:**
> 
Even better, if you're just trying some experiments with the server version, turn off the radio in the second router and use only its wired Ethernet ports.  Plug in the server and a test client.  Wi-fi is convenient but not always the best approach.

This is the best approach if you want to play with networking. Wifi is nice but it can be a pain to configure on the server edition and unless it's locked down properly, it can be a major security problem.

---

### Post by squakie on 2012-12-21
Yeah, I'm already well versed in router setup.   Obviously I was going to use encryption and probably MAC filtering as well - even though MAC can be cracked easily enough and WPA2 as well with enough time.  Everyone else in the house are the ones with no clue on networking.

Can't connect via hard-wire to the router being used through out the house - it's in the living room by the TV and I'm messing around in the basement.  I could, however, connect via hard-wire from at least 1 of my PCs down here to the testing router - I was just planning on wireless (with the signal strength set low in the router) so I wouldn't have to move my laptops around to connect a hard-wire.  Guess I'll try hard-wire from 1 for now.

I also know I can't just broadcast my own made up domain name, but I should still be able to connect via the IP address, so I should be fine that way if I need to.

Guess it's time for me to start playing.  No big deal - thanks everyone for the input.

---

### Post by DuckHook on 2012-12-22
Hi squakie. Trust all is well.

To other posters. @squakie is being perhaps a tad too humble here, as he is a pretty experienced user.

@squakie:

I take it you are trying to convert your old decrepit laptop into an experimental tire-kicking machine but it has no built-in WIFI capacity, so you are thinking of using a spare WIFI-capable router as a makeshift WIFI card? You would then, say, ssh into the laptop to tinker with it? I'm doing exactly this with a couple of old computers of mine. It's how I explore the command line, try out CLI utilities and do crazy things to a throw-away minimal install without fear of borking my important machines.

This setup is quite doable with the right router, but you need to set the spare router up as a bridged client, turn off all host functions including dhcp, dns, etc, assign it a static IP and then make sure that your wireless security settings are identical to that of your primary router. If your router has its original firmware, it likely does not support this mode of operation since most residential-grade commercial routers are designed too simplistically. If you are lucky, then your router may have a chipset that allows you to replace the brain-dead vendor firmware with a Linux-based alternative.

In my case, I've got a bunch of ancient Linksys routers that are not even N-band capable. However, their one extremely redeeming feature is that they allow me to reflash with a much more feature-rich Linux-based firmware. In my case, I use DD-WRT. The resulting router offers client bridging, which is what you are looking for.

To see if your router can be reflashed, see [here]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices").

Once the new firmware is installed, the instructions for setting it in bridged mode is [here]("http://www.dd-wrt.com/wiki/index.php/Client_Bridged").

Let us know how it goes.):P

---

### Post by squakie on 2013-06-25
Solved.

---

