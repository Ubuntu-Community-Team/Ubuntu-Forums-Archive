---
title: "sky broadband (when attmpting to forward a port for nicotine+) 14.04"
date: 2014-07-05
forum: New to Ubuntu
---

### Post by Un_Known on 2014-07-05
i'm attemtping to set up port forwarding for nicotine+ (soulseek) on ubuntu 14.04.
nicotine+ appears to be doing exactly what it says on the tin,however, not getting an open port.
so, being with sky broadband, home hub (dont laugh!), u apparently have to go to this IP address: [COLOR=#333333][FONT=SkyTextMedium !important]192.168.0.1  click the "security" tab and it (if u can GET INTO IT) configures some inbuilt firewall.
now when u do click security tab, it gives a pop-up asking to authenticate by username, and password.
sounds simple?
but no, its not my ordinary authentication (like when u get ubuntu updates or have to install anything), and no,it appears not to be my sky username and password either.
WHICH PASSWORD (that i dont seem to have) will this be?

sky arnt ANY help. they only help with mere consumerist questions like bills, sport, phone, buy buy buy.

incidently, when still a windows user, (and i hated windows een back then) whichever provider i had, i never had this issue, hence asking on this forum[/FONT][/COLOR]

---

### Post by 3rdalbum on 2014-07-05
It's the username and password into the modem. Check your modem's instruction book for details. Usually these sorts of devices have a default username and password of "admin". (that is, for username you type "admin" and the same for the password).

---

### Post by sotiris2 on 2014-07-06
Also pick it up and look for some kind of sticker under it. A quick google search suggests an admin / sky user/pass combo.

---

### Post by Vladlenin5000 on 2014-07-06
> **Un_Known said:**
> [COLOR=#333333][FONT=SkyTextMedium !important]incidently, when still a windows user, (and i hated windows een back then) whichever provider i had, i never had this issue, hence asking on this forum[/FONT][/COLOR]

That's because you never had to manage the router's/modem's configuration before. It doesn't matter which OS you're using. The configuration you need is at the device your service provider installed and is OS independent -> All you need is a web browser to access its LAN (internal) IP. The authentication you're looking for is specific to that device and have nothing to do with the one you use to start a session a session on Ubuntu (or Windows, or any other OS for that matter). In a nutshell, your reasoning about asking here because it never happened before is flawed in any way you look at it. The help we can provide is limited to the information given by previous posts and reiterated here.

---

### Post by Un_Known on 2014-07-17
> **Vladlenin5000 said:**
> That's because you never had to manage the router's/modem's configuration before. It doesn't matter which OS you're using. The configuration you need is at the device your service provider installed and is OS independent -> All you need is a web browser to access its LAN (internal) IP. The authentication you're looking for is specific to that device and have nothing to do with the one you use to start a session a session on Ubuntu (or Windows, or any other OS for that matter). In a nutshell, your reasoning about asking here because it never happened before is flawed in any way you look at it. The help we can provide is limited to the information given by previous posts and reiterated here.

thank you.that makes sense!
i have successful user name and password now, so i'm in.
and now i need to figure out these details:

service:
                                                                                                                                  Action:                                                                                                 
                        Send to LAN Server:                          .                          .                          .                        
                        WAN Users                                                                                  
                        Start:                          .                          .                          .                        
                        Finish:                          .                          .                          .                        
                        Log                                                                                                 
                                                                                                                                                                                                                        [HR][/HR]          service should be http (tcp:80)?or something else?
i THINK i have the "send to LAN" server number,but i dont know what the other two fields are for (start and finish).
i assumed these would be for the port range? (2234 to 2239)but maybe not.

---

### Post by Un_Known on 2014-07-17
a particular problem is,the "port range" is 2234 to 2239,or 2240,however,in the sky hub firewall settings page, the "action" setting gives 3 choices: "any","single address",and "address range",i havnt a clue what to set it tothere.
and also,with the above port range, i see nowhere to insert that.
there is ther "start",and "finish" fields,but they appear to be asking for IP addresses as the fields are exactly the same as the "send to LAN user" field.
any suggestions anyone?

---

### Post by Un_Known on 2014-07-17
i managed to get the sky hub set for port forwarding.anyone wishing advice just get in touch!
and thanks to everyone above for their suggestions! most appreciated

---

### Post by Vladlenin5000 on 2014-07-17
[http://nicotine-plus.sourceforge.net/NicotinePlusGuide/Settings/Basics.htm](http://nicotine-plus.sourceforge.net/NicotinePlusGuide/Settings/Basics.htm)

It probably works with UPnP whcih means you probably don't have to (open ports, the router opens the ports one app demand). Check your router's settings, something with this name most certainly will be there somewhere. Enable it (if not already).
Finding the settings for port forwarding is usually easy in traditional small office / home office routers but in those installed by some ISPs may not be possible.

---

### Post by gnowair on 2014-08-28
> **3rdalbum said:**
> It's the username and password into the modem. Check your modem's instruction book for details. Usually these sorts of devices have a default username and password of "admin". (that is, for username you type "admin" and the same for the password).

in my experience username "admin", word "sky"
and simple to change it to your own ones.

---

### Post by gnowair on 2014-08-28
> **Vladlenin5000 said:**
> [http://nicotine-plus.sourceforge.net/NicotinePlusGuide/Settings/Basics.htm](http://nicotine-plus.sourceforge.net/NicotinePlusGuide/Settings/Basics.htm)

It probably works with UPnP whcih means you probably don't have to (open ports, the router opens the ports one app demand). Check your router's settings, something with this name most certainly will be there somewhere. Enable it (if not already).
Finding the settings for port forwarding is usually easy in traditional small office / home office routers but in those installed by some ISPs may not be possible.


yep, however, i installed miniUPnPd and it worked a treat. i set the start and finish ports ten ports below,and ten ports above that needed for nicotine+, and still left the nicotine+ ports forwarded for nicotine+ itself.
maybe unecassary,but it certainly works wonderfully.

if Un KNown messages me i' d be happy to lead him through the steps.
maybe even post instructions from that on this thread, perhaps.

---

### Post by gnowair on 2014-09-15
incidently, this issue has begun happening again since i had issues with tor, and something else.
if there' anyone that can help, i'd be happy to post required info with whatever the  relevant commands.

also, is there a get-a-round for forgetting the new password/username i made up for my router without having to reset/reboot?

---

