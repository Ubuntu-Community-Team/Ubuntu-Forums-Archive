---
title: "Upgrade to 12 crashed the system"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by susanpenter on 2012-05-28
I hope someone can help. I have not used my desktop with Ubuntu on for a couple of years but I've decided to get back into it. It upgraded through 3 distributions with no problems but now on 11:10 this is what happens when I boot up (I have tried putting the newest version on a disk but the boot menu overrides my selection of boot to disk - I assume - and boots in to hard disk. The black screen has this on it.

nd      ng save kernel message [ok]
*Starting regular background program processing daemon [ok]
Rather than invoking init scripts through /etc/init.d, use the service(8) [ok]
*stopping anac(h)ronistic cron   utility,
eg service S25 bluetooth startsp2/debian.webapp
*To fix it, you need to instalinitctl: Unknown job:S25bluetoothike asp.net2-examples)
* Stopping GNOME Display Manager   Since the script you are attempting to invoke has been converted to anpatcher
*Stopping save kernel messages   Upstart job, you may also use the start(8)utility, e.g. start S25bluetooth
Ubuntu 11:10  *PulseAudio configured for per-user sessions
  saned disabled;e .  .  .  .efault/saned  [ok]
apache2: Could not reliably determine the server's fully qualified domain name, using::1 for ServerName
* Starting web server apache2     [ok]
* Starting CUPS printing spooler/server  [ok]
* Starting anac(h)ronistic cron    [ok]
*Stopping anac(h)ronistic cron  [ok]


I really hope someone understands this as my PC seems 100% unusable at the moment.

Many thanks,
Susan

---

### Post by fantab on 2012-05-28
Ubuntu version 11.10 was a major upgrade from Gtk2 to Gtk3... 

Instead of fixing your upgrade, I suggest you do a Clean Install to the latest 12.04.

---

### Post by susanpenter on 2012-05-28
Thanks but as I mentioned I have tried doing that and I couldn't, when I tried to change the boot menu to boot from the CD rom it constantly ignores this and logs into the hard drive when it only gets as far as the text above.

I go to boot and move down to the correct drive and hit enter but it won't take... I have tried using both the Cd/DVD Roms and it won't boot from either.

---

### Post by fantab on 2012-05-28
> **susanpenter said:**
> Thanks but as I mentioned I have tried doing that and I couldn't, when I tried to change the boot menu to boot from the CD rom it constantly ignores this and logs into the hard drive when it only gets as far as the text above.

I go to boot and move down to the correct drive and hit enter but it won't take... I have tried using both the Cd/DVD Roms and it won't boot from either.

Maybe you should try updating the BIOS... since you say its an old PC. Also verify the integrity of your ISO by doing md5sum check.  Also is DVD drive in a good condition? could be a lens issue.

---

### Post by susanpenter on 2012-05-28
> **fantab said:**
> Maybe you should try updating the BIOS... 
Hi I'm afraid I have no idea how to do this.

The PC is all in fine working condition it terms or hardware. There is nothing on the system I need to keep as all my data is on a removable hard drive. I just need a way to start again from a blank canvas but without it booting from disk i have no idea how to make this happen...

---

### Post by steeldriver on 2012-05-28
if you were able to boot from the CD/DVD drive previously, then most likely:

a) the BIOS settings have been changed 

b) the disc didn't write properly so isn't a valid bootable iso image

I think (b) is more likely if you haven't been playing around in the BIOS - you could try popping the disc in another computer to see if it will boot there, if not toss it and burn a new copy

---

### Post by fantab on 2012-05-28
First make sure that you have downloaded the correct architecture 32bit or 64bit. Then do [**md5sum**]("https://help.ubuntu.com/community/HowToMD5SUM") on the downloaded ISO an the CD/DVD you've created. If all the checks are Ok and you still can't use your CD/DVD drive then:

Try using a USB Boot with [**Unetbootin**]("http://unetbootin.sourceforge.net/").

---

