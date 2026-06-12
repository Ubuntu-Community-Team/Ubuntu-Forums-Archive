---
title: "Black screen on Ubuntu 16.04 Live CD."
date: 2016-10-22
forum: New to Ubuntu
---

### Post by OctaVive on 2016-10-22
So I want to dual boot Windows 10 and Ubuntu 16.04 on an UEFI system. So I come to the GRUB screen, I press "Try Ubuntu", then I see the Ubuntu logo and it loads up, then the screen goes black.

Here's what I tried so far:

- Disabling Secure Boot
- Disabling Fast boot
- Disabling Fast Startup in Windows.
- Turned iGPU off, i thought it maybe was a glitch because I am using two monitors, i tried unplugging one, no success. I had one monitor plugged into the GPU and one into the motherboard, i turned the iGPU off in the UEFI and unplugged the monitor from the motherboard. 

I also had a disc with Linux MINT laying arround, i put that one in and it works. But when I try the Ubuntu disc it just hangs at a black screen.

Here's my system specifications:

i3-4130 @ 3.4 ghz
8 GB of RAM
GTX 750 Ti
Gigabyte H81M-HD3

I really need help.

---

### Post by leunam12 on 2016-10-22
Depending on how are you booting you can press 'e' or F6 (options will be at the bottom, if there are no options at the bottom, then press e) to change your boot options to 'nomodeset' maybe that will help you. Just type nomodeset at the end of the line after quiet splash.

[https://ubuntuforums.org/showthread.php?t=2340468&highlight=nomodeset](https://ubuntuforums.org/showthread.php?t=2340468&highlight=nomodeset)

---

### Post by OctaVive on 2016-10-23
Hi Leunam,

Thanks for you rreply, and I´m very proud to say that this method worked. It looked like crap at the installation,  but once installation was done everything looked great. Installed Nvidia drivers and everything´s done.

I´m typing this from the linux machine itself, it has windows for games and i use Linux for other stuff.


I must say, that the community of Linux is awesome, very helpful and give you real solutions unlike Windows who gives ******** like: ¨Have you restarted your computer?¨
See this is a compliment to all Linux users :)

---

### Post by leunam12 on 2016-10-26
Good! you can mark the thread as solved now.
Glad to help.

---

