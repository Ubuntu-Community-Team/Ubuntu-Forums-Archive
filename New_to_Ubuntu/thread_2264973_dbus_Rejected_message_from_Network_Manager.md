---
title: "dbus Rejected message from Network Manager"
date: 2015-02-11
forum: New to Ubuntu
---

### Post by Alex_Botev on 2015-02-11
So I was inspecting the /var/log/auth.log, for reasons of the bug as listed here: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1311316](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1311316) and I found this, which possibly is not related to the bug, but I did not manage to find what it means, why it happens and should I worry:

dbus[479]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.74" (uid=0 pid=2050 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=817 comm="NetworkManager ")

---

### Post by ian-weisser on 2015-02-11
dnsmasq in the application that assigns IP addresses to other machines on a subnet.
You use it if your system is acting like a dhcp server. For example, when you install a container or VM that needs an IP address, or when you share your internet connection with an ad-hoc network.

Many users never use dnsmasq.

The error message simply means that dnsmasq was trying, at some point in time, to do something inappropriate and Network Manager refused. That doesn't mean it's a security flaw nor related to your bug. You could have, for example, been fiddling with your connection settings or shutting down a VM.

---

