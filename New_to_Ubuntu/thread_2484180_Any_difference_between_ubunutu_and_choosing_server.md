---
title: "Any difference between ubunutu and choosing server and ubuntu server iso"
date: 2023-02-19
forum: New to Ubuntu
---

### Post by damien455 on 2023-02-19
HI all if there any difference between choose ubuntu server iso and the normal ubuntu iso and choosing the server option please?

Cheers

D

---

### Post by MAFoElffen on 2023-02-19
If you install the Desktop ISO, you are getting the GUI and a full suite of GUI applications, such as FireFox, Thunderbird, Nautilus File Manager, Network Manager, Gedit, Libre Office, etc, etc, etc.

If you install the Server ISO, you are getting just Ubuntu Base, Ubuntu Server minimal, Ubuntu Server... Console, basic console apps, networkd for network rendering, etc.

I guess your choice might be based on your comfort level, knowledge and experience in working from a console cli. 

Any GUI has it's security risks in an outward facing server, and uses resources that could be going to other things. If it is not outward facing, then the risks are less. You can load any server service on both Server Edition and Desktop Edition.

The choice is yours.

---

### Post by tea for one on 2023-02-20
> **damien455 said:**
> HI all if there any difference between choose ubuntu server iso and the normal ubuntu iso and choosing the server option please?
The normal Ubuntu Desktop iso such as [COLOR="#0000FF"]ubuntu-22.04-desktop-amd64.iso[/COLOR] does not offer a server option in the installation process.
The choices are normal or minimal .
More info here [https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup](https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup)

---

### Post by ActionParsnip on 2023-02-20
Server is command line only. The desktop ISO has a GUI. You can install a desktop environment on the server install if you like. This is how I install Ubuntu myself

---

### Post by damien455 on 2023-03-09
I am happy using the ubuntu server, but so far i been installing from an ISO manually either in a VM or usb.  Looking to swapping to netboot.xyz but does not seem to have an entry for ubuntu server

---

### Post by TheFu on 2023-03-09
> **damien455 said:**
> I am happy using the ubuntu server, but so far i been installing from an ISO manually either in a VM or usb.  Looking to swapping to netboot.xyz but does not seem to have an entry for ubuntu server

Google found them here:  [https://cdimage.ubuntu.com/netboot/](https://cdimage.ubuntu.com/netboot/)
Can't remember the last time I used it.  Perhaps 2012.   Ah .... Canonical does a bait-n-switch!  No more netboot, it seems.

---

### Post by TheFu on 2023-03-09
> **damien455 said:**
> HI all if there any difference between choose ubuntu server iso and the normal ubuntu iso and choosing the server option please? 

As others said, it is mostly the choice around having an integrated GUI or not.  Any server program can be installed on any desktop.  Some people prefer to install the server without a GUI, then add a lite window manager-only GUI. This doesn't bring the bloat that integrated desktops include with their 50 default applications.  It also doesn't add GUI interfaces to manage networking.

If you need a server, then avoid the GUI to reduce security risks. As others have said, GUIs use more system resources that could be better used by a running server instead AND there are many more security implications.  The Desktop ISOs also setup some things that don't make sense on servers, like mDNS/Avahi to discover LAN resources like media servers and printers.  With Avahi running, setting up supported printers is really, really, easy.  Avahi also allows DHCP network computers to locate each other using their hostname.local, even if their IP addresses change from time to time. This removes the need to run a DNS on the LAN and use static LAN IPs, if you want to interconnect different systems and network services easily. But if you want to run a more secure setup, having static IPs allows specific firewall rules to be created between each system, which can be handy.

In short, pick the right tool for the right job.

You have me curious about the netboot ISO files.  Think I'll try one out this morning, though I usually would use  LXD to manage LXC containers for specific services.  LXC is a little more than Docker, but not much. It can be very useful. Ah .... Canonical does a bait-n-switch!  No more netboot, it seems.

---

### Post by ian-weisser on 2023-03-09
> **TheFu said:**
> Canonical does a bait-n-switch!  No more netboot, it seems.

The netboot image was a byproduct of the older installer. With the switch to the newer Subiquity installer, that byproduct no longer exists.

Several Ubuntu developers have said in public that netboot was never part of their envisioned Ubuntu experience (it was a byproduct), and that they were unwilling to provide support for netboot. Whether or not we agree, that's their opinion and they are the ones doing the work.

When netboot was removed, discourse.ubuntu.com had quite the angry mob for a few weeks. Lots of complaints, lots of shouting about this mighty injustice...yet strangely none of the complainers were willing to fork the code that created netboot and simply keep producing it as a community project. They still can.

---

