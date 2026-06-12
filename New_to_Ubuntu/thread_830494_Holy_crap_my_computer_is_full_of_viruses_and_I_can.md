---
title: "Holy crap my computer is full of viruses and I can't boot from CD. HELP"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by papuccino1 on 2008-06-15
I want to install Ubuntu and I can't even open up the BIOS menu to select "Boot from CD".

I think a virus cause this. 

Options?

How can I make my computer boot from the Ubuntu CD and COMPLETELY format my hard drive.:guitar:

---

### Post by ChameleonDave on 2008-06-15
> **papuccino1 said:**
> I want to install Ubuntu and I can't even open up the BIOS menu to select "Boot from CD".

I think a virus [has] cause[d] this. 


I highly doubt that.  It would have to be a very good virus indeed to affect the BIOS.

Have you been able to access the BIOS before?  Have you booted from other CDs?  Have you tried pressing various keys when you first turn on your PC (Delete, Insert, all the Function keys...)?

---

### Post by iaculallad on 2008-06-15
Try to "short" your motherboard's setting (Adjust the pin jumper placement) to reset your BIOS to default values and retry accessing your BIOS settings.

---

### Post by powerpleb on 2008-06-15
Try hitting F12 (it may be different on your machine) at the BIOS screen and choosing to boot from a CD

---

### Post by papuccino1 on 2008-06-15
> **iaculallad said:**
> Try to "short" your motherboard's setting (Adjust the pin jumper placement) to reset your BIOS to default values and retry accessing your BIOS settings.

Sounds to risky, and I have no idea what you mean by adjusting the pin. :S I'd rather not try something physical.

To the second poster:

Yes, I have installed OS's before and I have accessed the menu as well.

What used to happen was I rastarted the PC > a boot screen would come up that said "press DEL to access BIOS menu".

But now, I restart and nothing comes up on screen (the monitor LED remains yellow) and after about 20 seconds the Windows logon screen comes up.

I don't even SEE the BIOS screen anymore.

Should I be concerned?

---

### Post by tamoneya on 2008-06-15
it is possible in the bios to make the "enter setup" prompt not show up.  Just hit delete anyways and you should get into the bios.

---

### Post by JoshuaRL on 2008-06-15
Are you using a USB or Wireless keyboard?  That might be your problem, that BIOS doesn't recognise it.  If you have any old keyboards lying around, especially if they're PS2, try them out.

---

### Post by ibuclaw on 2008-06-15
9 times out of 10 it will either be one of the following keys:
[LIST]
[*]**F2**
[/LIST]
[LIST]
[*]**F8**
[/LIST]
[LIST]
[*]**Del**
[/LIST]
Be sure to hold one of them down when you boot up.

Also, make sure you are using a PS2 Keyboard.

Regards
Iain

---

### Post by louieb on 2008-06-15
Please post the type and age of the computer.
May be something simple and cheep hardware related like the CMOS battery (Does it keep time?)   You may have to open the case sometimes theres no way around it.  
 
Have you been running a virus scanner?   
Try pressing the delete key while it booting maybe the BIOS setting screen will come up.
> 
Also, make sure you are using a PS2 Keyboard. +1

---

### Post by papuccino1 on 2008-06-15
1. Using a PS2 keyboard. CHECK
2. Pressed F2, F8, DEL. CHECK.
3. Bought the computer brand new parts two years ago. CHECK.

What could it be????

One thing I've noticed, when I don't press F2, F8 or DEL, Windows boots fine. But when I press one of those keys at boot, my PC freezes. 

Does my computer have cancer?


Edit:

Can I just FORMAT MY C DRIVE and hope that erases the virus?

---

### Post by JoshuaRL on 2008-06-15
I sincerely doubt that is the issue.  BIOS settings and the hard drive are separate.  Tell you what, try out louieb's idea:

Turn off the computer, take out the CMOS battery for a couple minutes, replace it, and then restart.  See if that helps you.

---

### Post by subaruwrc01 on 2008-06-15
I hardly doubt it's a virus. Besides, the biggest virus on there is Windows.

It appears something has damaged the BIOS.  If this is true, reformatting the hard disk won't help since the BIOS is not located on the hard disk.

Open the computer case and see if there are any signs of damage on the key components.

---

### Post by papuccino1 on 2008-06-15
> **JoshuaRL said:**
> I sincerely doubt that is the issue.  BIOS settings and the hard drive are separate.  Tell you what, try out louieb's idea:

Turn off the computer, take out the CMOS battery for a couple minutes, replace it, and then restart.  See if that helps you.


Where do I find this CMOS battery, on what component? (Picture please)

I remove it for three minutes and then place it back into it's slot? You think would fix it?

---

### Post by ChameleonDave on 2008-06-15
If your BIOS firmware is damaged, and yet you are able to boot into an operating system, then you are lucky.

Boot up, and go to the manufacturer's website.  Follow their instructions for downloading and installing the latest firmware for your motherboard.

Otherwise, it may be possible to force the motherboard to prioritise the CD drive over the hard drive by physically moving the IDE cables connecting them around.

---

### Post by papuccino1 on 2008-06-15
So my firmware may be damaged, but I can still go on my OS.

I have no clue what to do now.

---

### Post by subaruwrc01 on 2008-06-15
> **papuccino1 said:**
> Where do I find this CMOS battery, on what component? (Picture please)

I remove it for three minutes and then place it back into it's slot? You think would fix it?

