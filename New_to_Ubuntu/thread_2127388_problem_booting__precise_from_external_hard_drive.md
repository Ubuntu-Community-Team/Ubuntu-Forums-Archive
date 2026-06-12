---
title: "problem booting  precise from external hard drive"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by allynm on 2013-03-19
Hello everyone,

I have a Seagate external hard drive that has a copy of 12.04 on it.  I also have a HP laptop with Windows 7 Professional as the base OS.  I am trying to set the system up so that when I start up the laptop I get a choice of 12.04 or Windows 7.  As far as I know, this can be achieved if the boot order is set so that the system can boot first from the external hard drive.  Here's the problem:  When I hit F10 during POST the window that shows up does not give me any options to change the boot order, as far as I can tell.  In fact, none of the options that are presented by hitting ESC during POST seem to give me the ability to change the boot order.  

Could someone more experienced in this problem give me some help.  I've been all over the web looking for a solution.  All the solutions I have seen presume that the user can get to a BIOS screen that allows the user to change the order.  My Windows 7 doesn't seem to present such a screen.  I don't get it.

Thanks,
Mark Allyn

---

### Post by gatoruss on 2013-03-19
FWIW - On my Dell L502x XPS laptop, I hit F2 during while booting up and the BIOS screen is loaded.  Across the top are menu selection, one of which is "Boot."  If I select "Boot," the screen displays a menu for "Boot Priority Order." I know that it will vary depending on make/model, but isn't F10 usually for recovery?

---

### Post by varunendra on 2013-03-20
> **allynm said:**
> Hello everyone,

I have a Seagate external hard drive that has a copy of 12.04 on it.  I also have a HP laptop with Windows 7 Professional as the base OS.  I am trying to set the system up so that when I start up the laptop I get a choice of 12.04 or Windows 7.  As far as I know, this can be achieved if the boot order is set so that the system can boot first from the external hard drive.  Here's the problem:  When I hit F10 during POST the window that shows up does not give me any options to change the boot order, as far as I can tell.  In fact, none of the options that are presented by hitting ESC during POST seem to give me the ability to change the boot order.
The BIOS boot menu gives you the choice of 'device', not the OS installed on them. You can choose between one drive or the other from that menu, and the chosen drive will boot the OS installed on it.

If you want to get a menu that gives you Ubuntu and Win7 as choices, boot the external drive, then run -
```
sudo update-grub
```
in a terminal. It will detect the windows installation on the other drive and add it to the Grub menu. Next time you boot the external drive, you will get the menu you want.

However, if you mean that the external drive itself is not showing up in the BIOS boot menu, then try a hot reboot (Ctrl+Alt+Del when the external drive is connected and the screen is paused on some BIOS menu), then go again in the BIOS boot menu using Esc/F10 or whatever key is assigned for that and see if the drive gets listed this time.

It works when the device detection time of the BIOS is too short while the time for the drive to get ready is longer. Hot reboot restarts the boot sequence without powering off the connected devices, so the drive remains ready this time.

---

### Post by allynm on 2013-03-20
Gatoruss and Warunendra (hope I spelled this correctly):

I wish I could do what you both are assuming I can do.  First, on my HP the F10 key supposedly gets me to the boot menu, not F2.  The problem is that when I hit F10 and get to the boot menu there is no option that allows me to alter the boot sequence.  On my XP and other machines it is quite straightforward to alter the boot sequence, but for some crazy reason on this HP (HP ProBook 4525s) I can't get a screen during POST that lets me change the order.  

Thanks for trying to help.  I do appreciate it.  And the suggestion from Warunendra about sudo apt-get grub is useful for the future.  But, to implement it I have to figure out how to get to the external drive's OS.

Ugh.

Mark

---

### Post by varunendra on 2013-03-20
Different BIOS versions and different OEM variations of it have different behaviour. Unless I am misunderstanding again, you are unable to get a boot device selection menu at all? I'm not surprised if so.

I have seen more than one systems where that option didn't exist at all (or I couldn't figure out how).
Some BIOS versions (mostly in laptops) are programmed in such a way that they give you that option only when an alternate boot device is detected. In that case, the hot-reboot trick may help.

In any case, if the BIOS supports booting from USB, you can permanently set it to boot first when detected. So go into the BIOS setup and see if the USB drive is listed somewhere in the Boot device list. If found, make it first boot device. The BIOS should automatically fall back to internal drive when the external one is disconnected.

---

### Post by allynm on 2013-03-20
Hi Varunendra,

When I restart the laptop and hit "esc" key I get a men.  F10 key gives me access to "Bios Setup".  When I hit F10 I get a window with 3 tabs at the top.  One of them is labeled "system configuration".  When I select this tab a menu appears and the second item is "Boot Options".  When I select that I get status information ONLY.  One of the status items is "USB device boot".  It is market as "Enabled".  This is all I get.  There is no capability I can see that allows me to change the order in which devices are searched for booting.

Now, this is all very strange.  Because until yesterday I was able to boot nicely into the external drive.  As far as I know, I did nothing to change any of the settings on this system.

Thansk for your assistance.

Mark

---

### Post by varunendra on 2013-03-20
> **allynm said:**
> When I restart the laptop and hit "esc" key I get a men.  F10 key gives me access to "Bios Setup". When I hit F10 I get a window with 3 tabs at the top.  One of them is labeled "system configuration".  When I select this tab a menu appears and the second item is "Boot Options".
....so far so good. But..
> ...When I select that I get status information ONLY.  One of the status items is "USB device boot".  It is market as "Enabled".  This is all I get.  There is no capability I can see that allows me to change the order in which devices are searched for booting.
Not sure where to go from here. The only guess I can make at this point that maybe the USB drive wasn't detected at all. What if you boot with the local drive > connect the external one > let it get detected > do a "Restart" (without powering off) > re-visit the BIOS and see if it is listed or the option to change the boot order is enabled.

May be look into user manual of the laptop for BIOS setup ?

Also, did you try a hot reboot with the drive connected ?

---

### Post by schragge on 2013-03-20
Hope [this link](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00364979&product=18703) can be of some help. Also, on some BIOSes an external USB drive gets listed as additional hard drive instead of USB device.

---

### Post by allynm on 2013-03-20
Hi Varunendra,

Good news!  It turns out that the BIOS interface was the culprit.  I had gotten to the correct window, but on the HP machine the designers did a poor job (my opinion) in designing the UI.  One has to scroll down to the bottom of the page with the arrow key.  The bottom-most entry has to be selected--it is initially dimmed and other entries are highlighted (so one assumes, at least I did, that this means that it is inoperable on this particular machine.  This assumption is incorrect.  If one highlights it by selecting it, then ADDITIONAL options become visible.  The addtional options do in fact allow you to set the boot order.  When I did this, the machine booted correctly to the external drive.

Whilst I was at it I upgraded my BIOS...so it wasn't a complete waste of time.  And this is one more problem I don't have to fix again.  Of course, there will be others....

Thanks again for your ideas and time.

Mark

---

### Post by allynm on 2013-03-20
Schragge,

My apologies for not thanking you for your link.  Thanks.  Folks like you and Varunendra make this Forum the best I have ever participated in.

Mark

---

### Post by varunendra on 2013-03-20
Good news indeed! And thanks for your kind remarks. :)
I've handled many old & new hp/compaq laptops, but never came across such a dodgy bios interface.... but then again, I learn something new everyday!

Please consider marking thread as [Solved] now. The method to do so is in my Signature's 'see how' link.

---

