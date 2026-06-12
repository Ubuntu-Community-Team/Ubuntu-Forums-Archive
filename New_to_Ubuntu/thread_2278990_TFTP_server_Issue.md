---
title: "TFTP server Issue"
date: 2015-05-20
forum: New to Ubuntu
---

### Post by hail3 on 2015-05-20
Hi
I have installed tftpd-hpa service on my Ubuntu 12.04 machine.
The service is running fine , I have checked the status. But when I am trying to access the file from the TFTP server using a windows machine(TFTP client service enable) I am getting the error connect request failed. Kindly resolve the issue

---

### Post by HermanAB on 2015-05-20
Howdy,

TFTP has no authentication.  It protects you by only allowing access to files if they are marked Read Only.

So try something like:
$ cd /tftp
$ chmod 444 *

---

