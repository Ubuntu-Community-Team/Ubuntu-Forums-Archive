---
title: "newbie issue with firestarter and network drive"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by guiliker on 2008-06-22
My host OS is Hardy and through vmware server my guest OS is Windows XP Pro spk3. They are working well together except for when it comes to sharing files between the two. I followed the How-To at [http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/]("http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/") this works OK except for Windows only "finds" the networked drive when Firestarter is switched off. How do I configure Firestarter or whatever so I don't have to switch it off?

I've had a search of the forums and a google and I cannot find an answer so far. Thanks in advance.

---

### Post by cariboo on 2008-06-23
How are you connecting to the internet? Is it a direct connection or through a router. If you connect through a router, then in ufw (firestarter is just the gui) open ports 139 and 445.

Jim

---

### Post by guiliker on 2008-06-23
I'm not directly connected to the internet that is as much as I can say. I connect via a LAN socket in the wall. My internet connection comes as part of the "fittings and fixtures" and "service charges" of where I live.

I've already got port 445 open so i'll open 139 and see what happens.

OK well I just tried that and it makes no difference. I still have to disable firestarter through the gui.

---

### Post by bodhi.zazen on 2008-06-23
IMO you should use ufw rather then firestarter.

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

You then allow samba ports :

135
139
445
137
138

---

### Post by guiliker on 2008-06-23
I've got rid of firestarter in favour of ufw option. I've therefore added the ufw rules to allow the suggested samba ports. It still didn't work but on further reading about the ```
bind interfaces only = true
``` in the samba config file I have realised that the option will only work on directly connected machines. Mine isn't so i've commented that option and now I can access the samba shared file.

Thanks for the replies....my only hope is that my machine isn't open to anyone via the internet!

---

