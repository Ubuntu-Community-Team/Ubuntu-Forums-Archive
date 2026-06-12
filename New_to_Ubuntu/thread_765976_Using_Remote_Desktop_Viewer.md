---
title: "Using Remote Desktop Viewer"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by TaintedBllack on 2008-04-24
I would like to view my laptop (windows xp) on my main computer (ubuntu). How would I go about doing this?

---

### Post by handband2 on 2008-04-29
> **TaintedBllack said:**
> I would like to view my laptop (windows xp) on my main computer (ubuntu). How would I go about doing this?

I recommend using [UltraVNC]("http://www.uvnc.com/install/installation.html") for windows xp.

---

### Post by lazyart on 2008-04-29
You'll need to make sure remote desktop is enabled on your laptop (Control Panel->System->Remote).  Next you need the name and/or ip address of your laptop.  (find the computer name from the same window you just opened, just look for the Computer Name tab.  For the IP address, go to Start->Run, type CMD, then in the balck window type IPCONFIG. Your address is four sets of numbers with periods between them.  It's likely 192.168.#.# ... that number can change every time you turn on the computer).

Open up the Terminal Server Client in Ubuntu (Applications->Internet->Terminal Server Client) and enter the name or ip address of your laptop.  Set the protocol to RDP (or RDPv5).  A window should open up with the familiar Windows logon screen.

If TSC doesnt work when you use the of the computer, try using the address.

---

