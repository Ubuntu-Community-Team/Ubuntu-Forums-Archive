---
title: "After using live CD: Computer does not boot."
date: 2012-04-04
forum: New to Ubuntu
---

### Post by basboos on 2012-04-04
Hello people!

I have (had) a working windows 7 installation on my desktop, then I tried re-starting the system and rebooting from an Ubuntu live CD (the latest version: 11.10). However this is where things went crazy. 

The system did not get past the motherboard splashscreen (American Megatrends in my case), and would not allow me to enter the BIOS system. I removed the CD and tried again, but still no luck. I even with an Ubuntu 10.10 Live CD which has worked for me on a similar Desktop in the past, but same problem.

I do not have the system recovery CD.


Any ideas?:confused:

Thank you!

---

### Post by santosh83 on 2012-04-04
> **basboos said:**
> Hello people!

I have (had) a working windows 7 installation on my desktop, then I tried re-starting the system and rebooting from an Ubuntu live CD (the latest version: 11.10). However this is where things went crazy. 

The system did not get past the motherboard splashscreen (American Megatrends in my case), and would not allow me to enter the BIOS system. I removed the CD and tried again, but still no luck. I even with an Ubuntu 10.10 Live CD which has worked for me on a similar Desktop in the past, but same problem.

I do not have the system recovery CD.


Any ideas?:confused:

Thank you!

Nothing that either Windows or Ubuntu normally does should mess up your system bad enough to not get past the BIOS splash screen!

At what point exactly does it stop? Does the BIOS print any sort of message to screen, or makes any sound? Are you able to press the shortcut key to enter BIOS setup?

Sometimes switching off the computer, opening the case and thoroughly cleaning the inside of dust, and optionally taking out and re-inserting the RAM module can often fix these types of startup errors.

If that doesn't then you probably have a serious hardware issue, and you might have to take it to servicing.

---

### Post by mastablasta on 2012-04-04
BIOS boots first, then boot manager and only then the operating system. operating system can not change BIOS settings and does not touch it.

---

### Post by Delphiq on 2012-04-04
Reset the bios settings. Google how.

---

### Post by basboos on 2012-04-05
Thank you very much for your replies!

Well, I ended up doing nothing and the next day the computer went back to working normally. The only thing I did do was open the desktop casing and look inside. I did not even touch anything!

I dont understand why, but everything is working now :)

---

### Post by santosh83 on 2012-04-06
> **basboos said:**
> Thank you very much for your replies!

Well, I ended up doing nothing and the next day the computer went back to working normally. The only thing I did do was open the desktop casing and look inside. I did not even touch anything!

I dont understand why, but everything is working now :)

Nothing mysterious! By looking inside the case, you collapsed the wave function of the computer, and forced it choose either a working or non-working state! I guess you've got a quantum computer over there... :-P

---

### Post by Irihapeti on 2012-04-06
Yes, an OS can do things to the bios settings.

I wouldn't have thought it could, either, but I've had it happen to me a couple of times when testing 12.04. A total lockup of the Xserver and then, on reboot, the computer couldn't find my second internal sata drive (where my working OS lives). According to the bios, there was no second drive at all.

I have no idea why it should do that, but it did. Getting it working again was a matter of disconnecting the computer from the mains and waiting a few minutes, then rebooting.

My guess is that when the OP opened the box, he/she unplugged the computer first, and that reset things.

---

### Post by mastablasta on 2012-04-06
> **basboos said:**
> Thank you very much for your replies!
 
Well, I ended up doing nothing and the next day the computer went back to working normally. The only thing I did do was open the desktop casing and look inside. I did not even touch anything!
 
I dont understand why, but everything is working now :)
 
one of disk cables might be faulty or loose. this can happen. and you will experience the problem later unless you find out which cable caused it and replace it.

---

### Post by ColeTurner on 2012-04-06
> **Delphiq said:**
> Reset the bios settings. Google how.

Can't the person take out the BIOS battery and put it back in after a few minutes. 

[COLOR=Red]**If the person does this, they should be electrically grounded fully! _Or, better yet, let someone who has more computer experience do it._**[/COLOR]
[COLOR=Black]Another problem it *could* be is drive jumper settings.[/COLOR]

---

### Post by mörgæs on 2012-04-06
> **basboos said:**
> Thank you very much for your replies!

Well, I ended up doing nothing and the next day the computer went back to working normally. The only thing I did do was open the desktop casing and look inside. I did not even touch anything!

I dont understand why, but everything is working now :)

Good, then please mark the thread 'solved'.

---

