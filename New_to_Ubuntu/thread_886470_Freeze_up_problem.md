---
title: "Freeze up problem"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-08-11
Several things have happened over the last couple of weeks and I think they may be related.

1. My laptop freezes up completely and I have to crash it if I preview more than 3 or 4 screensavers (I've just put it to blank screen and thats fine now).

2 A couple of times I put it to hibernate, closed the lid and when I came to use it again it was complaetely frozen with a terminal type of comande line occupying the whole screen prompting for password. there were shadows of this accross the whole screen too.

3. Now when I click either HIbernate or Shut down I get a brief error msg "not enough free swap" before a flashing cursor for a few secsonds , along with a fragment of boot up sound.

My swap is 400MB which is what the install chose, My RAM is 1GB.
Can someone tell me whats going on? or how to fiure it out?

---

### Post by Iceni on 2008-08-11
Hardy?

I know that one of the screensavers crashes my system. Or used to in gutsy and hardy anyway.

Don't know about the others sorry.

---

### Post by forger on 2008-08-11
> **mariane_08 said:**
> Several things have happened over the last couple of weeks and I think they may be related.

1. My laptop freezes up completely and I have to crash it if I preview more than 3 or 4 screensavers (I've just put it to blank screen and thats fine now).


You might be having problems with acpi or something like that.. Try using some boot options in your grub configuration:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/BootOptions#Kernel%20Options](https://help.ubuntu.com/community/BootOptions#Kernel%20Options)

---

### Post by mariane_08 on 2008-08-11
> **forger said:**
> You might be having problems with acpi or something like that.. Try using some boot options in your grub configuration:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/BootOptions#Kernel%20Options](https://help.ubuntu.com/community/BootOptions#Kernel%20Options)

I'll try that. But trhe screen saver freeze is only one part of what seems to be the same problem as described above. When I put it into hibernate it comes up now with this "not enough swap" msg!

---

### Post by mariane_08 on 2008-08-11
> **forger said:**
> You might be having problems with acpi or something like that.. Try using some boot options in your grub configuration:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/BootOptions#Kernel%20Options](https://help.ubuntu.com/community/BootOptions#Kernel%20Options)

OK I can edit the boot options as described in that link but TBH I don't know what I should be editing them too. i.e I change it to what? there seem to be alsorts of posibilities there.

Does this all depend on my system specs, hardwhare etc? I can provide more information if that will help. I can live with screensavers causing freeze up as I'm happy with it going to blank screen. But what concerns me more is the msg about not enouth swap when I go to hibernate!

---

### Post by forger on 2008-08-15
I've never had problems with freezing, so I can't really suggest anything in particular :(
try **pci=noacpi** or **noapic** or both, it worked for a some people I know

The "not enough swap" means that probably your swap partition doesn't have enough space.
You should probably resize your swap partition with the ubuntu live cd (and boot from it - go to System > Administration > Partition Editor)

---

