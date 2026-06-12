---
title: "Problem with Ubuntu and Mac OS X"
date: 2011-02-22
forum: Philippine Team
---

### Post by jaceleon on 2011-02-22
Nag create ako boot camp partition para sana mag-install ng Ubuntu sa MacBook Air. Kaya lang biglang naging black yung screen habang nagpapartition ako at napilitan akong patayin since 4 hours na siyang black. 

Walang nangyari sa Mac, except sa nagamit yung space na yun at wala siya sa boot camp.

eto yung report ng partition inspector...

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    489972567  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    490234751  ee  EFI Protective

MBR contents:
 Boot Code: None
[B]
Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)
[/B]
Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+


Paano kaya i-repair to? I want to just put it on Ubuntu, since convert na yung may-ari, parang si Kuya Killer_D lang. Of course what I need to happen is:

1. Mawala yung fat32 na yun, and release it to hfs+
2. partition it then make it read by bootcamp
3. install ubuntu on bootcamp.

Tnx.

PS.... calling kuya killer, ano ginawa mo sa Mac mo to make that possible. Pwede ba USB for that?:lolflag:

---

### Post by jepong on 2011-02-22
if i may suggest... since overkill naman ang resources ng apple... why not virtualbox on mac na lang?

anyway, i googled few and baka pwede mo try 'to... [https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Ubuntu_Feisty_On_Intel_Mac_Mini_Quick-Start_Guide?highlight=%28mac%29%7C%28mini%29](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Ubuntu_Feisty_On_Intel_Mac_Mini_Quick-Start_Guide?highlight=%28mac%29%7C%28mini%29)

luma na kasi yung article pero baka almost the same lang

---

### Post by jepong on 2011-02-22
i suddenly bump in this article...

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Dual-Booting_Mac_OS_X_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Dual-Booting_Mac_OS_X_and_Ubuntu)

---

### Post by jaceleon on 2011-02-25
I solved this problem already by using the Mac OS X Installer. Used disk utility to check the HFS+ Partition. Now he's happy with Ubuntu on Virtualbox. Thanks for the help though.:popcorn:

---

