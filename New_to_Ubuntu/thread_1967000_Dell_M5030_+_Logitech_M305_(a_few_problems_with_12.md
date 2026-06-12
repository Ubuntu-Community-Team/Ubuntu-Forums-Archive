---
title: "Dell M5030 + Logitech M305 (a few problems with 12.04)"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by Ganeshx on 2012-04-27
Hey guys, I have a couple problems with the newest Ubuntu.  I upgraded from 10.04 (clean install).

First thing, I can't use regular Ubuntu, but only the 2D version.  The regular one doesn't fully load.  I've installed the graphic drivers, so that's not the problem.

Second thing, I have a Logitech M305, and it doesn't work with my laptop.  The receiver plugs in, and the mouse works in a rudimentary fashion, but it is very stuttery and glitchy, when it moves around very slowly.

Third, there are two graphics drivers I can install.  First one is "ATI/AMD proprietary FGLRX graphics driver" and the second one is "ATI/AMD proprietary FGLRX graphics driver (post-release updates)"  The second one fails to install.

That is all, as far as I know.  If anyone has any fixes, that will be great.  Thanks so much!

---

### Post by gordintoronto on 2012-04-27
Can you confirm that you did a clean install of 12.04, not an upgrade? You say you installed the graphic drivers, do you mean you ran "Additional Drivers" and installed the FGLRX driver? If so, you should be able to select "Ubuntu" from the gear at the logon screen. I'm not sure what you mean by, "doesn't fully load."

Can you describe "fails to install" more fully? Bear in mind that the web site is terribly busy because people do not use bittorrent downloads.

Do you have a fresh battery in your mouse?

---

### Post by Ganeshx on 2012-04-27
Yes, I did a clean install.  Downloaded the iso yesterday and installed it just today.

Yes, I ran the additional drivers app.  Included are two screenshots.  One of the failed to install message, the other showing that by failing to install, it also canceled the other driver.

When it fails to load, it loads the desktop and the side launcher (on the left).  The top bar does not load and it is impossible to click (left or right) on anything.  The mouse, however, moves around fine (when I use my touchpad . . . the mouse still isn't working right).  The 2D version still loads fine.

As for the mouse, yes.  The batteries are fine.  It works fine on a Windows 7 machine, and the light indicating that the batteries are good is on.

Thanks for your help!

---

### Post by eric forman on 2012-05-06
Hi,
ly
I have the same laptop & mouse combination and I tried upgrading from 10.10 with exactly the same results (slow, choppy mouse movement and same error message on installing the "updated" driver).

-Eric

---

### Post by eric forman on 2012-05-06
After playing with different settings all day, I found that setting "nomodeset" in GRUB will make both the mouse and Unity3D behave normally.  \\:D/

---

### Post by TomSwift98 on 2012-08-23
I also had that exact same issue, and nomodeset did nothing for me.  Were there any other fixes you tried?

---

