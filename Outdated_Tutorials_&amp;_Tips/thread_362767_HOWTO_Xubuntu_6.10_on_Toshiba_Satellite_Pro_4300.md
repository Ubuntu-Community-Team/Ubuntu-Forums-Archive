---
title: "HOWTO: Xubuntu 6.10 on Toshiba Satellite Pro 4300"
date: 2007-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by eok on 2007-02-16
**Xubuntu 6.10 on Toshiba 4300 Laptop (PIII 7000, 320mb ram, 40gb drive, floppy)**
Initial install seemed to work great.  However, some rough edges needed to be smoothed over.  Here's what I did...

**Preparation:**
Upgraded BIOS to 2.70.  This is the last BIOS released for the 'pro 4300 series.  Get BIOS from [http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp)

Booted the Xubuntu 6.10 livecd/install CD.  Installed it to the hard drive.

**Wireless:**
Asus WL-107G PCMCIA Card 
Recognized at boot,  rt2500 driver automatically used (serialmonkey).  I have to use WPA/PSK.  To get WPA/PSK to work, I added this to end of /etc/network/interfaces:

[FONT="Courier New"]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ra0
iface ra0 inet dhcp
        pre-up iwconfig ra0 essid put_your_AP_name_here
        pre-up iwconfig ra0 mode managed
        pre-up iwpriv ra0 set Channel="11"
        pre-up iwpriv ra0 set AuthMode="WPAPSK"
        pre-up iwpriv ra0 set EncrypType="TKIP"
        pre-up iwpriv ra0 set WPAPSK="put_your_passphrase_here"
[/FONT]
Note: put your own values in place for essid, Channel (11 is a common default) and passphrase.

That's all I had to do.  I rebooted and it automagically worked without any additional fuss.

**ACPI:**
ACPI didn't work at first.  Fan never came on while running Xubuntu.  No /proc/acpi either.

Did this first: [https://help.ubuntu.com/community/ACPIBattery](https://help.ubuntu.com/community/ACPIBattery)

Next, setup ACPI “laptop_mode” by editing /etc/default/acpi-support and setting ENABLE_LAPTOP_MODE=TRUE .  There are other tunable values in this file too.

The kernel didn't like the age of the 4300's v2.70 BIOS and would not support ACPI by default.  This is a normal gotcha with older BIOS versions.  If you do a “dmesg | grep BIOS” you'll see what the kernel says about this.  The workaround: edit the /boot/grub/menu.lst file and add the kernel parameter “acpi=force” to the command line that boots your kernel.  Reboot.

End result: Totally stable – no problems.  Wireless rocks.  ACPI works well enough for me.  “acpi -V” now shows accurate info.  /proc/cpuinfo shows the right stuff too.  Fan engages periodically as it should, system runs much cooler.  I'm happy.  ;^)

---
eric

---

### Post by murlosad on 2007-02-21
Quick question to which you may not have the answer...

Did you have any trouble getting the pcmcia slots working?

I've got a pro 4300 that I've been running ubuntu 6.06 on for a while without trouble.  I decided to go wireless but I could not get the wireless card to activate in the pcmcia slot.  with or without the wired card in. (wireless is dlink dwl-g650, and wired is xircom creditcard)

So, I tried installing 6.10 hoping it would pick it up for me, and I lost the wired card as well as wireless. Near as I can tell, the pcmcia slots are not activating. I'm not sure if this is a hardware problem or not. But I though I would ask if you or anyone else has had similar problems.

Thanks for the how-to.

---

