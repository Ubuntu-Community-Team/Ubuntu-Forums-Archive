---
title: "what's my dns server address?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by gbstack on 2008-08-30
If I have connected to Internet,how to see my dns server address?

It means that what's my dns server address that I'm using.

---

### Post by gmxgeek on 2008-08-30
Rightclick on network icon in tray, Connection information. Should be listed

---

### Post by Too Late on 2008-08-30
Or in terminal, type:
```
cat /etc/resolv.conf
```

---

### Post by StOoZ on 2008-08-30
> **Too Late said:**
> Or in terminal, type:
```
cat /etc/resolv.conf
```

preceded with 'sudo' in this case

---

### Post by Too Late on 2008-08-30
> **StOoZ said:**
> preceded with 'sudo' in this case
Why? /etc/hosts has read permissions for everyone.

---

### Post by ChildOfMana on 2008-08-30
System > Administration > Network then click on the DNS tab in the resulting dialog box.

Et voila! :)

---

### Post by StOoZ on 2008-08-30
> **Too Late said:**
> Why? /etc/hosts has read permissions for everyone.

tried it now , it requires sudo in my case.

---

### Post by gbstack on 2008-08-30
but there are two dns server address(in /etc/resolv.conf and DNS Tab in Network tool),which is the dns server that I'm using?

thanks!:)

---

### Post by gmxgeek on 2008-08-30
You are probably using both. The first one should be the primary DNS, and the second one is the... *drumroll* ... secondary one!

---

### Post by gbstack on 2008-09-03
thank you all! :)

---

### Post by Sealbhach on 2008-09-03
The secondary one is a fallback DNS server in case the first one can't be reached.


.

---

### Post by trash on 2008-09-03
is it normal that mine would be my routers IP?

```
cat /etc/resolv.conf:
nameserver 192.168.1.1
```

---

### Post by halitech on 2008-09-03
if you are connected to a router and using DHCP then yes although you can manually set them to something different if you want (like OpenDNS)

---

### Post by trash on 2008-09-03
> **halitech said:**
> if you are connected to a router and using DHCP then yes although you can manually set them to something different if you want (like OpenDNS)

cool thanks, any pro's/con's to performance?

---

### Post by halitech on 2008-09-03
I've tried both and OpenDNS seems to be a little better. Your router will connect to your ISP DNS servers to get info and may or may not be patched for the recent DNS issue where OpenDNS is patched so you won't have to worry about bad redirects

---

### Post by trash on 2008-09-03
> **halitech said:**
> I've tried both and OpenDNS seems to be a little better. Your router will connect to your ISP DNS servers to get info and may or may not be patched for the recent DNS issue where OpenDNS is patched so you won't have to worry about bad redirects

ok, sounds very worth trying out then:)

---

### Post by Sealbhach on 2008-09-03
> **trash said:**
> ok, sounds very worth trying out then:)

Yes definitely worth doing.

You can add them by going System/Administration/Network and clicking on the DNS tab.

The addresses are:

208.67.222.222
208.67.220.220


.

---

### Post by trash on 2008-09-03
> **Sealbhach said:**
> Yes definitely worth doing.

You can add them by going System/Administration/Network and clicking on the DNS tab.

The addresses are:

208.67.222.222
208.67.220.220


.

Already added then to my router and think i am getting slowdowns but could be the satellite connection!
Also added them in Network but they keep getting removed, i guess by the router?

```
 cat /etc/resolv.conf
search anikast.net
nameserver 192.168.1.1

```

---

### Post by jerome1232 on 2008-09-03
Yeah when you connected via dhcp to the router everytime your computer gets an ip address the router assigns the dns servers, so it's easier to just change it in the router.

---

