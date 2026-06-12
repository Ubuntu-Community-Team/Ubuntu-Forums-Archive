---
title: "Check Point VPN client (certificate-based authentication)"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Sydius on 2008-07-30
I and two of my coworkers would like to use Ubuntu exclusively, but must connect to a company network using VPN via the Check Point VPN client in Windows.  We've all tried various ways of getting it to work, but none have so far done any good.  All the information I have found has been for password-based authentication, but we were given personal certificates too.

None of us know very much about VPN, and OpenSWAN has intimidated me quite a bit, so I was wondering if anybody out there has ever gotten Check Point VPN to work using certificates, and, if so, how hard it is.

We are willing to even go so far as to have Windows installed in a virtual machine, if that's what we have to do to get VPN access in Ubuntu, but would obviously prefer not to.

---

### Post by luisfcup on 2008-07-30
Install "openvpn" package and "network management framework (OpenVPN plugin)" the openvpn protocol has certificate authentication.
If you search for vpn in synaptic package manager you can find other vpn tool that you can try.
I use cisco and pptp based vpn that do not require certificates but my suggestion is that you try openvpn and see if you can set up a connection.

---

