---
title: "Disable IPv6"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by jbrevik on 2008-09-29
Hi,

I wanted to disable IPv6 and found a thread that said to insert these lines
into /etc/modprobe.d/aliases

```
alias net-pf-10 ipv6 off 
alias net-pf-10 off 
alias ipv6 off 
#alias net-pf-10 ipv6 
```

I rebooted and did an ifconfig on wlan0 and noticed that there was still an IPv6 address. Does the above fix only disable IPv6 for eth0 and if so what do I need to do to disable IPv6 for my wireless interface wlan0?

---

### Post by rybaxs on 2008-09-29
network settings -> host

---

### Post by nowshining on 2008-09-29
> **jbrevik said:**
> Hi,

I wanted to disable IPv6 and found a thread that said to insert these lines
into /etc/modprobe.d/aliases

```
alias net-pf-10 ipv6 off 
alias net-pf-10 off 
alias ipv6 off 
#alias net-pf-10 ipv6 
```

I rebooted and did an ifconfig on wlan0 and noticed that there was still an IPv6 address. Does the above fix only disable IPv6 for eth0 and if so what do I need to do to disable IPv6 for my wireless interface wlan0?

did u use super user privs when saving the file??

---

### Post by Cope57 on 2008-09-30
about:config in Firefox

network.dns.disableIPv6;**true** is all I do.

The connection may use IPv6, but my browsing does not.

---

### Post by walkingthecow on 2008-09-30
You do not have to add any lines to /etc/modprobe.d/aliases. You can either just edit aliases and change alias net-pf-10 ipv6 to alias net-pf-10 off, or you can "vi /etc/modprobe.d/bad_list" and add "alias net-pf-t10 off" to that. Either way, that's the only thing you need to edit, no adding.


Also, to check if ipv6 is still in use, just use this command: ip a | grep inet6.

---

### Post by frankleeee on 2008-09-30
If you want to sped up FF go here.
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by jbrevik on 2008-09-30
> **walkingthecow said:**
> You do not have to add any lines to /etc/modprobe.d/aliases. You can either just edit aliases and change alias net-pf-10 ipv6 to alias net-pf-10 off, or you can "vi /etc/modprobe.d/bad_list" and add "alias net-pf-t10 off" to that. Either way, that's the only thing you need to edit, no adding.


Also, to check if ipv6 is still in use, just use this command: ip a | grep inet6.

I ran```
ip a | grep inet6
``` and returned this
```
 inet6 ::1/128 scope host 
    inet6 fe80::21a:73ff:fe56:4a63/64 scope link 

```

Not really sure what to make of this. Btw I also went into about:config in FF and set network.dns.disableIPv6 to true.

---

### Post by bumanie on 2008-09-30
Disabling in firefox usually works. If that has not done the trick, there is a way to blacklist ipv6 in modprobe. > sudo gedit /etc/modprobe.d/blacklist Then at the bottom of the list type, "blacklist ipv6" (without the quotes). Save and reboot.

---

### Post by Nepherte on 2008-09-30
Blacklisting a module does NOT prevent a module from being loaded if it is needed by a system service, regardless of the fact that it has been blacklisted.

Disabling through /etc/modprobe.d/aliasses should be the correct one. Open up the file, uncomment the lines that say alias net-pf-10 ipv6 and add this line alias net-pf-10 off.

It should look something like this:
```
#alias net-pf-10 ipv6
alias net-pf-10 off
```
You will have to reboot before these changes take effect.

---

### Post by jbrevik on 2008-10-03
> **jbrevik said:**
> Hi,

I wanted to disable IPv6 and found a thread that said to insert these lines
into /etc/modprobe.d/aliases

```
alias net-pf-10 ipv6 off 
alias net-pf-10 off 
alias ipv6 off 
#alias net-pf-10 ipv6 
```

I rebooted and did an ifconfig on wlan0 and noticed that there was still an IPv6 address. Does the above fix only disable IPv6 for eth0 and if so what do I need to do to disable IPv6 for my wireless interface wlan0?


So I did the above and disabled IPv6 in FF and it seemed to increase my speed significantly. Even though I still see my IPv6 show up when i do an ifconfig wlan0 it really doesn't seem to matter.

Thanks for your help!!

---

