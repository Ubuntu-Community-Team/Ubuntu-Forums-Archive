---
title: "can not install Microsoft Edge on ubuntu 24.04"
date: 2024-05-17
forum: New to Ubuntu
---

### Post by carroca on 2024-05-17
i am a newbie tried installing microsoft edge using error by sudo apt install.  i get an error in terminal; microsoft-edge
MESA-INTEL: warning: cannot initialize blitter engine

When i try clicking on the icon, nothing happens.

i have a new laptop with an intel core ultra 9 185 prestige 16 AI Studio

please help.

---

### Post by TheFu on 2024-05-18
Since this post hasn't gotten any replies in the last day, thought I'd post so you knew someone read it.

Very few Linux users would touch Microsoft Edge.  It isn't a core part of any Linux distro, so you may find better responses from a MSFT-centric forum.  I've never loaded Edge on any computer.

If I were required to test my web-apps for Windows users, I'd have a Windows virtual machine and run the standard software inside it with our testing suite and all the test cases.

---

### Post by Dennis N on 2024-05-18
There is a Flatpak for Edge browser. You might have better luck with that.

```
dmn@Sydney:~$ flatpak remote-info flathub com.microsoft.Edge

Microsoft Edge - Introducing the new Microsoft Edge web browser. It’s time to
expect more. More privacy. More control. More productivity. More value.

        ID: com.microsoft.Edge
       Ref: app/com.microsoft.Edge/x86_64/stable
      Arch: x86_64
    Branch: stable
   Version: 124.0.2478.109-1
   License: LicenseRef-proprietary
Collection: org.flathub.Stable
  Download: 7.2*MB
 Installed: 20.6*MB
   Runtime: org.freedesktop.Platform/x86_64/23.08
       Sdk: org.freedesktop.Sdk/x86_64/23.08


```

You would have to install the Flatpak support first. See: [https://flathub.org/setup](https://flathub.org/setup)

---

### Post by MAFoElffen on 2024-05-18
Since by your command, you might start out by doing this to remove what you implied you did
```

sudo apt remove --purge microsoft-edge-stable
sudo rm /etc/apt/sources.list.d/microsoft-edge-dev.list
sudo find / -name "microsoft.gpg" -exec bash -c "sudo rm {}" \; 2>/dev/null
sudo apt update

```
My curiosity is why 'Edge'. Windows Users don't even like it forced on them...

---

### Post by Cleaton_Duguid on 2024-07-22
One can install Microsoft Edge via GDebi. See [https://itsfoss.com/gdebi-default-ubuntu-software-center/](https://itsfoss.com/gdebi-default-ubuntu-software-center/) for a good Howto

Note: Many, including myself, have found that Microsoft Edge will not launch, the first time, after it is installed in Ubuntu 24.04. This is simply resolved by rebooting the PC.

---

### Post by modismos on 2024-07-22
A senior developer explained the solution to a similar issue.


The error message "MESA-INTEL: warning: cannot initialize blitter engine" typically relates to graphics drivers or libraries.
 
Follow these commands in the same sequence:


```
sudo apt update && sudo apt upgrade
```


```
sudo apt install mesa-utils

```

```
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt update
sudo apt upgrade

```

```
sudo apt remove microsoft-edge
sudo apt install microsoft-edge
```

---

### Post by fyfe54 on 2024-07-23
Or use the Vivaldi browser.  Mostly open source (the UI is closed) and comes without the G***** baggage.
Very customzable.

[https://vivaldi.com](https://vivaldi.com)

---

