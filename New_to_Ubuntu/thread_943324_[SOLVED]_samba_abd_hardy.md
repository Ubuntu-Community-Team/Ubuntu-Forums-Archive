---
title: "[SOLVED] samba abd hardy"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by koba101 on 2008-10-10
Hi,

Can anyone please tell me how to get file sharing work with hardy.  I can't seem to get it working right (even though it works on my laptop with has gutsy)

I only see the $print folder shared everytime, even though i've got more folders shared.


This is what i keep getting with **smbclient**

```
	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (khalfan-desktop server (Samba, Ubuntu))
	PDF             Printer   PDF
	ML-2010         Printer   Samsung ML-2010
Domain=[KHALFAN-DESKTOP] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            KHALFAN-DESKTOP

```

---

### Post by Sycron on 2008-10-10
If you know the HOST IP (that computer you want to see the shared folders) you may try ```
nautilus smb://IP_address
```

---

### Post by koba101 on 2008-10-10
but this is my own computer i'm tryin to see

---

### Post by koba101 on 2008-10-11
anybody?

---

### Post by koba101 on 2008-12-20
might have been something wrong with the configuratio, i installed system-config-samba and enabled traffic to port 445 and 351...it works now

---

