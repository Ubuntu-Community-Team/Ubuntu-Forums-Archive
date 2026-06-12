---
title: "Problem with update 4 packages cannot be fetched"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by orionsg on 2012-01-15
Ubuntu version: 10.04 LTS
Its a fairly new  installation. 

When starting  the Update Manager it informs that the following updates needs to be loaded:
linux-generic
linux-headers-generic
linux-images-generic
linux-libc-dev

When I choose "Install updates" the following errors are reported in a dialog window:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.36.42_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.36.42_i386.deb)
  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.36.42_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.36.42_i386.deb)
  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.36.42_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.36.42_i386.deb)
  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-36.79_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-36.79_i386.deb)
  404  Not Found [IP: 91.189.92.167 80]


Is something broken in the Update manager?


Regards,

Frank

---

### Post by fantab on 2012-01-15
From UPDATE MANAGER - change the SERVER and try again.

---

### Post by Old_Grey_Wolf on 2012-01-15
If switching servers didn't help then try to update you repository index. Enter this command ```
sudo apt-get update
``` Update Manager should work after that.

---

### Post by orionsg on 2012-01-16
It worked when I changed the server from "Singapore server" to "Main server".

Thanks for the help.


Best regards,

Frank

---

