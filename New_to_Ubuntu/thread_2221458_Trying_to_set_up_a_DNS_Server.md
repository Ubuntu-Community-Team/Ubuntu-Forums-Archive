---
title: "Trying to set up a DNS Server"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by joelkelly2007 on 2014-05-02
I'm running Ubuntu 14.04 x64 CLI, I'm trying to get it up and running as a DNS server. I was wondering if anyone knows how I can go about doing this?

I've been trying to follow [this]("https://help.ubuntu.com/14.04/serverguide/dns-configuration.html") guide, but I get access denied when trying to access /etc/bind/named.conf.options

---

### Post by SeijiSensei on 2014-05-02
Probably you're not using [sudo]("https://help.ubuntu.com/community/RootSudo").  I glanced at that section of the Server Guide, and it doesn't make explicit that you must edit all the files for BIND9 as root with sudo.

---

