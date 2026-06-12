---
title: "Writing to /dev/ttys0 (JAVA or C)"
date: 2009-03-28
forum: Programming Talk
---

### Post by Xeli on 2009-03-28
Hello!

I'm quite new to Linux and programming as a whole so please bear with me ;)

For a school project (noooo don't run away just yet i'm not asking you to make my homework :P) i need to send and recive bytes to a cardreader connected to a serialport (well actually usb port, with usb-to-serial connector)

Since we're writing it in JAVA we've been advised to use javax.comm from sun, well that's all good and fun, but sun seems to have abandoned it, plus never really had good support for linux anyway. I've also tried rxtx, but that doesn't really do well with x86-64 systems, so i've decided to write a JAVA or C program (i'd prefer C cause I'm worse at C than JAVA :))

So the question arrises: How to write to a serial port in Linux?

I've heard that everything in linux is a file, so the 'devices' in /dev/ are also files then? And could i just write to them as if it were files?

Any help would be greatly appreciated, thanks! :)

-Richard

---

### Post by moma on 2009-03-28
Hello,

You are right. Device drivers are just special files.
Everything is a file in Unix/Linux. 

(my quick answer ;-)

Study this ([http://ubuntuforums.org/showthread.php?t=274167](http://ubuntuforums.org/showthread.php?t=274167) ) thread and follow the link to the opportunities page.

Google will also give you a couple of good examples. Check ["simple serial port c linux"]("http://www.google.com/search?q=simple+serial+port+c+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=pub-2070091971271392")

---

### Post by The Cog on 2009-03-28
It's /dev/ttyS0 (with a capital S). You need to use the command stty to configure the speed, parity etc. You could just make up the text command lines and Runtime.getRuntime().exec(command). But I have used javax.comm in the past and it did work.

---

