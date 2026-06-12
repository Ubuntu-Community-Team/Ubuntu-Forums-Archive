---
title: "eth1 confusion"
date: 2015-09-01
forum: New to Ubuntu
---

### Post by johnny36 on 2015-09-01
[COLOR=#000000]Hello everybody[/COLOR]

[COLOR=#000000]I just started using Ubuntu on my laptop not too long ago[/COLOR]

[COLOR=#000000]Today when I was fiddling around with it, I found that there was a "Wired connection 1" under my Ethernet. [/COLOR]

[COLOR=#000000]Since I use a USB wifi, I began a bit paranoid if this is some hacker thing going on.[/COLOR]

[COLOR=#000000]It says I used it one hour ago and currently says cable unplugged. When I search the MAC address on the wireshark site, it lead me to HP (which is my laptop)[/COLOR]

[COLOR=#000000]The only thing I did today was surf on the internet, plugged in an HDMI cable and installed unity tweak tool[/COLOR]

[COLOR=#000000]I figured it may be my HDMI cable that caused this ethernet connection thing, but when I unplug and plug again, it still said that it was last used one hour ago.

[/COLOR]i did not use any cables beside the HDMI and like i said before, when i tried plugging it again, it did not trigger anything.

the current settings are automically connect to this network when it savaliable and all users may connect to this network

should i uncheck it?

[COLOR=#000000]please help thank you[/COLOR]

---

### Post by grahammechanical on 2015-09-01
A wired (ethernet) connection requires a physical cable to make a connection between the laptop's ethernet port and the router's ethernet port. Have you plugged an ethernet cable between the laptop and the router? No? Then what are you worried about? Be more worried if you are using WiFi with an unencrypted connection to a wireless access point (router).

On my machine I have 2 ethernet adapters and 1 wireless adapter. I am connected to the router by both WiFi and wired connection 1. But not by my other wired/ethernet adapter. When I go to Network Manager> Edit Connections I am given this information:

WiFi =  2 minutes ago
Wired connection 1 = 2 minutes ago
Wired connection 2 = 1 day ago.

But I have never, I repeat, never connected Wired Connection 2 to my router. So, what is happening? It is 3 am where I live and that means that I last booted this machine yesterday. The OS then activated & accessed all 3 network adapters to see if any needed to be automatically connected to the router.

Active connections are polled regularly to maintain communication with the servers of the ISP. Non  active connections are only polled when the OS first loads.

HDMI connects to the video adapter. It is nothing to do with network adapters. If you disable Networking you will lose your WiFi connection. If the wired connection is set to automatically connect, then by all means disable it. But most of us do not bother.

Regards.

---

### Post by johnny36 on 2015-09-01
Now I know that eth1 is my ethernet controller/card/interface....

So

I deleted "wired connection 1" and remade it last night.

Now it just says never used.

Even after an entire night, I wake and restart my laptop, it still says the same.

If this is non-active connection, wouldn't a restart do a poll or whatever?

Edit 2.

When I do a Ubuntu boot on my USB, it says Wired Connection was last used (the time I boot in).

When I do a normal boot, it says Wired Connection last used never.

Whats happening?


Edit 3: Did a reinstall. Everything works as expected.
Thanks Gra for the help; I really went over my head this time...

---

