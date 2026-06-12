---
title: "Setting Network Configuration Manually"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by linuxyogi on 2012-07-20
Hi,
I am using Ubuntu Minimal Install. 

I want to set the ip address from Dynamic to Static.

I dont want to install Network Manger or Wicd.

How to achieve this ?

---

### Post by BkkBonanza on 2012-07-20
If NetworkManager or Wicd are installed you can remove them with,

sudo apt-get remove network-manager wicd

After that you can configure your ethernet manually by editing the /etc/network/interfaces file. Add a section that looks like this (with your own details of course):

auto eth0
iface eth0 inet static
  address 192.168.1.1
  netmask 255.255.255.0


For more details on that file use "**man interfaces**".

You can restart networking with,

**sudo /etc/init.d/networking restart**

You can verify the config with the **ifconfig** command. It should show the interface having an IP address and other details.

The same method will work with wifi interfaces but you would have to use the correct interface, eg. wlan0, and if WEP/WPA is being used you would have to go a step further ond configure wpa_supplicant.

Manual configuration is quite simple but the managers allow for auto updating the config as things change and make it easier for a gui user.

---

### Post by linuxyogi on 2012-07-20
Thanks. It worked.

---

### Post by linuxyogi on 2012-07-21
Problem is every time I reboot the PC /etc/resolv.conf looses its configuration (gets overwritten). How do I save my DNS settings?

---

### Post by Zill on 2012-07-21
> **linuxyogi said:**
> Problem is every time I reboot the PC /etc/resolv.conf looses its configuration (gets overwritten). How do I save my DNS settings?
If you configure all your ISP data in your DSL router you can save the DNS settings there.  All the PC then has to do is point to the router. eg. /etc/resolv.conf should just contain something similar to this:
```
domain 192.168.1.1
search 192.168.1.1
nameserver 192.168.1.1

```

---

### Post by linuxyogi on 2012-07-21
> **Zill said:**
> If you configure all your ISP data in your DSL router you can save the DNS settings there.  All the PC then has to do is point to the router. eg. /etc/resolv.conf should just contain something similar to this:
```
domain 192.168.1.1
search 192.168.1.1
nameserver 192.168.1.1

```

I am not using DHCP. Everytime I type nameserver 192.168.1.1 in /etc/resolv.conf it works but gets overwritten when I reboot the PC.

---

### Post by BkkBonanza on 2012-07-21
That's odd. I have several machines with static configs and they don't lose their resolv.conf values. That's usually the result of something "managing" the interface. 

I'd check what's running with **ps afx** command and see if anything that could be altering/changing the resolv.conf is active. dhclient, network-manager, wicd, dhcp3 etc.

My resolv.conf stays the same thru reboots...

---

### Post by Zill on 2012-07-21
> **linuxyogi said:**
> I am not using DHCP. Everytime I type nameserver 192.168.1.1 in /etc/resolv.conf it works but gets overwritten when I reboot the PC.
Overwritten to what?  Please open a terminal and post the output of ```
cat /etc/resolv.conf
```
DHCP or static IP is irrelevent.  All the PC needs to do is use the DNS server configured in the DSL router.

Have you removed Network Manager as described in post #2 above?

---

### Post by NikTh on 2012-07-21
> **linuxyogi said:**
> I am not using DHCP. Everytime I type nameserver 192.168.1.1 in /etc/resolv.conf it works but gets overwritten when I reboot the PC.

Hi , 
do you have Ubuntu or Lubuntu 12.04 ? 
Cause i recently read that resolv.conf behavior changed at 12.04 version. 

Take a look here --> [http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf](http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf) and try to understand how it works.. cause i am not fully understood. :P

Regards

---

### Post by linuxyogi on 2012-07-21
> **NikTh said:**
> Hi , 
do you have Ubuntu or Lubuntu 12.04 ? 
Cause i recently read that resolv.conf behavior changed at 12.04 version. 

Take a look here --> [http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf](http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf) and try to understand how it works.. cause i am not fully understood. :P

Regards

It worked. I created a file named tail in /etc/resolvconf/resolv.conf.d/ and added nameserver 192.168.1.1. Now thw configuration stays.

I am using Ubuntu Minimal install with LXDE core. 

Thanks.

---

