---
title: "Mounting BTHomeHub5 USB help"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by vilesy on 2014-05-04
Hello everyone!

OK, so I usually manage to find my way through things with no problems as I have been using Linux for a fair few years now, however I have now hit a brick wall with this BTHomeHub5 USB mounting after browsing many many forums.

Here is the scenario.

I am using on of my Raspberry Pis to create a sort of NAS. It's not really but basically I have a couple of HDD plugged into it and they can be accessed via a samba share. I can mount everything on my linux PC with no problems using cifs in its /etc/fstab. I mention this so you now I have a rough idea about samba and cifs mounting. :p 

What I am trying to do is make an /etc/fstab entry to mount the BTHomeHub on the raspberry PI.

Now, with this Home Hub USB, I know it uses samba sharing to share the USB drive on the network. I can even see it on the PI (as well as on my other Linux PCs) using `**smbclient -L bthub5**` as shown below:

```
Domain=[HOME] OS=[Unix] Server=[Samba 3.0.28]


    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (BT Home Hub 5.0A File Server)
    USB1            Disk      XXXXXXXXXXXXXXX (Rev: )
Domain=[HOME] OS=[Unix] Server=[Samba 3.0.28]


    Server               Comment
    ---------            -------
    BTHUB5               BT Home Hub 5.0A File Server


    Workgroup            Master
    ---------            -------
    HOME                 BTHUB5
```

When on my PC I can mount it, without a username or password prompt, via nautilus or by using `**gvfs-mount smb://bthub5/usb1**` in the terminal. This all works fine!

I cannot however mount it on any linux device using /etc/fstab:

```
//bthub5/usb1/                  /media/BTShare                  cifs            sec=none 0 0
```

I receive the following error when running mount -a:

**mount error(115): Operation now in progress**
**Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)**

I also get an error on the PI (via SSH I might add so I think this is the dbus thing I've been reading about) when running `**gvfs-mount smb://bthub5/usb1**`:

[B]"Error mounting location: volume doesn't implement mount"

[/B]
I have tried changing the workgroup, however I couldn't see this making any difference due to the fact I can already see it on my differently named workgroup as noted above.
I have tried changing the name-resolve order in the /etc/samba/smb.conf to bcast host as suggested in other posts.
I have changed the /bthub5/usb1 to //192.168.1.254/usb1 as suggested by the BT help pages. I can see this IP using `**arp -a**`so know it is there but it does not ping. This could be BT blocking ICMP on it though... maybe...
I have tried pretty much everything I can find and think of and I am completely stuck!

Basically I'm wondering if I've missed anything obvious that someone can see.
If there is a log I can check to see something to do with the errors (as I've checked most and cannot see anything more descriptive).
Or if anyone can provide me any information to get this working as I've been racking my brains for the past 24 hours on this one. It's driving me mad now :p

Thanks muchly in advance :-D

---

