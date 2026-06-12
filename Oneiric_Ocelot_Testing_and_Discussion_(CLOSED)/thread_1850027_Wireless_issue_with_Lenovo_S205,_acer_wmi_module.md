---
title: "Wireless issue with Lenovo S205, acer_wmi module"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by OrphanShadow on 2011-09-25
Hello all

I'm trying to get wifi fully up and working on my S205 laptop. It uses a Ralink rt3090 which is working via the rt2800pci module.

Since beginning my testing I have found a very strange problem.

When booting with the acer_wmi module enabled, networkmanager reports the wireless as being disabled. I can use 'sudo rmmod acer_wmi' and that kicks the wireless into gear.

So, I attempted blacklisting acer_wmi. Upon doing that and rebooting, however, networkmanager then reports the wireless as being 'disabled by hardware switch' (not just 'disabled'). To correct this I have to modprobe acer_wmi then rmmod it again in order to regain wireless.

Its a strange issue.

The laptop has 2 wireless switches: a keyboard switch and a switch on the side of the laptop.

Any ideas for this?

---

### Post by cariboo on 2011-09-25
What's the output of:

```
sudo rfkill --list 
```

---

### Post by OrphanShadow on 2011-09-26
Sorry for the late reply.

Here is the output with acer_wmi loaded:

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

Output after rmmod acer_wmi
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

EDIT: Output after reboot with acer_wmi blacklisted
```
0: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

---

### Post by cariboo on 2011-09-26
I'd remove acer_wmi from the blacklist and try:

```
sudo rfkill --unblock 3
```

to see if that works.

---

### Post by OrphanShadow on 2011-09-27
rfkill did not work. It still shows acer-wireless as soft-blocked after running either 'rfkill unblock 3' or 'rfkill unblock wlan'

The '--' before the command seems unnecessary, as the command only works without them.

---

### Post by cariboo on 2011-09-27
> **OrphanShadow said:**
> rfkill did not work. It still shows acer-wireless as soft-blocked after running either 'rfkill unblock 3' or 'rfkill unblock wlan'

The '--' before the command seems unnecessary, as the command only works without them.

I include the double dash, as I'm on my desktop system which doesn't have a wireless device connected at the moment.

---

### Post by OrphanShadow on 2011-09-27
> **cariboo907 said:**
> I include the double dash, as I'm on my desktop system which doesn't have a wireless device connected at the moment.

Ah okay. Sorry if I sounded confrontational there ;)

But yeah, do you have any idea as to why it not unblocking and what I can do to fix it?

---

### Post by OrphanShadow on 2011-09-29
Bump. Still haven't found a workaround for this.

---

### Post by nrosvall on 2011-09-29
I found someone saying that adding following to /etc/rc.local 
 
rfkill unblock wifi
rfkill unblock all
modprobe -r acer-wmi
 
will fix wireless in ubuntu 11.10 for Lenovo s205. He/She said that blacklisting does not work for some reason, but modprobe -r in rc.local will. I haven't tested this yet thought. I also have S205 and this same problem.
 
Could you test this and report does it work?

---

### Post by lucazade on 2011-09-29
or add a fake param to acer-wmi kernel module in order to stop loading
```
gksu gedit /etc/default/grub

```append after 'quiet splash' this:
```
acer-wmi.dummy=1

```and finalize grub with:
```
sudo update-grub

```
not really elegant solution but should work :)

EDIT: it is 'acer-wmi' and not 'acer_wmi' ... at least modinfo said that.

---

### Post by OrphanShadow on 2011-09-29
> **nrosvall said:**
> I found someone saying that adding following to /etc/rc.local 
 
rfkill unblock wifi
rfkill unblock all
modprobe -r acer-wmi
 
will fix wireless in ubuntu 11.10 for Lenovo s205. He/She said that blacklisting does not work for some reason, but modprobe -r in rc.local will. I haven't tested this yet thought. I also have S205 and this same problem.
 
Could you test this and report does it work?

That worked like a charm =) Thank you so so much. :KS

---

### Post by amirfoad on 2011-09-29
Good for you.
I'm using HP Mini 110 and it also uses rt3090 and after upgrading to Ubuntu 11.10 it has the same problem as you. What can I do? Can you help me? It's really important for me to have wireless connections.
Thanks a lot.

---

### Post by nrosvall on 2011-09-30
> **OrphanShadow said:**
> That worked like a charm =) Thank you so so much. :KS
 
 
No problem. I tested that too and it works for me too, so I can confirm. Also I was suprised that the hardware switch as well as the software switch works too.

---

### Post by nrosvall on 2011-09-30
> **amirfoad said:**
> Good for you.
I'm using HP Mini 110 and it also uses rt3090 and after upgrading to Ubuntu 11.10 it has the same problem as you. What can I do? Can you help me? It's really important for me to have wireless connections.
Thanks a lot.
 
 
Did you try to add
 
```
rfkill unblock wifi
rfkill unblock all
modprobe -r acer-wmi

```
 
to /etc/rc.local and reboot?

---

### Post by amirfoad on 2011-09-30
you know this code:> modprobe -r acer-wmi
will not work on an HP device!

---

### Post by nrosvall on 2011-09-30
> **amirfoad said:**
> you know this code:
will not work on an HP device!
 
Oh yes. It's propably hp-wmi or hp_wmi. Not sure..

---

