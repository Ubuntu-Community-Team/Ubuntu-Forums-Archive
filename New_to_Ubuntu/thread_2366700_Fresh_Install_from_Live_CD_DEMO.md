---
title: "Fresh Install from Live CD DEMO"
date: 2017-07-20
forum: New to Ubuntu
---

### Post by lmrios on 2017-07-20
Hi guys!!! I would like to say hello and comment on my installation experience 2017-July-18. Maybe it is worth for somebody else.
I have just installed lubuntu 16.04.2 on my laptop MSI X-Slim X410. Here are the specs:
Processor:	AMD Athlon NEO X2 Dual-Core Processor
Screen: 14 HD (1366×768)
Graphics: ATI Radeon X1250
RAM: 2GB
HDD: 320GB
Optical Drive: No
Network: Lan + WiFi

So this laptop is only to browse the web, read the news, maybe some coding Python3, answer some emails, and watch some Youtube videos. No big deal. It was running  Win7 and an older version from Debian smooth. 

By some weird  reason I decided to format and make a fresh install, Lubuntu 16.04.2 amd64 (nomodeset, has to be added).
Every single installation that I tried, let the machine completely slow (when I typed on the keyboard, the letters appear on the screen after a while) and  scrolling on a web page was choppy and of course Youtube was choppy too. So I tried installing Debian 9 with LXDE (nomodeset, has to be added), same result slow, laggy and YouTube choppy.

I try a LIVE CD and the performance was pretty reasonable, I read some threads that compiz has to be installed on Lubuntu, so once again I was ready to reinstall Lubuntu 16.04.2 amd64 (nomodeset, was added) and suddenly I confuse and I hit TRY LIVE CD DEMO, after the LIVE CD DEMO was running I google something  and then I double clicked on the Desktop icon to do the Install on the Hard Disk Drive - after all, I wanted to remove Debian 9, and install Lubuntu 16.04.2 amd64 and later on compiz -

Well here I am, compiz was not installed. In fact that last installation from the Live CD work PERFECTLY. There are some minors details like the HDMI is not with audio, and some times the processor is a full speed. But the system is working and most important it is usable.

I wanted to share my experience maybe is  helpful for some other newbie like me.
Do you know if there is any difference  installing  directly or installing from the Live CD (USB in my case) DEMO?

Best regards,
Leandro

---

### Post by vocx on 2017-07-20
> **lmrios said:**
> Hi guys!!! I would like to say hello and comment on my installation experience 2017-July-18. Maybe it is worth for somebody else.
I have just installed lubuntu 16.04.2 on my laptop MSI X-Slim X410. Here are the specs:
Processor:    AMD Athlon NEO X2 Dual-Core Processor
Screen: 14 HD (1366×768)
Graphics: ATI Radeon X1250
RAM: 2GB
HDD: 320GB
Optical Drive: No
Network: Lan + WiFi

So this laptop is only to browse the web, read the news, maybe some coding Python3, answer some emails, and watch some Youtube videos. No big deal. It was running  Win7 and an older version from Debian smooth. 

By some weird  reason I decided to format and make a fresh install, Lubuntu 16.04.2 amd64 (nomodeset, has to be added).
Every single installation that I tried, let the machine completely slow (when I typed on the keyboard, the letters appear on the screen after a while) and  scrolling on a web page was choppy and of course Youtube was choppy too. So I tried installing Debian 9 with LXDE (nomodeset, has to be added), same result slow, laggy and YouTube choppy.

I try a LIVE CD and the performance was pretty reasonable, I read some threads that compiz has to be installed on Lubuntu, so once again I was ready to reinstall Lubuntu 16.04.2 amd64 (nomodeset, was added) and suddenly I confuse and I hit TRY LIVE CD DEMO, after the LIVE CD DEMO was running I google something  and then I double clicked on the Desktop icon to do the Install on the Hard Disk Drive - after all, I wanted to remove Debian 9, and install Lubuntu 16.04.2 amd64 and later on compiz -

Well here I am, compiz was not installed. In fact that last installation from the Live CD work PERFECTLY. There are some minors details like the HDMI is not with audio, and some times the processor is a full speed. But the system is working and most important it is usable.

I wanted to share my experience maybe is  helpful for some other newbie like me.
Do you know if there is any difference  installing  directly or installing from the Live CD (USB in my case) DEMO?

Best regards,
Leandro
I don't remember how the installation goes because I installed my system two years ago, and haven't had to reinstall since. But if I understand correctly, you first installed directly, that is, you did not boot into the live session. After installation the system was slow. Then, the second time you booted into the live session, saw that everything ran okay, and then you decided to install. Is this how it went?

The only difference that I could think of, is the first case the installation was not able to detect your graphics card properly. The second time, as you booted into the live session, the system installed correctly the graphics drivers and thus you had a working system afterwards. Systems that have Nvidia or AMD/ATI graphics cards often require the appropriate drivers to run well. It may be the difference between not running at all, and running without problems.

I would always run the live session to make sure everything works okay before committing to an installation.

---

### Post by lmrios on 2017-07-21
> **vocx said:**
> But if I understand correctly, you first installed directly, that is, you did not boot into the live session. After installation the system was slow. Then, the second time you booted into the live session, saw that everything ran okay, and then you decided to install. Is this how it went?

Yeap exactly

Maybe you are right, I was a drivers problems. Thanks

---

