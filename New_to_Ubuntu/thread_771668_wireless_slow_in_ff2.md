---
title: "wireless slow in ff2"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by suddenlyben on 2008-04-27
I have just installed ubuntu 7.1 on my IBM T30 and i'm finding that i have very slow to no internet connection thru the wireless router.

i tried pinging the router and that looks ok (although slow)
i can also connect to the router thru ff. the internet connection (direct) on my desktop (windows) is fine.

any suggestions?

---

### Post by suddenlyben on 2008-04-27
When in doubt, read the instructions :)

I tried this fix which i found in the troubleshooting documentation, and it worked!


3.2.7.&#8195;IPv6 Not Supported

   1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4. Reboot Ubuntu.

---

