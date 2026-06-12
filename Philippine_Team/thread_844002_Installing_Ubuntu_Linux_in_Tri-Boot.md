---
title: "Installing Ubuntu Linux in Tri-Boot"
date: 2008-06-29
forum: Philippine Team
---

### Post by unit_731 on 2008-06-29
good day guys! help naman poh kung anong kulang sa ginawa ko!

i have a 80gig HD then partition it to 3..the 1st partition is for windows xp then is for vista and the 3rd is for ubuntu..i succesfully dual booting windows xp and vista and also created  another partition for ubuntu and also for its swap file..i succesfully install ubuntu from its cd i order from their site..but everytime a restart my computer..it also show 2 bootmenu..one for xp and one for vista!??? and i cant see  the ubuntu? may kulang paba sa ginawa ko!?? and what about this grub!??


TIA

---

### Post by jeffimperial on 2008-06-29
> **unit_731 said:**
> good day guys! help naman poh kung anong kulang sa ginawa ko!

i have a 80gig HD then partition it to 3..the 1st partition is for windows xp then is for vista and the 3rd is for ubuntu..i succesfully dual booting windows xp and vista and also created  another partition for ubuntu and also for its swap file..i succesfully install ubuntu from its cd i order from their site..but everytime a restart my computer..it also show 2 bootmenu..one for xp and one for vista!??? and i cant see  the ubuntu? may kulang paba sa ginawa ko!?? and what about this grub!??


TIA
[Recovering Grub After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by pendletone on 2008-06-29
Paano mo in-install yung 3 operating systems mo? Kasi pag in-install mo yung XP or Vista sa huli, it will overwrite GRUB with its own bootloader (NTLDR). That's why nde mo nakikita yung option for ubuntu sa boot menu.

Follow jeffimperial's advice and you'll be fine.

You can learn more about GRUB [here]("http://en.wikipedia.org/wiki/GNU_GRUB")

---

### Post by unit_731 on 2008-06-29
na try ko na rin yung above suggestion pero ayaw padin!!! also using a Easy BCD to mount the bootloader for ubuntu then nag appear naman siya kaya lang ..everytime i select ubuntu it show " No such Partition"...hmmm...may mali yata akong nagawa..

---

### Post by unit_731 on 2008-06-30
Guys thanks sa mga reply!!! problem solved!:D

---

### Post by jeffimperial on 2008-07-01
Kung gusto mo, pwede mo rin i-post ang iyong ginawa para kung sakaling may mapasok sa thread na ito, may makita siyang possible option :)

---

### Post by unit_731 on 2008-07-01
eto yung ginawa ko!

1. after installing xp(hd1)vista(hd2) and ubuntu(hd3 - ext3 and swapfile)

2. i used EASY BCD software para magkaron ng bootloader yung ubuntu...

3. then install a linux Neosmart bootloader and install grub..

4. after restart..makikita mo sa bootlist yung ubuntu(Neosmart Bootloader) / select

5. then select mo Vista Longhorn Bootloader(then mag aappear kung san HD# naka install yung grub mo para sa ubuntu)

6. select Ubuntu  2.xx.xx.x


 :)

---

### Post by rjmdomingo2003 on 2008-07-01
I-mark mo na rin na SOLVED sa thread title.:)

---

