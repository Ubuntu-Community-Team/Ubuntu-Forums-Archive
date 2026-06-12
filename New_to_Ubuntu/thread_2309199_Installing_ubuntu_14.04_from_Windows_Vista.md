---
title: "Installing ubuntu 14.04 from Windows Vista"
date: 2016-01-08
forum: New to Ubuntu
---

### Post by had2 on 2016-01-08
Hi, 

I have just unveiled my (old) PC:
-Aspire M5641
-windows 6.0
-Intel Core 2 Quad CPU Q8200 CPU Q8200 @ 2.33 GHZ (4 CPUs)
-3070 MB RAM
-NVIDIA GeFOrce 9600 GS

Using Unetbootin, I have created a USB-flash to install ubuntu 14.04. 

When I boot with the USB and try to either try or install ubuntu, I got the error ACPI PCC probe failed, then 10-20 min of a page with the logo, then my screen turns itself off. 

Would you have any advice for me?

Thanks a lot!!

---

### Post by grahammechanical on 2016-01-08
There might be an issue with the installer detecting the optimum resolution of the monitor. You may need to add a boot option. We do that at the first purple screen. The screen with an icon of a human & an icon of a keyboard. At the screen press Enter. Then select a language (English default) and press Enter. At the underlying screen press F6. A small menu will appear to the bottom right of the screen. Select nomodeset & press Enter or Space to select it. And then Esc to get back to the screen with the Try - Install options.

See this wiki page under the heading Changing the CDs Default Boot Options. see Section 6 - F6 Other options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Sometimes we need a combination of these F6 options to get the Ubuntu live/try session to load.

Oh, by the way, you will still see that "ACPI Probe failed" message after installation when you load Ubuntu. It is a common message. It has a certain meaning but it is not a critical error message that will affect the computer or the working of Ubuntu. I have seen it myself. It does not appear with Ubuntu 15.10 & it will not be present with Ubuntu 16.04.

Regards.

---

### Post by had2 on 2016-01-08
Thanks, as I am now using UNetbootin, I do not have access to the screen with the human & keyboard, so do not have access to the F6 command. 

Before using UNetbootin, I used rufus to create an ISO image but I thought this was not done to boot from a windows machine. This gave me access to the screen you are talking about though.
Should create another ISO image with rufus to do what you recommended me to do?

Thanks a lot

---

### Post by oldfred on 2016-01-08
You should see the accessibility screen just for a few seconds when booting in BIOS mode. Press any key, then f6 to add nomodeset.

After you install, you also will need nomodeset on the Linux line to get into lower quality graphics. Once you install the correct nVidia driver from Ubuntu repository then it should work without issue.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by had2 on 2016-01-08
Before recreating my USB device and follow your instructions (thank you infinetly) I'd just like to explain you better what happens as I looked closely the whole thing when booting with UNetbootin: 

-20 min of ubuntu logo loading screen
-Log in screen (purple background) : not able to putt my login nor move my mouse. This for 10 min
-Then an other log in screen but this time not centered : The background is black with white dots. 2 min
-The screen goes black (but does not sleep)

---

### Post by oldfred on 2016-01-08
My older system was core2 duo or slower, I did have 4GB of RAM and same video card. Once installed it took about 40 sec to boot. To boot from USB3 flashdrive on USB2 port was a bit longer or a minute or so.
Remove quiet splash when you add nomodeset to see what is taking so long.

---

