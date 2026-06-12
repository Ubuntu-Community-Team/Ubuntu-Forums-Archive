---
title: "Who's Connecting To My Router?"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by perito on 2012-01-24
Is there anyway to check who is connecting to my wireless network? I want to check if someone (outsider) is using/stealing my Internet bandwidth. 

Thank you

---

### Post by ubudog on 2012-01-24
There is usually a section under your router config, maybe under "Status", where you can view the client table.

Best,
ubudog

---

### Post by anewguy on 2012-01-24
Also - what type of protections do you have on the router - wep, wpa, MAC filtering?  WEP is extremely easy to crack, so you don't want to use it.  WPA/WPA2 is much better.  MAC filtering allows you to say what hardware addresses (not be confused with a TCP/IP address, etc.) are allowed to connect to the router.  If the "spy" is sophisticated enough, they can grab the MAC address and spoof it, but you have WPA/WPA2 encryption and MAC filtering you would be very secure.

Dave ;)

---

### Post by ubudog on 2012-01-24
> **anewguy said:**
> also - what type of protections do you have on the router - wep, wpa, mac filtering?  Wep is extremely easy to crack, so you don't want to use it.  Wpa/wpa2 is much better.  Mac filtering allows you to say what hardware addresses (not be confused with a tcp/ip address, etc.) are allowed to connect to the router.  If the "spy" is sophisticated enough, they can grab the mac address and spoof it, but you have wpa/wpa2 encryption and mac filtering you would be very secure.

Dave ;)

+1

---

### Post by whitethorn on 2012-01-24
I found this script a couple years back, it checks the network with a arp-scan and prints back the ips and some info about the computers found. 

To run it you need arp-scan, zenity

```

#!/bin/bash
#Script to view what's connected to your network

#Change this to name of your network interface being used. ex. wlan0, etho, ...
interface=wlan0


#Man program
PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin
{
echo "Beginning the ARP scan; this will take approximately 15 seconds..."
echo
arp-scan --retry 10 --interface $interface --localnet | tee /tmp/arpscan.tmp
echo
echo "ARP scan finished."
echo "================================================="

cat /tmp/arpscan.tmp | grep 192 | awk '{print $1}' | while IFS=$'\n' read IP_addr; do
	
	if [  ${IP_addr#*.*.*.*} != 1 ]; then
	echo "There are other computers on the LAN." >> /tmp/arpscan.tmp
		if [ "$echo_begin_scan" != "false" ]; then
		echo "DNS query results for each host:"; echo
		fi
	echo_begin_scan="false"
	Gateway_IP=$(route -n | grep UG | awk '{print $2}')
	host_name_with_domain=$(nslookup $IP_addr $Gateway_IP | grep name | awk '{print $4}')
	host_name=${host_name_with_domain%%.*}
	echo "$IP_addr = \"$host_name\""
	fi
done

if [ "$(tail -n 1 /tmp/arpscan.tmp)" != "There are other computers on the LAN." ]; then
	echo "DNS lookup skipped; only the gateway responded to the ARP scan."
fi

} | zenity --text-info --width=600 --height=500 --title="ARP Scan with DNS lookup"
rm -f /tmp/arpscan.tmp

```

---

### Post by Dangertux on 2012-01-24
I would say use a strong WPA/2 key. I wouldn't even bother with MAC filtering. For two reasons, the first it usually breaks things. The second, changing your MAC address is trivial (as is figuring out an accepted mac address). Also since people like to argue that you can't I highly recommend using the following command.

```

man ip

```I wouldn't worry about trying to find out who is doing anything so much as keeping them from doing it.


Hope this helps.

---

### Post by anewguy on 2012-01-24
Exactly.  I only mentioned MAC filtering in that you need to know how to snoop the packets to get a good MAC address, whereas if you leave your network either wide open or only with WEP pretty much anyone can get in.  As I mentioned WPA/WPA2 is the best way to go - hackable, but difficult - most won't spend the time trying to do it.  My main concern was indeed protecting from this point forward, not finding who has already hacked.  Can't do anything about the past, only the now and the future.

Dave ;)

---

