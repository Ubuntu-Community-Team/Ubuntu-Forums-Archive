---
title: "Ubuntu boot issue."
date: 2008-05-12
forum: New to Ubuntu
---

### Post by chrisu87 on 2008-05-12
Hello everyone,

I downloaded tried to use Ubuntu through the live cd, and it froze when the loading bar came up.  I did the install through windows and the same thing happened.

Celeron D - 2.9 Ghz
Nvidia GeForce FX 5500
1.5 Gb of RAM

Any help would be highly appreciated.  Thank you ahead of time.

- Chris

---

### Post by chrisu87 on 2008-05-12
I have never used Ubuntu before by the way, but I'd love to give it a shot.  Thanks again.

---

### Post by chrisu87 on 2008-05-12
Can anyone give me some help, or at least direction on this issue?

---

### Post by stevescripts on 2008-05-12
See the following about burning a live cd:

[http://help.ubuntu.com/community/BurningIsoHowto]("http://help.ubuntu.com/community/BurningIsoHowto")

Make sure to burn the cd slow (like 4x maybe)

Make sure to check its integrity (from the menu as it boots)

Make sure to use a CD-R, and not a CD-RW, as it wont have room for the entire cd...

Hope this helps.

Steve

---

### Post by chrisu87 on 2008-05-13
I used an older version of ubuntu (manufactured disc, not burned) and it gave me the same problem, so I doubt that it's the cd.

---

### Post by kesman on 2008-05-13
Did you try the safe graphics option? Also there's an option to edit the boot parameters. Remove the words "quiet" and "splash" from the end of the boot line, then you'll at least see what's going on when it hangs.

---

### Post by Tatty on 2008-05-13
Theres a few possible things it could be.

If you have not checked the cd integrity (as stevescripts has suggested) then it would be worth doing it first, as CD errors lie behind a lot of problems like this.

1. First try disabling the splash screen so we can get feedback as to which part it is freezing on.

I havent dont this recently enough to remember for certain, but I think its a case of pressing F6 when you get to the "start or install ubuntu" screen, then deleting "quiet" and "splash" from the boot line, then carrying on the boot.

If you could give the exact line that it freezes on it could help.


2. Sometimes it is a better idea to use the alternative CD rather than the liveCD, as the liveCD is not infallible.

3. Try adding the parameter "acpi=off" (without quotes) to the boot command using the same method as in 1.

4. It could always be a hardware problem, run a check on you ram with the "check memory" option when you boot from the cd.

I recently had a problem with the install hanging on a machine and it turned out to be a problem with the CD drive.


These are not an exhaustive list of problems, just the things that I have run into myself.

---

### Post by chrisu87 on 2008-05-13
So I disabled the splash screen and here's where it stops at

init: rcS main process (5746) killed by segv signal
init: Unable to execute "/bin/sh" for rc-default: no such file or directory
init: rc-default main process (7053) terminated with status 255

and thanks for the feedback so far.

- Chris

---

### Post by chrisu87 on 2008-05-13
Any ideas from those errors?

---

### Post by chrisu87 on 2008-05-13
Anything else I need to check?

---

### Post by doug4849 on 2008-05-13
My installation kept stalling at 82% until I disconnected from the internet.
With no internet connected, it installed with no problem.

---

### Post by chrisu87 on 2008-05-13
I unplugged my USB network adapter, and still froze up.

But when I booted it off the Hard drive it gave me a slightly diff error message.

"Segmentation fault
/etc/init.d/rc: 317: Sed not found
/etc/init.d/rc: 317: Sed not found
/etc/init.d/rc: 317: Sed not found
/etc/init.d/rc: 317: Sed not found
/etc/init.d/rc: 317: Sed not found
/etc/init.d/rc: 317: Sed not found
init: Unable to execute "/bin/sh" for rc-default. No such file or directory
init: rc-default main process (7267) terminated with status 255"

thanks again.

- Chris

---

### Post by chrisu87 on 2008-05-13
Okay, did find the source of the problem.  Removed video card, booted from HDD no issue except for my internet not working.

Only problem is that I want to use the vid card I have and my internet.

Linksys Wireless-G USB Network Adapter
Nvidia GeForce FX 5500

I thank everyone who has tried, and those who will try to help me.

- Chris

EDIT:  Forgot to mention that the graphics card is PCI

---

### Post by heatpumpcontrol on 2008-05-13
If you are booting from the live CD then I wouldn't worry too much about the video card issue. Now if you want to install and run it on the hard drive then what I would do is make sure it installs everything first using the onboard video or without the problematic video card you mentioned, then after that you can try to fix or find a fix ie: proper drivers for the video card at hand.

Now, once you have the system up install the video card back in and the system will pick up that you've changed the video and prompt you to use the default video drivers which will give you a start. Just make sure you know the model and make of your card. You may want to try to install [[COLOR="Red"]Envy[/COLOR]]("http://albertomilone.com/envyfaq.html#A") and have it install the drivers for you. It works pretty well.

---

### Post by chrisu87 on 2008-05-13
What about the internet connection?  What should I do about that?

---

### Post by heatpumpcontrol on 2008-05-14
> **chrisu87 said:**
> What about the internet connection?  What should I do about that?

What you are using is a USB wireless adapter? Hmmm. I know I had a hard time getting a Bluetooth adapter to work before so I don't know what you could do for a USB wifi adapter. 

Try reading [here]("http://ndiswrapper.sourceforge.net/joomla/").

Also you might try selecting different eth adapters. Right click properties on the wifi icon on the top panel and try to change the adapter being used. I don't have wifi so I'm not sure if these are the right steps.

Edit:

Found [this]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/ubuntu-linux-and-linksys-wireless-g-portable-usb-adapter-wusb54gp-problems-462105/") ... try reading there and I believe you'll find your fix

---

