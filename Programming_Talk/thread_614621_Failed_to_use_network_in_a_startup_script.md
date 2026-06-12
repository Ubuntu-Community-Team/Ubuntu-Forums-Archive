---
title: "Failed to use network in a startup script"
date: 2007-11-16
forum: Programming Talk
---

### Post by chenxing on 2007-11-16
I am writing a simple script. It runs when the system is booting up, and it mainly contains a "wget" to require a webpage.

I save the script as /etc/init.d/ipgw , and I make a symbol link /etc/rc2.d/S80ipgw to it.

The problem is when the script is executed, "wget" failed. (It seems that the network is still not ready.) How can I ensure the network is initialized when the script is executed?

(The same script runs well in debian unstable)

---

### Post by chenxing on 2007-11-17
Any suggestions?

---

### Post by geirha on 2007-11-17
Run the script from /etc/rc.local instead. It's the last script to be run during boot.

Alternatively, put it in /etc/network/if-up.d/. Each of the scripts in there are run for each interface, so you'll have to make a check if $1 is eth0 or whatever interface is the correct one.

---

