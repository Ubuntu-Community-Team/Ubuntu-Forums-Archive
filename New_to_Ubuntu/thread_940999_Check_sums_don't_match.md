---
title: "Check sums don't match"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by mregister on 2008-10-07
Hello all. I am not sure if this matters BUT just to check, I ran a tiger report and I get this:
> --WARN-- [osv004w] Unreleased Debian GNU/Linux version `lenny/sid'

AND

> --FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.pcimap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.dep' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.ieee1394map' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.usbmap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.isapnpmap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.inputmap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.seriomap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.alias' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.symbols' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/usr/share/php/.filemap' checksum differs from installed package 'php-pear'.
--FAIL-- [lin005f] Installed file `/usr/share/php/.depdb' checksum differs from installed package 'php-pear'.


So is this something to be concerned about or maybe these files chang during use?

---

### Post by LowSky on 2008-10-07
What version of Ubuntu are you running?

---

### Post by mregister on 2008-10-07
Hardy 2.26.24-19-server

---

### Post by mregister on 2008-10-07
sorry 2.6.24-19-server NOT 2.26

---

### Post by mregister on 2008-10-07
I found this post so maybe I don't have anything to worry about? I used rkhunter and it did not find any rootkits

[http://ubuntuforums.org/showthread.php?t=908771]("http://ubuntuforums.org/showthread.php?t=908771")

---

