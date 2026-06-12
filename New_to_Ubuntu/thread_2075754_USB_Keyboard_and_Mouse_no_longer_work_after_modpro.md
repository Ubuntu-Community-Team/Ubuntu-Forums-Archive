---
title: "USB Keyboard and Mouse no longer work after modprobe change"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by zlapidus on 2012-10-24
Hello, I've been using Kubuntu 12.04 since April with great results. I've been using the Apple USB Slim Keyboard that I also use with my Mac laptop, and it's worked fine, except for some annoyances, like needing to also hold down the fn key to press ALT-F2. On the usb mac keyboards, the fkeys have other functions, like media control, brightness, volume, etc, and using their normal f-key functionality can only be unlocked while holding the "fn" key.

So, I followed this advice I found in stackoverflow.org's wiki, and learned a valuable lesson about running terminal commands you don't understand:

> Out of the box, the Apple Slim Aluminum Keyboard requires you to hit  the "fn" key to get access to the F-keys (otherwise they send in  scancodes for their Apple-assigned operation such as brightness, expose,  dashboard, etc.)  To swap this so that you can simply hit the key and  get the F-key without having to hold down "fn" you have to edit /etc/modprobe.d/options and add: 
 # Apple keyboard "fn" key fix 
options hid pb_fnmode=2 
# After changing this, run: 
# sudo update-initramfs -u -v -k `uname -r`  

You then need to rebuild the initrd with: sudo update-initramfs -u -v -k `uname -r` 


I did this. There was no options file, so I created one. When I restarted, I could not use the keyboard and mouse at all, and couldn't even log in. I couldn't even use my USB keyboard in the recovery mode -- it worked in GRUB but stopped responding as soon as I left GRUB.

Thankfully I had a  ps2 keyboard on hand which worked, and thankfully had a terminal bound to a key command so I could log into a session, open a terminal, and try to repair things. What I did next was run "sudo rm /etc/modprobe.d/options" and then ran the "sudo update-initramfs -u -v -k `uname -r`" command again. My hope was that I would undo whatever I did. When I restarted, there was no change -- the USB keyboard and mouse still didn't work.

In Grub, I started one of the old kernel versions but still had trouble -- I couldn't use the usb mouse or keyboard in kdm, and couldn't enter my password to log-in. If I entered the password on my PS2 keyboard, I could log in, and strangely enough, when I actually got logged in, the usb keyboard and mouse would start working again. 

Unfortunately, when I tried this on the current, latest version I had installed, even if I entered the password on my ps2 keyboard, the usb keyboard and mouse do not work again. Because of this, I'm using my computer with one of the previous versions of the kernel that you can select in Grub.

I would appreciate any help here -- even though a new version of Kubuntu just came out, I'd prefer not to have to back up and reinstall, so any help would be greatly appreciated. If anybody could explain what I did, also, that would really help -- I'd just like to know a little about how things went wrong.

Thanks a lot!

---

### Post by NikTh on 2012-10-24
Hi , 

those commands you ran , are deprecated in Ubuntu 12.04 . If you want to add a configuration file inside /etc/modprobe.d/ it has to end with a .conf eg: options.conf , or the system is not aware of. 

The rebuilding of initramfs has nothing to do with this (I believe). 
So something else is going on. 

For start I suggest to look at the BIOS and search for an option like "USB legacy" support. Enable it and try again with the USB-keyboard. 

Thanks

---

### Post by zlapidus on 2012-10-24
Thanks so much for writing me back. That explanation is interesting.

You know, I had a weird problem last week where it was as if all my USB devices stopped responding -- keyboard and mouse, wireless, everything went out. No matter what I plugged in or unplugged, moved to a new port, or anything else, I couldn't get my usb wireless dongle or the keyboard or mouse to turn on. This only really happened once in the whole time I'd been using it.

You got me thinking that perhaps these two problem might be related. Before I messed with the BIOS, I noticed that suddenly my wireless dongle had stopped working, and I had to plug it into a new USB port. I looked at what was plugged into the USB ports on the back of my computer. Plugged into one port is a USB hard drive that I had physically powered off. I unplugged the device, which wasn't powered on anyways, restarted, and voila -- usb keyboard and mouse are working again!

I've fully upgraded my motherboard bios -- is there something else I might mess with to keep this weird USB behavior from happening? Is something having to do with the USB host crashing? I just don't know what happened that one time where it seemed like everything gave up. Does any of this make sense...or is this Ubuntu specific? I've never really had strange behavior like this when I was running Windows XP, 7, or Crunchbang on here?

Thanks a lot!

---

### Post by NikTh on 2012-10-25
Hi,

as you describe the history of the problem, the only thing I can think is a BIOS related problem 
OR 
USB hardware problem (motherboard I mean) .

The fact that you haven't this problem in the past (with XP or 7) has nothing to do. Maybe just you were lucky (or unlucky) to spot the problem then. 

I suggest to watch it and if was a BIOS problem , probably now solved. (I wish). 

Thanks

---

