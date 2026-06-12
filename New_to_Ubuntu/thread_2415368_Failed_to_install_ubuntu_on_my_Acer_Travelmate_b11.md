---
title: "Failed to install ubuntu on my Acer Travelmate b117 with preinstalled endless os."
date: 2019-03-24
forum: New to Ubuntu
---

### Post by mj.ong on 2019-03-24
I tried*installing ubuntu desktop on my acer travelmate b117 which comes with preinstalled endless os. I am totally newb when it comes to terminal commands on linux, never used it before. I tried to install ubuntu(i googled different linux distros cos i didn't like endless that much) via usb but failed. The things I tried, because I am having problems booting to usb, the 40_custom method. I still failed to boot to usb after that but I can still boot to endless. Then  I tried to change the boot uefi to legacy and the order to usb first, After that I got stuck. I now can’t even boot to endless os even if I changed it back to uefu and the order to linux.
While installing ubuntu, I get the error can't request region for resource [mcm 0x7a6... usb 2-1 device not accepting address. I googled it, tried to find a fix, but some instructions i found have to boot to their old os. Or have some root password, which i don't know. 
The error i found when booting to endless:
Failed to switch root. Specified switch root path /sysroot does not seem to be an os tree. os-release file is missing.

---

### Post by Autodave on 2019-03-25
I did a little research: maybe this will help you:
[https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwieuoL8xZ3hAhVtplkKHXq5Cm0QFjAAegQIAhAB&url=https%3A%2F%2Fforum.siduction.org%2Findex.php%3Ftopic%3D6272.0&usg=AOvVaw3EnqoYLKTjb8UeZiTpHmsc](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwieuoL8xZ3hAhVtplkKHXq5Cm0QFjAAegQIAhAB&url=https%3A%2F%2Fforum.siduction.org%2Findex.php%3Ftopic%3D6272.0&usg=AOvVaw3EnqoYLKTjb8UeZiTpHmsc)

---

### Post by mj.ong on 2019-03-27
Thank you! I hope this works. I'll try it as soon as I get home. Maybe after 10 days or so.. as I am currently busy with work. I'll post here again about the result.

---

### Post by oldfred on 2019-03-27
It is making sure grub is installed in UEFI mode & setting "trust" in Acer's UEFI.

I think these are all similar on setting trust, but some explain it better/differently which may help.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

---

