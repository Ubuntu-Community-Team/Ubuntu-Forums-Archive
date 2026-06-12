---
title: "8 Update error"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by asysma on 2008-05-25
hello..another problem..

when i want to update there is 8 update error

```

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.20-2ubuntu3.2_i386.deb
  404 Not Found [IP: 202.87.191.52 80]


W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.20-2ubuntu3.2_i386.deb
  404 Not Found [IP: 202.87.191.52 80]


W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.20-2ubuntu3.2_i386.deb
  404 Not Found [IP: 202.87.191.52 80]


W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core5_0.6.20-2ubuntu3.2_i386.deb
  404 Not Found [IP: 202.87.191.52 80]


W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.20-2ubuntu3.2_i386.deb
  404 Not Found [IP: 202.87.191.52 80]


W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.20-2ubuntu3.2_i386.deb
  404 Not Found [IP: 202.87.191.52 80]


W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.20-2ubuntu3.2_i386.deb
  404 Not Found [IP: 202.87.191.52 80]


W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.20-2ubuntu3.2_i386.deb
  404 Not Found [IP: 202.87.191.52 80]

```

what should i do??

thanks before!! :KS

---

### Post by philinux on 2008-05-25
Could be just the server being down. Either wait an hour or change the server in Software Sources.

---

### Post by drs305 on 2008-05-25
I checked the site the errors reference and, for the first error listed, the latest version on the server you used is now 3.3  Version 3.2 is no longer there. I just updated my synaptic and ran 'sudo aptitude update' but it still doesn't see the newer version listed.

The standard version in the synaptic servers I've checked is avahi-autoipd_0.6.22-2ubuntu4_amd64.deb

---

### Post by bgjmo on 2008-06-08
i had the same problem so i changed the server.  For some reason i was on the canadian server, so i changed it to a us server.  no problems now...

---

