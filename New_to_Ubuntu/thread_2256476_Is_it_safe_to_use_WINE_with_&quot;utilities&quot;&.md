---
title: "Is it safe to use WINE with &quot;utilities&quot;/&quot;tools&quot;-Dell,etc. to point to Linux install?"
date: 2014-12-12
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2014-12-12
Thanks for reading. 
Question. Is it safe to use WINE with "utilities"/"tools"-Dell,etc. to point to Linux install?  
Example---I'm trying to download the native Linux here. 

```
Intel® Graphics Media Accelerator Driver for Linux
[https://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/19158/a08/Intel-GMA500-5](https://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/19158/a08/Intel-GMA500-5)[1].0.0.0040.tar.gz&lang=eng&Dwnldid=19158

```
For whatever reason, the "I agree" button is not working (????) --no need to spec it/if browser-will fix self  (Pale Moon) 


```

However, (unfortunately) (Winx related) does download as expected
Automatically identify and find drivers
The Intel® Driver Update Utility keeps your system up-to-date

[http://www.intel.com/p/en_US/support/detect?iid=dc_iduu](http://www.intel.com/p/en_US/support/detect?iid=dc_iduu)
 
```

Asking before even attempting,  

I assume it see's my "real" box and not virtual? (thus "assume"--if true, wine would allow the mimic).

I really don't like (beliving necessity of/relining on) WINE (aka want to be 100% free of winx--thus--if true ("can"/"but" work---aka will always depend on wine is what I logically assume will be answer...

---not good for me. 

THANK YOU!






BUT, 
If this answer is yes, does it pertain to BIOS as well (aka since it's a "Flash"--why I ask) 
None of the 1/2 dozen I've read have helped-dos USB,etc. (or too complex--aka-repack a kernel--thus outside my domain). 
Only reason I "have to" flash is only way to see the extra ram installed. 



As per many threads, Dell/Linux not well (or barely) supported. can assure you, next box won't be a Dell.(Rather Embarassed:oops: with box, Vostro 200 but only reason I have it . Was owed $1000's with project work, given $400, here take the 2-basicaly brand new vostro,monitors,et.al printer (lieu of $1000's owed from defunct company--what can ya do).  
Thx

---

### Post by westie457 on 2014-12-12
Not exactly sure what your question is about. Could you clear some things here for us?

1, Is your Linux installation a VM (virtual machine) or a stand alone installation or a dual boot installation?
2, To the best of my knowledge installing device drivers for any OS via Wine will not work.
3. The link you posted causes a 'page not found' (404) error.

---

### Post by nerdtron on 2014-12-12
The default Intel Graphics included in Ubuntu will work out of the box. Why do you want to install getting from the website?

---

### Post by whereismymindat2 on 2015-03-31
apology for the neglected reply---still haven't learned how to see my open questions. 

@Nerdtron 

Some reason--my screen ws always "bleeding"----you know. Like the referesh wasn't working---so everything was leaving trails---ex--I drag a window box open---and see 20-30---dragging with them. "eventually" it would unhang----but very frustraing. 
(I have 4GB ranm, dual core, etc.etc.) --even upped swap to absurd high level 10GB to try and fix. 

When I installed the Latested (and updated a kernel to freshest stable from [https://www.kernel.org/)---Seems](https://www.kernel.org/)---Seems) fine now


*****OTHERS***** reading this, I seriously dobut that's a boiler plate fix.

---

### Post by mastablasta on 2015-04-01
you can't use wine to install drivers or to flash BIOS. usualyl to flash BIOS a Windows system disk is needed (either on floppy or maybe CD or USB also works these days.

Furthermore intel drivers are part of Linux kernel. I believe some newer version could be installed from intel website, however there is also a PPA offering development version. the PPA will patch the kernel with latest version of drivers.

you can upgrade kernel on LTS quite easily by using this: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
you can also use newer version of the OS. or you can try the beta version.

as I know, Vostro series is well supported in Linux by Dell.

---

### Post by Mark Phelps on 2015-04-01
> I really don't like (beliving necessity of/relining on) WINE (

Actually, that is correct -- you should NOT rely on Wine for doing utility work best done in Windows.

Wine is not a Windows emulator; instead, it is a "hack" in which some early Windows DLLs were rewritten to replace Window OS kernel calls with Linux OS kernel calls.  It works OK with some of the really OLD Windows apps, as they relied entirely on those calls.  But it does not work with recent Windows stuff, and can not be used to install drivers.

---

