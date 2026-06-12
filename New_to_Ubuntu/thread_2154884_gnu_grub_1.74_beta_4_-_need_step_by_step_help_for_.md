---
title: "gnu grub 1.74 beta 4 - need step by step help for an ABSOLUTE beginner"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Mavaan on 2013-06-16
Hi. I got this computer from a friend, it is supposed to Windows and Ubuntu (don´t know which versions) , but unfortunately the instruccions she gave me don´t work, and she´s left the country, so I am kind of looking for my way in a total darkness...

When I start the computer, I get this famous message "gnu grub 1.74 beta 4 minimal BASH-like line editing is supported. For the first Word, TAB lists posible command completions. Anywhere else TAB lists posible device/file completions.", that I´ve seen on other threads also, but the advices there don´t seem to work for me. Since I have no idea of these things, here´s a list of things I´ve tried, hope somebody can help me. For the moment I just want to have a computer that I can use, with one system or the other... I don´t have any backup cd´s or nothing.

1. First of all, I am in rescue :grub. The commands help or search don´t work.

2. with ls I get: (hd0) hd(0,8) hd(0,7) hd(0,6) hd(0,5) hd(0,3) (hd(0,2) hd(0,1) (fd0) fd(1). And then the line: error: no such disk

3. giving ls (hd + number), sometimes I get "unknown filesystem" or "bad filename".

4. with ls (hd0,1) I find /autorun/autorun.exe, and lots of other things, that might be interesting ? (look nlike Windows files to me)

5. ls (hd0,7) dives also "error: bad filename", but ls (hd0,7)/boot finds lots of files, f.e. the folder grub, with grub.cfg, and some Linux files, but from here on I have o clue what to do ...

So, I´ll appreciate all posible help and tips, but please make them very easy and step by step ;-)

---

### Post by Impavidus on 2013-06-16
Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). You'll need to create either a boot-repair disk or an ubuntu live disk. That last one is good to have anyway, because it can be used to rescue your system in various cases. If Boot-Repair can't fix your problem, it can at least provide us with a BootInfo summary, which will give us some useful information.

---

