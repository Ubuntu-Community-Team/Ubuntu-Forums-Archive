---
title: "Dual boot advice"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by nnjond on 2012-03-02
Hi,

I have a new laptop with  Windows 7 installed. Is it true I can resise my HDD using Gpart without disturbing the MS os?

I would like to add Ubuntu and have a third partition to which both oses have access. Can you direct me towards any advice?

Thanks

---

### Post by seawolf167 on 2012-03-02
I would *highly* suggest resizing the Windows 7 partition with the built-in Windows partition editor which can be found via right-clicking "My Computer", then selecting "Disk Management" under "Storage" and resizing the volume through there. Once it is resized, you can install Ubuntu on the empty space.

As always, I suggest making a [backup image ]("http://clonezilla.org/")of your hard drive before you start just in case something happens.

---

### Post by oldfred on 2012-03-02
+1 on seawolf167 suggestions.

Most Windows 7 laptops also come with all 4 primary partitions used, unless it is a very new system with UEFI booting and gpt partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

