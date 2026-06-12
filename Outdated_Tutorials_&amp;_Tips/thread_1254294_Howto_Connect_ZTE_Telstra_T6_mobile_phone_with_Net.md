---
title: "Howto: Connect ZTE Telstra T6 mobile phone with NetworkManager 0.7.0+"
date: 2009-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by foobic on 2009-08-31
Hi folks,

Many thanks to all who've contributed here - coming from other distros to Ubuntu for the first time I've learned a lot in the process of installing 9.04 on a couple of new laptops. Just one thing really bugged me though, and having wasted an afternoon working it out I thought I'd share the knowledge in hopes that it helps someone else avoid the same.

The Telstra T6 is a cheap mobile phone made by ZTE, manufacturer of the oh-so-popular [usb modems]("http://ubuntuforums.org/showthread.php?t=1017630"). On a prepaid plan though, it does offer a very low-cost way to get occasional access to Telstra's widespread Australian data network. So obviously I wanted to use it with the linux laptop. I had it working before using some modprobe.conf and wvdial tweaking but I really like how NM now *actually works* for all my other devices, so...

The model's not in the standard hal fdi information of course, so I added this (from the other thread, changed to the T6's model id) to /etc/hal/fdi/information/10-modem.fdi (if the file already exists on your system you'd just add the device section):
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- xml -*- -->
<deviceinfo version="0.2">
  <device>
    <!-- Qualcomm: ZTE Telstra T6 NextG -->
    <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <match key="@info.parent:usb.product_id" int_outof="0x0010">
          <match key="@info.parent:usb.interface.number" int="0">
              <append key="modem.command_sets" type="strlist">GSM-07.07</append>
              <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
     </match>
  </device>
</deviceinfo>
```Then reboot (does it need a reboot?), plug in the device and if the NetworkManager "new mobile broadband device" doesn't pop up (it didn't for me, but that might have been because of all the farting around I did earlier), Right click -> Edit connections... -> Mobile Broadband tab -> Add and follow the prompts.

So easy! So why did it take me so long? Tips to avoid what I did wrong:

1. Both ttyUSB0 and ttyUSB1 are created, but only ttyUSB0 seems to work as a modem (hence the int="0" setting above).
2. You need to set the phone to connect by USB cable, not bluetooth (Settings -> Handset -> PC Connection).
3. None of these suggestions from the other thread and elsewhere are required (it will work with or without them): udev-extras, usb_modeswitch, the latest PPA network-manager, the tweaked /lib/udev/nm-modem-probe.
4. (the real time-killer) NM doesn't seem to play nicely with custom modprobe.conf settings. I had set up an options line for usbserial in /etc/modprobe.d/usbserial.conf (previously in /etc/modprobe.conf.local on a SuSE system). Simply (or so I thought) telling the system that this device should be handled by usbserial. And it works, but for some reason with this in place, NetworkManager never sees the connection.

Hope this helps someone.

Chris

References:
[http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)

---

### Post by kofo500 on 2009-09-29
Thanks mate, worked a treat first time with 9.04 :]

All I had to do was create the 10-modem.fdi file, reboot, and plug in the phone via usb.
Followed the broadband connection wizard, and the 3g data pack appeared in network connections, connect and bang, done.

Cheers, many thanks!

---

