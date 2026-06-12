---
title: "A safe method of passing login credentials to openvpn automatically?"
date: 2020-10-25
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-10-25
Hello all,

So every time I want to connect to my VPN, I have to open the providers site, sign in, get my login credentials for openvpn and then copy them across and connect from the terminal. Not the most arduous task as I set the login page as my home screen and aliased the openvpn command, but it would be nice if it connected automatically each time I connected to the internet. 

Is there some method of automating the procedure which is also secure?

---

### Post by TheFu on 2020-10-25
I use login.cf.

Inside the .ovpn file, 
```
auth-user-pass /etc/openvpn/login.cf
```
OpenVPN says this method can make the keys available in RAM.

Inside /etc/openvpn/login.cf
```
{userid}
{password}

```
and nothing else. For example:
```
thefu32299
ac01ad25c06ea%96@e2eZd*0(d
```

The /etc/openvpn/ directory is 700 root:root 
and the file is
```
# ll ../login.cf 
-rw------- 1 root root 21 Mar 31  2016 ../login.cf
```

---

### Post by jcdenton1995 on 2020-10-25
This is amazing, thanks.

---

### Post by TheFu on 2020-10-26
> **jcdenton1995 said:**
> This is amazing, thanks.

Be certain you can accept the security implications of doing this.  There are some internal to the OpenVPN code, not just on your local file system.
For me, it removed the hassle of entering passwords almost daily.  OTOH, I'm running the client AND the server and use IPs, not DNS, to make the connection between clients and servers.  All my home wifi devices use a VPN to connect into my wired LAN, for example.  There are too many security faults with wifi implementations.

I use 1 commercial VPN service too, mainly to shift my apparent location on the planet. This year, that need has dropped off to almost zero thanks to the virus.

I also have a calendar reminder to change VPN passwords every 6 months and follow that religiously with a commercial VPN provider.

---

### Post by jcdenton1995 on 2020-10-27
> **TheFu said:**
> Be certain you can accept the security implications of doing this.  There are some internal to the OpenVPN code, not just on your local file system.

You mean with regards to an attacker being able to reveal my VPN password by exploting openvpn or gaining access to /etc/openvpn/login.cf?

What would be the consequence if this did happen? that they would be able to operate a VPN as myself?

---

### Post by sdsurfer on 2020-10-27
I know this is marked solved, but we like to secure our VPN connections with SSL certs as well.

---

