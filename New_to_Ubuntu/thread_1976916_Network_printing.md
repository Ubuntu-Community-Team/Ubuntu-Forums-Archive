---
title: "Network printing"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by baditaflorin on 2012-05-05
> **cjazz said:**
> Two questions, more for my clarity than anything else:

1. What is kind of printer is it?

2. Have you tried to set it up using the "New printer > Windows printer via Samba" option under System > Administration > Printing?

For a printer directly connected to a Windows computer, the entry smb://WORKGROUP/COMPUTER_NAME/printer_name tends to work very well for me, with WORKGROUP being your own workgroup name, COMPUTER_NAME being the name of the Windows computer to which the printer is connected and printer_name being the share name of the printer as set under Windows. Obviously the printer needs to be shared in Windows, and it often helps to turn off bi-directional printing.


I tried and get "There were no print shares found.  Please check that the Samba service is marked as trusted in your firewall configuration" i have to dig more. I don`t want to be a geek anymore.

---

### Post by mastablasta on 2012-05-05
smbtree

and try smb restart or something along those lines. my printer didn't show up for some time (was frustrating as i wasn't sure what was wrong) until i restarted samba.

also what printer is it. it might be you need to install drivers on your linux maschine first.

---

### Post by baditaflorin on 2012-05-09
> **mastablasta said:**
> smbtree

and try smb restart or something along those lines. my printer didn't show up for some time (was frustrating as i wasn't sure what was wrong) until i restarted samba.

also what printer is it. it might be you need to install drivers on your linux maschine first.

adita@vivi:~$ smbtree
Enter badita's password: 
WORKGROUP
	\\VIVI           		vivi server (Samba, Ubuntu)
		\\VIVI\IPC$           	IPC Service (vivi server (Samba, Ubuntu))
		\\VIVI\print$         	Printer Drivers
badita@vivi:~$ 

Is something with my confuguration

---

### Post by oldos2er on 2012-05-09
Posts moved to their own thread.

---

### Post by baditaflorin on 2012-05-10
> **oldos2er said:**
> Posts moved to their own thread.

Now it`s fixed :)  It can be closed :) 10x Ubuntu community

---

### Post by czgirb on 2012-05-10
> **baditaflorin said:**
> I tried and get "There were no print shares found.  Please check that the Samba service is marked as trusted in your firewall configuration" i have to dig more. I don`t want to be a geek anymore.

Me too! I found NO printer on my LAN.
How to check that the Samba service is marked as trusted in my firewall configuration?
Where is my Firewall? Please guide me

---

### Post by oldos2er on 2012-05-10
> **baditaflorin said:**
> Now it`s fixed :) 

Great! Would you please mark the thread as 'Solved' under Thread Tools? Thanks.

---

