---
title: "[SOLVED] 8.04 - firewall"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by anewguy on 2008-05-28
I notice in the console messages as my system is booting that is says the universal firewall is not activated - something like UFW.  Is there something I need to specify somewhere so that a firewall really is activated?  I know we are supposed to be protected in some ways, and I know my DSL modem/wireless router has a built-in firewall, but I am curious about this.

Thanks in advance!  :)

---

### Post by sayakb on 2008-05-28
Well, install firestarter and reconfigure the IPTables configuration.

---

### Post by Scyron on 2008-05-28
Your router firewall operates separately from your default Ubuntu firewall, so if the former is up you're somewhat OK. To configure your router firewall, you need to get your Gateway Address (Either at System > Administration > Network > Properties or by right-clicking and selecting "Connection Information" on your network icon) and enter it into the URL bar. I believe PortForward.com should have the default passwords for accessing and changing settings.

If you want to configure your system firewall, I recommend Firestarter (Applications > Add / Remove > Search for Firestarter).

---

### Post by RSingh on 2008-05-28
> **LinuxIsInnovation said:**
> Well, install firestarter and reconfigure the IPTables configuration.

You can also enable UFW via terminal by:
```

ufw enable
```

More info here:
[https://wiki.ubuntu.com/UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall")

---

### Post by sayakb on 2008-05-28
Or perhaps:
```
sudo ufw enable
```

---

