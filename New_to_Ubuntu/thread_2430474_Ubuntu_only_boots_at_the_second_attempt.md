---
title: "Ubuntu only boots at the second attempt"
date: 2019-11-02
forum: New to Ubuntu
---

### Post by nuno-c on 2019-11-02
Hi, i just started to use ubuntu, so forgive me for being noob

I installed ubuntu in my desktop in a secondary disk. To do that i disconnected the main disk with windows 10 and successfully installed ubuntu.
The thing is that now i can boot into windows normally only by powering the desktop, but when i try to boot ubuntu this happens:

My steps:

Turn desktop on;
Press F2 to load bios;
Choose the disk with ubuntu (only ubuntu);
Grub 2.0 appears;
Choose ubuntu;
The purple screen shows up with the ubuntu logo but it stays in here. Sometimes the screen goes black but the logo get's back after a few seconds or by pressing Esc;
Press the reset button and repeat the same process.

But at the second attempt ubuntu will boot with no issues. 

May someone help me with this? Thank you

---

### Post by Autodave on 2019-11-02
Why do you have Grub?  If the Win disc was disconnected, then there should be no Grub.  I have the same set up here: turn on, hit F11 for boot order, choose correct disk, Xubuntu boots up (or Win10 depending on what I chose).

---

### Post by nuno-c on 2019-11-03
Hi, thak you for your reply.

I don´t know why i have grub. The only thing that i did after installing ubuntu was an update. Should i uninstall grub?

---

### Post by oldrocker99 on 2019-11-04
> **nuno-c said:**
> Hi, thak you for your reply.

I don´t know why i have grub. The only thing that i did after installing ubuntu was an update. Should i uninstall grub?

I wouldn't bother removing grub; even if it doesn't get used, you may still come to grief removing it. It'll do no harm not to uninstall it, and it's a tiny program anyway.

---

### Post by RobGoss on 2019-11-05
**Audodave**, is correct you should not have grub if you disconnected the main drive. **F-11** should allow you to choose which drive you want to boot I also have the same setup

---

