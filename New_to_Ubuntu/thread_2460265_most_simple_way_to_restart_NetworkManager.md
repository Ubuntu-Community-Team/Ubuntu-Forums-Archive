---
title: "most simple way to restart NetworkManager"
date: 2021-04-06
forum: New to Ubuntu
---

### Post by maketopsite on 2021-04-06
Classical way - opening terminal, typing  ```
sudo systemctl restart NetworkManager
``` is too complicated for some non technical user.

Is there please simpler way  ?

Ubuntu 20.04, icewm.

---

### Post by Tadaen_Sylvermane on 2021-04-06
reboot.

---

### Post by TheFu on 2021-04-06
Put those commands into a shell script that is located in the PATH. It won't work for normal users, but it will for users in the sudo group.

But if this isn't a laptop, perhaps **not using** network manager is an option? A desktop would probably be best with static IP. NetworkManager can be removed then.  No need to restart somethings that always works.

---

### Post by ActionParsnip on 2021-04-06
Why are you restarting network manager so much? What is the use case here

---

### Post by maketopsite on 2021-04-07
> **Tadaen_Sylvermane said:**
> reboot.

well, thank you

---

### Post by maketopsite on 2021-04-07
well, thank you.

It is a laptop using one IP address from wifi router. It is still on one same location "as desktop".

Wifi was not working once time after start of Ubuntu. Full reboot did not help. Wifi had started to work after
```
sudo systemctl restart NetworkManager
```

---

### Post by maketopsite on 2021-04-07
> **ActionParsnip said:**
> Why are you restarting network manager so much? What is the use case here

