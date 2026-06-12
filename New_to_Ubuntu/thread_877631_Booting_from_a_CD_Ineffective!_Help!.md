---
title: "Booting from a CD? Ineffective! Help!"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by metacognition on 2008-08-02
In a nutshell: I can't seem to boot from a CD. Right now I'm running Kubuntu and the disc I'm using worked previously when I had a an XP.

Could someone troubleshoot me through this?
Thanks in advance.

---

### Post by bks on 2008-08-02
> **metacognition said:**
> In a nutshell: I can't seem to boot from a CD. Right now I'm running Kubuntu and the disc I'm using worked previously when I had a an XP.

Could someone troubleshoot me through this?
Thanks in advance.

Are you getting any errors, or just no boot at all?

---

### Post by metacognition on 2008-08-02
No boot at all, when it boots it almost doesn't notice it. I don't think the problem would be with the iso because I have installed an OS Linux-on-Linux before.

---

### Post by bks on 2008-08-02
Have you checked the cd you're using for errors and is your cd-rom set before your HDD in the boot order?

---

### Post by metacognition on 2008-08-02
I've checked the CD twice for errors and it says it's clean. I'm not to sure on the second question, could you tell me how to set the boot order? Thanks.

---

### Post by bks on 2008-08-02
> **metacognition said:**
> I've checked the CD twice for errors and it says it's clean. I'm not to sure on the second question, could you tell me how to set the boot order? Thanks.

When your computer first starts up and the BIOS screen appears, press F2 to get into Setup and there should be a tab that says "BOOT" (or something to that effect). There will be a list of devices that the BOIS will attempt to boot the computer from. If your hard drive is above your CD-ROM in the list, the HDD will boot before the BOIS ever checks the CD-ROM. If this is the case move the CD-ROM above the HDD, Save and restart.

---

### Post by metacognition on 2008-08-02
Alright, Thanks. I guess I'll post results in a couple minutes.

---

### Post by metacognition on 2008-08-02
Hmm, I just realized that I need the command and the file path. Do I use boot? Anyway, I'm trying to get to cdrom0 or scd0. Whichever is the right one.

---

