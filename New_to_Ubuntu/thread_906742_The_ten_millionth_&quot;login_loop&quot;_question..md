---
title: "The ten millionth &quot;login loop&quot; question."
date: 2008-08-31
forum: New to Ubuntu
---

### Post by detroit/zero on 2008-08-31
Uptime tells me that my Toshiba Satellite has been running for four days nonstop, and it's acting a little sluggish. I decide to do a quick reboot.

GDM pops up, I click my username, enter my password, and everything looks OK.

My wallpaper comes up, AWN, the top panel, and then conky starts to appear, when the screen goes black, and GDM re-appears asking for my username/pass again. It does this endlessly.

I am able to login under failsafe mode, but trying to use a standard session just leads to more looping.

I don't have a fancy video card or anything; just a standard Toshiba laptop. Here's my lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

auth.log gives me an error "cannot determine username" or some such thing.

Here's auth.log from when I rebooted til now:
```
Aug 31 23:59:52 zero-laptop gdm[6060]: pam_unix(gdm:session): session closed for user zero
Sep  1 00:01:13 zero-laptop gdm[6070]: pam_nologin(gdm:auth): cannot determine username
Sep  1 00:01:17 zero-laptop gdm[6070]: pam_unix(gdm:session): session opened for user zero by (uid=0)
Sep  1 00:01:36 zero-laptop gdm[6070]: pam_unix(gdm:session): session closed for user zero
Sep  1 00:01:45 zero-laptop gdm[6616]: pam_nologin(gdm:auth): cannot determine username
Sep  1 00:00:48 zero-laptop gdm[6616]: pam_unix(gdm:session): session opened for user zero by (uid=0)
Sep  1 00:00:54 zero-laptop gdm[6616]: pam_unix(gdm:session): session closed for user zero
Sep  1 00:02:21 zero-laptop gdm[6059]: pam_nologin(gdm:auth): cannot determine username
Sep  1 00:02:33 zero-laptop gdm[6059]: pam_unix(gdm:session): session opened for user zero by (uid=0)
Sep  1 00:02:51 zero-laptop gdm[6059]: pam_unix(gdm:session): session closed for user zero
Sep  1 00:03:15 zero-laptop login[4824]: pam_unix(login:session): session opened for user zero by LOGIN(uid=0)
Sep  1 00:06:48 zero-laptop sudo:     zero : TTY=tty2 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/nano /etc/modprobe.d/modules
Sep  1 00:06:48 zero-laptop sudo: pam_unix(sudo:session): session opened for user root by zero(uid=0)
Sep  1 00:06:48 zero-laptop sudo: pam_unix(sudo:session): session closed for user root
Sep  1 00:06:59 zero-laptop sudo:     zero : TTY=tty2 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/nano /etc/init.d/modules
Sep  1 00:06:59 zero-laptop sudo: pam_unix(sudo:session): session opened for user root by zero(uid=0)
Sep  1 00:06:59 zero-laptop sudo: pam_unix(sudo:session): session closed for user root
Sep  1 00:07:12 zero-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=zero ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Sep  1 00:07:12 zero-laptop sudo: pam_unix(sudo:session): session opened for user zero by (uid=0)
Sep  1 00:07:12 zero-laptop sudo: pam_unix(sudo:session): session closed for user zero
Sep  1 00:07:12 zero-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=zero ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Sep  1 00:07:12 zero-laptop sudo: pam_unix(sudo:session): session opened for user zero by (uid=0)
Sep  1 00:07:12 zero-laptop sudo: pam_unix(sudo:session): session closed for user zero
Sep  1 00:07:12 zero-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=zero ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Sep  1 00:07:12 zero-laptop sudo: pam_unix(sudo:session): session opened for user zero by (uid=0)
Sep  1 00:07:12 zero-laptop sudo: pam_unix(sudo:session): session closed for user zero
Sep  1 00:07:52 zero-laptop sudo:     zero : TTY=tty2 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/killall
Sep  1 00:07:52 zero-laptop sudo: pam_unix(sudo:session): session opened for user root by zero(uid=0)
Sep  1 00:07:52 zero-laptop sudo: pam_unix(sudo:session): session closed for user root
Sep  1 00:08:05 zero-laptop sudo:     zero : TTY=tty2 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/killall -u zero -v
Sep  1 00:08:05 zero-laptop sudo: pam_unix(sudo:session): session opened for user root by zero(uid=0)
Sep  1 00:08:05 zero-laptop sudo: pam_unix(sudo:session): session closed for user root
Sep  1 00:08:20 zero-laptop sudo:     zero : TTY=tty2 ; PWD=/etc/init.d ; USER=root ; COMMAND=/etc/init.d/gdm start
Sep  1 00:08:20 zero-laptop sudo: pam_unix(sudo:session): session opened for user root by zero(uid=0)
Sep  1 00:08:20 zero-laptop sudo: pam_unix(sudo:session): session closed for user root
Sep  1 00:08:48 zero-laptop sudo:     zero : TTY=tty2 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/killall -v -u zero
Sep  1 00:08:48 zero-laptop sudo: pam_unix(sudo:session): session opened for user root by zero(uid=0)
Sep  1 00:08:48 zero-laptop sudo: pam_unix(sudo:session): session closed for user root
Sep  1 00:09:01 zero-laptop CRON[7124]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  1 00:09:01 zero-laptop CRON[7124]: pam_unix(cron:session): session closed for user root
Sep  1 00:09:05 zero-laptop sudo:     zero : TTY=tty2 ; PWD=/ ; USER=root ; COMMAND=/etc/init.d/gdm restart
Sep  1 00:09:05 zero-laptop sudo: pam_unix(sudo:session): session opened for user root by zero(uid=0)
Sep  1 00:09:05 zero-laptop sudo: pam_unix(sudo:session): session closed for user root
Sep  1 00:09:13 zero-laptop gdm[7162]: pam_nologin(gdm:auth): cannot determine username
Sep  1 00:09:15 zero-laptop gdm[7162]: pam_unix(gdm:session): session opened for user zero by (uid=0)
Sep  1 00:09:20 zero-laptop gdm[7162]: pam_unix(gdm:session): session closed for user zero
Sep  1 00:09:50 zero-laptop gdm[7410]: pam_nologin(gdm:auth): cannot determine username
Sep  1 00:09:52 zero-laptop gdm[7410]: pam_unix(gdm:session): session opened for user zero by (uid=0)
Sep  1 00:10:00 zero-laptop gdm[7410]: pam_unix(gdm:session): session closed for user zero
Sep  1 00:10:15 zero-laptop gdm[7709]: pam_nologin(gdm:auth): cannot determine username
Sep  1 00:10:18 zero-laptop gdm[7709]: pam_unix(gdm:session): session opened for user zero by (uid=0)
Sep  1 00:14:15 zero-laptop gdm[7709]: pam_unix(gdm:session): session closed for user zero
Sep  1 00:14:25 zero-laptop gdm[7709]: pam_nologin(gdm:auth): cannot determine username
Sep  1 00:14:34 zero-laptop gdm[7709]: pam_unix(gdm:session): session opened for user zero by (uid=0)
Sep  1 00:14:40 zero-laptop gdm[7709]: pam_unix(gdm:session): session closed for user zero
Sep  1 00:14:48 zero-laptop gdm[8916]: pam_nologin(gdm:auth): cannot determine username
Sep  1 00:14:55 zero-laptop gdm[8916]: pam_unix(gdm:session): session opened for user zero by (uid=0)
Sep  1 00:17:01 zero-laptop CRON[9544]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  1 00:17:01 zero-laptop CRON[9544]: pam_unix(cron:session): session closed for user root
Sep  1 00:20:36 zero-laptop passwd[10086]: pam_unix(passwd:chauthtok): new password not acceptable
Sep  1 00:33:49 zero-laptop sudo:     zero : TTY=unknown ; PWD=/home/zero ; USER=root ; COMMAND=/usr/sbin/synaptic
Sep  1 00:33:49 zero-laptop sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Sep  1 00:33:49 zero-laptop sudo: pam_unix(sudo:session): session closed for user root
Sep  1 00:39:01 zero-laptop CRON[21689]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  1 00:39:01 zero-laptop CRON[21689]: pam_unix(cron:session): session closed for user root
```

