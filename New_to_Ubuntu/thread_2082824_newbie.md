---
title: "newbie"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by sagonne on 2012-11-10
hi
I got ubuntu  for quite a while but I havn t really used it.

I have few questions
1: where can I find a driver for  a USB WIRELESS N MICRO ADAPTER SURF N300 (Belkin).

2: any way I could put Ubuntu Linux in a external hard drive with a memory  for booting.

3 do i need a anti virus software I think I picked up some virus in the pass, my wife just bought me a new laptop and I want to make sure I m safe

Best regards 

  :) sagonne

---

### Post by newb85 on 2012-11-10
Welcome to the forums!

1. Have you tested it to make sure the generic drivers don't get the job done?  

2. Very easily.  If you hook the external HDD up while running from the Live CD/DVD/USB, you can choose to install on the external HDD.  For your objective, you'll want to also choose the external HDD as the "Device for boot loader installation".  If you have your BIOS set to boot from the external HDD first, then whenever you boot with the external attached, it will boot Ubuntu, and otherwise, it will boot Windows (assuming that's what is on your main HDD.)

3. The chances of your Ubuntu system getting infected are slim.  The chances of you passing along a malicious file to a machine running Windows (or your own Windows partition) are not so slim.  There are packages available for Ubuntu you can use to scan files for Windows viruses before passing them along.  Ultimately, though, the Windows setups need to have their own protection installed.

For future reference, your questions are more likely to be answered if the title says something about your question.  In this case, you actually had three questions, and probably should have put them in three different threads.

---

### Post by Gone fishing on 2012-11-10
Just to add a little - if the wireless doen't work when you start up Ubuntu has a utility "Additional Drivers" that will download and install any additional drivers that are easily available, just use a cable and plug the ubuntu computer into a router so that it can connect to the internet.

Virus protection you probably don't need to protect Ubuntu however, it can be useful when sharing with Windows PCs and in a dual boot environment cleaning your Windows partitions.

---

### Post by Mopar1973Man on 2012-11-10
Typically virus problem are slim to none for Linux unless you happen to be working both sides (windows / Linux). Then you take a risk. Also if you have WINE installed its another spot to take a possible hit from Windows virus / malware. So as long as your careful there shouldn't be any need to worry.

---

### Post by DuckHook on 2012-11-10
Your questions actually highlight some important differences between Linux and Windows:

1. In Linux, most of the "drivers" that are needed in Windows are unnecesssary because they are already designed into the operating system itself. Therefore, for most mainstream hardware, the operating system will recognize the hardware without issues and "just work". My guess is that the Belkin N300 wireless adapter should be mainstream enough that Linux will just recognize it and automatically use the proper module to make it work. If yours is not working, there are some tests involving the command line that must be done to figure out what its underlying chipset is, but let's not go there unless we have to. In short, is your wireless not working?

2. Ubuntu can easily be installed in an external drive, as @newb85 instructs. However, it will be slower and more fragile than it would be were it installed to the internal drive. This is due to the fact that external drives are slower than internal drives and USB cords can be disconnected while the drive is in mid operation. The one thing that no operating system can recover from is a physical disconnection while in the act of writing a file to disk. If you are okay with this sort of risk then Linux will happily reside in an external disk, but it smacks of living rather dangerously to me.

3. Linux does not need antivirus and this is one if its many significant advantages over Windows. Not only does this make Linux natively more secure than Windows, but by foregoing antivirus, the operating system is freed of the bloat and overhead that Windows must sustain. At first, you feel rather naked without an antivirus program running in the background, but it won't be long before you start asking why Windows can't be designed the same way Linux is. Even though there are antivirus programs for Linux (ClamAV) I do not recommend installing them because they address a non-existent threat and will only scan for Windows viruses that cannot infect Linux. Yes, this is an oversimplification because, as some respondants have pointed out, you are still at risk if you run WINE or Windows in another partition, but that remains a Windows problem and you should defend against that sort of exposure by slowing down Windows with antivirus; not Linux.

If you really don't want to partition your internal drive and install Linux permanently, then I would suggest that you either experiment with Linux using the Live CD or go ahead and install it on an external drive. Just make sure that you don't use it for important data, due to the fragility of your setup as per point #2 above.

---

