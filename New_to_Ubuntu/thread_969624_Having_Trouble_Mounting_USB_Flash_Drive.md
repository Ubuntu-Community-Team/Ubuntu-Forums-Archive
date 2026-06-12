---
title: "Having Trouble Mounting USB Flash Drive"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by jasimp on 2008-11-03
I just installed Intrepid Ibex and having a little trouble mounting my USB drive. It is a Kingston DataTraveler, DTI highspeed series. According to their site ([here]("http://www.kingston.com/support/USBFLASHDRIVES/FAQ/faq_dti_hs_2.asp") the drive is supported on Linux. I installed pmount to make this process a little easier but it is still not working. Just to make sure, to correctly install pmount all you do is click 'install' in the Synaptic Package Manager? Any help would be greatly appreciated.

---

### Post by taurus on 2008-11-03
Plug in the drive, open a terminal, and post the output of this command here.

Applications -> Accessories -> Terminal
```
dmesg | tail
```

---

### Post by kansasnoob on 2008-11-03
My first thought is to unplug the drive, then at terminal:

```
 sudo apt-get install --reinstall pmount
```

The only dependency I'm aware of is hal which should be there by default, but just to be sure also run:

```
sudo apt-get -f install
```

Then try plugging the drive in again.

I don't recall having to restart the desktop to get those changes to take hold.

---

### Post by C.S.Cameron on 2008-11-03
oops.

---

### Post by jasimp on 2008-11-04
> **taurus said:**
> Plug in the drive, open a terminal, and post the output of this command here.

Applications -> Accessories -> Terminal
```
dmesg | tail
```

Sorry for the late reply. 

Here is the output
```
[  271.178076] type=1503 audit(1225818751.182:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5292 profile="/usr/sbin/cupsd"
[  271.178936] type=1503 audit(1225818751.182:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5292 profile="/usr/sbin/cupsd"
[  271.179781] type=1503 audit(1225818751.182:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5292 profile="/usr/sbin/cupsd"
[  272.223867] ppdev0: registered pardevice
[  272.270045] ppdev0: unregistered pardevice
[  272.604006] ppdev0: registered pardevice
[  272.650195] ppdev0: unregistered pardevice
[ 9024.633268] __ratelimit: 3 callbacks suppressed
[ 9024.633274] flashplayer-ins[9278]: segfault at bf354ffc ip b7e3de06 sp bf355000 error 6 in libc-2.8.90.so[b7dc7000+158000]
[ 9050.490426] flashplayer-ins[9308]: segfault at bf42bffc ip b7f15dd5 sp bf42c000 error 6 in libc-2.8.90.so[b7e9f000+158000]
```

---

