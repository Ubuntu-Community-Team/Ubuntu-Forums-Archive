---
title: "Booting Problems"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Lambsauce on 2008-06-27
Heya. I'm a brand new Ubuntu user, finally got fed up with Vista once and for all, but Ubuntu has given me so much grief I'm seriously considering switching back. I'd almost rather take the constant blue screens and spazzing over security than this.

So, what is "this", you ask? Well...

I've been having a LOT of issues with booting my computer. I have no idea if they're related or not--I am a total n00b--so any help with any of them will be much appreciated.

Firstly, sometimes my computer doesn't boot at all. I'll go through the Dell startup and the Ubuntu startup screens, and then it'll go to a bunch of text saying things like "Starting xxxx... [Ok]". But then it'll say:
Starting powernowd...
Killed

And then I have to do a hard reboot.

Secondly, sometimes after I've booted and logged in, I will be greeted by the following message:
> There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the reply timeout expired or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in.

Then, when I finally get everything running, my wireless won't work.
Sometimes it just doesn't give me any sort of wireless option when I go into the manual configuration (and then--guess what--I have to reboot),
and other times it will attempt to connect to my home network, HOWEVER, it will ask for the key--and if it does, I never get connected. It just asks for the key over and over again (and yes, I do type it right). It's only when I reboot and it connects without asking for the key at all that I can finally get on the internet.


And, once again, with Ubuntu continually switching these four issues around, I can only finally get everything running smoothly about once every ten reboots. So, yeah, definitely NOT a good situation!

I'm running a Dell Inspiron 1520, and my wireless card is a Broadcom BCM4312 (rev 02), which I managed to get working with [this wonderful guide.]("http://ubuntuforums.org/showthread.php?t=766560")

I have permanently added noapci to the boot as suggested below, which appeared at first to rectify the issue--but it has recently started happening again. I also tried adding the other suggested switches (noapic, nolapic, noirqpoll, and nosmp) but they did nothing.


Any help would be much, MUCH appreciated as I am really getting frustrated with this... please keep in mind, though, that I can barely run Terminal :) I need to work through these problems before I can learn how to use Ubuntu!

---

### Post by svk on 2008-06-28
Hey, I feel ya.  Getting Linux working and running smoothly on my laptop took me a few days, and a truckload of frustration.  I was willing to go back all the way to Windows 95.

But stick with it -- it's worth it in the end!

I don't have the same laptop as you, but some of the issues you're running into sound very similar, right down to the proportion (1 in 10).  In my case, my laptop could not run ACPI and APIC.  (Feel free to look up what these things mean).  Fixing my laptop required me to disable these services.

There's no harm in trying to see if it will work for you.  You can temporarily disable these right before the computer boots.  When you're still in GRUB, and your Linux OS is highlighted, hit the 'e' key.  This will take you to a different menu where you can edit some options before you boot in.  Scroll down until you highlight the line that begins with "boot".  Again, hit the 'e' key to edit this line.  This will take you to the end of this line and show you a blinking cursor, allowing you to edit stuff.

Here's what you do.  First of all, see the words "quiet splash"?  Delete those two words.  What this does is, instead of giving you a pretty splash screen and hiding all the diagnostic messages from you, when you go to boot the system, it will spew a lot of information to the screen while the system is booting.  Even if disabling the services (which I am about to get to) will not help, this extra information will help others tremendously in helping you solve the problem.

We're not done editing yet, though.  You deleted 2 words, but you will add a few others instead.  For starters, add these three words:

noapci noapic nolapic

