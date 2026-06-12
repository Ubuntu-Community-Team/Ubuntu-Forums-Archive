---
title: "Ubuntu Server 14.04 installed but not loading. Blank screen with blinking cursor."
date: 2014-06-19
forum: New to Ubuntu
---

### Post by mike196 on 2014-06-19
I'm pretty new to Ubuntu and Linux in general. 

I built a home server as a summer project. Now I'm trying to get Ubuntu server up and running. 

I've installed the Oh, but when I try to start the machine, I get a black screen with a blinking cursor. There are no messages and I can't type anything. 


My machine currently:

MSI A78M-E35 motherboard
AMD A6-5400K APU 3.6 Ghz processor. 

There is no video or sound card. I have three hard drives an old 500 gb that I'm using as the bood drive, and two 2 TB for storage. Previously, I had a version of Debian installed on the 500GB drive and that booted just fine on the machine.


I downloaded Ubuntu Server 14.04 from the main download page. Because I have no cd/dvd drive in the machine, I installed from a 4GB usb stick. I created the boot stick using UNetbootin. I installed Ubuntu onto the 500gb disk (I've confirmed this) using the settings found [here](linuxhomeserverguide.com/initial/OSInstall.php) (though it's 14.04 and not 11.04). I don't know if it's important, but I didn't get the Ubuntu splash screen when I installed. I got a UNetbootin menu instead.


Ubuntu appears to install successfully. I make it to the end where it says to remove the boot device and restart. I do and enter BIOS to make the hard drive the primary boot device (again, I've confirmed that the 500gb is the primary boot device). 

When I turn on the computer, it goes to a black screen with a blinking cursor. There is no message and I can't input anything. Nothing happens when I press any key on the keyboard.

I've tried disconnecting the other two hard drives. That did not solve the issue.


I have tried to bring up the grub menu by holding shift after I turn the computer on, but nothing happens. The motherboard splash screen is displayed telling me how to access BIOS and boot options, then proceeds directly the the black screen with a blinking cursor. The only operating system on the computer is Ubuntu Server 14.04. I removed Debian Wheezy when I installed Ubuntu because I have no interest in dual booting.

I don't know what else to try, so any  help would be greatly appreciated.

---

