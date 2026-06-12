---
title: "[Solved] No sound from my monitor: HDMI/DisplayPort unplugged"
date: 2017-12-08
forum: New to Ubuntu
---

### Post by OxySK on 2017-12-08
Hello, I` m using ubuntu 16.04 and lately i cant listen any sound from my monitor, I` m using a DisplayPort.

In the audio settings the *HDMI/DisplayPort* is disappeared, I can only see S/PDIF and internal audio; I`ve installed p*ulse audio volume control *and all* HDMI/DisplayPorts* are unplugged, I don`t know how to enable those ports.

 If I run the command *aplay -l* I can see this list:

> **** Lista di PLAYBACK dispositivi hardware ****scheda 0: SB [HDA ATI SB], dispositivo 0: ALC892 Analog [ALC892 Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 0: SB [HDA ATI SB], dispositivo 1: ALC892 Digital [ALC892 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 1: HDMI [HDA ATI HDMI], dispositivo 7: HDMI 1 [HDMI 1]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: HDMI [HDA ATI HDMI], dispositivo 8: HDMI 2 [HDMI 2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: HDMI [HDA ATI HDMI], dispositivo 9: HDMI 3 [HDMI 3]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0




I have a window partition on the same pc and the sound works as expected, so it is not an hardware problem.

---

### Post by OxySK on 2017-12-09
I found a solution:

> [COLOR=#111111][FONT=Ubuntu]Unfortunately, this is not an configuration issue but a problem of the current kernel. The original drivers for RX 480 and other systems will merged into kernel at 4.15, with lower kernels, some features do not work, e.g. sound. My current workaround is to use the AMD proprietary kernel from [https://github.com/M-Bab/linux-kernel-amdgpu-binaries](https://github.com/M-Bab/linux-kernel-amdgpu-binaries) . It can be installed via:[/FONT][/COLOR]
cd /tmp
git --git-dir=/dev/null clone --depth=1 [https://github.com/M-Bab/linux-kernel-amdgpu-binaries](https://github.com/M-Bab/linux-kernel-amdgpu-binaries)
cd linux-kernel-amdgpu-binaries
sudo dpkg -i *.deb
[COLOR=#111111][FONT=Ubuntu](To use the kernel, reboot and eventually choose it in grub).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Fortunately, ubuntu 18.04 will ship with 4.15 kernel ([https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-18.04-LTS-Linux-4.15](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-18.04-LTS-Linux-4.15)), so hopefully this will fix the issue.[/FONT][/COLOR]


---

