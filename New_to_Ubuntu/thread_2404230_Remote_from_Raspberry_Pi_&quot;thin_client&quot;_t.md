---
title: "Remote from Raspberry Pi &quot;thin client&quot; to GUI Ubuntu guest on headless KVM host"
date: 2018-10-21
forum: New to Ubuntu
---

### Post by filonowst on 2018-10-21
[FONT=Arial][FONT=tahoma]Hello All,[/FONT][/FONT]

[FONT=Arial][FONT=tahoma]I've been googling for hours now with no luck. I'm playing with these technologies for the first time, so any direction would be greatly appreciated.[/FONT][/FONT]

[FONT=Arial][FONT=tahoma]I have very minimal headless Ubuntu 18.04 LTS installation running on my desktop (installed from [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD")). It has KVM installed and is running a guest VM with a less minimal, but still minimal Ubuntu 18.04 LTS installation with Gnome 3 (normal Desktop ISO, Lite installation or something like that, don't remember the exact terminology). I would like to access the guest remotely with a Raspberry Pi running Raspbian Stretch Lite with [/FONT][FONT=Verdana]RPD installed[/FONT][FONT=tahoma]. I am able to do this with this command from the Pi:[/FONT][/FONT]
```
[FONT=Arial][FONT=tahoma]ssh -X user@kvmhost virt-manager[/FONT][/FONT]

```
[FONT=Arial][FONT=tahoma]which launches a remote virt-manager session from which I can access a GUI desktop of my guest; however, it is very laggy. I understand that SPICE is the protocol made for this sort of thing and that virt-viewer is a spice client, but everything I have tried has failed. My goal is to provide the remote GUI access like the virt-manager command above, except using spice, presumably providing much less latency. I don't want to manage KVM or the VM configuration via GUI; I will do that over SSH.)[/FONT][/FONT]

[FONT=Arial][FONT=tahoma]I ran:[/FONT][/FONT]
```
[FONT=Arial][FONT=tahoma]sudo apt-get install spice-vdagent[/FONT][/FONT]

```[FONT=Arial][FONT=tahoma]on the guest and it was already installed. I installed virt-viewer on the KVM host and on the Pi. From the Pi, I ran:[/FONT][/FONT]
```
[FONT=Arial][FONT=tahoma]sudo virt-viewer --connect qemu+ssh://user@kvmhost/system guestname[/FONT][/FONT]

```[FONT=Arial][FONT=tahoma]and I get "Failed to connect: Unsupported graphic type 'spice'". If I add port 5900 to that address, I get "Unable to connect to libvirt with URI".[/FONT][/FONT]
[FONT=Arial][FONT=tahoma]
[/FONT][/FONT][FONT=Arial][FONT=tahoma]I may have some of the fundamentals wrong. Any guidance is VERY much appreciated![/FONT][/FONT]

---

