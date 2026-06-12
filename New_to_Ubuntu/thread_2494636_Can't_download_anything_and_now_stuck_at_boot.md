---
title: "Can't download anything and now stuck at boot"
date: 2024-01-22
forum: New to Ubuntu
---

### Post by sunhatzhenya on 2024-01-22
Hi all, I converted to Linux recently and am having a handful of issues. When I initially set up Ubuntu on my new laptop, I kept the Windows 11 it came with as a dual boot. However, shortly after I did the partition and everything, I realized how little space I had left Ubuntu and that I also had no real need for Windows on this machine. I have been trying to get rid of the dual boot so Ubuntu can have the whole disk, but I'm running into a few problems.

1) It stopped letting me download anything - I tried downloading the pieces I needed for setting up the live flash to fix the partition, but all my downloads failed.

2) Booting into Ubuntu gives me the following readout:

[0.254829] ACPI BIOS Error (big): Failure creating named object [\_SB.PCI0.GP17.VGA._STA], AE_ALREADY_EXISTS (20221020/dswload2-326)
[0.255265] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221020/psobject-220)
[1.090688] hub 6-0:1.0: config failed, hub doesn't have any ports! (err -19)
/dev/nbme0n1p5: recovering journal
/dev/nbme0n1p5: clean, 278845/1525920 files, 5835463/6102272 blocks
[3.518655] Bluetooth: hci0: Failed to read codec capabilities (-22)
[6.072619] Bluetooth: hci0: Failed to read codec capabilities (-22)

This is where it sits until I manually power it off.

3) Windows boots into Automatic Repair and tells me "Automatic Repair couldn't repair your PC". When I click "Exit and continue to Windows 11" it just takes me back to the start where I'm choosing between Windows and Ubuntu. It also offers a "reset this PC" option, but I'm reluctant to use that if there's another way to fix my mistakes that doesn't involve me going back to square 1.

My specs are:
Processor: AMD Athlon™ Gold 7220U Processor(Athlon™ Gold 7220U)
Memory: 1x4GBLPDDR5-5500
Operating System
Windows 11 Home in S mode 64(EN:English)
Hard Drive: 128 GB SSD PCIe
Wireless Network:
1x Wi-Fi 6 2x2 AX; Bluetooth® 5.1 or above
Ports
1x SD Card reader; DC Jack(round); Combo of 3.5mm Stereo Headphone Output; HDMI; 1 USB 2.0; 1 USB 3.0; 1 Type C (USB 3.2 Gen 2 + DP 1.2)
Camera: 720P HD with Dual Microphone and Privacy Shutter
Graphics: 1x AMD Radeon™ 610M
Monitor: 15.6" FHD

Thanks in advance for the help!!

---

### Post by Rubi1200 on 2024-01-22
Hi and welcome to the forums :-)

Are you able to boot with the liveUSB you used to install Ubuntu in the first place?

If yes, choose to Try Ubuntu and then open a terminal with Ctrl+Alt+T on the desktop.

Show us the output from the following command:

```
sudo fdisk -l
```

When replying click on Go Advanced >> paste the output and then highlight and click on the # icon to wrap with code tags.

This is just a first step for us to get an overview of the disk layout.

---

### Post by sunhatzhenya on 2024-01-22
I don't have the original liveUSB (misplaced it when traveling), though I did just now try to boot with a different one I was able to set up. However, it's not letting me boot from that USB, for some reason? When I load the BIOS it shows up as an option that I can't select, but when I go out to GNU GRUB it only offers me Ubuntu, Ubuntu Advanced Options, and Windows Boot Manager.

---

### Post by ajgreeny on 2024-01-22
Is your Windows setup to use  faststart which means it hibernates and does not shutdown properly.

It is not possible to start a hibernated Windows OS from grub which may explain your problem.

I no longer use Windows but I am aware that it uses a lot more space than Ubuntu and will have huge problems if there is a shortage of space which could be the case on your single hard disk of just 128G.

---

