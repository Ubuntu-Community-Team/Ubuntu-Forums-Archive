---
title: "How do I make Ubuntu my default OS?"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by Adam Jensen on 2012-02-24
I'm dual-booting by laptop with Ubuntu 11.10 and Windows 7. Whenever I turn my laptop on, the windows boot manager (i think that's what its called) loads up and asks me to choose which OS I would like to use. If I don't choose, Windows starts by default. Is there any way to change this? I would like Ubuntu to be my default OS.

---

### Post by cbanakis on 2012-02-24
I cannot remember the exact details, but I am pretty sure Ubuntu uses the Windows Boot Manager.

So you should be able to change it in Windows, by right clicking on My Computer, and selecting Properties, then somewhere from there...

I think under performance options?

You should know it when you see it, somewhere in there you should see boot options, where you can change the time before auto selecting an OS, and the default OS.

---

### Post by cbanakis on 2012-02-24
Its also listed in control panel under system preferences or system settings, if you do not have a "My Computer" to right click on...

---

### Post by Adam Jensen on 2012-02-24
Oh ok. I will try this. Thanks for answering. I now have a new question- since Ubuntu loads with the Windows Boot Manager, does Ubuntu run under Windows? Is Windows running in the background? Educate me please.

---

### Post by roelforg on 2012-02-24
> **Adam Jensen said:**
> Oh ok. I will try this. Thanks for answering. I now have a new question- since Ubuntu loads with the Windows Boot Manager, does Ubuntu run under Windows? Is Windows running in the background? Educate me please.
No, linux is a seperate OS.
A boot loader is the program the BIOS loads to load the OS-kernel in mem and run it.
The BIOS doesn't know how HD's work; it's the bootloaders job to know how and start the os.
Wikipedia has a better explanation: [http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)

---

### Post by Mark Phelps on 2012-02-24
This is an Ubuntu forum, not Windows 7. In a real Windows 7 forum (sevenforums.com), instead of directing you to 10-year old stuff  (My Computer), they would have told you the following:

Click the Windows icon (there is no Start button anymore)

Right-click on "Computer" in the menu (there is no My Computer anymore)

Click on Advanced System Settings on the left.

Click the Advanced Tab

Click the Settings button in Startup and Recovery

In the pulldown in the Default operating system area, choose the on you want.  Click Apply.

---

### Post by cortman on 2012-02-24
If you installed Ubuntu inside Windows using Wubi, you are using the Windows bootloader, and Mark Phelps' advice applies. If you actually installed Ubuntu to the HDD on its own partition (a true dual-boot), you can edit your Grub menu. Determine which is which, and if it's Grub we can tell you how to edit that too.

---

### Post by Adam Jensen on 2012-02-24
> **Mark Phelps said:**
> This is an Ubuntu forum, not Windows 7.

Thanks for the help Mark, but the smart comment was unnecessary...

---

### Post by bcbc on 2012-02-24
Be careful not to reduce the 'time to display operating systems' to less than 10. For some reason, Windows boot manager will hide if less that a certain amount (I think it's 6 secs) and if you default to boot Ubuntu you cannot change it without a Windows repair CD/USB. So it's a good idea to create one beforehand.

---

### Post by alegomaster on 2012-02-24
Did you install Ubuntu under wubi or did you install it in its own partition by using a live-cd

---

### Post by bogan on 2012-02-25
Hi!,[B]Mark,
[/B]
In your mini Windows tutorial, you Posted:> Right-click on "Computer" in the menu (there is no My Computer anymore)

Click on Advanced System Settings on the left. You missed out a bit, it should read: > Right-click on "Computer" in the menu (there is no My Computer anymore)

Click on "Properties" in the drop-down menu.

Click on Advanced System Settings on the left.Chao!,** bogan**.

---

### Post by Adam Jensen on 2012-02-25
> **alegomaster said:**
> Did you install Ubuntu under wubi or did you install it in its own partition by using a live-cd

I installed it using Wubi

---

### Post by forrestcupp on 2012-02-25
> **Mark Phelps said:**
> 
Click the Windows icon (there is no Start button anymore)


[It's still officially called the Start Menu](http://windows.microsoft.com/en-US/windows7/Whats-new-with-the-Start-menu). It just doesn't say the word "Start" on the button anymore. And the button is actually called the Start Orb now.

---

### Post by Adam Jensen on 2012-02-26
Thanks guys. You've all been very helpful!

---

