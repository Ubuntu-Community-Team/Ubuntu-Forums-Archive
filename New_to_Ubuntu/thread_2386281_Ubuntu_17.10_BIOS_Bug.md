---
title: "Ubuntu 17.10 BIOS Bug"
date: 2018-03-03
forum: New to Ubuntu
---

### Post by aubreybourke on 2018-03-03
Hi,

I have a Lenovo B50-30 Laptop with an Insyde H20 UEFI BIOS that was corrupted after using a Lubuntu 17.10 Live CD.
The Bug is listed here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

My HDD is running Windows 10. And I no longer have my Live CD. My laptop refuses to boot anything except the HDD or the Live CD. No USB, No CD, No other HDD.

I downloaded the Lubuntu 17.10 iso. Specifically the version with the bug from the archives. It was released in 2017.
[http://ubuntu-cdimages.mirror.liquidtelecom.com/lubuntu/releases/17.10/release/](http://ubuntu-cdimages.mirror.liquidtelecom.com/lubuntu/releases/17.10/release/)
I'm hoping I can boot into Lubuntu again to fix the problem. 

If anyone has any other suggestions of how to repair my BIOS from Windows, please let me know.

Thanks,
Aubrey

---

### Post by oldfred on 2018-03-03
Did you download 17.10 or 17.10.1? 

You want 17.10.1 as that includes fixes.

---

### Post by aubreybourke on 2018-03-03
I tried it. But it refuses to boot. Cant seem to boot anything except the HDD. The live CD I had used to boot as well. But nothing else. I even tried swapping the hard drive. But no luck.

---

### Post by aubreybourke on 2018-03-03
No luck booting the iso from the archives.

I'm really stuck here. I cant boot anything except windows.

---

### Post by oldfred on 2018-03-03
Have you updated UEFI from Lenovo?
If you can boot Windows, I believe you can do it from Windows? Do not know details.

Some systems need full cold boot, or reset of system to get into UEFI to change settings.
Cold boot with laptop is full power down, remove battery, hold power switch for 10 sec or so to drain any left over power, then boot and immediately press correct key to get into UEFI. Some have reset pins on motherboard, or need coin battery on motherboard removed for a bit for full reset.
Note that reset of UEFI or update to UEFI may revert settings to defaults. So plan on reviewing and changing settings in UEFI again. I made a list to settings I change with my system as I have several.

My desktop did similar lock up. And my cold boot procedure did not work. But just disconnecting sda drive and then booting (after full cold boot procedure) did work.

---

### Post by aubreybourke on 2018-03-03
I can get into the BIOS settings. And change the values. But when I save and exit, the settings are not saved.

---

### Post by oldfred on 2018-03-03
Is that with an updated UEFI?

---

### Post by aubreybourke on 2018-03-03
I downloaded the latest bios from Lenovo. But when I try to flash it just shuts down.

---

### Post by oldfred on 2018-03-03
Do not know about flash issues.
For that issue you want to look at a Lenovo help site or forum. They may know more about those kind of issues.

---

### Post by aubreybourke on 2018-03-03
Yes I was in touch with the manufacturer. Lenovo offer a repair service. And they even pay for the postage.

I think that's the only sensible solution for me.

Because I don't want to buy this and install it:
[https://www.ebay.com/itm/BIOS-CHIP-LENOVO-B50-30-/382137491010](https://www.ebay.com/itm/BIOS-CHIP-LENOVO-B50-30-/382137491010)

Thanks for the help!
Aubrey

---

