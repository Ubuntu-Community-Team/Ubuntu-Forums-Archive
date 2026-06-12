---
title: "Slow Fesity Boot Time Fix For Laptop"
date: 2007-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by bubbalouie on 2007-04-21
Hi All,

This is my first post so apologies if anything is awry, I felt I have learned so much from these forums that I should try contribute something (although right now I have nothing significant).

I found that Feisty has a terrible boot time on my laptop compared to my server (roughly 3x as long) even though it is a faster computer. I have managed to bring my boot time from over a minute to roughly 30 seconds by doing the following:

```
sudo kate /etc/network/interfaces
```

Now comment out the wireless card (in this case *eth1*)

```


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[B]#auto eth1
#iface eth1 inet dhcp[/B]

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```

The boot time has improved immensely, and my wireless still works fine (with WPA2) once KDE boots, I expect that mounting of network shares at boot may break if you use wireless though, right now I haven't verified this.

Cheers

Ryan

---

### Post by Atticka on 2007-04-21
I tried this out on my NX9420 HP Laptop and it fixed my slow boot time (used to hang on "configuring network"). This laptop uses a restricted Intel wireless driver.

After rebooting my wireless connected just fine and my mapped network drive work fine as well.

Thanks for the fix!

---

### Post by emrextreme on 2007-04-21
I am using ethernet (only eth0) for internet connection. What if i comment them all but eth0 out, would i lose my connection?

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by fusionisthefuture on 2007-04-21
dont comment out the lo adapter, that ones needed (its just the onboard loopback adapter, it doesnt actually access the outside world) but all the other ones besides eth0 and lo should be able to be commented out.

---

### Post by bubbalouie on 2007-04-22
Thanks, glad to know someone found this useful :)

---

### Post by Rinzwind on 2007-04-22
You might also want to check this page:
[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

Your change didn't work for me (42.56 seconds before and 42.34 after changing).
The changes on  the page I posted made it from 42.34 to 42.12 :P ) so it's not alot :D

---

### Post by cdmn on 2008-02-16
I'm using Gibbon, and tried out things you said in your post but all got was this

```
auto lo
iface lo inet loopback

```

no eth0 or eth1 and also my boot time is over 3 minutes... I had the same problem when I tried to install Xubuntu. My computer is a Compaq Evo N1015v AMD Athlon XP processor with 1.6 GHz.

:confused::(

---

