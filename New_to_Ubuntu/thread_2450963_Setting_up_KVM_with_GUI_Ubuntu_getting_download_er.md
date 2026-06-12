---
title: "Setting up KVM with GUI Ubuntu getting download errors"
date: 2020-09-23
forum: New to Ubuntu
---

### Post by wildmanonfiber on 2020-09-23
[COLOR=#242729][FONT=Arial]Hey all I am new to the world of Ubuntu.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I am trying to install [UBUNTU in GUI mode]("https://linuxize.com/post/how-to-install-xrdp-on-ubuntu-20-04/") so I can log into it like a normal remote desktop would work. So far I installed the GUI by doing this:

[/FONT][/COLOR]
```
sudo apt install ubuntu-desktop

```[COLOR=#242729][FONT=Arial]It went through all of its things and i *think* it was successful.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now I am trying to install the Xrpt so that I can use the remote desktop to get into the GUI Ubuntu.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]When trying to use this:[/FONT][/COLOR]
```
sudo apt install xrdp

```

[COLOR=#242729][FONT=Arial]It asks me the normal y/n about hard drive space and when I do Y it seems to do some things but ends up stopping because it was unable to find what it needed via the https links that no longer seem to work?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][[IMG]https://i.stack.imgur.com/YOXzq.png[/IMG]]("https://i.stack.imgur.com/YOXzq.png")

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have tried the suggested:[/FONT][/COLOR]
```
apt-get update

```[COLOR=#242729][FONT=Arial]And that also does not seem to work because of https links not working?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][[IMG]https://i.stack.imgur.com/Un7IV.png[/IMG]]("https://i.stack.imgur.com/Un7IV.png")

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So am I doing something incorrect?[/FONT][/COLOR]

---

### Post by TheFu on 2020-09-23
Are you stuck on using xrdp or would a better solution be considered?  xrdp has poor security.
[LIST]
[*]a) Gnome3 is bad for remote desktops.  Almost any other DE should be used.  Gnome3 is just too heavy and wants direct access to a GPU. Obviously, that isn't possible with a virtual machine or with remote access.
[*]b) A full remote desktop is usually a bad idea, but it depends on the use case. Best avoided.
[*]c) If remote access to applications is acceptable, don't use a remote desktop, use remote X11 which has been working well for decades.
```
ssh -X userid@remote-server "command to be run"
```
[*]d) If a remote desktop is required for some reason, use **x2go** and a "lite" DE (xcfe, mate, KDE, LXQt) or no DE, just a window manager like openbox or fvwm.  x2go has a client-side and a server-side.  All connectivity is through ssh, so get ssh working. Install the x2go PPA on both the client and the server.  There are x2go clients for Windows and OSX as well.  I know the Windows client was very stable.  The Linux x2go client seamlessly supports ssh-keys.
[/LIST]

If your KVM host has a GUI and you are running the guest VM on the same physical machine, you can connect to it using SPICE provided the VM guest machine supports QXL video drivers.  SPICE on the same machine is pretty freakin' fast.  I've watched hidef videos that way by accident.  The local connection commands are:
/usr/bin/virt-viewer -a -d  CaseSensitiveGuestVMNAME &

Over the LAN, you can use 
/usr/bin/virt-viewer --connect qemu+ssh://{insert-vm-hostname-or-IP}/system CaseSensitiveGuestVMNAME &

Replace {insert-vm-hostname-or-IP} with the name that works on your network.  I have a script that gets copied to different systems, so I don't need to remember which command type is needed:
```
#!/bin/bash
GO=regulus
if [[ $HOSTNAME == "hadar" ]] ; then
    # For local connection on hadar
    /usr/bin/virt-viewer -a -d  $GO &
else
    # For remote connections on the LAN
    /usr/bin/virt-viewer --connect qemu+ssh://hadar/system $GO &
fi
```

hadar is my VM host running KVM.
regulus is the guest VM running Ubuntu 20.04 Mate.

I only use this when a full DE is desired, which is almost never.  I prefer to use X11 for GUI applications, so to run libreoffice on regulus, but display it on my current physical machine:
```
ssh -X regulus "libreoffice ~/TODO/GTD-Todo.xls"
```
The libreoffice window shows up in about a second.

As for doing maintenance on Ubuntu Desktops, here's a short guide: 
  [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
It was republished on a huge tech/life improvement website. I've updated it over the years to stay current with new releases.

On both the physical machine and inside the VM, you need to run:
**sudo apt update && sudo apt full-upgrade**
Do that every week on both. If either fail to work. Fix those issues before doing anything else.  Always mention that you are using a KVM virtual machine for issues within the VM.

Above, I've shown multiple options. You don't need them all.

---

