---
title: "smb nuked after update?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-07-16
I had setup a smb share between my Ubuntu and my popcorn-a100 media center. To mount the mediacenter I just went to Places --> Network --> and found the popcorn smb share folder there. Double clicking it mounted the folder so I could delete or transfer files to it.

But after a hardy proposed update this morning the popcorn folder can no longer be seen/found at the usual place. The only visible proof on my Ubuntu that popcorn exists is when I use Ping - Network tools. Can someone help me to mount the media center like before?

---

### Post by nowshining on 2008-07-16
try mounting it thru the terminal :)

but i don't know how to mousnt a smb share or whatever - only drives..it may or may not be the same..

---

### Post by peakshysteria on 2008-07-16
Damn irritating. Everything looks just like before.  Only thing that is missing from the network folder is a shared folder from within Ubuntu and the popcorn media center share folder. Can't find any command for mounting the folder.

---

### Post by JillSwift on 2008-07-16
I think probably there's been a shift in master browser.
Re-starting the popcorn appliance might bring it all back (forcing your machine to be the browse master).
If you know the appliance's IP number you can use that to get to the appliance too, but this isn't a solution just a work-around.

BTW, how do you like the Popcorn? It looks like a nifty little device.

---

### Post by peakshysteria on 2008-07-16
The share is setup default from popcorn as smb://pch-a100/share/
This worked like a charm before the update of Ubuntu this morning. I think there was an update for smb in Hardy proposed. So this might be the reason.

Restarting popcorn didn't help at all. And restarting Ubuntu didn't work either. I have the ip for popcorn. As mentioned above i can ping popcorn. But not sure how to mount it so it lies under Places --> Network. I guess my problem isn't unheard of. But I'm such a n00b when it comes to networking that I'm stuck. Reading guides and commands haven't helped at all.```
 mount smb://pch-a100/share/
```gives me:```
mount: can't find smb://pch-a100/share/ in /etc/fstab or /etc/mtab
```

I guess this is the wrong command...

---

### Post by JillSwift on 2008-07-16
Well, [smbmount]("http://www.linuxcommand.org/man_pages/smbmount8.html") may be what you're after there.

---

### Post by peakshysteria on 2008-07-16
Thanks man. But I must admit I not much worth when it comes to the terminal (yet). But i found a command bringing me closer:
```
smbclient -L (popcorn ip) -U%
```gives me:
> Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]

	Sharename       Type      Comment
	---------       ----      -------
	share           Disk      
	IPC$            IPC       IPC Service (SMP8634 Share)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]

	Server                         Comment
	---------                      -------
	PCH-A100                       SMP8634 Share

	Workgroup                       Master
	---------                       -------
	WORKGROUP                       PCH-A100

But how do I mount the share from terminal from here on? And how do I transfer this into a gui and back to how it was? (when the share folder was accessible via Places --> Network --> ). Right now I can't get anywhere.

Apparently there is a bug that might be my problem:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411)
The apparent solution```
sudo /etc/init.d/winbind stop
``` doesn't work for me. Anyone have a different solution?

---

