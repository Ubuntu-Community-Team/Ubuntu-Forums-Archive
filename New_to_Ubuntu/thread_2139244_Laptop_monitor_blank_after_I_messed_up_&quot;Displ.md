---
title: "Laptop monitor blank after I messed up &quot;Display settings&quot;"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by plasticframedglasses on 2013-04-26
I was trying to connect my laptop (Ubuntu 12.10) to an external LCD TV. I was messing around with the display configurations and then disconnected the LCD and restarted my computer. However, after the initial boot-up, I get the Ubuntu splash screen and then my screen turns gray / blank. Every single time after I start up, I get the Ubuntu splash screen and then the blank / gray screen.

But when I try booting from a live disk, my screen displays normally. How can I fix this? I've only been using Ubuntu for 3 days. Help!

---

### Post by Kopkins on 2013-04-26
Try booting without full graphics. At the grub screen choose the option that has (recovery mode) near the end of it. It may be in Advanced Settings. Once you're there you should just be able to resume boot and it should boot with fallback graphics. From there you should be able to try to adjust settings so that your screen works again. 

Good Luck

Kopkins

---

### Post by plasticframedglasses on 2013-04-27
> **Kopkins said:**
> Try booting without full graphics. At the grub screen choose the option that has (recovery mode) near the end of it. It may be in Advanced Settings. Once you're there you should just be able to resume boot and it should boot with fallback graphics. From there you should be able to try to adjust settings so that your screen works again. 

Good Luck

Kopkins

Hey, thanks for your reply. I've tried that but it didn't work. This whole blank screen thing happened after I followed this xorg creation thing that you were supposed to save in your etc folder that some guy suggested. 

I've tried almost every variation of booting and command line hackery that people were suggesting online, all sorts of grub tricks and whatnot... nothing. After 3 hours of frustration, I was just about ready to let go of my files that weren't uploaded in the cloud yet and just charge everything to experience. That's when I tried, as a last attempt, to upgrade to 13.04 and whaddyaknow, it worked! 

I would've still liked to know what exactly went wrong and how I could've fixed it without updating but, oh well.

---

### Post by Kopkins on 2013-04-27
Just as a heads up, if your install is ever broken and you can't boot, you can still use a live cd and an external drive to recover files. Unless your filesystem is corrupted or your HDD failed you can usually get your data back. Also, you could chroot into your install and remove that file you made that broke your system.

Kopkins.

---

### Post by plasticframedglasses on 2013-04-28
> **Kopkins said:**
> Just as a heads up, if your install is ever broken and you can't boot, you can still use a live cd and an external drive to recover files. Unless your filesystem is corrupted or your HDD failed you can usually get your data back. Also, you could chroot into your install and remove that file you made that broke your system.

Kopkins.

Yeah, that's what I thought but when I was trying to get my files (after booting from a live cd), it would'nt let me copy my folders to an external drive. It was saying I didn't have root access. Weird huh. Hence the desperate attempt to upgrade to 13.04.

I'll read up on doing that chroot thing you're suggesting. Sounds like it might be useful to know down the road. Thanks, man!

---

### Post by Kopkins on 2013-04-29
The live cd's don't provide you with a root environment as a safegaurd. But you can still get root access with sudo.

---

