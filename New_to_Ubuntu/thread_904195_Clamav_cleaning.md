---
title: "Clamav cleaning"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by logicus on 2008-08-29
hey there

I'm trying to fix my mother in law's computer. She has got a virus. So I thought of using my live cd and try to run clamav on her windows partition. It worked ! 

Since it's the first time I use it, though, I dont know if whether it just scans the computer and reports the virusses or if it can actually clean them and if not then what I should do. Can you guys help me ?

Sincerely

Peter

---

### Post by nicedude on 2008-08-29
Yes it can clean them but it may just delete virus infected files and then the PC may not work if any system files were so infected and then deleted ( which is commonly the case with Viruses in Windows ) I would probably say it is better to clean viruses from within windows than with a live linux CD but that is of course if you can get windows to boot etc and nowadays the crafty little virus writers usually have their viruses try and block anti virus websites and software from working so that may be a stumbling block as well. If you can get the machine to boot up into Windows then try using either free avg or clamwin to remove the virus both are free. Last resort would be to have clam try and deal with the infected files from inside Linux but that may make her PC not bootable with windows. I just am not sure that clam from linux live will heal windows system files and instead I think it deletes virus infected files which would be bad in your case.


Man I so love Linux because I no longer have to even think of viruses as something my computer can get, they are now in my mind back to their original meaning as in the FLU :-)

---

### Post by bumanie on 2008-08-29
As far as I am aware, clamav run via a live cd will remove virus/malware issues, not 100% certain, but believe this is the case as a number of linux live cd distro's are touted as being able to save windows machines from such threats. Certainly from an installed linux distro, clamav will do this.

---

### Post by rykel on 2010-04-03
Guys,

I am using ClamavTK... the GUI for clamav...

I scanned a virus-laden Windows partition, but have no idea whether I should "quarantine" or delete the infected files.

What exactly is a "quarantine"?

If I quarantine the infected files, will they still be infected when I boot into Windows on that infected partition?

Thanks for answering so many questions on ClamAV. But free and open source is GOOD.    :)

---

