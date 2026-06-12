---
title: "hi, I am struggling to use my ubunut on a usb, on my parents laptop."
date: 2022-01-13
forum: New to Ubuntu
---

### Post by bob1111 on 2022-01-13
Hi, I am having problems using Ubuntu on this laptop, on my old computer it was an option to boot Ubuntu instead of windows, I don't know how to run it on my laptop?

---

### Post by Bashing-om on 2022-01-13
bob1111 - Hello

What gets booted for an operating system is dependent on what is selected in the firmware (bios). Each manufacturer implements this function differently.
One must look in the firmware to set the USB as a booting device. If after looking you still have difficulties then provide us with the computer name and model. We see what we can do to guide you in order that you can boot your ubuntu.

-if at first you do not succeed
     ask on the forum :D-

---

### Post by bob1111 on 2022-01-13
its an hp laptop, it doesnet let me pick from bios to go to ununtu model-15da0002dx

---

### Post by Bashing-om on 2022-01-13
bob1111; Hey

Ya got to set up in the firmware so the booting points to the USB rather than to the internal drive.

See here for hints: [https://www.hp.com/us-en/shop/tech-takes/how-to-boot-from-usb-drive-on-windows-10-pcs](https://www.hp.com/us-en/shop/tech-takes/how-to-boot-from-usb-drive-on-windows-10-pcs)

[INDENT]hope this helps
[/INDENT]

---

### Post by QIII on 2022-01-14
Caveat:

Remember to set it back to boot from the internal drive when you are done, or your parents may be fit to be tied.

---

### Post by LuddDjur on 2022-01-14
Ususally those machines boot the next option if you unplug the USB drive - so having USB as first boot device and internal drive as second would work quite well if you always unplug the USB drive after you are finished with ubuntu.

---

### Post by QIII on 2022-01-14
That is generally the case.  However, that is not universal.

It is their machine and should be returned in the state it was found in.

---

### Post by yancek on 2022-01-14
>  its an hp laptop, it doesnet let me pick from bios to go to ununtu model-15da0002dx 				

I have 2 HP laptops.  On both, I need to tap the Esc key to get options.  In your  case, you should have a Boot Options (F9 key) to make a one time change to boot the usb.  Do you see that option?  If not what do you see?   These may not be the options for your specific computer so you may need to do an online search.

What software did you use to create the bootable Ubuntu usb?  Have you tested the usb on another computer to see if it boots?  Does this computer have another OS installed?  If so, what is it?  Is this an EFI install?

---

### Post by mIk3_08 on 2022-01-14
> **bob1111 said:**
> Hi, I am having problems using Ubuntu on this laptop, on my old computer it was an option to boot Ubuntu instead of windows, I don't know how to run it on my laptop? 
> **bob1111 said:**
> its an hp laptop, it doesnet let me pick from bios to go to ununtu model-15da0002dx
Try to search around about your laptop on how to boot to Bios/UEFI so you will see the boot configuration if it has a dual Operating System. 
There you can configure what Operating System you wanted to boot if it has a dual Operating System. So Good Luck and Cheers.

---

### Post by nginmu on 2022-01-14
Just for reference

[https://support.hp.com/us-en/document/c06165573](https://support.hp.com/us-en/document/c06165573)
[http://h10032.www1.hp.com/ctg/Manual/c06558304.pdf](http://h10032.www1.hp.com/ctg/Manual/c06558304.pdf)

> 
9 Using Setup Utility (BIOS)

Setup Utility, or Basic Input/Output System (BIOS), controls communication between all the input and output
devices on the system (such as disk drives, display, keyboard, mouse, and printer). Setup Utility (BIOS)
includes settings for the types of devices installed, the startup sequence of the computer, and the amount of
system and extended memory.

NOTE: To start Setup Utility on convertible computers, your computer must be in notebook mode and you
must use the keyboard attached to your notebook.

Starting Setup Utility (BIOS)

CAUTION: Use extreme care when making changes in Setup Utility (BIOS). Errors can prevent the computer
from operating properly.

Turn on or restart the computer and quickly press f10.
&#8211; or &#8211;
Turn on or restart the computer, quickly press esc, and then press f10 when the Start menu is displayed.


---

### Post by bob1111 on 2022-01-14
it goes straight to user login, i still need help.

---

### Post by bob1111 on 2022-01-14
i have a mental disability, i need more help

---

### Post by bob1111 on 2022-01-14
i need more help, i dont knowwhat im doing

---

### Post by bob1111 on 2022-01-14
can someone screen share with me?

---

### Post by QIII on 2022-01-14
> **bob1111 said:**
> can someone screen share with me?

No.  Not only is it exceptionally dangerous for you to do such a thing with random, anonymous people on a forum, it would also deprive everyone else in the community with similar problems a possible answer.

Do not ask for such an arrangement again.

Thanks.

---

### Post by bob1111 on 2022-01-25
Hi, I changed the bios so that boot from USB is enabled but when I restart the laptop it goes straight to windows. Also I can't share a picture of bios, any advice? Thank you.

---

### Post by Bashing-om on 2022-01-25
bob1111' As the struggle continues :)

> 
I changed the bios so that boot from USB is enabled but when I restart the laptop it goes straight to windows.


With Windows we can "assume" this is a EFI endowed machine - such then "Secure Boot" may be at play.
Please advise us of the status of secure boot in Bios -and with secure boot disabled in bios-  what results when attempting to boot from the USB device ?

-there is a process-

---

### Post by oldfred on 2022-01-25
Is this flash drive a live installer, or a full install?
If a full install, Ubuntu's Ubiquity installed grub2's boot files to system you used to install it.
Then you need an ESP - efi system partition FAT32 on the flash drive and reinstall grub on the flash drive, not your system. 
Then UEFI boot options can show boot from the USB flash drive.

Post this and identify drive that is flash drive with Ubuntu.
sudo parted -l

---

### Post by bob1111 on 2022-01-27
I don't know if this is a live installer or a full installer, it worked on my computer.

---

### Post by bob1111 on 2022-01-28
Re: hi, I am struggling to use my ubunut on a usb, on my parents laptop.

---

### Post by bob1111 on 2022-01-28
I am mentally disabled, I meed more help, what do I do.

---

### Post by mIk3_08 on 2022-01-29
> **bob1111 said:**
> Re: hi, I am struggling to use my ubunut on a usb, on my parents laptop. Try to search around about the hardware on the ubunut laptop of your parent on how you can access to uefi/bios so you can configure it. 
Once you figured it out you can easily modify it using clover for multi boot. But usually, I always encounters error with ubunut so please aware your parents once you have a plan on modification to their machine. So Good Luck and Cheers.

---

### Post by bobunderwood99 on 2022-01-29
Hello,

You enabled boot from USB but did you change the boot order so USB is first?

---

