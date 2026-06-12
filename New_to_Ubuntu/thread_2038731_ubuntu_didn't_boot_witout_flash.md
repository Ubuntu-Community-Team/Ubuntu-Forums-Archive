---
title: "ubuntu didn't boot witout flash"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by waleed.mohammed on 2012-08-07
i installed ubuntu by minimal cd i but it in flash by [COLOR=Black][unetbootin]("https://www.google.com/search?hl=en&client=ubuntu&hs=2Aj&channel=fs&sa=X&ei=kPsgULDVA4nbtAbd5oHICA&ved=0CG4QvwUoAQ&q=unetbootin&spell=1")[/COLOR] i choosed lubuntu desktop after installation finished the computer dosen't boot witout the flash but when i boot from the flash after boot i can disconnent the flash and work with lubuntu normally and install updates but if i retart the computer i have to connect the flash again

---

### Post by Kalanac on 2012-08-07
Did you accidentally install grub to the flash hard drive by mistake?  It happens from time to time.  Try either re-installing and double check your settings when installing the boot loader (you want it in the MBR (master boot record) of the built in hard drive usually) or you could try using a boot repair program.

---

### Post by waleed.mohammed on 2012-08-07
> **Kalanac said:**
> Did you accidentally install grub to the flash hard drive by mistake?  It happens from time to time.  Try either re-installing and double check your settings when installing the boot loader (you want it in the MBR (master boot record) of the built in hard drive usually) or you could try using a boot repair program.
thank you now it work fine after i remove grub2 and install it again

---

