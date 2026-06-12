---
title: "Wireless, Static IP, No PW"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Flynsarmy on 2008-06-19
Is it possible to set the IP to a static address on a wireless connection? 

If i go manual confiruation - wireless connection - properties and uncheck
roaming, there is no option for 'None' in password type drop down. I'm 
aware it's insecure. Is it possible? I'm trying to get my IP to 10.0.0.20. 

If i leave the password field empty and enter the rest of my settings
the wireless option disappears when i click on the network icon in the
top bar and just leaves a greyed out wired network checkbox.

---

### Post by hyper_ch on 2008-06-19
whether you enter a password or not depends on the access point whether it requires one or not...

it does not depend on whether you have a dynamic or static ip.

---

### Post by Flynsarmy on 2008-06-19
> **hyper_ch said:**
> whether you enter a password or not depends on the access point whether it requires one or not...

it does not depend on whether you have a dynamic or static ip.

I know. I'm trying to set a static IP and we dont' have a password on our network. I set my static ip in the options but leaving the password field blank doesn't work.

---

### Post by Dedoimedo on 2008-06-19
Hi,

Not in front of a Debian machine, so please forgive if I give you wrong details ...

Here's how you can set a static IP:

1. First determine what is the network interface (let's asumme wlan0).

2. Go to /etc/network/interface file, back it up, open it.

3. In this file should be entries (called stanzas), which define per interface configurations.

4. Look for wlan0 (or whatever your NIC is called) and then do the following:

auto wlan0
iface wlan0 inet static
address 10.0.0.2
netmask 255.255.255.0

Additionally, you can add the broadcast address, network ID address, DNS server, default gateway etc.

5. Save, restart networking: /etc/init.d/networking restart

6. See if this helps you in any way.

Cheers,
Dedoimedo

---

### Post by Flynsarmy on 2008-06-19
> **Dedoimedo said:**
> Additionally, you can add the broadcast address, network ID address, DNS server, default gateway etc.

Where could i find a list and possible examples of these in use?
I'm assuming you can't just type 'DNS server 10.0.0.138'. Is it primary?

My network interface is ath0. I made my file this but it didn't work:

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 10.0.0.20
netmask 255.255.255.0
default 10.0.0.138

---

### Post by Dedoimedo on 2008-06-19
Hi,

Did you restart the network?
Did you try rebooting?

Try also:

sudo ifdown ath0
sudo ifup ath0

See what comes up.

BTW, what is default? You mean default gateway? Then the entry should be "gateway x.x.x.x" Besides, is your gateway a higher IP address than the specific machine? Or is it the DNS, then the entry is "dns-nameservers x.x.x.x"

As to possible values, well type man interfaces or info interfaces in the terminal and see what you get, then you can try the same search in google, for instance.

Some other values:

network - network id
broadcast - broadcast address
gateway - default gateway
dns-nameservers dns server

If you're not sure about these values, try ifconfig ath0 and then take values from there.

Dedoimedo

---

