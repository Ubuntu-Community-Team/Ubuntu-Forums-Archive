---
title: "HMA install/run"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by ZPZK on 2012-11-15
Greetings, I'm a newbie on Ubuntu, and not a skilled 'geek', so thanks in advance for any help you can provide.  I had been using a legally purchased version of HMA when I was using windows, as I'm outside of the USA and could only purchase shows/movies on Amazon or ITunes when I would login through HMA's servers based in the USA.  Now that I'm on Ubuntu, I downloaded the different version of HMA, unzipped the file, and I can see the .exe file.  However, I cannot for the life of me get the thing to actually install and run in Ubuntu.  Any help would be greatly appreciated...remember I'm not a skilled programmer type...just a common user.

---

### Post by sandyd on 2012-11-15
> **ZPZK said:**
> Greetings, I'm a newbie on Ubuntu, and not a skilled 'geek', so thanks in advance for any help you can provide.  I had been using a legally purchased version of HMA when I was using windows, as I'm outside of the USA and could only purchase shows/movies on Amazon or ITunes when I would login through HMA's servers based in the USA.  Now that I'm on Ubuntu, I downloaded the different version of HMA, unzipped the file, and I can see the .exe file.  However, I cannot for the life of me get the thing to actually install and run in Ubuntu.  Any help would be greatly appreciated...remember I'm not a skilled programmer type...just a common user.
see [http://wiki.hidemyass.com/Tutorials:HMA_VPN_via_OpenVPN_on_Ubuntu_with_Network_Manager](http://wiki.hidemyass.com/Tutorials:HMA_VPN_via_OpenVPN_on_Ubuntu_with_Network_Manager)

---

### Post by ZPZK on 2012-11-16
> **sandyd said:**
> see [http://wiki.hidemyass.com/Tutorials:HMA_VPN_via_OpenVPN_on_Ubuntu_with_Network_Manager](http://wiki.hidemyass.com/Tutorials:HMA_VPN_via_OpenVPN_on_Ubuntu_with_Network_Manager)


Thank you SandyD, I had reviewed the HMA wiki help site prior to writing to Ubuntu forum, and found a lot of their language was total Greek to me, unfortunately including the page you reference.

 (Installing and  Running HMA under Windows was pretty simple, but w/ Ubuntu it seems a person needs A LOT more programming experience?  

Here are the instructions you reference, and my experience next to each line in italics:
(many thanks in advance for your guidance...)
[INDENT] 
[LIST]
[*]Install network-manager-openvpn-gnome (*Sandy D, I have no idea what "openvpn-gnome" means)*
[*]Download the vpn-config.zip ( [http://hidemyass.com/vpn-config/vpn-config.zip](http://hidemyass.com/vpn-config/vpn-config.zip) )* (SandyD, I did download this)*
[*]Download the linux installer ( [https://vpn.hidemyass.com/linux.zip](https://vpn.hidemyass.com/linux.zip) )*(SandyD, I did download this)*
[*]Create vpn folder (I used ~/vpn)* (ok, I created a folder on my desktop labelled vpn and moved both files there)*
[*]Extract both zip files there *(ok, I extracted both files in the folder)*
[*]Open network-manager (System->Preferences->Network Connections) *(On my Ubuntu I have no "system", just "System Settings"; and under "System settings" - no "preferences", but there is a "Network". Under "Network" there is no VPN Tab)*
[*]Go to [VPN]("http://wiki.hidemyass.com/VPN") tab *(No VPN Tab, so here I get stuck.. no clue what to do next )*
[*]Import the *.ovpn entry for the location you wish to connect
[*]Edit the entry and change the "Type" to Password with Certificates (TLS)
[*]The gateway and cert/keys should already be populated from the import
[*]Add your vpn username and password
[*]Apply
[*]Use the network icon in the panel to navigate to your [VPN]("http://wiki.hidemyass.com/VPN") entry and connect
[/LIST]
 [/INDENT]

---

### Post by sandyd on 2012-11-23
```

sudo apt-get install network-manager-openvpn-gnome

```

The VPN settings should be accessable if you click on the network icon (its two arrows, or a wifi thingy depending on how you are connected), and select VPN Connections -> Configure VPN.

---

