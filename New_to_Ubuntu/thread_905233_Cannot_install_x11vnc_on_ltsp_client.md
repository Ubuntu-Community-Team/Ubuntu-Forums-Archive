---
title: "Cannot install x11vnc on ltsp client"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by abg on 2008-08-30
I tried instruction on [https://wiki.edubuntu.org/InstallX11VncOnLtspClients]("https://wiki.edubuntu.org/InstallX11VncOnLtspClients") to install x11vnc on my ltsp client. But it refused with message more/less that it can't mount cdrom. So the /opt/ltsp/i386/etc/apt/sources.list being omitted.

what's wrong????

please help me..
thanks for advance.

---

### Post by Mip5 on 2008-11-07
The sources.list for your ltsp server is different from that of your ltsp client. From the sounds of your error, your sources.list for your client is the default install (which only includes the cdrom source listed, but does not include internet sources). I just checked the directions you referenced, and it looks (based on the error you posted) like you failed to address this. 

[quote]
Before installing in the ltsp environment, make sure that apt-get sources in ltsp are consistent with the base install:

sudo cp /etc/apt/sources.list /opt/ltsp/i386/etc/apt/sources.list
[quote/]

Let us know how it goes once you issue the above command to correct your sources.list

Thanks,

M

---

### Post by Mip5 on 2008-11-07
It looks like the thin-client sources.list are incorrect. They will be corrected by the following command (which comes from the page you linked above).

> 
Before installing in the ltsp environment, make sure that apt-get sources in ltsp are consistent with the base install:

sudo cp /etc/apt/sources.list /opt/ltsp/i386/etc/apt/sources.list


Try it again, and let us know how it goes.

Thanks,

M

---

