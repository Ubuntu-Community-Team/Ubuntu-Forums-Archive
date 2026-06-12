---
title: "Logitech Keyboard - Media Key won't launch player"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by crjackson on 2008-04-28
I'm really pleased with Hardy 32-bit and wonder if anyone else has this issue.

When I press the Media Player key on the keyboard it doesn't launch the media player.  I've checked the keyboard mapping applet and it is correctly configured.

**Does anyone know how to make it actually Launch Rhythmbox?**  It worked out of the box on Gutsy, but I can't figure out how to make it work in hardy.

---

### Post by crjackson on 2008-04-29
bump

---

### Post by crjackson on 2008-04-30
So I guess I'm the only person who has this problem.  Strange...

Here's the link to the bug report I posted: [https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/224807](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/224807)

Here's the text of the report:

After a clean install of Ubuntu Hardy 32-bit, I find that I can no longer press the media key on the keyboard to launch rhythmbox which is my default media player. This worked out of the box with Feisty and Gutsy. I went to the Keyboard Shortcuts tools in the system preferences and reset the accelerator (even though it was already displaying the correct values) to no avail. I can only conclude this is a bug.

I'm using a Logitech Corded Keyboard with a PS2 adapter. This is an older model internet/media keyboard. P/N: 867395-0100 (131723-301 A)

My System Specs:

AMD ATHLON 64 X2 4800+ @ 2.6 GHz
MSI K8N Neo4 Platinum/SLI - BIOS 3.11 - 2 GB Curcial DDR
GeForce 7900 GTO, Pioneer DVR-108, Pioneer DVR-115D
2x 74 GB WD Raptors SATA , 2x 250 GB Hitachi SATA (Data)

---

### Post by crjackson on 2008-05-11
I've been trying to find a solution to this issue.  This is just an update.

Installing many other music players to test I've found that none will work.  It's a problem of Ubuntu not actually executing the command.  The key press is recognized.

I even configured the key manually using the keyboard shortcut applet.  This didn't work either.  I'm still trying to find a workaround.  If I find a way to make it work, I'll report the solution.

---

### Post by KaliVoid on 2008-05-11
try using (installing)"KeyTouch"
its working for my multimedia keyboard

---

### Post by crjackson on 2008-05-13
> **KaliVoid said:**
> try using (installing)"KeyTouch"
its working for my multimedia keyboard

I'll give it a try and see what happens...

---

### Post by waldir on 2011-03-04
I'm also using a Logitech corded keyboard with a PS2 connector (through a PS2&#8594;USB adapter), model Y-SZ49. I managed to get this working through the Keyboard Shortcuts app that comes by default with Ubuntu (found at System > Preferences > Keyboard Shortcuts, or through the command gnome-keybinding-properties).

---

