---
title: "installing an old XP hard rive"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Razerblader on 2008-11-02
I just took an old hard drive with Xp in it and put it in my ubuntu machine, when I tried booting from the XP hard drive it just blue screens and goes to the black screen that asks you what method to boot. what do I do for it to boot without a hitch?

---

### Post by Paqman on 2008-11-02
> **Razerblader said:**
> what do I do for it to boot without a hitch?

Windows doesn't like being switched between hardware at all. You'll have to reinstall Windows. That'll overwrite Grub, which you'll then have to reinstall. Reinstalling Grub is pretty easy though, just Google or search these forums for instructions.

---

### Post by linux6994 on 2008-11-02
Well some might say to put the old XP drive back in the closet. Had the drive booted the last time you used it? Are the master slave staps correct so that it can be seen properly from the motherboard? Look at the strapping on the Ubuntu drive and compare. Perhaps place both drives on the IDE bus at the same time and see what it does, either boot to Ubuntu or XP. If it does then you can work with it.

Just some things to try.

I had a XP sitting on the same bus and would boot it only once in a while and eventually wiped it out and went to Virtualbox XP. Just a thought.

---

### Post by Razerblader on 2008-11-02
well I don't have windows install CDs, so I just wanted to boot Xp without switching computers. but my main hardrive is SATA and the old hard drive is PATA or IDE I don't really know just the big ribbon.It's recognised the only thing that happens though is I see the "Windows did not start normally last time how would you like to boot" whatever I choose it just blue screens and goes back to BIOS.

---

### Post by Paqman on 2008-11-02
> **Razerblader said:**
> well I don't have windows install CDs

You're out of luck then. Windows can't handle big changes in hardware, as you can see from their [documentation](http://support.microsoft.com/kb/824125). Any major change in hardware will almost always require a reinstall, or at least a repair install.

---

### Post by Razerblader on 2008-11-02
I don' know if I should say this here but can Is it plausible to download a Vista/XP CD and use my original product key and run everything fine or what should I do?

---

### Post by Paqman on 2008-11-02
> **Razerblader said:**
> I don' know if I should say this here but can Is it plausible to download a Vista/XP CD and use my original product key and run everything fine or what should I do?

Not recommended:

a) Illegal!
b) Huge security risk. Installing an OS from an untrusted source is a baaaaaad idea. Never install _any_ software from a torrent unless you know the correct MD5 hash for that software.

If you can get an install disk for the correct version of Windows (ie: if you have a key for XP Home, you need an XP Home disk) then it will work fine. Keys aren't matched to disks. Somebody you know should have a disk they can lend you.

---

### Post by L Campbell on 2008-11-02
> **Razerblader said:**
> I don' know if I should say this here but can Is it plausible to download a Vista/XP CD and use my original product key and run everything fine or what should I do?

You might be able to get a 'recovery' disk from here:-

[http://www.recovery-cds.com/](http://www.recovery-cds.com/)

---

