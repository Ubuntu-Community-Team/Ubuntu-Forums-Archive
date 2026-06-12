---
title: "How to triple-boot Ubuntu, Windows XP, and Windows Vista."
date: 2006-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Some_Person on 2006-12-29
Here's how you can set up a triple-boot with XP, Vista, and Ubuntu.

1. Get all 3 installed, in any order.
2. If you installed GRUB to your Ubuntu partition, skip to step 13.
3. Boot to the Ubuntu CD.
4. Go to a terminal.
5. Type "install-grub /dev/x" (replacing x with your Ubuntu partition).
6. If, when you first installed Ubuntu, you did not install it to the MBR, or Ubuntu was not the last OS installed, skip to step 13.
7. Boot to you XP setup disc. If you do not have this, download a recovery disc [here](http://drehmini.net/tools/xp_rec_con.zip).
8. After loading, press R to start the Recovery Console.
9. Choose your XP installation.
10. After logging in, type fixmbr and press enter.
11. Press "y" and enter to confirm.
12. Type exit, and press enter.
13. Boot to Windows XP (may be called "Earlier Version of Windows").
14. Download EasyBCD from [here](http://neosmart.net/downloads/software/EasyBCD/EasyBCD%201.52.exe).
15. Run EasyBCD, and check if Windows XP (may be called "Earlier Version of Windows") is in the list. If it is, skip to step 21.
16. Go to Manage Bootloader on the left side.
17. Select Reinstall the Vista Bootloader, and click Write MBR.
18. Go to Add/Remove Entries on the left side.
19. Under Version, choose "Windows NT/2k/XP/2k3".
20. Type in the letter of your XP drive, type a name, and click Add Entry.
21. Go to Add/Remove Entries on the left side.
22. Choose the Linux/BSD tab at the bottom.
23. Under Type, select Grub.
24. Name it something, and set the hard drive and partition to your Ubuntu partition.
25. Click Add Entry.
26. Create a folder called NST in your XP partition.
27. Download BootPart from [here](http://www.winimage.com/bootpa26.zip), and extract it to "X:\bootpart" (replacing X with your XP partition).
28. Open Command Prompt.
29. Type "X:\bootpart\bootpart.exe" (replacing X with your XP partition).
30. Determine the number of your Ubuntu partition.
31. Type "X:\bootpart\bootpart.exe # X:\NST\nst_grub.mbr" (replacing # with the number of your Ubuntu partition and X with your XP partition).

That's it! You now have an XP/Vista/Ubuntu triple-boot!

---

