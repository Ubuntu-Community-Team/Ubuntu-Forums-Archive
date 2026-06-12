---
title: "Unicast WoL works only for minutes after suspend while magic packet WoL always works"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by pneum on 2012-08-09
Unicast WoL works only when it's done within a few minutes after suspend.

For example, I suspend the desktop and ping it from another within a few minutes after the suspend, then it wakes up. But if I ping it after more than a few minutes, it does not wake up. Still it wakes up if I send magic packet. Magic packet always works however late I send it.

I'd appreciate any comments, thanks.

My uneducated guesses:

Would it be possible that some networking mechanism retains the info about the suspended desktop's LAN card only for a few minutes from suspend and after that the unicast packet does not know where to go?

Or would it be possible that the suspended desktop's LAN card can retain network presence only for a few minutes from suspend?

Motherboard: Intel D845BG
PCI LAN card chip: Realtek 8139 (I haven't opened the box and checked it but lspci says so.)
OS: Ubuntu desktop 12.04 LTS 32bit

---

### Post by papibe on 2012-08-09
Hi pneum. Welcome to the forums ):P

The arp table maps the IP address to the hardware address (mac). When a computer goes to sleep or down, it can't have the table on memory so no longer know its IP address. On the other machines the table gets eventually updated and the entry is deleted.

Try this command on the terminal:
```
arp
```

On the other hand, the magic packet works because it uses directly the hardware address instead of an IP.

I hope that helps. Let us know how it goes.
Regards.

---

### Post by pneum on 2012-08-10
As instructed, arp command revealed that unicast WoL worked only before the entry disappeared from the arp cache. After static mapping, unicast WoL always worked.

Thank you very much.

---

