---
title: "Problem connected to an encrypted/password required wireless network"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-08-06
Hi all,

Today I need to connect to a wireless which requires password/key/code (whatever that is), I do know the code but I couldn't find a way to connect to the network.
EDIT: If you may ask whether the code is correct or not, it indeed is! Because my friends have no problem connecting to it using Windows, they were prompted a window, enter the code and simply got connected, unlike me :(

Normally, my laptop detects the wireless network just fine, if that's an unencrypted wireless network (which requires nothing like password, code etc) then I have no problem connecting to the wireless network.

But when I tried to connect to an encrypted wireless network, it prompted me a network manager window (it looked like that) and some options like "WEP passphrase, WEP Hex, WEP ASCII, LEAD" and 2 more about the key are "Open System" & "Shared Key" (I don't remember very correctly, sorry), I tried to enter the code to all of them but none worked. The best result that I seemed to get is it tried to obtain the IP address but then returned nothing.

So does anyone know how to solve this problem? Please let me know, thanks in advance

I have to manually plug the cable to the wireless modem to post this :(

---

### Post by keylime on 2008-08-06
What does iwconfig from the command line state? 

Also, when you click on the network icon what happens?

---

### Post by Dani Filth on 2008-08-06
I'm not at my friend's place where the network is right now so I can't say for sure.
But I did check "ifconfig wifi0" & "ifconfig wlan0" and it returned some weird IP begins with 169.54.... (I say this is weird because I know some concepts about IP, they should be 192.168.x.y or 172.16.x.y for LAN, plus, when I did "ipconfig" on his PC, the IP was 192.168.1.x - I even manually set my IP to become static IP with the similar form of 192.168.1.x but it didn't work either)

When I clicked on the network icon, it opened up a list of available networks, some wireless networks were there, I chose my friend's network and got stuck there.

P.S This had no problem when the network is not encrypted/password protected, only when it comes to password/key/code then this problem occurs.

Thanks

---

### Post by keylime on 2008-08-06
K, so the 169 addy is a privately assigned address, so it's not getting any internet access at all. 

You'll want to make sure that you have wpa_supplicant running - if your wifi hotspot uses WPA, this item will allow you to get onto the hotspot (assuming that MAC address filtering is not enabled).

---

### Post by cgkades on 2008-08-06
I'm not at my computer right now so the directions may be a little off. 

There is a Network prefrenc you can set, i think it's in system>settings or preferences. you should see all your devices. click unlock. then click on your wireless card, and click (i think) properties. take it out of roming, and set your essid, wpa or wep and set it to DHCP. Thats what i did, and i got my laptop to go on my network

---

### Post by cmb11 on 2008-08-06
Install an application called (wicd)

WICD is an application that replaces the network manager, it supports ALL kind of networks,it works flawlessly on ubuntu, and has a nice and easy to use GUI...

see these threads if you don't trust me: :):)

[http://ubuntuforums.org/showthread.php?t=414001](http://ubuntuforums.org/showthread.php?t=414001)
[http://ph.ubuntuforums.com/showthread.php?t=587010](http://ph.ubuntuforums.com/showthread.php?t=587010)

---

### Post by Dani Filth on 2008-08-06
> K, so the 169 addy is a privately assigned address, so it's not getting any internet access at all. 

You'll want to make sure that you have wpa_supplicant running - if your wifi hotspot uses WPA, this item will allow you to get onto the hotspot (assuming that MAC address filtering is not enabled).
Yes, MAC filtering is not enabled here.

Sorry if I didn't make it clear.
I want to know if I want to connect to the encrypted wireless network then which option should I choose? As aforementioned, there were "WEP Passphrasse", "WEP HEX", "WEP ASCII", "LEAD" (if I remember correctly) and 2 options about the key are "Open System" & "Shared Key".
In fact, I tried all of those options, but none work.

I also gave WiCD a try, it provided me even more options which make me even more confusing.

Cheers for your replies :D

---

### Post by Dani Filth on 2008-08-07
Anyone else have a suggestion?

---

