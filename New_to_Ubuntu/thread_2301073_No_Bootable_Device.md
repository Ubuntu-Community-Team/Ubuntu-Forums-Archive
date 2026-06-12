---
title: "No Bootable Device"
date: 2015-10-30
forum: New to Ubuntu
---

### Post by Rammeloschie on 2015-10-30
Hello everyone

I bought a new netbook today ( Acer Aspire ES 11 ) without an operating system. I prepared an usb-device with actual ubuntu. Installation is successful and I need to restart. If the usb is still connected to the computer i return to the install-setup. But if disconnect the stick before the computer restarts I get "No Bootable Device"-error. I run bootrepair and attach the link below. I hope someone can help me =( Tell me whatelse u need to know about the config pls.

paste.ubuntu.com/13009227


Thanks =)

---

### Post by oldfred on 2015-10-30
Somehow you installed grub legacy??
I do not think grub legacy supports gpt much less UEFI.

Also your system is promoting the flash drive to sda. And that may confuse installer as grub always installs to sda. It either will not install or overwrites the installer with the installed copy of grub which is different configuration.

All Acer seem to require you to enable a supervisory password and set "trust" on the Ubuntu/grub efi boot files.
       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by Rammeloschie on 2015-10-30
What do u mean with 'somehow u installed grub legacy??'
sry im new to ubuntu xD 
i set supervisory password and followed the instructions in that link but still got some problems ( [http://itsfoss.com/no-bootable-device-found-ubuntu/](http://itsfoss.com/no-bootable-device-found-ubuntu/) )
Im also not sure if I understand what this means: '[COLOR=#000000]Also your system is promoting the flash drive to sda.'

Please tell me in simple words xD[/COLOR]

---

### Post by oldfred on 2015-10-30
You did not make your link clickable and easy to use.
Is this yours?
[http://paste.ubuntu.com/13009227/](http://paste.ubuntu.com/13009227/)

If so right at the top it says grub legacy in sdb.
And further down it says sda is your 8GB drive and sdb is your 500GB drive. Size shown is usable not drive mfg number.
Which drive is sda or sdb is defined by UEFI/BIOS not by grub or Ubuntu.

Your link shows the procedure to set a supervisory password and set trust on the grub/ubuntu boot files. Is that not working when you reboot? You should be able to choose ubuntu entry in UEFI boot tab or one time boot key. Not sure what key Acer uses but often f12 or f10, check Acer manual.

You do need to always boot in UEFI boot mode. Your UEFI boot tab should show two entries for flash drives, one clearly UEFI and the other just name of flash drive for BIOS boot.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

