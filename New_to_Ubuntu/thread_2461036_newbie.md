---
title: "newbie"
date: 2021-04-23
forum: New to Ubuntu
---

### Post by matanica66 on 2021-04-23
Hello.
I'm very new and trying to install Tailscale in Terminal using:

curl -fsSL [https://pkgs.tailscale.com/stable/ubuntu/focal.gpg](https://pkgs.tailscale.com/stable/ubuntu/focal.gpg) | sudo apt-key add -
curl -fsSL [https://pkgs.tailscale.com/stable/ubuntu/focal.list](https://pkgs.tailscale.com/stable/ubuntu/focal.list) | sudo tee /etc/apt/sources.list.d/tailscale.list

I get the following error:

Command 'curl' not found, but can be installed with:

sudo apt install curl

Any help is appreciated.

Thanks

Mat

---

### Post by ActionParsnip on 2021-04-23
Run:
```

sudo apt install curl

```
as stated in the output. The system is telling you the command to run to install curl.

---

### Post by matanica66 on 2021-04-23
Thank you so much!

---

### Post by grahammechanical on 2021-04-23
For those like myself who don't know and are also curious -

> **curl** is a **command**  line tool to transfer data to or from a server, using any of the  supported protocols (HTTP, FTP, IMAP, POP3, SCP, SFTP, SMTP, TFTP,  TELNET, LDAP or FILE). **curl** is powered by Libcurl. This tool is preferred for automation, since it is designed to work without user interaction.15 May 2019

Apparently, it is not part of the default Ubuntu installation. And as for Tailscale, well, I am not that curious. :)

Regards

---

