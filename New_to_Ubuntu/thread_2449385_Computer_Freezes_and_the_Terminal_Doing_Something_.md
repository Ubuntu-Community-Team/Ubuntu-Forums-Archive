---
title: "Computer Freezes and the Terminal Doing Something in Background"
date: 2020-08-25
forum: New to Ubuntu
---

### Post by printna on 2020-08-25
Twice now I have had my computer freeze up since installing Ubuntu and when I open the console with ctrl, alt, f5 I get this going on endlessly. The only things I was running at the time were Chromium, the terminal, and LibreOffice. The attached files contain my system info and a gif of what the console is doing.

---

### Post by simon-webb on 2021-01-19
Hi Printna.

Unfortunately the photo of your console is largely illegible to me (it looks as though it must have been scrolling at the time, and the camera has blurred two frames of screen output together into one). What I can see though are some messages related to your wireless networking subsystem...so it's possible (though by no means certain) that the freezes you're experiencing are related to your WiFi hardware and your (kernel's) drivers for that hardware. Even if this is indeed the case, knowing this may not be very helpful for you (unless you happen to be using a USB WiFi dongle that can easily be swapped for another): it would really be good to see precisely what those messages are...they're just too blurry in the photo. Could you try poking around in the logs (files under /var/log) or maybe directing kernel messages to a file (dmesg > dmesg.txt) so that you can examine them...or are the other ttys locked up too (so it's not possible to log in via CTRL-ALT-F3 and have a look from there)?

Another possibility is that the scrolling console on tty5 might respond to CTRL-S or the "scr lk" key on your keyboard, either of which should (ideally, with a working system) lock the scrolling so that you're able to read it (or take a clear photo of it). The kernel did respond to CTRL-ALT-F5 so it's receiving keyboard input and might respect CTRL-S too. Beyond that, I can't offer much help as I can't really see what those messages are (not that there's any guarantee they'd identify the problem, but I think you're right that they're probably related...if the kernel's spewing continual messages about the networking hardware to the console, that sounds like the kind of thing that could lock up your system). I hope the suggestion that it may be WiFi-related helps you to narrow down the possibilities.

---

### Post by wildmanne39 on 2021-01-19
Old thread closed, the OP has not logged in since the thread was created.

---

