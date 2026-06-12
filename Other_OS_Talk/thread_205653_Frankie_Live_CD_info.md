---
title: "Frankie Live CD info"
date: 2006-06-28
forum: Other OS Talk
---

### Post by NewDisciple on 2006-06-28
Just finished downloading Frankie Linux, burned cd. etc.  It booted up just fine and looked pretty nice.  One major problem, couldn't use my mouse or my touchpad nor could I navigate with my keyboard.  I went to this distro homepage and looked in the troubleshooting guide and this is what the author had to say about this problem:
 How to use serial (COM) mouse in Frankie Linux?
Serial mouse can't be autodetected and currently I don't know how to configure it automatically. If you have a serial mouse connected to your computer, you will need to use one of the following lines to enable it.

ln -sf /dev/tts/0 /dev/mouse
or
ln -sf /dev/ttyS0 /dev/mouse

Use /dev/tts/0 (or /dev/ttyS0) for COM1, /dev/tts/1 (or /dev/ttyS1) for COM2, etc.

Kind of hard to do when you are totally incapacitated.  So much for using this one on a laptop.  I have been playing with live cd's for several weeks now.  The best two I have found so far are puppy and slax.  I should mention: Dell E1705, dual core, using i686.

---

### Post by RAV TUX on 2006-06-28
Great! moved to "Other OS" forum
[URL="http://www.ubuntuforums.org/forumdisplay.php?f=147"]
[/URL]

---

### Post by xinematik on 2006-11-24
Another help, it worked for me to install Ubuntu Drapper with a serial mouse

Press CTRL ALT F1 to go to a terminal.
then type

ln -sf /dev/ttyS0 /dev/input/mice 

That was the only way to make work the mouse in the Drapper Live CD, the others didnt worked.

---