I haven't installed anything lately.. I haven't even had an update come through in the last four or five days.

Let me know if I can provide any other logs or info.

Thanks.

---

### Post by nitro_n2o on 2008-08-31
are you trying to log in with the user name 'root'? 

the root account is not activated by default in ubuntu.. 
log in with the user name u chose when u installed the system

---

### Post by detroit/zero on 2008-08-31
> **nitro_n2o said:**
> are you trying to log in with the user name 'root'? 
No, actually, my username is zero. That was just from me using sudo nano to look at logs from the virtual terminal and such.

---

### Post by detroit/zero on 2008-09-01
Still stuck in failsafe mode.

Bump.

---

### Post by Bodsda on 2008-09-01
Boot up, get to the gdm screen then press

ctrl+alt+F1

this will change run levels and you will be presented with a login prompt, if you can login succesfully here press

ctrl+alt+F7        (i think its F7)

to get back to the normal run level

if you cant log in, what hapens??

---

### Post by detroit/zero on 2008-09-01
I can log into the virtual terminal no problem.

After I log in, it says root has 6 mail messages. From inside the mail command, there's 6 messages from anachron saying something about a problem verifying the server name, and defaulting to 127.0.0.1

After checking those out, going back to a regular command prompt and hitting ctrl-alt-f7 to change run level just takes me back to the gdm login screen, where I either use gnome failsafe mode or suffer the never-ending-loop.

---

