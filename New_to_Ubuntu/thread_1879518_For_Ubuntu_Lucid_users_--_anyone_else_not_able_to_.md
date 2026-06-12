---
title: "For Ubuntu Lucid users -- anyone else not able to download the latest kernel update?"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Brushstroke on 2011-11-11
There's a kernel update available for Ubuntu Lucid 10.04.3. The kernel has been upgraded to 2.6.32-36, but every time it tries to retrieve the new kernel from the server, Synaptic gives me this, indicating the kernel just isn't there: 

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.32-36-generic_2.6.32-36.79_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.32-36-generic_2.6.32-36.79_amd64.deb)
  404  Not Found [IP: 91.189.92.179 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-2.6.32-36_2.6.32-36.79_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-2.6.32-36_2.6.32-36.79_all.deb)
  404  Not Found [IP: 91.189.92.179 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-2.6.32-36-generic_2.6.32-36.79_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-2.6.32-36-generic_2.6.32-36.79_amd64.deb)
  404  Not Found [IP: 91.189.92.179 80]

Why is this happening...? :|

---

### Post by jtarin on 2011-11-11
Try changing the server in software sources>Synaptic

---

