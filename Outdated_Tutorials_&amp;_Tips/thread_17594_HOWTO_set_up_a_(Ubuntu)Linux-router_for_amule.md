---
title: "HOWTO: set up a (Ubuntu)Linux-router for amule"
date: 2005-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by t.rei on 2005-03-01
This is supposed to help people who are running an ubuntu router and want to run an amule client behind it.

Note:
The system this was done on was a woody debian router with ancient software (it still ran ipchains). I simply upgraded to warty by editing the /etc/apt/sources.list and installing ubuntu-base and upgrading everything else. clean reboot, and started configuring. (Read the next post for some really helpfull information!)

**Step1: **
getting started
Install ubuntu on the router. (ubuntu base is sufficient, ubuntu desktop just contains a whole bunch of gui packets)

If you have ipmasq on your Router - Uninstall it!
```
/etc/init.d/ipmasq stop
/etc/init.d/ipmasq-kmod stop
apt-get remove ipmasq
```

**Step2:**
Setting up iptables for ip-masquerading and for amule port-forwarding (and ssh access from outside)

*(optional) enabling autosave of iptables:*
```
sudo gedit /etc/default/iptables
```
scroll down to the bottom of the file and you will find a line "enable_autosave=false". Replace that with "enable_autosave=true".
Save and exit.
note: This could be bad. If you screw something up and reboot your computer. Your mistakes will still be autosaved!

*Get a root shell:*
```
sudo bash
```

*Now to get iptables to load on bootup:*
```
ln -s /etc/init.d/iptables /etc/rcS.d/S41iptables
```

[i]Now to activate ip_forwarding:
[/i]Add this line to: /etc/init.d/iptables
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
look at the last section of this file where it says:
```

case "$1" in
  start|restart|reload|force-reload)
	initd_load active
	if test ${enable_autosave-false} = true; then
	  touch $autosave

```
and change it to look like this:
```

case "$1" in
  start|restart|reload|force-reload)
	initd_load active
	[color=Red]echo 1 > /proc/sys/net/ipv4/ip_forward[/color]
	if test ${enable_autosave-false} = true; then
	  touch $autosave

```

*And finally configuring the firewall:*
```
iptables -F; iptables -t nat -F; iptables -t mangle -F
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i ! ppp0 -j ACCEPT
iptables -P INPUT DROP
iptables -A FORWARD -i ppp0 -o ppp0 -j REJECT
```

*And forwarding the ports for amule: *
(assuming the computer running amule has the ip "192.168.0.7")
```
iptables -t nat -A PREROUTING -i ppp0 -p tcp --destination-port 4662 -j DNAT --to-destination 192.168.0.7:4662
iptables -t nat -A PREROUTING -i ppp0 -p udp --destination-port 4672 -j DNAT --to-destination 192.168.0.7:4672
iptables -t nat -A PREROUTING -i ppp0 -p udp --destination-port 4665 -j DNAT --to-destination 192.168.0.7:4665
```
4662, 4665 and 4672 are the default ports set in amule. Its best you leave it that way.

**Step3:**
Since you might want to still be able to login to your router via ssh from the outside, you will need to open the ssh port (22)
```
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

**Step4:**
*Testing and saving everything:*
* Run amule and check if the "you have a low id" message is absent in the connected to server message. If it is: congratulations. If not - doh!
* Try to login from somewhere outside your LAN via ssh(If you can) - That should work as well.
* Run nmap from outside your lan on your router. It should not show any open ports (not even ssh). 
* If you are happy with it save your iptables:
```
/etc/init.d/iptables save active
```
* And you probably should create a backup of your rules by:
```
iptables-save -c > ~/iptables_backup
```
You can restore them (if you should have messed up something) by:
```
cat ~/iptables_backup | iptables-restore
```

**Step5:**
Reboot the router! (do not hit the reset button - reboot cleanly!)

---

### Post by p!=f on 2005-03-01
> **t.rei]
If you have ipmasq on your Router - Uninstall it!
```
/etc/init.d/ipmasq stop
/etc/init.d/ipmasq-kmod stop
apt-get remove ipmasq
```
[/quote]
```

apt-get --purge remove ipmasq

```
is stronger because it also removes configuration files (backup if needed) which could be potentionally used to reveal your router setup.
[QUOTE=t.rei]
**Step2:**
Setting up iptables for ip-masquerading and for amule port-forwarding (and ssh access from outside)

*(optional) enabling autosave of iptables:*
```
sudo gedit /etc/default/iptables
```
scroll down to the bottom of the file and you will find a line "enable_autosave=false". Replace that with "enable_autosave=true".
Save and exit.
note: This could be bad. If you screw something up and reboot your computer. Your mistakes will still be autosaved!
[/quote]
I don't have /etc/default/iptables (Ubuntu Hoary) but I can remeber it was present on my previous Debian Sid installation.
```

[~] > dpkg -l iptables
ii  iptables                      1.2.11-10                     Linux kernel 2.4+ iptables administration tools

```
[QUOTE=t.rei]
*Now to get iptables to load on bootup:*
```
ln -s /etc/init.d/iptables /etc/rcS.d/S41iptables
```
[/quote]
There's no /etc/init.d/iptables script on Ubuntu Hoary. Looks like you're running mixed environment.
[QUOTE=t.rei]
[i]Now to activate ip_forwarding:
[/i]Add this line to: /etc/init.d/iptables
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
look at the last section of this file where it says:
```

case "$1" in
  start|restart|reload|force-reload)
	initd_load active
	if test ${enable_autosave-false} = true said:**
> echo 1 > /proc/sys/net/ipv4/ip_forward[/color]
	if test ${enable_autosave-false} = true; then
	  touch $autosave

```

No need for this...
```

[~] > cat /etc/network/options
ip_forward=yes
spoofprotect=yes
syncookies=yes

```

---

### Post by t.rei on 2005-03-02
ah ok - thx for all those hints.
yes - I do have a little bit of a mixed system. I will check back with all your hints and fix the howto. thx for the detailed feedback.

---

### Post by t.rei on 2005-03-02
ok - i can confirm all of your statements. I will leave things as they are but paste lines mentioning the woody->warty upgrade @ first lines.

---

### Post by Rick Z on 2007-10-18
Hi I am a newbie in ubuntu/linux.  I am trying to setup my ubuntu 7.4 as router, but I am not sure where to start.  I prefer not use any GUI.  Therefore, I install webmin, but I seem lost in places how to enable the second NIC as DHCP to allow other pc (LAN) to connect.  Please help.

---

