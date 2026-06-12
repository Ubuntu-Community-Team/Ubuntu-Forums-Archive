---
title: "Dual boot problem"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by dnns123 on 2008-04-25
I had a Ubuntu 7.10, a main partition for data, and a Windows partition for games. After I made a fresh installation of Hardy, I tried to boot into my Windows partition. Now, the windows can't boot, but I still access the files inside.

---

### Post by oloapota on 2008-04-25
Does it just boot into ubuntu without asking? Or do you get a specific error?

---

### Post by dnns123 on 2008-04-25
I get the usual choice on the OS i want to boot. Ubuntu, Safe mode Ubuntu, Memtest, Windows.
When I chose Windows, it just says it needs a hall.dll in the system 32 folder.
I looked into the windows partition using Ubuntu and hall.dll is there.
Weird...

---

### Post by meierfra. on 2008-06-07
Did you solve your problem by now? The "hal.dll" error often means that "boot.ini" needs to be [edited]("http://support.microsoft.com/kb/289022"). Did you move your Windows Partition? Or created a partiton in front of it?

---

