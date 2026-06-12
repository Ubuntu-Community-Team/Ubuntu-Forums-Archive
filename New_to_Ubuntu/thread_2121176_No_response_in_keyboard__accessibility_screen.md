---
title: "No response in keyboard / accessibility screen"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by LinkeLoutje on 2013-03-01
Hey Guys, I've dusted off an old pc and installed Linux through the windows installer wich is working fine except that it's awfully slow. (slower than windows...) I figured it would be best to format a partition to ext4 and then run linux? Thus I created a bootable USB with the latest Ubuntu image (12.10)

When Trying to boot from that USB I'm stuck at the following screen. The info on the page I found the picture on tells me I should just press any key and select my language, though there is no response when doing so except some sounds from the speaker connected to the motherboard. The keyboard works fine in windows, the wubi installed linux and bios, so that shouldn't be a problem right?

What could I do to move past this screen? 

[IMG]http://blog.siliconforks.com/wp-content/uploads/2010/05/ubuntu-out-of-range.png[/IMG]

---

### Post by audiomick on 2013-03-01
Are you sure the USB installer is good? Can you boot from it on another machine? 

It has bee a few months since I ran an install, but, if I remember correctly, what should happen at that screen is

if you do nothing: it will progress to a screen where you can choose a language and then choose "install" or "try ubuntu without changing the computer".

if you press any key: you can choose a language and then you come to the menu which allows, alonside "install" and "try ubuntu", things like checking the installer and running memtest.

---

### Post by LinkeLoutje on 2013-03-02
It does work at my laptop and I have tried creating the bootable USB again. Ctrl+alt+del does restart the PC. 

BTW I've been looking around but can't seem to find any evidence that I would benefit from another file system. In that case I'd better try an k or l Ubuntu distribution?

---

### Post by grahammechanical on 2013-03-02
You will find that all the flavours of Ubuntu use the same installer/live session. Some give us that purple screen. Some give us the choose a language text screen, And some give a different coloured screen. Try the suggetion given to hit the enter screen as soon as that purple screen comes up.

If you get past the choose the language screen and select either to Try Ubuntu or Install Ubuntu and the process stops after that point, then start again at the first purple screen and press Enter twice (not in quick succession) to get the TRY - Install screen and then press F6. From the drop-down menu select one or two of the options and fix the selection by pressing Enter. Then press Esc to get back to the Try - Install screen and go from there. Two F6 options to try are acpi=off and nomodeset. But you may need to work your way through them.

Regards.

---

### Post by LinkeLoutje on 2013-03-03
I've noticed indeed I get a similar screen for other distributions. However I'm not able to get past that particular screen. When pressing Enter the motherboard does make a sound over the speaker, but nothing happens unfortunately. I suppose the keyboard should be the problem though anyway?

---

