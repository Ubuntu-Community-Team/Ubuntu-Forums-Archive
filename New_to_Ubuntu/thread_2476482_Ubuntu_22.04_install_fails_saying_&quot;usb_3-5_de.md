---
title: "Ubuntu 22.04 install fails saying &quot;usb 3-5 devicedescriptor read/64 error -71&quot;"
date: 2022-06-27
forum: New to Ubuntu
---

### Post by r2020r on 2022-06-27
Hi

I am installing Ubuntu 22.04 on** HP Zbook** and it is failing with 
1) ACPI BIOS Error (Bug): Could not resolve symbol (\_Tz.psl.cfgd)
2) ACPI Error Aborting method
3) usb 3-5 device descriptor read/64 error -71

I am stuck and can not proceed with installation, please help.

Thanks

---

### Post by cyberkingdom on 2022-06-27
Do you have the usb device plugged into a usb hub or into a cable? The reason I ask is in this document [https://askubuntu.com/questions/262141/usb-error-71-eproto-with-a-gamepad](https://askubuntu.com/questions/262141/usb-error-71-eproto-with-a-gamepad) it talks about "Universal serial bus connector types and covers some cables can only be used for charging.

---

### Post by sudodus on 2022-06-27
Please help us help you by answering our questions and telling us more details about the computer at this stage. At the next stage we know more, and can probably help you ...

- Please specify the **name and model** of the 1. computer and 1. graphics chip/card.

- What **operating system** is running in the computer **now**? Windows 10 or something else?

- Did you check with **sha256sum**, that the downloaded iso file is good?

- How did you create the USB boot drive (**tool/method**)?

- Did you **try** the USB boot drive **in some other computer**? If not, can you do it now, for example borrow a computer from a friend or colleague? *When running 'Try Ubuntu' **nothing** is written to any internal drive* (unless **you** start the installer or some other program to write into it).

- **How far** did the installation succeed? Is the output in your opening post from the boot process of the USB boot drive? Or from some later step in the installation process? Please explain.

---

### Post by r2020r on 2022-06-27
Yes, I have connected USB Mouse, SD card reader to USB ports

After seeing your response, I disconnected USB mouse and that did not help.
SD card reader has bootable installer. I removed the SD card reader and directly inserted the SD card to *SD card slot*. Unfortunately machine will not boot from *SD card slot*(i have enabled it in BIOS).


Thank you

---

### Post by tea for one on 2022-06-27
> **r2020r said:**
>  I removed the SD card reader and directly inserted the SD card to *SD card slot*. Unfortunately machine will not boot from *SD card slot*(i have enabled it in BIOS).Thank you

Is there any reason why you have not created a live installer/system USB rather than use an SD card?

---

### Post by r2020r on 2022-06-27
Hi sudodus

1) HP Zbook 15" inch. Intel i7 - 4800MQ, NVIDIA Quadpro K21xxx
2) No OS is running now. I have not used this machine from past 2years. Previously I had Win7 for sure. I might have installed Ubuntu also, not sure. But now there is no OS on it. I put brand new DD
3) did not check iso checksum
4) Used Rufus for creating bootable SD card
5) I can try on another machine and see if it is ISO problem.


Thanks

---

### Post by r2020r on 2022-06-27
I do not have USB stick so use sd card along with card reader. I have used this method of installation for win 10, ubuntu, mint, on Lenovo machine many times.

---

### Post by r2020r on 2022-06-28
> **sudodus said:**
> Please help us help you by answering our questions and telling us more details about the computer at this stage. At the next stage we know more, and can probably help you ...
- **How far** did the installation succeed? Is the output in your opening post from the boot process of the USB boot drive? Or from some later step in the installation process? Please explain.

1) Error appears before even Ubuntu logo appears with spinning circle. After I select "Try Ubuntu", I think some hardware check happens and installation fails right there. 

2) Installation media is good because I did not get this error on Lenovo laptop. I went until "Install Welcome" screen and exited the installation. On my HP Zbook installation fails way ahead of this step.

3) TPM Error. I was getting TPM error also, and resolved it. By default TPM is grayed out in Zbook bios. By setting BIOS password will enable TPM. That is how I was able to resolve it.


I can try these 
a) Do not host install media on USB drive, instead create DVD boot image
b) Do BIOS update for laptop
c) Try installing MINT XFE. If that works I am good. Since both MINT and Ubuntu use same kernel I am afraid of encountering same error. If MINT gets same error, it will be bad. I can not install Linux on Zbook.

Thanks

---

### Post by sudodus on 2022-06-28
Thanks for all these details :-)

So booting from the SD card in that adapter works in a Lenovo. Then we know that it is good, but your HP Zboot is still not booting correctly from it.

But it is booting, reaches grub. There can be different problems. One of them is due to the nvidia graphics. It might help with the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) **[FONT=Courier New]nomodeset[/FONT]**.

When in the grub menu, press 'e'  to edit a command. Put **[FONT=Courier New]nomodeset[/FONT]** it onto the 'linux' line (surrounded by spaces).

If that is enough, fine. Otherwise boot again, this time with the boot options **[FONT=Courier New]nomodeset[/FONT]** and also with **[FONT=Courier New]acpi=off[/FONT]**.

You might get some low quality graphics, but good enough to install. After installation, you must probably use one or two of those boot options in the installed system. With that kind of graphics, try to install a proprietary graphics driver for the nvidia card and reboot. After this your computer's graphics might perform well. Depending on the wifi chip you might also need a proprietary driver for that.

Edit: If there is a real read error from the card via the adapter, I suggest that you

- try via all USB ports, and if still no luck
- get a USB pendrive and try to boot from that way instead

---

### Post by r2020r on 2022-06-28
Some improvement.

I chose** Ubuntu(Safegraphics)** and installation of OS **completed successfully**. But After that system is booting in a loop. Before every reboot, it prints** "Reset System" on the screen**.
I installed the OS with and without 3rd party drivers but problem continues. Note: If I chose **"Try on Install"** there were errors that I have already reported,  additionally color bands were appearing, as if there was a graphics problem so I tried **Ubuntu(Safegraphics)**

I will try the suggestion given by you.

Thanks

---

