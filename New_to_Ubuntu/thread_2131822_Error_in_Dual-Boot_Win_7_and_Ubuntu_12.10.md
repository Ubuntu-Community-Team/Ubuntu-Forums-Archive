---
title: "Error in Dual-Boot Win 7 and Ubuntu 12.10"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by Bresser on 2013-04-02
[COLOR=#000000]Hello Ubuntu Community,[/COLOR]
[COLOR=#000000]Let me start with a general low-down of all the "materials" I have here:[/COLOR]

[LIST]
[*]Windows 7 Home Edition
[*]Plot Boot Manager (Because my BIOS does not want to boot from USB)
[*]Ubuntu 12.10 downloaded straight from this site.
[/LIST]

[COLOR=#000000]Okay, so what I did was I downloaded Universal USB installer so that it would put the .iso file onto the flashdrive and make it bootable. Then I downloaded Plot Boot Manager because my BIOS will only let me boot from HDD or CD/DVD Drive. Let me say that I have dual-booted with Ubuntu and Windows 7 before with no problems, but I don't see what I'm doing wrong. Okay so after the ISO was on the USB, i restarted my computer and booted from the USB. It came up normally opened up Ubuntu to the screen where it says: "Try Ubuntu" and "Install Ubuntu". I clicked on Install Ubuntu and then it gave me three options (really five but it would only let me select three of them.):[/COLOR]

[LIST=1]
[*]Install Ubuntu inside of Windows 7
[*]Replace Windows with Ubuntu
[*]Also, use Custom Partions
[/LIST]

[COLOR=#000000]I don't have much computer technical knowledge, I do have programming knowledge though. Because of this, I selected Install Ubuntu inside of Windows. It went to a DOS-like screen (outputting what it was doing) then it showed the Ubuntu loading dots. (The Five Dots that start lighting up) this was still on the "DOS" screen but they werent there the whole time. Then my Computer which is a Laptop if that info is needed, automatically restarted and went to my selection screen where it asks me if I want to boot to Windows 7 or Plot Boot Manager. There was no sign of Ubuntu anywhere. But if I go into Windows and go to my Uninstall Programs list, Ubuntu is listed inside there.[/COLOR]

[COLOR=#000000]Thanks,[/COLOR]
[COLOR=#000000]Bresser.[/COLOR]

---

### Post by oldfred on 2013-04-03
wubi only installs as direct download in Windows, not from CD with 12.04 and later
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

If your system is so old that it does not boot from USB, you may be happier with Lubuntu. But if system came with Windows 7, it will boot from USB, if USB is bootable. My XP systems both 6 years old boot from USB.
      
 [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
Lubuntu is an Operating System that is using LXDE.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

Most Windows 7 systems use all 4 primary partitions, also. 


 Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

