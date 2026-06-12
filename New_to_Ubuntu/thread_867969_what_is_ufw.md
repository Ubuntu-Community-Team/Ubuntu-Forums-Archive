---
title: "what is ufw?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by waggingwabbit on 2008-07-23
the latest update today was this file only. its a firewall? or firewall setting program? I hear that, on windows atleast, its not good to have 2 software firewalls or 2 hardware firewalls running at the same time. is it okay to have this program running along with iptables and firestarter? iptables is the default firewall right?

---

### Post by justin whitaker on 2008-07-23
> **waggingwabbit said:**
> the latest update today was this file only. its a firewall? or firewall setting program? I hear that, on windows atleast, its not good to have 2 software firewalls or 2 hardware firewalls running at the same time. is it okay to have this program running along with iptables and firestarter? iptables is the default firewall right?

ufw is [Uncomplicated Fire Wall]("https://wiki.ubuntu.com/UbuntuFirewall"), and it is basically an easy, paired down, method of creating iptables firewall rules. It's more like an interface to iptables than a replacement. 

Firestarter is a firewall similar to the commerical ones...you know, an all in one application (firewall, rules management tool, monitor).

You can run both without much of a penalty to your performance.

---

### Post by mikewhatever on 2008-07-23
Here is the description of the package:
> Ufw is a tool to manage a local host-based firewall. It provides a command line interface and aims to be uncomplicated and easy to use.

As you see, it's not a firewall, but only a configuration tool. Needless to say, that no such process runs by default.

> **justin whitaker said:**
> 

Firestarter is a firewall similar to the commerical ones...you know, an all in one application (firewall, rules management tool, monitor).

This is a very common misconception. Firestarter is only a GUI tool for configuring iptables.

---

### Post by waggingwabbit on 2008-07-24
so why was this in the auto update for? if its not a program that runs by default...

---

### Post by Methuselah on 2008-07-24
IIRC the linux firewall is built right into the operating system kernel.
There are separate applications for configuring the feature though, basically as a user convenience. I think ufw is one of them,

---

### Post by ibutho on 2008-07-24
> **waggingwabbit said:**
> so why was this in the auto update for? if its not a program that runs by default...

Its a program built into Ubuntu, just like system-config-firewall in Fedora and SuSEfirewall in openSUSE. These type of programs are meant to make it easier for you to configure firewall settings although you can opt to use different frontends to iptables+netfilter e.g. shorewall, if you wish.

---

### Post by hyper_ch on 2008-07-24
(1) ufw is a "easy" way to configure iptables (as most other "firewall" stuff in linux).

(2) ufw gets installed by default, hence the upgrade

(3) IMHO in most cases you don't even need to alter the default configuration of iptables

---

### Post by RomeReactor on 2008-07-24
> **waggingwabbit said:**
> so why was this in the auto update for? if its not a program that runs by default...

Hi. UFW is installed by default in Hardy, but it's not enabled by default. Run:
```
sudo ufw status
```
it should return 'Firewall not loaded' or something very similar. Also try:
```
man ufw
```for more information on how to use it. Basic commands are:
```
sudo ufw enable
```
to start it. It will remain enabled even after a restart or shutdown/startup. Once it's enabled, let's open port 51413 for Transmission:
```
sudo ufw allow 51413
```
If you only want to enable TCP:
```
sudo ufw allow 51413/tcp
```
It also looks for protocols in **/etc/services**, so you can use the name of the protocol instead of the port number.

---

### Post by waggingwabbit on 2008-07-24
ok...

i just did sudo ufw status and it said firewall isn't loaded, so i did sudo ufw enable and it enabled the firewall...does that mean the firewallon ubuntu by default is always off?

I restarted the computer after enabling it, i did sudo ufw status again to see if it really was enabled, and it said it was. but after the restart it was disabled again. But, when i open up firestarter, it says the fire wall is active...while ufw says its not...

---

### Post by hyper_ch on 2008-07-24
ufw is not a firewall
firestarter is not a firewall

iptbles is a firewall --> check if iptables is running

besides, are you shure you need to mess with it?

---

### Post by mcduck on 2008-07-24
> **waggingwabbit said:**
> ok...

i just did sudo ufw status and it said firewall isn't loaded, so i did sudo ufw enable and it enabled the firewall...does that mean the firewallon ubuntu by default is always off?

I restarted the computer after enabling it, i did sudo ufw status again to see if it really was enabled, and it said it was. but after the restart it was disabled again. But, when i open up firestarter, it says the fire wall is active...while ufw says its not...

If you are already sing Firestarter you don't need to use UFW.

Just like people have already pointed out, they are both just configuration tools controlling the same firewall (which is part of the Linux kernel).

Actually you _shouldn't_ try to control it with multiple tools at the same time..

edit: Yes, in the default install the Firewall is not active. This is because the default install has no services running that would respond to incoming network connections, so there isn't anything that would need to be controlled with a firewall. You don't really need a firewall unless you install programs that listen to incoming connections, like different servers and such.

---

