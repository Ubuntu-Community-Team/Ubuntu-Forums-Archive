---
title: "Big trouble with little usb drive install - mbr screwy"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Matrimforever on 2008-08-12
Hello all,

Okay(deep breath), I tried installing to a usb flash drive, but i must have installed to the mbr because my drive is no longer plugged in and my hard drive was disconnected. So I can't do anything when Ubuntu loads as my keyboard and mouse are not recognized, i figure cuz there arent any drivers on the MBR. Ive tried to do bootrec and fixmbr to no avail(from the Vista DVD). I don't get why its still there. I mean I thought the mbr was too small for anything like an install.

-ps ive since reformatted the drive and stuck it back in. Now when linux loads it gets to the windowed screen and shows the usb drive, but i cant do anything(no keyboard/mouse).

When i try to reinstall again, i still get no keyboard/mouse. What the heck?
Please someone help me figure out what I've done!Thanks!


ps. Please if this post makes no sense, let me know and i'll revise it.

---

### Post by carlinuxlearner on 2008-08-12
If you could please explain your self better I'm sure I can help.

"I tried installing to a usb flash drive" Ubuntu 8.04?

"but i must have installed to the mbr because my drive is no longer plugged in and my hard drive was disconnected." This makes no sense. What is the problem? Your drive is no longer plugged in? (So in that case why would anything run?)

C@RL

---

### Post by Matrimforever on 2008-08-12
Hehe, okay sorry about that.

As per instruction to a flash drive, I disconnected the hard drive so as to not install over it accidentally. I installed the latest version of Ubuntu on the usb drive. Rebooted. And the boot hung where it says Searching for boot image on USB(or something)...OK. So I thought I would try reinstalling on the flash drive(maybe I didn't get a clean install). I booted from the install disc and selected 'install'. It gets to the language selection screen, I select English and it goes to the Install window. Here, keyboard and mouse don't work(i took both out and plugged them back in). So I wonder what I did. I take the flash drive out, and reboot. This time Ubuntu does the same thing but loads to a windowed screen(like the installation worked). Still can't use either keyb/mouse.

Take the install disc out next time, and it says Searching for Boot record from USB RMD-FDD..OK. Where it hangs again...
Actually this time around it shows Disk Error / Press any key to restart. Hope this provides some better info. 

ps. the keyb/mouse worked fine throughout the first install, its afterwards I can't use 'em.

---

### Post by carlinuxlearner on 2008-08-12
OK, try this and let me know what happens.

#1
Disconnect your HD.
#2
Unplug your flashdrive. 
#3
Insert the Ubuntu install disk into your CD/DVD ROM (whatever it is).
#4
Turn your computer on, and see if it boots, if it does, see if the keyboard and mouse work, if they do, let me know, and we can move on from here.

C@RL

---

### Post by Matrimforever on 2008-08-12
ok.
it gets to the installation screen. After I select Install Ubuntu, it no longer works.

---

### Post by Matrimforever on 2008-08-12
Its stuck at the Welcome screen, of the install.
No keyboard, no mouse.

ps. the weird part is, they both worked before, and with this install, i dont see why they
wouldn't now :(

---

### Post by carlinuxlearner on 2008-08-12
What do you mean by the "install screen"?

At the boot screen did you select to install it?
Or did you click the install icon after just booting it up in the "try Ubuntu" mode? (or whatever it is called)

C@RL

---

### Post by Matrimforever on 2008-08-13
> **Matrimforever said:**
> After I select Install Ubuntu, it no longer works.

So, I selected Install. The install screen is the window that loads up with the next choices.

---

### Post by Matrimforever on 2008-08-13
I just tried again for giggles, and THIS time it booted into the desktop, like a finished install. No hard drive, no flash drive installed, just booted from the CD. Now how is that possible? :)

ps. and yes still now keyboard/mouse functionality.

---

### Post by falcon61102 on 2008-08-13
Sounds like you booted into the LiveCD version which is run off of the disc.  It may be that you have a bad disc, have you tried running Check CD from the boot menu of the CD?  

If you can't select that because your keyboard doesn't work on that menu, have you tried either entering your BIOS or another install disk, possibly a windows disk?

