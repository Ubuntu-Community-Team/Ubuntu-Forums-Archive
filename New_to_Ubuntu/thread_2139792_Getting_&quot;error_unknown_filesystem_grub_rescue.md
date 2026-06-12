---
title: "Getting &quot;error: unknown filesystem grub rescue&gt;&quot; after Activating Windows 8"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by rdp1976 on 2013-04-27
I'm fairly new to Xubuntu, though I have used Unix/Linux on and off in the past. I just setup Windows 8 and Xubuntu 13.04 to dual boot on a Dell XPS 13 (2013) Ultrabook.

The back story: I created a Dell Windows Recovery USB, removed the stock 128 GB SDD and replaced with a 480 GB SDD. Then installed Windows 8. Then installed Xubuntu 13.04. Apart from a "dimming" bug in Xubuntu, everything was working fine.

Given that I had now recovered Windows 8 onto a different SDD, I had to go through the Activation process. When I did that, I rebooted and got this:

error: unknown filesystem
grub rescue>

I've seen several posts about this online, but nothing clear enough to explain how I can fix this problem. I can boot into Xubuntu with the USB choosing "Try Xubuntu" option. I just need to know what to do next to repair the grub menu.

Any assistance would be greatly appreciated.

RDP1976

---

### Post by Impavidus on 2013-04-28
You can try boot repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
If it doesn't fix the problem, it can at least create a summary. You can post a link to the summary in this thread. It will help us diagnose the problem.

---

### Post by rdp1976 on 2013-04-28
Did a full re-install of everything. This time Windows was activated for my hard-drive. Everything was working great. Then I deleted the 30 GB Windows 8 Recovery Partition and BAM!!! Same thing happened again.

I ran Boot Repair and it didn't fix anything........ Frustrated.

[http://paste.ubuntu.com/5614621/](http://paste.ubuntu.com/5614621/)

---

