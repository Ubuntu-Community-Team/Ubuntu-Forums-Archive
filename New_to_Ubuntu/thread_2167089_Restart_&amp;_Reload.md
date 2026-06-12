---
title: "Restart &amp; Reload"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by bhndbluiz on 2013-08-12
Hi!

I am currently running and old laptop of mine as a Minecraft server for myself and some friends. Like with any computer (and more so this computer since its from 2003) as it runs longer and as more work gets done on the world map, the computer starts to slow down. 

I was wondering if there was a program or script that is out there that would let me automatically restart the computer on a set schedule, but also reload the minecraft server. Right now I am just running vanilla minecraft server off openbox. But I am planning on replacing the laptop to a newer desktop computer thats alot more powerful and possibly run bukkit off it as well instead of vanilla. As I do not have anything installed on the newer desktop, if switching to another version of linux would help in this instance, I have no issues doing that. 

Any help or pointing me in the right direction would be great!

Thanks!

---

### Post by DuckHook on 2013-08-12
I don't know much about Minecraft (except what I have read on Wikipedia and the general press) but imagine that it must conform to the same conventions that almost all server-based apps do: there are likely configuration options that must be tweaked for it to run optimally on a given HW spec. In other words, you need to read the Minecraft guide on their site to optimize its settings for your equipment. These settings will likely change once you upgrade your HW.

Aside from the above, there is one major point that should be mentioned: most users new to Linux tend to run a GUI on their server (whether this be a fileserver, webserver or mailserver). The GUI needlessly eats up resources that can be better used for server functions. If you download and install the server distro of Ubuntu, it doesn't come with a GUI by default. Of course, a desktop environment can be easily added post-install, but the default is a CLI interface. If you wish to improve the response of your HW, then running a CLI-only environment will aid significantly. This is often impractical for new users, but you did ask for observations and alternatives.

---

### Post by Bucky Ball on 2013-08-12
No idea about Minecraft, but whatever flavour you opt for, try and make it an LTS release (if available in that flavour). Intended for servers and production machines and five years support life (Ubuntu in any case).

---

### Post by The-Server-4dmin on 2013-08-12
Did you install MSM? If so you can make a cron job reboot the system nightly and MSM will save the world.

---

### Post by bhndbluiz on 2013-08-17
I have no installed MSM, I will look into that. 

I was running straight linux without a GUI, but it was giving me issues when trying to run the server so loaded up xubuntu and openbox and it helped alot.

---

