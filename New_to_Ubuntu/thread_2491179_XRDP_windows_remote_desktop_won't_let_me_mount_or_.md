---
title: "XRDP windows remote desktop won't let me mount or modify FSTAB"
date: 2023-09-28
forum: New to Ubuntu
---

### Post by mvinsky on 2023-09-28
[COLOR=#232629][FONT=-apple-system]I have several internal nvme drives and I discovered they weren't mounted. I couldn't get them to mount using "disks" because I'm "not authorized to perform operation". My account belongs to the adm and sudo groups so I can't figure out why it wouldn't let me. When I open the terminal and log into root I can mount the drives so I think its a permission issue but I don't know why. This is on Ubuntu 22.04.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The only thing I can think of is that because I'm connecting remotely using Windows Remote Desktop through XRDP/XCFE there must be some restrictions that a local user doesn't face. I can't find any references on the internet, can someone help with this?

I want to use "disks" to change the mount settings for the drives because I'm a new user and modifying the FSTAB file using the terminal is intimidating. I know mistakes could cause some real issues so lifting these restrictions would be a big help.[/FONT][/COLOR]

---

### Post by TheFu on 2023-09-28
> **mvinsky said:**
> The only thing I can think of is that because I'm connecting remotely using Windows Remote Desktop through XRDP/XCFE there must be some restrictions that a local user doesn't face. I can't find any references on the internet, can someone help with this?

I want to use "disks" to change the mount settings for the drives because I'm a new user and modifying the FSTAB file using the terminal is intimidating. I know mistakes could cause some real issues so lifting these restrictions would be a big help.

No. Local or remote doesn't matter. Linux doesn't care.  Linux isn't like MSFT with different privileges if you are remote or local.  Now, if the storage you are trying to mount to Linux is on Windows, then MSFT's arbitrary rules about that can impact success.

OT follows, but I was on a roll typing .... so you get it:

gnome-disks is full of issues and bugs. Best to use pretty much any other method.  Beware that mounting NTFS on a remote system means using CIFS as the protocol.  Much better to use native Linux file systems and NFS for a number of reasons.  Modifying the fstab isn't hard. Just don't touch any existing lines and it will be fine.
I don't use XRDP (or any RDP) and stopped using CIFS when we powered off our last Windows system running on hardware a few years ago.  As for mounting, I don't use fstab for network mounts, since they may not always be there. For on-demand mounting, I much prefer to use autofs, which mounts configured storage as needed and removes it when that need is gone.

MSFT's implementation of CIFS has changed drastically the last few years, so you'll need to be very specific about the client and the server to get useful help.

I don't know what XCFE is. Could you mean XFCE4?  XFCE4 is a good choice for any remote desktop.

---

