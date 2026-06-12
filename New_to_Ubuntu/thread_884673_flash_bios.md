---
title: "flash bios"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by matchstich on 2008-08-09
i have an old box and it will not shut down , so found the manufacturer and 

they sent me a newer revision for my bios.  i opened and have the readme:

LASH BIOS UPDATE PROCEDURE



1. Please check the current BIOS revision and make sure it is more current then your BIOS.

2. Unzip the BIOS update file and you will find three files, readme.txt (flash instructions), sm2flash.com (BIOS flash utility), and the BIOS image file (xxxxxx.rom).

3. Place these files on a bootable floppy and reboot your system, there are no BIOS boot block protection jumpers on the motherboard.

4. At the DOS prompt please enter the command "sm2flash", this will start the flash utility and give you an opportunity to first save your current file, flash the boot block and enter the name of the update BIOS image file.

5. It is very important that you save your current BIOS and name it "super.rom" in case you need to recover from a failed BIOS update.

6. Select flash boot block then enter the update BIOS image.  Select "Y" to start the BIOS flash procedure, do not disturb your system until the flash utility displays that the procedure is complete.

7. After updating your BIOS please clear CMOS then load and save Optimal Values in the BIOS







EMERGENCY BIOS RECOVERY PROCEDURE



1. Turn your system off and place the floppy disk with the save BIOS image file (see above procedure, step 5) in drive A.

2. On your keyboard press and hold "CTRL" and "Home" low-level BIOS flash hot keys.

3. Turn on power with the hot keys depressed until your floppy drive is accessed.  Your screen will remain blank until the BIOS program block is flashed.

4. If your system either reboots or displays a message to reboot system then the procedure was successful.

5. If the recovery procedure was not successful, please contact our RMA department for replacement.





NOTE:

There is always some potential risks during the BIOS flash procedure.

Please do not flash your BIOS chip, if you do not have any problem with the current BIOS.

Usually the newer BIOS files are supporting some special devices or new processor micro code update.




my question is:; how do i save a copy of the my bios. as stated in step 5.

there are no instructions.  this will be a first for me.

thanks

---

### Post by wpshooter on 2008-08-09
I would go back to their website and look for these instructions.

---

### Post by brian_p on 2008-08-09
> **matchstich said:**
> 

my question is:; how do i save a copy of the my bios. as stated in step 5.

Step 4.

---

### Post by matchstich on 2008-08-09
ok, one more question on this.

is there a package i need to get to copy those files to floppy?

thanks

when i click on places- the floppy drive is listed but the only option

i see is to scan the drive.

---

