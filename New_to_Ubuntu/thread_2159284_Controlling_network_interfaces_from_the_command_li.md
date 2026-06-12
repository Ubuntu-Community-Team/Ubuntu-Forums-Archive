---
title: "Controlling network interfaces from the command line"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by Cubytus on 2013-07-02
Hello all, 

this is probably a trivial question for many here. I just installed Ubuntu server on a laptop (LG R510), selecting the WLAN interface as the main interface. However, my router is not very stable at the moment for a reason I am still trying to know, and it lost connectivity. 

How do I manually reconnect the WLAN (or connect-cycle) in the command line?

Besides, when typing *ifconfig* it seems the wired connection is not visible. I know the card is compatible however from using Desktop edition Ubuntu.

---

### Post by newbie-user on 2013-07-02
Try:
```
lshw -class network
```
then look for the line "logical name: " for the interface you want to manage
Then once you figure out what the interface name is,
```
ifdown wlan#
ifup wlan#
```

Also, if your wired connection isn't showing up, the cable might not be connected properly. I'm assuming your wired connection uses DHCP? If you set it statically, it will always show in ifconfig.

---

### Post by Cubytus on 2013-07-03
Ok, I plugged in the cable, but got:
```
$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
```

---

### Post by steeldriver on 2013-07-03
AFAIK ifup relies on there being a definition for the interface in your /etc/network/interfaces file - if you only configured wireless during the install and didn't subsequently edit it, then likely no eth0 def exists there

If you are connecting the wired ethernet to a LAN router with DHCP then a minimal eth0 definition would be something like

```
iface eth0 inet dhcp
```

You could preface that with 'auto' if you want it to come up at boot, but don't need to if you just want to be able to bring it up manually for testing

 ```

auto eth0
iface eth0 inet dhcp

```

If you *do* make eth0 auto, you will probably want to comment out (or at least comment out the 'auto') of the wlan0 interface, at least until you get everything working right

---

### Post by Cubytus on 2013-07-08
In fact, I just followed Ubuntu's installation wizard and I don't recall it asking to configure another interface. The wording used was misleading in the sense that it implied this interface would be the one used for setup, but didn't say anything about running the server itself. I thought wired connection would be set up automatically.

I would like the server to use wifi when available, but since my router, for some reason, doesn't seem stable and sometimes cuts off radio, or internet access (Overclocked WRT54GL with radio power lowered at 20mW), I would like the server to automatically use wired connection if plugged in. It is configured in DHCP with static assignation for known computers.

Would there be a conflict if I don't comment out the "auto" for wlan0¿

---

### Post by wsxadf on 2013-07-08
If you do not want to create scripts for purpose of yours, perhaps you can try command-line programs such as wicd and wicd-curses. It works pretty good for me.

---

### Post by Cheesehead on 2013-07-08
> **Cubytus said:**
> In fact, I just followed Ubuntu's installation wizard and I don't recall it asking to configure another interface.
The installer asks just enough to install the system. It does not ask post-install configuration questions. Testing showed that users found extra questions tedious and confusing.

> **Cubytus said:**
> I thought wired connection would be set up automatically.
It would have been, if connected during the install.
Setting up a wired connection, as you have discovered, is very very easy.


> **Cubytus said:**
> I would like the server to use wifi when available [...and...] to automatically use wired connection if plugged in.
The priority you want is confusing. Usually you want the system to use wired first, then wireless. That's why Network Manager works that way, too.

Simply set up both in /etc/network/interfaces.
I recommend you make both auto, and let the system determine the best route to the gateway.


> **Cubytus said:**
> Would there be a conflict if I don't comment out the "auto" for wlan0
No, but you will do more work by hand than you really need to.

---

### Post by semaphore45 on 2013-08-08
> **Cheesehead said:**
> The installer asks just enough to install the system. It does not ask post-install configuration questions. Testing showed that users found extra questions tedious and confusing.Maybe not as a mandatory step to perform before being able to use the server, but at least provide a script in the user directory, asking all the other questions, to be run whenever a user wants it?


> It would have been, if connected during the install.
Setting up a wired connection, as you have discovered, is very very easy.
It was connected, as well as the wireless interface.


> The priority you want is confusing. Usually you want the system to use wired first, then wireless. That's why Network Manager works that way, too.It is, on the opposite, very clear. This server is physically a laptop that may need to be moved to different locations, sometimes hidden ones, where it would be impractical to lay a cable.


> No, but you will do more work by hand than you really need to.I want this server to be the most reliable as possible. It needs to be trouble-free, as maintenance-free as possible, able to recover by itself from power outages and gracefully go to sleep and wake-up. How can this be achieved?

---

### Post by semaphore45 on 2013-08-10
Addition to topic: now I made the change advised in [post #4]("http://ubuntuforums.org/showthread.php?t=2159284&p=12716860#post12716860"), but now the machine takes more than one minute trying to turn on the interfaces, before failing.

The command *ifonfig* only displays interfaces lo and virbr0, missing eth0 (defined as written above), and wlan0.
Command *ifup wlan0* ends with an error message:
```
/etc/network/interfaces:8: option with empty value
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

Error disappears when I comment out the 8th line and following except the eth0-related ones. This is however not a solution, merely a diagnosis helper.

I want to change the WPA2 key. How do I control this wireless interface from the command line, and have its configuration automatically saved?

---

