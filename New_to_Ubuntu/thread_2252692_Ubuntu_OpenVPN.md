---
title: "Ubuntu OpenVPN"
date: 2014-11-13
forum: New to Ubuntu
---

### Post by Zach_Mallet on 2014-11-13
Hello,

I'm rather new to Ubuntu, but here is my situation. I am currently using a Chromebook running ubuntu and trying to get a vpn up. Here are the errors messaged I get:


```
cannot find device "tun1"Linux ip link set failed: external program exited with error status: 1
Execting due to fatal error
```

Thanks for any help!

---

### Post by nerdtron on 2014-11-13
What part of the installation of openvpn is that? how far have you gone to setting it up? Did you follow a link/tutorial?

---

### Post by Zach_Mallet on 2014-11-13
After I installed open vpn I ran this:

sudo openvpn "location of vpn file"

Then it runs, I input username and password and it gives me those errors.

---

### Post by sandyd on 2014-11-13
> **Zach_Mallet said:**
> After I installed open vpn I ran this:

sudo openvpn "location of vpn file"

Then it runs, I input username and password and it gives me those errors.

Do you have the tun module loaded?
Does
```

lsmod | grep tun
```
return anything?

If no, run
```
 sudo lsmod tun
```

Then,
```

sudo openvpn --mktun --dev tun1
```

---

