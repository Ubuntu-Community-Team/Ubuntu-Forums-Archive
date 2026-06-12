---
title: "Ubuntu won't boot even after boot-repairs"
date: 2018-02-14
forum: New to Ubuntu
---

### Post by rphl on 2018-02-14
So my ubuntu doesn't want to boot, it goes past the BIOS then shuts down and restarts.

I booted from a USB, did the disk check and it said it was fine, but no.
Then I installed boot-repairs from the live-ubuntu session, ran the recommended repair, said it was successful, but again no it doesn't boot.

I'm running it on a Lenovo Thinkpad T470p.

Here is my pastebin:

 [https://paste.ubuntu.com/p/MqYrkGhqmf/](https://paste.ubuntu.com/p/MqYrkGhqmf/)

Any clue as to the issue at hand?

---

### Post by rphl on 2018-02-15
Managed to boot in the F12 boot menu, it seems that there is something wrong with the automatic boot-order, not clear to me why.

---

### Post by oldfred on 2018-02-15
Lenovo has a lot of different models. Not sure if any of these may apply?
With most vendors issues are common across many models.

 T540 works but UEFI settings critical or it may brick reset w/ Switching "OS Optimized Defaults
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

