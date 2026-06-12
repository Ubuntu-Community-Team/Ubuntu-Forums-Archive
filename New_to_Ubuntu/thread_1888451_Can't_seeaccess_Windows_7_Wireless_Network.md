---
title: "Can't see/access Windows 7 Wireless Network"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by Inkpot on 2011-11-29
So here's my problem:

I am unable to get my Ubuntu laptop to see my wireless Windows 7 network or access any of the files. I've searched for tutorials, installed Samba, prayed, cried, swore....you get the idea. What happens is this - A little window pops up that says 'Opening "WORKGROUP". You can stop this operation by clicking cancel'. This window stays there for about three minutes before I get an error that says the following:

Unable to mount location

Failed to retrieve share list from server.


Can anyone help? I'm running Ubuntu 11.10 with Gnome classic.

---

### Post by dolphin194 on 2011-11-29
Are you able to connect to the wifi network? Is it only the file server you are having issues with?

---

### Post by Inkpot on 2011-11-29
Wireless internet works just fine. I just can't access any of the other computers on the network.

---

### Post by dolphin194 on 2011-12-03
Sorry it took me so long to reply. Have you tried disabling the firewall on your Windows machine? Also, make sure that in Network and Sharing Center on your Windows machine that password-protected sharing is disabled. Disabling your security may get things to work a little better. You can then modify your security policies if it works.

---

### Post by Mark Phelps on 2011-12-03
If the other PCs are all Win7 and you're using a HOMEGROUP for those PCs, as far as I know, there is no way to access that outside of Win7.  Even Vista and XP can't access HOMEGROUPs.

---

### Post by zero2xiii on 2011-12-03
Hay,

So internet browsing works? Awsome, means there is only a problem with the shares.

If you open nautilus to the IP of the computer you want to access the shares of, does it work? for example in a terminal:

nautilus smb://192.168.1.2

Should open the samba shares at IP 192.168.1.2 in a nautilus browser (if you use another one than nautilus, just substitute, should work the same?)

If this fails aswell, change the workgroup on the Win 7 machine to something other than HOMEGROUP, and make sure your network config is HOME not PUBLIC or WORK.. (+1 for Mark Phelps's post)

Cherz

---

