---
title: "security problem with apt-get"
date: 2005-02-07
forum: Repositories &amp; Backports
---

### Post by jamaas on 2005-02-07
Newbie here, attempting to update kernel package to 686 but get a security error such as 

What have I done wrong?

Thanks

Jim

The following NEW packages will be installed:
  linux-686 linux-image-2.6-686 linux-image-2.6.8.1-4-686 linux-image-686 linux-restricted-modules-2.6-686
  linux-restricted-modules-2.6.8.1-4-686 linux-restricted-modules-686
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.9MB of archives.
After unpacking 54.3MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main linux-image-2.6.8.1-4-686 2.6.8.1-16.10
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main linux-image-2.6-686 2.6.8.1-14
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main linux-image-686 2.6.8.1-14
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out

---

### Post by nocturn on 2005-02-07
This is actually not a security error.

Apt is just saying that it cannot connect to the server  security.ubuntu.com.

Is your networkconnection up?
Can you resolve the host (in a terminal: 'host security.ubuntu.com')
Can you ping the host?

---

### Post by jamaas on 2005-02-07
Thanks nocturn

I can resolve it but not ping it, just hangs.  Could this be a firewall or proxy server problem?  I think I have to deal with both....

thanks

Jim


[QUOTE=nocturn]This is actually not a security error.

Apt is just saying that it cannot connect to the server  security.ubuntu.com.

Is your networkconnection up?
Can you resolve the host (in a terminal: 'host security.ubuntu.com')
Can you ping the host?[/QUOTE]

---

### Post by nocturn on 2005-02-07
[QUOTE=jamaas]Thanks nocturn

I can resolve it but not ping it, just hangs.  Could this be a firewall or proxy server problem?  I think I have to deal with both....

thanks

Jim[/QUOTE]

Yes, it seems you have a network access problem.
Can you see any other servers.?

---

### Post by Razvan on 2005-02-08
can you ping google?

---

### Post by jamaas on 2005-02-08
Thanks guys,  It is/was a proxy server problem, found an example of using

export http_proxy=http://my.proxy.server:3128/

and that fixed the problem!


Thanks

Jim

---

