---
title: "Connection dropped during upgrade - now stuck"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by duncan2a on 2013-01-20
Hi

I'm upgrading to 12.10 and my connection dropped during 'Installing upgrades'. I got the connection up and running again, but the upgrade is stuck. The package it't trying to download is the flash installer. 

I can't cancel the upgrade to start it again and I can't move forward. I've tried disabling and re-enabling the wifi in the hopes that it notices that the connection is back, but nothing.

How do I fix this?

---

### Post by duncan2a on 2013-01-20
Just noticed - the distribution upgrade program seems to have frozen altogether

---

### Post by tgalati4 on 2013-01-20
Don't panic.  And don't reboot.  If your system is running, it will keep running.

Close any open upgrade dialog boxes.  Open a terminal:

```
sudo apt-get check
sudo apt-get dist-upgrade

```

---

### Post by monkeybrain2012 on 2013-01-20
One reason I don't do upgrade.

---

### Post by HunterDX77M on 2013-01-20
> **monkeybrain2012 said:**
> One reason I don't do upgrade.

I got into a scenario similar to the OP's situation and learned this lesson the hard way. I think the LTS is really the only way to go.

---

### Post by monkeybrain2012 on 2013-01-20
> **HunterDX77M said:**
> I got into a scenario similar to the OP's situation and learned this lesson the hard way. I think the LTS is really the only way to go.

I meant I always do clean install.

---

