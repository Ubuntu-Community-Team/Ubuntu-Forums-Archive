---
title: "BRAND new to ubuntu/Linux..."
date: 2012-03-05
forum: New to Ubuntu
---

### Post by mzimmers on 2012-03-05
...I just booted from a thumb drive, using the directions on ubuntu's site. Very simple, very impressive...but, my wireless mouse doesn't work. I know the keyboard works, because it accepted my "Enter" command to boot from the flash drive.

Keyboard/mouse is a Logitech Dinovo Edge.

Any suggestions? I'm really encouraged by what I see so far, but...I do need my mouse to work!

---

### Post by mastablasta on 2012-03-05
since i dont' know which verison you are using (10.04-11.04): [http://awesomelinux.blogspot.com/2010/05/ubuntu-1004-lucid-logitech-dinovo-edge.html](http://awesomelinux.blogspot.com/2010/05/ubuntu-1004-lucid-logitech-dinovo-edge.html)
 
verison 11.10: [http://awesomelinux.blogspot.com/2011/10/ubuntu-logitech-dinovo-edge-bluetooth.html](http://awesomelinux.blogspot.com/2011/10/ubuntu-logitech-dinovo-edge-bluetooth.html)

---

### Post by mzimmers on 2012-03-05
Thanks for the quick reply. I should have mentioned, I'm using 11.10. 

If I understand the fix in that link, I need to edit a file in a /lib directory. But, on my flash drive, there's no such directory at the root level (as least not one that's visible).

Also, the problem he describes seems a little different from mine, but I'm willing to give it a try if I can find the file to edit.

Thank you for responding.

---

### Post by mastablasta on 2012-03-05
hmm yes you are using it live. Well you might want to try and install it next to your current os. Plenty times things are resolved on install (when you get these config files). it could also be you need to turn it on somwhere. I have no experience with these bluetooth devices.

---

### Post by pootan on 2012-03-05
I had a problem very similar to yours with my old wireless mouse and keyboard and Linux. The problem was fixed by enabling legacy usb mouse and legacy usb keyboard in the BIOS options. You might have a quick look there and  see if that's the issue.

---

### Post by Harry.k on 2012-03-05
For the installation procedure, try using xkbset. After installing, try the method in the above posts. Xkbset  is similar to mouse keys. Dont let small bumps knock you off. Once you get there, its totally worth it

---

### Post by mzimmers on 2012-03-05
Thanks for the suggestions, guys.

Pootan: I'm not sure this is a BIOS issue, since my keyboard/mouse works under Windows 7 with the same BIOS settings.

Harry: is an installation package available for xkbset somewhere?


mastablasta: I might install it, though my preference is to at least play with it a little before I do so.

Thanks again...

---

### Post by mastablasta on 2012-03-05
> **mzimmers said:**
>  
mastablasta: I might install it, though my preference is to at least play with it a little before I do so.
 
 
wubi install is ment for that (it install in a large virtual drive). you will be able to choose it on boot and also uninstall it from windows like any other pogramme.

---

### Post by pootan on 2012-03-05
> **mzimmers said:**
> 
Pootan: I'm not sure this is a BIOS issue, since my keyboard/mouse works under Windows 7 with the same BIOS settings.


Yes that was the case for me as well. Windows XP had the drivers available by default and so did the full  install of Ubuntu but the Live CD did not and was relying on Bios settings.

---

### Post by mzimmers on 2012-03-05
It turns out that Legacy USB support was already enabled.

I also chose the install option, but that too requires a mouse that works.

It looks like I'll have to plug in a wired keyboard to make this work. Hopefully, once it's installed, I can go back to my DiNovo.

Or, I could try the xkbset that Harry mentioned. I found an installation program here:

[http://abhijeetmaharana.com/blog/2007/08/31/mousekeys-on-ubuntu/]("http://abhijeetmaharana.com/blog/2007/08/31/mousekeys-on-ubuntu/")

But, how do I get started? Without keys, I don't know how to get to a shell to execute the commands on the page above.

Thanks for any suggestions.

---

### Post by mzimmers on 2012-03-07
OK, I dug up an old wired keyboard. That enabled me to do the installation (successfully, according to the messages. But, on system restart, I thought I was going to get a choice of which system (Windows or Ubuntu) to boot. Instead, it goes straight to Windows. Can someone tell me what I need to do about this?

Thanks...from the glimpse of Ubuntu I've seen, I really hope I can go forward with it.

---

### Post by mastablasta on 2012-03-07
how did you install it eventually? Did you use Wubi or did you install on separate partition side by side?
 
if Ubuntu install was succesfull windows shouldn't boot, because Linux is the first system in the boot choice (unless you change that).

---

### Post by mzimmers on 2012-03-07
I chose the side-by-side partition method. The messages said it was successful.

---

### Post by mastablasta on 2012-03-07
ok so you either instaleld it onto separate disk. or you cretaed a partition and installed it there. but somewhere during the process you installed GRUB in the wrong place. 
 
or you can try to get that GRUB menu (the bootloader where you choose the OS) to show up by holding shift key on boot.
 
hard to say what went wrong running boot info script might help (booting form live cd and then following these instructions: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
might be a bit annoying for you if you only have a keyboard present.
 
but something (probably GRUB) definatelly got installed on the wrong place. that is my suspicion.

---

### Post by mzimmers on 2012-03-07
I can try re-installing from a DVD image. Should I do something to "wipe out" the old installation, and any partitions it may have created?

If the answer is "yes," I could use some direction in that as well. (I'm not only new to Linux, but to Windows -- I'm a Mac guy.)

Thanks.

EDIT: I tried holding the shift key down; that didn't do anything. My boot options are activated by F11, but that only seems to prioritize what devices are prioritized.

EDIT 2: I'm trying to follow the directions on the sourceforge page you linked. Where is the applications directory? My poking around, and using search doesn't reveal it for me. Thanks.

---

### Post by mzimmers on 2012-03-09
I'm still playing with this off and on. I attempted to do an install, but something went wrong, the screen went black and a bunch of very small white print appeared. 

So, this morning, I booted from the DVD again, and now, my Internet connection (for Ubuntu) is down, so the installer is unhappy. The HW is connected to my router by Ethernet, and Windows 7 gets on the network OK...anything I should be looking for here?

I'd prefer not to go any further until I get this resolved. Thanks...

---

### Post by Erenith on 2012-03-09
> 
EDIT 2: I'm trying to follow the directions on the sourceforge page you  linked. Where is the applications directory? My poking around, and using  search doesn't reveal it for me. Thanks.

Instead of searching for applications, you can use the shortcut Ctrl + Alt + T to open the terminal and proceed from there

---

### Post by mzimmers on 2012-03-09
That's good to know; thanks, Erenith.

My networking issue seems to have self-corrected as well. I restarted, and this time I got a boot menu, offering me a few choices of Ubuntu (one of which said something about recovery), and one for Windows. I chose the recovery one, and it ran and when it booted, my wired network was magically working.

When it booted, the Update Manager said I needed 377 updates, so it's churning through that. Once that's taken care of, and if restarting continues to give me no networking troubles, then I'd like to see about getting my wireless keyboard working. I'll report back later.

Thanks again.

---

### Post by mzimmers on 2012-03-09
My updates all seemed to download and install OK. It did seem to undo the patch to the file that was suggested at the top of this thread, though, so I re-edited the file, and now the keyboard is working. 

That's the end of this thread, I guess. Thanks for all the help, everyone. Do I do something to mark this solved or answered?

---

