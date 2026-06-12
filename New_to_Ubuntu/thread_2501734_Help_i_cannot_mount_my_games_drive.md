---
title: "Help i cannot mount my games drive?"
date: 2024-10-18
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-18
Heyo everyone.

I need help.  I was going through gnome tweaks, and the only thing that I did was change my mouse pointer colour and that is it, I have not changed anything else.  I was so running steam in the background and getting it to do the vulkin shaders things as it does for Warframe, and then as I was looking around in the tabs of gnome tweaks everything froze and I didn't know what to do so I forced a reboot.

Then when I went to mount my games drive again I got:

"Error mounting /dev sdb2 at /media/tony/Games wrong fs type, bad operation bad superblock on dev/sdb2 missing codepage or helper program or other error"

How can this be fixed without loosing my games etc?

[IMG]https://cdn.discordapp.com/attachments/1023718295410577432/1296969170600067093/image.png?ex=6714382a&is=6712e6aa&hm=7c007627f845d39f8acf452703fe27320450216534a72a0c59f5bb105969e114&[/IMG]

---

### Post by shadowtabby on 2024-10-18
It still shows there in this tool that is in ubuntu:

[IMG]https://cdn.discordapp.com/attachments/1023718295410577432/1296968759747022888/image.png?ex=671437c8&is=6712e648&hm=dca4daf033e6aa315ac2f251f9cf0076a486fa405aa3e49cd0b70f2d22788687&[/IMG]

---

### Post by nicolasdentremont on 2024-10-18
That's an issue that I've had myself. It has to do with NTFS filesystems.

For me, it was with the wife's external HDD and I fixed it by plugging it into her Windows laptop. Windows detected an error right away and fixed it.

I've also seen some other solutions for that on this forum like the one here.

[https://ubuntuforums.org/showthread.php?t=2500423&highlight=bad+superblock](https://ubuntuforums.org/showthread.php?t=2500423&highlight=bad+superblock)

NTFS is a Windows filesystem so it sometimes  creates issues when used in Linux. If you don't need to share the files on that drive between Linux and Windows I'd recommend looking into a Linux filesystem for that drive.

---

### Post by Bashing-om on 2024-10-18
shadowtabby - Hello

As Games is a NTFS file system - Windows - I do suggest that run a file system check/repair from Windows.

OH nicolasdentremont beat me to it :D

-good advise-

---

### Post by shadowtabby on 2024-10-18
Heyo guys,

Thank you for the reply.  So after I do this it should be fixed then?

My sister still has windows on her computer so I could probably take the drive out and put it in her PC and do it.

Does this happen a lot?

---

### Post by shadowtabby on 2024-10-18
IT WORKED!!! DAMN hehe Thank you so much guys!!!

---

### Post by shadowtabby on 2024-10-18
> **nicolasdentremont said:**
> NTFS is a Windows filesystem so it sometimes  creates issues when used in Linux. If you don't need to share the files on that drive between Linux and Windows I'd recommend looking into a Linux filesystem for that drive.


How?  My NAS is qnap, and anything I need I get off there or download it and then put it there.

My sister and I sometimes remote desktop though.

---

### Post by Bashing-om on 2024-10-18
> **shadowtabby said:**
> IT WORKED!!! DAMN hehe Thank you so much guys!!!

Yay !

---

### Post by nicolasdentremont on 2024-10-18
> **shadowtabby said:**
> How?  My NAS is qnap, and anything I need I get off there or download it and then put it there.

My sister and I sometimes remote desktop though.

I don't know much about NAS, I figured that this was a drive physically attached to your system.

---

### Post by shadowtabby on 2024-10-18
Heyo,

Nope but the nas is the one that says Windows Shares on 192 I access that via SMB cause I don't know any other way to do it.

---

