---
title: "PC crashing and / or shutting down"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-09-28
For about the past three days, my Oneiric test system has been behaving very strangely. If I walk away from it for some amount of time (like an hour or so), when I come back it is powered down.It is difficult to turn back on, too. If I simply power it back up, it does not boot. Then, if I press the reset button, it will reboot.

Every time, it looks like the network goes down, then the crash or shutdown. I have no idea what is causing this. Here is a few seconds of syslog entries up to the crash:

```

Sep 28 10:10:20 tim-oneiric kernel: [12338.750326] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0
Sep 28 10:10:20 tim-oneiric kernel: [12338.750331] /home/tim/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.c:3861 assert KeyIdx < 4failed
Sep 28 10:10:20 tim-oneiric kernel: [12338.750334] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8405)
Sep 28 10:10:20 tim-oneiric kernel: [12338.750344] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
Sep 28 10:10:20 tim-oneiric kernel: [12338.750346]              WCIDAttri = 0x1
Sep 28 10:10:20 tim-oneiric kernel: [12338.750348] AsicRemovePairwiseKeyEntry : Wcid #1
Sep 28 10:10:20 tim-oneiric kernel: [12338.750349] AsicRemoveSharedKeyEntry: #5
Sep 28 10:10:20 tim-oneiric kernel: [12338.750356] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0
Sep 28 10:10:20 tim-oneiric kernel: [12338.750361] /home/tim/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.c:3861 assert KeyIdx < 4failed
Sep 28 10:10:20 tim-oneiric kernel: [12338.750364] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8406)
Sep 28 10:10:20 tim-oneiric kernel: [12338.750371] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
Sep 28 10:10:20 tim-oneiric kernel: [12338.750373]              WCIDAttri = 0x1
Sep 28 10:10:20 tim-oneiric kernel: [12338.750375] AsicRemovePairwiseKeyEntry : Wcid #1
Sep 28 10:10:20 tim-oneiric kernel: [12338.750376] AsicRemoveSharedKeyEntry: #0
Sep 28 10:10:20 tim-oneiric kernel: [12338.750383] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0
Sep 28 10:10:20 tim-oneiric kernel: [12338.750388] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8401)
Sep 28 10:10:20 tim-oneiric avahi-daemon[918]: Interface ra0.IPv4 no longer relevant for mDNS.
Sep 28 10:10:20 tim-oneiric NetworkManager[922]: <info> (ra0): cleaning up...
Sep 28 10:10:20 tim-oneiric NetworkManager[922]: <info> (ra0): taking down device.
Sep 28 10:10:20 tim-oneiric kernel: [12338.753762] -->WriteDatThreadInit()
Sep 28 10:10:20 tim-oneiric kernel: [12338.753863] <--WriteDatThreadInit(), status=0!
Sep 28 10:10:20 tim-oneiric kernel: [12338.753867] -----> WriteConfToDatFile
Sep 28 10:10:20 tim-oneiric kernel: [12338.754289] <----- WriteConfToDatFile
Sep 28 10:10:20 tim-oneiric kernel: [12338.754859] ===> rt28xx_close
Sep 28 10:10:20 tim-oneiric kernel: [12338.754861] ==> MlmeHalt
Sep 28 10:10:20 tim-oneiric kernel: [12338.754863] --->Disable TSF synchronization
Sep 28 10:10:20 tim-oneiric kernel: [12338.754886] RTMPSetLED::Mode=1,HighByte=0x00,LowByte=0x00
Sep 28 10:10:20 tim-oneiric avahi-daemon[918]: Interface ra0.IPv6 no longer relevant for mDNS.
Sep 28 10:10:20 tim-oneiric avahi-daemon[918]: Leaving mDNS multicast group on interface ra0.IPv6 with address fe80::ca3a:35ff:fecf:26ea.
Sep 28 10:10:20 tim-oneiric avahi-daemon[918]: Withdrawing address record for fe80::ca3a:35ff:fecf:26ea on ra0.
Sep 28 10:10:20 tim-oneiric kernel: [12338.759867] <== MlmeHalt
Sep 28 10:10:20 tim-oneiric kernel: [12338.759869] MacTableReset
Sep 28 10:10:20 tim-oneiric kernel: [12338.759883] RTMPSetLED::Mode=1,HighByte=0x20,LowByte=0x01
Sep 28 10:10:20 tim-oneiric kernel: [12338.759885] RT28xxPciMlmeRadioOFF===>
Sep 28 10:10:20 tim-oneiric kernel: [12338.759887] -->MlmeRadioOff() return on bRadio == TRUE;
Sep 28 10:10:20 tim-oneiric kernel: [12338.759925] <---RTPCICmdThread
Sep 28 10:10:20 tim-oneiric kernel: [12338.759974] RT28xxPciAsicRadioOff ===> Lv= 2, TxCpuIdx = 41, TxDmaIdx = 41. RxCpuIdx = 81, RxDmaIdx = 82.
Sep 28 10:10:20 tim-oneiric kernel: [12338.760245] <=== rt28xx_close
Sep 28 10:10:20 tim-oneiric kernel: [12338.762797] INFO::Network is down!
Sep 28 10:10:20 tim-oneiric dbus[869]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 28 10:10:20 tim-oneiric dbus[869]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 28 10:10:20 tim-oneiric kernel: [12338.784511] INFO::Network is down!
Sep 28 10:10:20 tim-oneiric kernel: [12338.784521] INFO::Network is down!
Sep 28 10:10:20 tim-oneiric kernel: [12338.784556] INFO::Network is down!
Sep 28 10:10:21 tim-oneiric anacron[2432]: Anacron 2.3 started on 2011-09-28
Sep 28 10:10:21 tim-oneiric anacron[2432]: Normal exit (0 jobs run)
Sep 28 10:10:21 tim-oneiric kernel: [12339.827085] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Sep 28 10:10:21 tim-oneiric kernel: [12339.844743] INFO::Network is down!
Sep 28 10:10:22 tim-oneiric kernel: [12340.860457] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line: 64


```

