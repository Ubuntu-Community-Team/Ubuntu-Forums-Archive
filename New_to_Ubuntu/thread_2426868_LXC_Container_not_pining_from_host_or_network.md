---
title: "LXC Container not pining from host or network"
date: 2019-09-14
forum: New to Ubuntu
---

### Post by girish2404 on 2019-09-14
[COLOR=#242729][FONT=Arial]I recently started looking at LXC container for hosting tunnel service (IPv6 over IPv4 and IPv6 over IPv6). On my Window 10 machine I have Ubuntu 18.04 VM and I set up a Ubuntu 18.04 LXC Container which can ping VM, Host Window machine and 8.8.8.8.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]But When I ping my container from Windows Host or any other Network machine it does not respond and shows Response Time out.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Please let me know if need more information.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks for any help in Advance!

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]More Information[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Ubuntu VM iptables -t nat -L[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][[IMG]https://i.stack.imgur.com/CJQVZ.png[/IMG]]("https://i.stack.imgur.com/CJQVZ.png")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]LXC Container ip a s[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][[IMG]https://i.stack.imgur.com/w4Pvn.png[/IMG]]("https://i.stack.imgur.com/w4Pvn.png")[/FONT][/COLOR]

---

