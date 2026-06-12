---
title: "How to get 127.0.0.1 in /etc/resolv.conf as only IP address"
date: 2019-05-18
forum: New to Ubuntu
---

### Post by LwIh%*7 on 2019-05-18
I've been trying for a number of weeks now of getting the Network Manager with dnsmasq to implement the 127.0.0.1 nameserver in /etc/resolv.conf however it keeps generating the IP 127.0.1.1 instead and I've tried doing the configuration changes as described on the Ubuntu wiki under the article dnsmasq but it keeps putting in the wrong nameserver and it should be using 127.0.0.1 for dnsmasq via the NetworkManager in the /etc/resolv.conf file but for some reason it doesn't and implements the incorrect IP nameserver. Is there an easy way of correcting this? Currently I'm using Windows 10 but would prefer to use Ubuntu and/or other Ubuntu-based systems like Kubuntu etc. the reason why I need dnsmasq to use 127.0.0.1 is so that steam stops fluctuating the download speed and found it works on systems like Arch Linux when dnsmasq is set to the correct nameserver and even when the family for example uses Netflix the steam client stays in the Mbps but on Ubuntu with the incorrect protocols it stays in the 100-300Kbps speed. Could anyone please provide an easy way to correct the Network Manager generating the wrong nameserver if possible? Linux is suppose to be more flexible than Windows but I'm finding that its not at the moment and the net speed is more stable and fast on Windows 10 than Linux in general at the moment.

---

### Post by #&amp;thj^% on 2019-05-18
Please Note that if you plan to use dnsmasq for the local system only, you should lock it down by adding the line
```

listen-address=127.0.0.1
```

to the dnsmasq configuration file (/etc/dnsmasq.conf). 
With time and experience you too will find Linux more flexible than Windows, and again with time and usage it becomes easier. (We just have to adapt)

Exactly how to do this depends on the method(s) of network configuration in use. If you're manually hardcoding the nameservers (either in /etc/resolv.conf or elsewhere, such as a stanza in /etc/network/interfaces or in the Wicd GUI), then just add a reference to 127.0.0.1 as the first entry in the list. If you're using DHCP, then instruct your client to prepend 127.0.0.1 to the DHCP servers it receives. E.g., with dhclient, include the line
```

prepend domain-name-servers 127.0.0.1;
```

in the dhclient configuration file (/etc/dhcp3/dhclient.conf).
Also if needed see this: [https://wiki.archlinux.org/index.php/Dnsmasq](https://wiki.archlinux.org/index.php/Dnsmasq)

---

### Post by LwIh%*7 on 2019-05-19
Thanks for the help 1fallen,

I think I've managed to fix the download speed issue on steam basically dnsmasq would not work for me even when setting dns to dns=dnsmasq in NetworkManager.conf would not work however installing unbound and setting the dns to dns=unbound in the conf file did and removing the /etc/resolv.conf afterwards and restarting the NetworkManager had generated a new file for resolv and this time by the Network Manager configuration after awhile even when Netflix is in use the net speed stays in the Mbps and doesn't go to the Kbps. Strange that dnsmasq wouldn't work but at least I've solved it with unbound I did find the help guide on this site: [https://steamcommunity.com/discussions/forum/1/412446292762583371/](https://steamcommunity.com/discussions/forum/1/412446292762583371/) 
I did follow what they did and it worked for me. Yet again thanks for helping out!

---