This will disable APCI, APIC, and local APIC, all of which caused me a lot of headaches.  Maybe it will work for you, maybe not.  When you add these words, hit 'enter'.  This will take you back to the list of options you can edit (you'll be back at the line starting with 'boot').  For your first trial, you're ready to try booting, so hit the 'b' key to boot.

Does it work?  Let us know.  If the system still freezes, at the very least, you'll be armed with additional clues because the boot-up messages will be printed to the screen.  What line is the last one you see before the system freezes?

If the system still freezes, try this trick.  Either in addition to the three options above, or instead of them, try this option:

nosmp

(This means "no symmetric multiprocessing"). If you're on a multicore system, this will disable multithreading, and it will be as if you're on a single core system.  Multithreading is often the culprit behind boot problems, so there's a chance it might work with this option.  This should hopefully not be the final solution because you're not really taking full advantage of your processor's capabilities if you do this.  But if the system boots with this option, we at least have an additional hint as to what could be wrong.

Good luck!  And don't give up!  It's possible to make Linux run on anything, but it can take a lot of patience at times.

---

### Post by Victormd on 2008-06-28
There are several switches you can add to the boot, such as noapic noapci nolapic noirqpoll nosmp.  You should add these switches, not necessarily all of them as not all laptops behave the same.
When you boot, at the grub menu, highlight the entry you will boot (usually the first on the list) and hit e, next, search for the line that looks something like this:
> kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ro quiet splash
hit 'e' again. After the terms quiet splash, add the switches (you should add one at a time to experiment - try noapic and noapci first) so it will look something like this:
> kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ro quiet splash noapic noapci
Note that everytime you reboot, these switches will be reset, the above is a temporary edit to your boot line and will allow you to evaluate which parameters should be included. Once you've determined the parameters to include, make the solution permanent:
Open a terminal and type:
```
 sudo gedit /boot/grub/menu.lst
```
and scroll down until you reach something like this:
> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
**kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ro quiet splash**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
and add the switches that worked (during your boot edit) after "quite splash" so it looks like this:
> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
**kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ro quiet splash noapic**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
Save the file and now, everytime you boot, you should get a smooth ubuntu...

Let us know how this works out.

---

### Post by Lambsauce on 2008-06-29
It appears as though noapci has done the trick. I tried noapic first, and all I got was a black screen, but noapci got me up and running even faster than when I got a successful boot before! This is fantastic, thank you both very much--I'll keep trying to make sure this is the one.

---

### Post by Victormd on 2008-06-29
yeah, noapic and noapci are usually the deal breakers...
Now that you know how to get it up and running, don't forget to add it to your menu.lst file to make it permanent.

---

### Post by Lambsauce on 2008-07-02
I hate to have to re-open this thread, but the problems started happening again, exactly as before.

I've changed my OP to include the exact GNOME Desktop error message I occasionally receive, as well as the suggested fixes I have tried.

Any more ideas anyone could offer would be so appreciated... thank you!

---

### Post by eapache on 2008-07-02
If you recently ran an update, and it updated your kernel, you'll have to re-add the options to menu.lst because the update manager just sticks the normal ones on the end after a kernel change.

There should be a line in menu.lst ```
# defoptions=
```If you add whatever extra stuff you did to that as well, it will automatically add those to any new kernel updates in the future.

EDIT: Just a note, but if you're running graphical apps using sudo (like gedit), you should really run gksudo instead, because it provides a few extra graphical functions that regular sudo doesn't.

---

### Post by Lambsauce on 2008-07-02
Ok, I added the noapci and noirqpoll to #defoptions=... however, the two switches were still there when I first opened up menu.lst, so I don't think I'd updated the kernel since adding them. Thanks for the heads up, though.

---

### Post by svk on 2008-07-02
The only way you can know for sure if those switches are *actually* being applied when you boot the kernel is to check the kernel command line in the GRUB menu before you boot.  To do that, again, reboot, go into GRUB, select the Ubuntu OS, hit 'e', scroll down to the "kernel /boot/..." line, hit 'e' again, and check if the switches are all there.

If not, try adding all 5:

noapic noapci nolapic noirqpoll nosmp

---

### Post by Lambsauce on 2008-07-03
Everything was in place in the GRUB menu... haha I'm sorry for being so difficult!! It's just, everything I've done is still there, and I really don't know what's going on.

---

### Post by Lambsauce on 2008-07-05
Is there anything else I can try?
(And some more information, in hopes of making this a little meatier than a simple "bump" post)

I thought of disabling powernowd because of the one problem I mentioned in the OP, but I haven't received that specific error in a while; it seems to primarily be an issue with the wireless connection.

I did try to install Wicd, but couldn't manage to connect at all through it so I ended up re-installing GNOME Network Manager. Actually, come to think of it, these problems resurfaced after my installation and subsequent uninstallation of Wicd. It's probably just a coincidence, but maybe not? I am completely in the dark here.

---

### Post by eapache on 2008-07-06
If nothing else works you can try copying your data to an external drive, reinstalling Ubuntu, and working through the steps until you figure out exactly what causes it.

Reboot between each step, and figure out what it was you did that caused it to stop working. Possibly a lot of work, but you could then report it as a bug at launchpad.net/ubuntu

Good luck!

---