[http://www.sacada2.net/cmos-battery-cmos-battery-replacement/](http://www.sacada2.net/cmos-battery-cmos-battery-replacement/)

---

### Post by subaruwrc01 on 2008-06-15
> **papuccino1 said:**
> So my firmware may be damaged, but I can still go on my OS.

I have no clue what to do now.

It is probably a good idea to take your computer to a computer technician and let them handle it.  Better safe than sorry.

---

### Post by papuccino1 on 2008-06-15
I found this tool in my Motherboard driver CD. 

Can someone give me a download link for the firmware upgrade thingy.

Thanks

[img]http://i30.tinypic.com/2ij1aj8.png[/img]

---

### Post by Raccoon1400 on 2008-06-15
Can't enter bios menu?
using a machine a couple years old? usb keyboard? try using a ps/2 adapter.
My p4 won't support usb in bios.

---

### Post by Kronie on 2008-06-15
first thing i would do is reset the bios by removing the battery? it wont affect your windows or anything, just reset bios settings. 
and if that wont work, THEN i would look for firmware update..
to find updates just google "award bios firmware update"

---

### Post by papuccino1 on 2008-06-15
Need advice on how to remove electricity from my body before touching my computer parts.

---

### Post by sdennie on 2008-06-15
> **papuccino1 said:**
> Need advice on how to remove electricity from my body before touching my computer parts.

Touch the power supply first.  ;)

---

### Post by cariboo on 2008-06-16
Make sure your power supply is still plugged in but turned off touch the power supply then pull the power cord.

Jim

---

### Post by Barriehie on 2008-06-16
You can probably pull some of the RAM out and it will default to booting into the BIOS setup.  That's what I've had to do years ago when I forgot a password... :confused:

Barrie

---

### Post by kalesh7 on 2008-06-16
Do you by some chance have a graphic card installed?
if so and your monitor is connected to it, connect the monitor to the graphics port on motherboard.(or if its connected to motherboard and you have card installed connect to card)

I think that the bois bootup is showing on one device and windows on another, so when you don't press anything it just goes though to windows, but when you do press it enters setup and waits for you, outputting display to another device.

---

### Post by nowshining on 2008-06-16
are you for chance trying to hack a computer?

if not

u may have to re-flash the BIOS - get the latest BIOS version from the Manufacturers website and make sure it's for ur Specific Computer or else u will have to get a new motherboard if u use the wrong BIOS.

---

### Post by hyper_ch on 2008-06-16
> **subaruwrc01 said:**
> Besides, the biggest virus on there is Windows.
I veto here. Viruses are small, smart, efficiently programmed, sleek... windows is quite the opposite...

Anyway, common keys to enter the bios are:
Esc, Enter, Space, Backspace, F1, F2, F8, F10, F12.... maybe some more, but that's those I have experienced so far.

---

### Post by bigken on 2008-06-16
personally before you flash the bios I would short the cmos to restore it to a factory default if you look at your cmos battery you should see two pins with a jumper sitting on one pin place the jumper over both pins this will reset the cmos then replace the pin to its origional place

---

### Post by JoshuaRL on 2008-06-16
> **hyper_ch said:**
> I veto here. Viruses are small, smart, efficiently programmed, sleek... windows is quite the opposite...

Heh, nice.  You're right, Windows is not a virus.  Windows is the host, and is for sure bloatware.

---

### Post by housam on 2008-06-16
> **JoshuaRL said:**
> Heh, nice.  You're right, Windows is not a virus.  Windows is the host, and is for sure bloatware.

No, windows is the most efficient virus detecting tool.

---

### Post by Joeb454 on 2008-06-16
I think this has got a little off-topic :)

@ OP - Have you had any luck getting the CD to boot

---

### Post by forestpixie on 2008-06-16
> **Joeb454 said:**
> I think this has got a little off-topic :)

@ OP - Have you had any luck getting the CD to boot

It's the batman title

---

### Post by Joeb454 on 2008-06-16
I guess it is

Just insert "Batman" in between "crap" and "my" and it could well be straight from a modern day batman film :)

---

### Post by Sef on 2008-06-16
> Can I just FORMAT MY C DRIVE and hope that erases the virus?

That will erase the virus (if it is on the C drive), the operating system, and any data on that partition.

**Back up** your data (even if it is on another partition) before reformatting.

---

### Post by Gannon8 on 2008-06-16
When the computer boots up (when you see the screen with your computer's or motherboard's manufacturer on it) look for some type of key on the menu. Next time you boot up, press that key, and look for an option that says something like "Boot order" or "Boot configuration" and make sure that "CD Drive" or whatever it says is above something like "Internal HDD." Then press escape, click "Save Changes and Exit" and boot.

---

### Post by bigken on 2008-06-16
look its not a virus you need to reset your bios by using the jumper on the motherboard :mad:

---

### Post by papuccino1 on 2008-06-16
Hello guys. Removing the CMOS and placing it back did the trick.

Who knew, huh? :S

Thank you all for the support and answers.

---

### Post by JoshuaRL on 2008-06-16
> **papuccino1 said:**
> Hello guys. Removing the CMOS and placing it back did the trick.

Who knew, huh? :S

Thank you all for the support and answers.

Glad to hear it!  You can mark this thread as solved by going up to the top and looking in the Thread Tools menu.  And don't forget to thank those that helped you.

Ubuntu Forums FTW!

---

