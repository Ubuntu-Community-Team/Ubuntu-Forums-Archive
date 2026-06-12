---
title: "Error run/installing program!"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by AprendizZ on 2012-03-23
Hello!
I try to install and run a similar program that I use in Windows, but to Linux. The program is Checkpoint VPN-1 SecureClient who have the linux name SNX VPN-1. I already installed by terminal with sudo su and run ./scinstall.sh. Also I receive the message that I needed to install extra packages, libsigsegv2 and libsigsegv2 schem2c, and I proced with this instalation too. Finish this all instalations I only need to use the program, first add the site I connect my vpn, with command "scc add <sitename>".
But when I digit this in prompt I receive the error messages: gcc: error: add: no such file or directory; gcc: error: <sitename>: no such file or directory.
Also I try one thing, digit in prompt only scc. The error messages are: /usr/bin/ld: cannot find -lsigsegv; collect2: ld returned 1 exit status.
Any help, please!

---

### Post by AprendizZ on 2012-03-23
I forgot to tell, I have Ubuntu 11.10  .

---

### Post by d4m1r on 2012-03-23
Sorry, I don't have any experience with that software.

Do you need to use that specific software? What kind of VPN connection is it? Ubuntu has built in support for many VPN connection types in Network Manager, and if you need a special kind, you can just install a plugin to add that support. VPN software on Ubuntu is picky, thats why I recommend trying different VPN software.

---

### Post by AprendizZ on 2012-03-24
Thanks. I already try to use OpenSwan and KVpnc but this are used in terminal mode. I need one with windows (GUI). Rigth now I try to test the Shrew VPN, but till now I cannot to configure this to use IPsec without certificates. 
If someone can help me I apreciate. Thanks again.

---

