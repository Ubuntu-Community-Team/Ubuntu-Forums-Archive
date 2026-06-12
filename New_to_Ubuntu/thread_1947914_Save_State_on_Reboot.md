---
title: "Save State on Reboot?"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by solocommand on 2012-03-27
Is there any method I can use to save the state of my ubuntu environment when I restart? Similar to suspend/hibernate, except I'd like to save on disk somewhere.

I have a dual boot setup on my workstation, and I frequently need to switch to Windows to use in-house apps, or apps that won't run in Wine (MSSQL interface, etc).

What I'd like to do, is have a quick option that allows me to instantly save all my running applications/windows, reboot to Windows, and have everything restore itself when I return to ubuntu.

Does anything like this exist, or any pointers on where I could find more information about doing this?

I am running Ubuntu 11.10, with Windows 7 on my second partition (both 64-bit).

Thanks!

---

### Post by I8NY on 2012-03-28
Well I can't test this since Unity (I think) is breaking hibernation for me. If I'm correct, when you select hibernate it will turn off the PC just like a shutdown. Boot it back up and select windows in GRUB or select ubuntu to resume your state.

---

### Post by solocommand on 2012-03-28
I'll give that a shot. Thanks!

---

### Post by solocommand on 2012-04-04
Unfortunately I wasn't able to get this working correctly. After hibernating and booting to windows, my applications did not restore (normal login). Hibernating and resuming normally did seem to work correctly.

For now, I have Virtualbox set up to use a raw disk containing only my Windows partition(s), and after some trial and error, that's working pretty well. Running it headless and remoting into it when I need to use something on the windows side is working pretty well, haven't noticed much of a resource draw unless I'm doing something fairly intensive in the VM.

Thanks for the suggestion though!

---

