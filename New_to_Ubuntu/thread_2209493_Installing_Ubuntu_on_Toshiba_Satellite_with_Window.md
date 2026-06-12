---
title: "Installing Ubuntu on Toshiba Satellite with Windows 8"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by andreygaganov0 on 2014-03-06
[B]
All I want to do is install Linux Ubuntu 12.04 LTS as another OS on my laptop (which already has Windows 8).[/B]

I can't disable UEFI because I can't get into BIOS not matter how hard I try. I found out about this option in Windows 8, which for some reason has something to do with recovery: "Change advanced start-up settings"/"Advanced startup". Seems like at this point I do not have to deal with BIOS, UEFI, and Secure Boot, **nor do I want to; this installation process is already complicated enough.** (I'm writing this because I don't know if this is relevant to the problem I'm about to address.) I boot from the DVD with Ubuntu .iso image properly burnt on it. At the start-up I saw a suspicious line:

```
Could not open "\EFI\BOOT\fallback.efi": 14
```

Then it moves on to the boot partitions menu without Windows 8 on it. Now I'm booting into the trial mode of Ubuntu. Even during the installation process it does not recognize Windows 8:

[[IMG]http://i360.photobucket.com/albums/oo49/Armanaeus/2014-03-05201857.jpg[/IMG]]("http://s360.photobucket.com/user/Armanaeus/media/2014-03-05201857.jpg.html")

On this blog [https://coderwall.com/p/ydbldg](https://coderwall.com/p/ydbldg) the author says that she "had to manually partition the hard drive, because the Ubuntu installer didn't recognize that Windows 8 was already on the computer." I don't know if this is safe for an amateur like myself to carry it out, considering that partitioning cannot be undone and I don't know how to do it right:

[[IMG]http://i360.photobucket.com/albums/oo49/Armanaeus/2014-03-05202003.jpg[/IMG]]("http://s360.photobucket.com/user/Armanaeus/media/2014-03-05202003.jpg.html")

**Problem/question:** How do I get it to recognize Windows 8 so that I can partition the memory correctly?

Hope I didn't put up too many findings. Any help would be appreciated.

---

