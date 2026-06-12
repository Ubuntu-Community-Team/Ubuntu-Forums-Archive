---
title: "&quot;Cannot display this video mode&quot; while installing"
date: 2013-07-20
forum: New to Ubuntu
---

### Post by pondweed on 2013-07-20
Hello,
I built a basic mini-itx computer for everyday use and thought I'd try Ubuntu 13.04 as my OS on it. Here's my first problem:
When booting from the live-USB, it gets as far as the screen with the 'progress-bar' then my monitor displays:

Cannot display this video mode, change computer input to 1080 x 1024 @ 60Hz

I don't have access to another monitor or want to buy a new one as this one is fine on my XP system. If it helps, the monitor is a philips 170B4, the motherboard is an intel D2550MUD2 with built-in graphics.

How can I solve this please? Thank you very much for any help.

---

### Post by dongatto on 2013-07-31
Hi,

Can you reach the Advanced Welcome page? ("By pressing any key when the small logo appears on the bottom of your screen.")
[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

If you can make it there, you can just hit F6 and select *nomodeset*, that usually solves problems with the resolution.

---

