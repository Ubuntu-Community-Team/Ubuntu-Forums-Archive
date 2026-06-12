---
title: "Updated ISP Service (now have port 443 open) - - Security risk??"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by JeQhdMD on 2013-11-30
My ISP & phone company (CenturyLink) installed a new wireless gateway in my basement, and I connect via a usb adapter (desktop) and laptop wireless receivers.

Formerly, when I connected via ethernet directly or via my own netgear router, I had all the first 1056 ports closed (stealthed?).   Now, according to the GRC "Shields-UP" website [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) - - port 443 is open.

From a security standpoint, is this something that should concern me . . . can I close it by accessing CenturyLink's gateway device, without breaking my TV and phone connectivity (phone, PrismTV and web are all controlled via the gateway)?

Thanks for any input.

---

### Post by The Cog on 2013-11-30
Do you have an HTTPS server running? It wouldn't surprise me if it's not the routers own web server that grc is seeing.

---

### Post by JeQhdMD on 2013-11-30
As far as I know, I am not running an HTTPS server, and yes, I think you're right that it's the gateway device web server.   I "assume" that's setup that way so as to enable CenturyLink's technical support staff to access the wireless network for troubleshooting, firmware updates and so on.   So, this is not something to be concerned with?? (I'm a novice when it involves networking .. . .)

---

### Post by DuckHook on 2013-12-01
You may think of yourself as a "novice", but you have the instincts of a "pro". That's an uncommonly healthy spirit of curiosity, vigilance and skepticism you have and it will serve you well and keep you out of a lot of trouble. Even the link you researched is very useful and it is always a good idea to approach an open port that you cannot account for as if it were a live snake.

If I were you, I'd contact your ISP and ask them if they left this port open for their own use. If so, I would want to know exactly what they use it for, what they run through it without my knowledge, how they sandbox it, and what its precise firewall details are. If I were not satisfied with their reasoning (and in my case, it would be almost impossible for them to convince me), I might also want to know how I can close the port off outright and only open it manually, under my sole exclusive control, in the event that it requires remote servicing.

If they can't or won't help me change this setting, then I would install a proper router/firewall, bypass their device, and treat it as just a dumb modem. I would use my own router under my own complete control and running a solid firewall as the true WIFI/router/dhcp server. There are a number of routers that come preinstalled with DD-WRT, which is an open-source project that replaces typical router firmware with truly amazing alternate software. I believe that Buffalo makes such a series. There are others. You can look them up in DD-WRT's web site. Open-WRT and Tomato are other worthy firmware replacements, although I've never used them and only know of them by reputation. I just don't trust the proprietary firewall implementations that so many commercial vendors install on their routers.

I should note that my friends and family think me a lunatic for the extent to which I will take security. But I just had to help out a close relative after her entire /home directory was wiped clean because she had left a VNC port open for remote help. There was little I could do for her except to install a pristine system and close the barn door after the horses had bolted. The world is filled with malicious jerks who like to vandalize just for kicks, and a lot of them look for their victims online. In my opinion, open ports are an open invitation.

---

### Post by The Cog on 2013-12-01
> In my opinion, open ports are an open invitation.
Absolutely!
Any old jerk has an opportunity to come along and meddle with your router settings.

---

### Post by JeQhdMD on 2013-12-01
Thanks for the good advice, I'll be following up my my ISP tech support to learn why 443 can't be closed by default.

---

### Post by thatredbird on 2013-12-02
I know on uverse that 443 is the port they use for the tv casting, so that might be the reason for CenturyTel(note, that I am not suggesting more research is un-needed)

---

