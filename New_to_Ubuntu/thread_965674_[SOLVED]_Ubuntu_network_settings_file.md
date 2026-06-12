---
title: "[SOLVED] Ubuntu network settings file"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-10-31
Why Ubuntu doesn't use the file interfaces for the network settings like every distro? because if i set my interfaces file with a setting the OS dont see it, Only works when you use the gui to set your ip settings, the network manager, there is a way to do it in a text file?
thanks in advance

---

### Post by stephanvaningen on 2008-10-31
I don't know exactly but could it be that changes will be forced after restarting the /etc/init.d/'s network-service?

---

### Post by drakeman007 on 2008-10-31
> **stephanvaningen said:**
> I don't know exactly but could it be that changes will be forced after restarting the /etc/init.d/'s network-service?


Mmm dont know i made ```
sudo /etc/init.d/networking restart
```
after i modify the interfaces file, but ubuntu doesnt take care of that file! i dont know where it saves the configuration file!

---

### Post by aeiah on 2008-10-31
have you tried disabling the network manager? it isnt just ubuntu, network manager takes control in fedora too.

---

### Post by stephanvaningen on 2008-10-31
In any way, /etc/network/interfaces contains the network settings. If I change that file's 'iface eth0 inet static'-addres-line, and then I do this:
 ```
sudo /etc/init.d/networking restart
```
If after that I do this:
 ```
ifconfig
```
I see my ip addres changed.

---

### Post by drakeman007 on 2008-10-31
> **stephanvaningen said:**
> In any way, /etc/network/interfaces contains the network settings. If I change that file's 'iface eth0 inet static'-addres-line, and then I do this:
 ```
sudo /etc/init.d/networking restart
```
If after that I do this:
 ```
ifconfig
```
I see my ip addres changed.

But in my case this file is blank, just have the loopback interface defined ....

---

### Post by drakeman007 on 2008-10-31
Anyone else knows about this topic, and can explain a little more in how ubuntu handles the network config file?
thanks

---

### Post by drakeman007 on 2008-11-01
Anyone have an idea about this, or a link with a how to?
pleaseee!
thanks

---

### Post by wgrant on 2008-11-01
Before Ubuntu 8.10, Network Manager only handled DHCP. Static addresses were configured in /etc/network/interfaces, and NM would ignore any such interfaces.

In Ubuntu 8.10, Network Manager handles static IP addresses too. You can still put things in /etc/network/interfaces, but there's very little point in doing that if you can use Network Manager.

---

### Post by drakeman007 on 2008-11-01
> **wgrant said:**
> Before Ubuntu 8.10, Network Manager only handled DHCP. Static addresses were configured in /etc/network/interfaces, and NM would ignore any such interfaces.

In Ubuntu 8.10, Network Manager handles static IP addresses too. You can still put things in /etc/network/interfaces, but there's very little point in doing that if you can use Network Manager.

Thanks for the info! 
Really appreciate W grant!
:guitar:

---

### Post by waffen on 2008-11-01
> **wgrant said:**
> Before Ubuntu 8.10, Network Manager only handled DHCP. Static addresses were configured in /etc/network/interfaces, and NM would ignore any such interfaces.

In Ubuntu 8.10, Network Manager handles static IP addresses too. You can still put things in /etc/network/interfaces, but there's very little point in doing that if you can use Network Manager.
Hello,

Uhm...I just replace my /etc/network/interfaces file with this:

> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 201.234.63.82
        netmask 255.255.255.192
        network 201.234.63.0
        broadcast 201.234.63.255
        gateway 201.234.63.65


and the NetworkManager dont appeat when I restart my Ubuntu, because when I try:

sudo /etc/init.d/network restart

the changes dont save and in the restart, Ubuntu take the changes but I dont have internet.. My network params are OK? 

Thanks!

---

### Post by xxxpse on 2008-11-02
Hi

another question about Ubunut 8.10 and the network.

I got 8.10 installed as update and this was the last time I could connect to the internet. After restarting (which was caused by the 8.10 update), I do not get any connection to the internet anymore. In network manager I cannot modify the static ip address as it says that it is read-only?
I returned back to windows to be able to participate here now :-(

---

### Post by waffen on 2008-11-02
Hello,

I foun the solution:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

I installed Wicd and all my problems go out! :) I can connect with my static IP address I see the wifi.

I have a problem with thew intrepid repos for Wicd, but I downloaded from sourceforge de deb. packages, uninstall NetworkManage and WifiRadar if you have preintalled both of them.

I can not test with wifi network (actually I can see a pair of wifi network more.. :D) but another user can try it?

---

