---
title: "Is this RAM compatible with my computer?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by chevriley on 2008-05-08
I'm looking to get bang for my buck and this caught my eye. planning to buy 2 of them.

[http://www.7dayshop.com/catalog/product_info.php?cPath=777_11&products_id=103355](http://www.7dayshop.com/catalog/product_info.php?cPath=777_11&products_id=103355)

currently i have 2 sticks of SAMSUNG 512MB DDR PC32003....

if you need more regarding y setup than my current RAM just ask.

edit: link should be fine now.

---

### Post by tamoneya on 2008-05-08
product not found.
I would get somethign like this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231036](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231036)

---

### Post by chevriley on 2008-05-08
fixed!

that works out at about £80 for 4gig versus about £40 for mine. what advantages are there?

---

### Post by tamoneya on 2008-05-08
definately not.  It will probably make your computer slower.  They are faster memory but you will lose that since your motherboard will clock them to 400 MHz instead of 667 MHz.  However they have a CAS latency of 5 instead of 3 so it will take longer than your current memory.  You should get these sticks
[http://www.7dayshop.com/catalog/product_info.php?cPath=777_11&products_id=104004](http://www.7dayshop.com/catalog/product_info.php?cPath=777_11&products_id=104004)

---

### Post by chevriley on 2008-05-08
my motherboard will clock them at that speed even if remove the existing cards and get rid of them?

---

### Post by tamoneya on 2008-05-08
it depends on your motherboard but probably not since those sticks were probably selected to be at your motherboards max speed. Can you post your motherboard model and then we can figure out exactly what your max speed is.

---

### Post by chevriley on 2008-05-08
sudo dmidecode | moreBIOS Information
        Vendor: American Megatrends Inc.
        Version: 080012 
        Release Date: 07/20/2005
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 512 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported

---

### Post by chevriley on 2008-05-08
edit: forum went wacky

---

### Post by chevriley on 2008-05-08
edit: forum went wacky

---

### Post by tamoneya on 2008-05-08
that is the bios information.  You should either try to pull the model number off the board by opening up the case and grabbing a flashlight or you can try ```
sudo lshw
```

---

### Post by chevriley on 2008-05-08
description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (07/20/2005)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.15.0
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cp

---

### Post by tamoneya on 2008-05-08
your motherboard only supports up to PC3200 so it would be a waste to buy the ones you suggested.  Grab the ones that I linked earlier.  


Here is a page that shows that PC3200 is the max since I cant seem to find the official specs sheet.

[http://www.memoryx.net/msimsmome91.html](http://www.memoryx.net/msimsmome91.html)

EDIT: I just found the official specs: [http://www.nec-computers.com/support/pib.asp?platform=spec_orion2&mode=default&source=1409](http://www.nec-computers.com/support/pib.asp?platform=spec_orion2&mode=default&source=1409)

DDR 400 = PC3200

---

### Post by chevriley on 2008-05-08
thanks a million for all your help. $5 ubuntu donation in your honour. :)

---

### Post by tamoneya on 2008-05-08
go Ubuntu

---