---

### Post by dino99 on 2011-09-28
this is gnome-settings-daemon default setting, change it into system settings

---

### Post by ratcheer on 2011-09-28
Please explain. Both what is happening and where I am supposed to change it.

It must be something new, because I have been testing Oneiric for months and this just started happening.

Thank you,
Tim

---

### Post by dino99 on 2011-09-28
Applications -> system tools -> system settings -> power

---

### Post by ratcheer on 2011-09-28
Thank you. I had already looked at that, and this is what it says:

Suspend when inactive for: Don't suspend
When power is critically low: (null)

Nothing there would seem to indicate that my PC (a desktop) should ever be suspended or shut down. So, I remain confused.

Is this a bug?

Tim

---

### Post by dino99 on 2011-09-28
if you have installed the latest updates, this issue might be gone.

---

### Post by dino99 on 2011-09-28
ah my bad, still not fixed

[https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485](https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485)

---

### Post by ratcheer on 2011-09-28
Thanks again, dino. I have added "affects me too" to the bug.

Tim

---

### Post by ratcheer on 2011-09-28
Well, I must say that gnome-shell handles this much better than Unity. When it suspended under a gnome-shell session, and I pressed the power button to bring the PC back up, it came up to an unlock screen, I entered my password, and it immediately put me back into my session.

Tim

---

### Post by dino99 on 2011-09-28
i'm always logged as gnome-classic, to me unity is useless and lack so much things thats is easier to use scroll down menu, more friendly and quicker.

---

### Post by ratcheer on 2011-09-28
That sounds like a good plan. I like just about everything except KDE. I need to try the Gnome Classic.

Tim

---

### Post by ratcheer on 2011-10-03
I received this update today. I hope it works.

```
Message: 3
Date: Mon, 03 Oct 2011 08:39:23 -0000
From: Rodrigo Moya <[EMAIL="rodrigo.moya@canonical.com"]rodrigo.moya@canonical.com[/EMAIL]>
To: [EMAIL="oneiric-changes@lists.ubuntu.com"]oneiric-changes@lists.ubuntu.com[/EMAIL]
Subject: [ubuntu/oneiric] gnome-settings-daemon 3.2.0-0ubuntu4
        (Accepted)
Message-ID:
        <[EMAIL="20111003083923.6366.41607.launchpad@chaenomeles.canonical.com"]20111003083923.6366.41607.launchpad@chaenomeles.canonical.com[/EMAIL]>
Content-Type: text/plain; charset="utf-8"

gnome-settings-daemon (3.2.0-0ubuntu4) oneiric; urgency=low

  * debian/patches/00git_dont_sleep_on_idle_by_default.patch:
    - Don't sleep on idle by default (LP: #860485)
  * debian/patches/00git_dont_revert_pre_idle_brigthness.patch:
    - Do not revert to the pre-idle brightness if idle dimming is disabled
  * debian/patches/50_add_dell_backlight.patch:
    - Add 'dell_backlight' module to gsd-backlight-helper (LP: #862474)

```Tim

---

### Post by ratcheer on 2011-10-03
I left my PC for at least an hour, came back, and it was still on. Looks like the fix is good.

Tim

---