Please see previous post [https://ubuntuforums.org/showthread.php?t=2460265&p=14030586#post14030586](https://ubuntuforums.org/showthread.php?t=2460265&p=14030586#post14030586)

---

### Post by TheFu on 2021-04-07
> **maketopsite said:**
> well, thank you.

It is a laptop using one IP address from wifi router. It is still on one same location "as desktop".

Wifi was not working once time after start of Ubuntu. Full reboot did not help. Wifi had started to work after
```
sudo systemctl restart NetworkManager
```

I'd setup the network using netplan and disable network-manager (everything).  Once netplan was proven to be stable for a week, then I'd purge network-manager-{everything}.  None of my systems have any network-manager software on them. My laptop that does move from time to time uses wicd for wifi.  At home, that laptop uses a wired ethernet connection with a USB-to-ethernet adapter.

---

### Post by Tadaen_Sylvermane on 2021-04-07
Give it a static ip assignment at the router? This way you can keep the laptop on dhcp for mobility but at home or whatever it will always get whatever ip you set? I used to avoid doing that, now I live by it rather than setting ip's on every device / machine in my home that I control.

---

### Post by TheFu on 2021-04-07
> **Tadaen_Sylvermane said:**
> Give it a static ip assignment at the router? This way you can keep the laptop on dhcp for mobility but at home or whatever it will always get whatever ip you set? I used to avoid doing that, now I live by it rather than setting ip's on every device / machine in my home that I control.

I do this for laptops and devices that are hard or impossible to set static IPs, but for any system that will be a server, I set any static IPs on-the-OS so a dhcp failure doesn't prevent communications on the LAN. LAN systems don't need a router to talk.
Sometimes the dhcp reservation setup is easy.  Sometimes not.  [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

---

### Post by maketopsite on 2021-04-14
> **TheFu said:**
> I'd setup the network using netplan and disable network-manager (everything).  Once netplan was proven to be stable for a week, then I'd purge network-manager-{everything}.  None of my systems have any network-manager software on them. My laptop that does move from time to time uses wicd for wifi.  At home, that laptop uses a wired ethernet connection with a USB-to-ethernet adapter.

Does it need [FONT=courier new]systemd-networkd[/FONT] ?

---

### Post by TheFu on 2021-04-14
> **maketopsite said:**
> Does it need [FONT=courier new]systemd-networkd[/FONT] ?

I don't know. I've never had to install anything special.
```
$ dpkg -l '*networkd*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version      Architecture Description
+++-===================-============-============-=====================================>
ii  networkd-dispatcher 2.0.1-1      all          Dispatcher service for systemd-networ

```
is the only package with "*networkd*" in the name.

---

### Post by maketopsite on 2021-04-15
> **TheFu said:**
> I don't know. I've never had to install anything special.
```
$ dpkg -l '*networkd*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version      Architecture Description
+++-===================-============-============-=====================================>
ii  networkd-dispatcher 2.0.1-1      all          Dispatcher service for systemd-networ

```
is the only package with "*networkd*" in the name.

From example on [https://netplan.io/examples/](https://netplan.io/examples/)   :
```
renderer: networkd
```

```
Netplan supports both networkd and Network Manager as backends. You can specify which network backend should be used to configure particular devices by using the renderer key.
```

Is it necessary to use renderer ?

Are you running systemd-networkd ?
```
# systemctl status systemd-networkd
&#9679; systemd-networkd.service - Network Service
     Loaded: loaded (/lib/systemd/system/systemd-networkd.service; disabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:systemd-networkd.service(8)
```

---

### Post by TheFu on 2021-04-15
```
renderer:
```
is required as part of the netplan.io config file.

If NetworkManager is listed, then networkd won't be used and all the issues that NetworkManager has come to the system.
But a simple netplan config file for static IPs removes the need for NetworkManager and all those issues:

Here's an example from a 20.04 system:
```
$ more /etc/netplan/[COLOR="#0000FF"]01-ens3-static[/COLOR].yaml 
network:
  version: 2
  renderer: networkd
  ethernets:
     [COLOR="#0000FF"]ens3[/COLOR]:
       addresses:
          - [COLOR="#0000FF"]172.22.22.3/24[/COLOR]
       dhcp4: false
       dhcp6: false
       gateway4: [COLOR="#0000FF"]172.22.22.1[/COLOR]
       nameservers:
         addresses: [ [COLOR="#0000FF"]172.22.22.80, 172.22.22.81[/COLOR] ]

```
I've colored the parts you should insert different values for in blue.

After changing those parts, run these commands:
```
sudo netplan generate
sudo netplan apply --debug
```

That's it. No more network-manager problems.

---

### Post by ActionParsnip on 2021-04-15
Watch the spacing. YAML is picky. Some you have to TAB, some are SPACES.

---

### Post by TheFu on 2021-04-15
> **ActionParsnip said:**
> Watch the spacing. YAML is picky. Some you have to TAB, some are SPACES.

The YAML spec doesn't mandate either, just be consistent.  I've never used tabs in a yaml file.  There is a requirement that at least 2 spaces are needed for an indentation level, but as long as there are 2 or more spaces, the number doesn't matter, provided all entries of the same level have the same number of spaces.  Different levels can use different numbers of spaces. I suppose at least 1 tab could be used to create an indentation level. Just not my style.

**Be consistent in spaces, that's the rule for YAML.**

Some people may have their editor setup to swap 
spaces for tabs 
  Or
tabs for spaces
automatically.  This will always cause problems, IME.

Now, gmake and other versions of Makefiles **do** have a tab character mandate, but that isn't YAML.

---

### Post by The Cog on 2021-04-15
I believe that yaml disallows tabs. Ref: section 6.1 here: [https://yaml.org/spec/1.2/spec.html#id2777534](https://yaml.org/spec/1.2/spec.html#id2777534) :
> To maintain portability, tab characters must not be used in indentation, since different systems treat tabs differently.

I just tried python yaml module and it allows tabs equal to 4 spaces.

---

### Post by Tadaen_Sylvermane on 2021-04-17
> **TheFu said:**
> I do this for laptops and devices that are hard or impossible to set static IPs, but for any system that will be a server, I set any static IPs on-the-OS so a dhcp failure doesn't prevent communications on the LAN. LAN systems don't need a router to talk.
Sometimes the dhcp reservation setup is easy.  Sometimes not.  [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

Good point. I have had this problem a few times.

> **The Cog said:**
> I believe that yaml disallows tabs. Ref: section 6.1 here: [https://yaml.org/spec/1.2/spec.html#id2777534](https://yaml.org/spec/1.2/spec.html#id2777534) :


I just tried python yaml module and it allows tabs equal to 4 spaces.

I've used single spaces without a problem thus far. Anything else has always failed for me.

---

### Post by TheFu on 2021-04-17
> **The Cog said:**
> I believe that yaml disallows tabs. Ref: section 6.1 here: [https://yaml.org/spec/1.2/spec.html#id2777534](https://yaml.org/spec/1.2/spec.html#id2777534) :
I just tried python yaml module and it allows tabs equal to 4 spaces.

[https://yaml.org/spec/1.2/spec.html#id2775170](https://yaml.org/spec/1.2/spec.html#id2775170)
> Section 5.5: 
YAML recognizes two white space characters: space and tab. 

There is an example with both spaces and tabs used for indentation.  It is important to make things complicated, whenever possible to increase confusion, no doubt. :D

---

### Post by maketopsite on 2021-04-19
> **TheFu said:**
> ```
renderer:
```
is required as part of the netplan.io config file.

If NetworkManager is listed, then networkd won't be used and all the issues that NetworkManager has come to the system.
But a simple netplan config file for static IPs removes the need for NetworkManager and all those issues:

Here's an example from a 20.04 system:
```
$ more /etc/netplan/[COLOR=#0000FF]01-ens3-static[/COLOR].yaml 
network:
  version: 2
  renderer: networkd
  ethernets:
     [COLOR=#0000FF]ens3[/COLOR]:
       addresses:
          - [COLOR=#0000FF]172.22.22.3/24[/COLOR]
       dhcp4: false
       dhcp6: false
       gateway4: [COLOR=#0000FF]172.22.22.1[/COLOR]
       nameservers:
         addresses: [ [COLOR=#0000FF]172.22.22.80, 172.22.22.81[/COLOR] ]

```
I've colored the parts you should insert different values for in blue.

After changing those parts, run these commands:
```
sudo netplan generate
sudo netplan apply --debug
```

That's it. No more network-manager problems.

Thank you. I spent some time but I'm sorry it does not work. I can't spent more time on it now. Maybe I will return to it when it can save my time.

---

