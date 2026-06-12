---
title: "[SOLVED] Installing .msi file in wine"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2008-07-31
I am trying to install the file "FlashCardManager.msi" using:
```

wine msiexec /i FlasCardManager.msi
```\

I copied the file to the wine C:/ drive, but I get this:

```
err:msi:copy_package_to_temp failed to copy package L"FlasCardManager.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"FlasCardManager.msi"
```

I also tried it from the Desktop but I get the same error.
I am running Ubuntu Hardy with kernel version 2.6.24-19-generic

Thanks in advance!

---

### Post by LinuxRocks713 on 2008-07-31
> **TadeoDiaz said:**
> I am trying to install the file "FlashCardManager.msi" using:
```

wine msiexec /i FlasCardManager.msi
```<snip size="medium"></snip>

You **should not** install drivers inside Wine. If it isn't a driver, try to unpack it with the "Universal Extractor (http://legroom.net/software/uniextract)" then run the setup.exe (or whatever) yourself.

---

### Post by TadeoDiaz on 2008-07-31
It not a driver, it's a study aid. I actually just tried it again and it seems to have worked! 

Navigated to the Desktop and ran

```
wine msiexec /i FlashCardManager.msi
```

Im using it right now trying to see if there are any problems with it, Thanks though!

---

### Post by Nepherte on 2008-07-31
You made a type: 'FlasCardManager' vs. 'FlashCardManager'

---