---

### Post by Matrimforever on 2008-08-13
> **falcon61102 said:**
> Sounds like you booted into the LiveCD version which is run off of the disc.  It may be that you have a bad disc, have you tried running Check CD from the boot menu of the CD?  

If you can't select that because your keyboard doesn't work on that menu, have you tried either entering your BIOS or another install disk, possibly a windows disk?

I ran the CheckCD utility and it passed. The keyboard works fine until the LiveCD thing is loaded.

ps. That must be what it is doing, it boots into LiveCD, it only does that about half the time, the other half it goes to the installation screen window.

---

### Post by falcon61102 on 2008-08-13
Are your keyboard and mouse USB or PS2 Serial connections?  It sounds to me as if your hardware isn't loading correctly when the kernal loads.

---

### Post by Matrimforever on 2008-08-13
Well they are ps2(the round connector), but they worked just fine throughout the initial installation(see above). And work until after I select 'Intall Ubuntu'.

Also, how is it booting into desktop with no hard drive or usb connected?

---

### Post by falcon61102 on 2008-08-13
It's called a LiveCD, and it's called that because you can run the operating system directly from the CD.  It's a way you can try out the OS and use it as a recovery system when needed.

---

### Post by Matrimforever on 2008-08-13
Hmm okay, that makes sense, but where do I go from here? Why would keyb/mouse work first time, then not after?

---

### Post by falcon61102 on 2008-08-13
When you boot from the CD, after selecting which language you want, try hitting F3 which will allow you to select the keyboard layout.  Select your keyboard layout, default is US and then select "Try Ubuntu without making any changes to your computer," the top link.  See if that works.

---

### Post by Matrimforever on 2008-08-13
Or, for that matter, why would it boot to a full desktop instead of the install window after I selected install? :confused:


ps. i'll try that, thanks for the suggestion.

---

### Post by Matrimforever on 2008-08-13
Nope, didn't work. I've tried a 2nd CD to no avail too. I'm getting to give up on flash drive linux :(.

---

### Post by falcon61102 on 2008-08-13
That's really weird.  If you want to experiment further, after selecting your language, hit F6 to get further options with booting.  There are four options and you can try using those.  Also, do any of the keys work when you boot the OS?  Try hitting CTRL+ALT+BACKSPACE.  That will reload the GNOME.  See if those work.  Also, you could try CTRL+ALT+NUM LOCK; that will switch between the keypad acting as the mouse or a keypad.

---

### Post by Matrimforever on 2008-08-13
> **falcon61102 said:**
> do any of the keys work when you boot the OS?  Try hitting CTRL+ALT+BACKSPACE.  That will reload the GNOME.  See if those work.  Also, you could try CTRL+ALT+NUM LOCK; that will switch between the keypad acting as the mouse or a keypad.

Thanks for the suggestions so far, really good stuff, i just wished they worked. None of the keyboard ones worked simply because it doesn't function. :(

I dont understand why it would boot the OS, when I installed it on the jump drive originally?

---

### Post by Matrimforever on 2008-08-13
Does it have anything to do with the Windows MBR you think?

---

### Post by Matrimforever on 2008-08-13
UM...
Hehe, well i tried a usb mouse for giggles too, and guess what? The mouse works! OMG, you've got to be kidding, so I'm hoping I have a usb/ps2 adapter laying around here somewhere for my keyboard...


This leaves the question hanging out there...why did the ps2 work, and then not work? Hmm...

---

### Post by falcon61102 on 2008-08-13
> **Matrimforever said:**
> I dont understand why it would boot the OS, when I installed it on the jump drive originally?

What exactly do you mean by that?

---

### Post by carlinuxlearner on 2008-08-14
@ falcon61102

He's still lost as to how a live CD works. That all that question is.

@ Matrimforever

       I can not explain why the mouse and keyboard worked once and never again. But I can guaritee it has nothing to do with the windows MBR.

       A "Live CD" simply has the whole OS installed on it, and it's configured to detect all hardware each time it boots up so it can run on just about anything. It not a crazy concept, it's just like running a OS off your Hard drive (it loads the data off the drive and runs it), only all data is loaded off the CD.

C@RL

---

