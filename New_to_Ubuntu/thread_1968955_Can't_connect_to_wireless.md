---
title: "Can't connect to wireless"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by Rampo98 on 2012-04-29
I recently installed ubuntu 12.04 on my toshiba satellite l655 and i  doesnt want to connect to my wireless network which worked before my  transition over to ubuntu. Ubuntu see other wireless connections but not the my(my connection is open). Any help? please. I've seen others with this  problem but i assume this differs from machine to machine.
(Sorry for my bad english :D )

---

### Post by Hadaka on 2012-04-29
If you can see other wireless stations then your internal wifi card is
working. Perhaps unplugging the power from your router and the pluffing it
back in will reslove thie issue.
please post
# lspci -nnk | grep -iA2 "wireless"
# nm-tool

---

### Post by rgreener25 on 2012-04-29
can you confirm this -- it is showing other networks but not yours is that correct? if so i would believe that it is a problem with your router have you tested it on another device

---

