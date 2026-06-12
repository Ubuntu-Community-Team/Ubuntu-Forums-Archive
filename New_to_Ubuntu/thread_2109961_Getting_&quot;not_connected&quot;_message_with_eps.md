---
title: "Getting &quot;not connected?&quot; message with epson nx430 on ubuntu 12.04"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by lupulin on 2013-01-29
I'm hoping someone can help. I have never used a printer on ubuntu before.


[LIST]
[*]I recently set up my epson NX430 which is supposed to work as a wireless printer. It doesn't even come with a printer cable. I set up the printer to access my wireless network which it seems to do.
[/LIST]

[LIST]
[*]I downloaded and installed the .deb driver package from Epson here: [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16876&DSCCHK=b32e8a0bd44cc61369c3fa75fbab6b877ce71d25](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16876&DSCCHK=b32e8a0bd44cc61369c3fa75fbab6b877ce71d25)
[/LIST]

[LIST]
[*]I added the printer via "printers" in system settings. Ubuntu was able to detect and add the printer without any trouble.
[/LIST]

[LIST]
[*]However, whenever I try to print something, nothing prints, and the print manager thing says "not connected" and never prints. I tried pinging the IP address that the printer displays and get nothing back. I also tried entering the printer's IP address in my browser and it fails to load. Is there something I can do to get this working? Thanks for any help.
[/LIST]

---

### Post by sanderj on 2013-01-29
I would focus on making the printer reachable on its IP address. Maybe the printer is not connected at all, or just on a different IP address.

---

### Post by DuckHook on 2013-01-29
1. Do you use a router/gateway that assigns your IP addresses through DHCP?
2. If so, did you set up your printer for DHCP or using a static IP address?
3. When you say...

> **lupulin said:**
> I set up the printer to access my wireless network which it seems to do.

...how do you know this? If your printer tells you either with a successful configuration test page or on its status screen, please note the contents, especially the IP address.

4. Other things to check: is the address being assigned by DHCP or BOOTP? Ubuntu has trouble recognizing addresses assigned by BOOTP. Don't know why, it just does. I had to disable BOOTP on my printer and force it to get its address with DHCP for my Ubuntu boxes to recognize it.

5. Do you have overly restrictive firewall rules set up on your own machine? This is highly unlikely, but need to ask. Actually, most beginning users have firewall rules that are too lax.

6. Go into your router web interface and see if it recognizes your printer and has assigned it an IP address.

---

### Post by lupulin on 2013-01-29
> **DuckHook said:**
> 1. Do you use a router/gateway that assigns your IP addresses through DHCP?
2. If so, did you set up your printer for DHCP or using a static IP address?
3. When you say...



...how do you know this? If your printer tells you either with a successful configuration test page or on its status screen, please note the contents, especially the IP address.

4. Other things to check: is the address being assigned by DHCP or BOOTP? Ubuntu has trouble recognizing addresses assigned by BOOTP. Don't know why, it just does. I had to disable BOOTP on my printer and force it to get its address with DHCP for my Ubuntu boxes to recognize it.

5. Do you have overly restrictive firewall rules set up on your own machine? This is highly unlikely, but need to ask. Actually, most beginning users have firewall rules that are too lax.

6. Go into your router web interface and see if it recognizes your printer and has assigned it an IP address.

Thanks for the response. According to the printer display it is set up for DHCP. The WiFi confirmation says:
Printer name: EPSON2260E0
Connection: WIFI 54 Mbps
Signal Strength: excellent
Obtain IP Address:auto
IP address: 192.168.2.6
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.2.1
WIFI:Manual
Communication: Infrastructure
Network SSID: [my SSID]
Security: WPA-PTK(TKIP)
Password: ************
MAC Address: A4:EE:57:22:60:E0

I do not have any firewall restrictions unless Ubuntu 12.04 has some by default. I checked my router admin page and the printer is listed in the DHCP Client List with the same IP address as the printer gives.

Hopefully that printer confirmation gives you some idea, because if the router can see the printer, I am pretty confused.

---

### Post by sanderj on 2013-01-29
So ... can you ping 192.168.2.6 from your Ubuntu system?

---

### Post by lupulin on 2013-01-29
When I do ping it, I just get "destination host unreachable" over and over.

---

### Post by sanderj on 2013-01-29
> **lupulin said:**
> When I do ping it, I just get "destination host unreachable" over and over.

And what is your own IP address? Check with 'ifconfig'.

---

### Post by DuckHook on 2013-01-29
Then do the following:

1. As per #4 in my original post, go through your printer settings to see if the IP was assigned by DHCP or BootP. Your "Obtain IP Address" setting is currently set to :Auto". Set it to DHCP.

2. Powercycle the printer and try pinging the address again.

3. If you still cannot see the printer, try assigning a static IP address. Most routers reserve a range of IP addresses for static assignment. Determine what these are for your router, then assign such an address to your printer.

4. Powercycle the printer and try pinging the address again.

It is possible that the default Linux drivers that came with your printer don't work. [This]("http://ubuntuforums.org/showthread.php?t=1966978") thread may help.

---

