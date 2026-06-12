---
title: "Resetting Network Settings"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by nktrox on 2008-09-02
Hi!

I have just installed a multi-boot Ubuntu with Windows. However, whenever i boot to Ubuntu from Windows, the lan connection does not work, no internet and no network. I have to restart Ubuntu to get the lan working again. 

I guess restarting is just resetting the network settings. How can i do this without restarting?

---

### Post by jemate18 on 2008-09-02
> **nktrox said:**
> Hi!

I have just installed a multi-boot Ubuntu with Windows. However, whenever i boot to Ubuntu from Windows, the lan connection does not work, no internet and no network. I have to restart Ubuntu to get the lan working again. 

I guess restarting is just resetting the network settings. How can i do this without restarting?

So correct me If I understood it wrong.
1. You have a dual-boot setup
2. When booting to Windows, Networking is fine
3. After logging out from windows and booting to Ubuntu (first boot after windows) the network conn doesnt work.
4. To be able to make the network conn work, you have to restart Ubuntu?

OK. so if you don't have the connection on Ubuntu? What is the output of these command
1. Application -> Accessories -> Terminal
2. Type
```
ifconfig -a
```

---

### Post by xadder on 2008-09-02
I don't have any Windows stuff, but occassionally I lose the network. I was given the advice to try either:


sudo dhclient eth0

or,

sudo /etc/init.d/network force-reload

Works great.

---

### Post by jemate18 on 2008-09-02
> **xadder said:**
> I don't have any Windows stuff, but occassionally I lose the network. I was given the advice to try either:


sudo dhclient eth0

or,

sudo /etc/init.d/network force-reload

Works great.

an alternative is:
```
sudo /etc/init.d/networking restart
```

---

