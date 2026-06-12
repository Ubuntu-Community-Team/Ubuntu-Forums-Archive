---
title: "Random Freezes: New Install"
date: 2020-05-13
forum: New to Ubuntu
---

### Post by pszumlas on 2020-05-13
Hi folks; 

First, the past few weeks have been my only experience with Linux in well over a decade - even then, it was a fun experiment, but not on something that was ever going to be a primary machine.

Around two weeks ago, I installed what I assume was an absolutely standard version of Ubuntu from a downloaded CD image. This was done on a brand new, solid-state hard drive.

Almost immediately, I started fiddling around with monitor drivers. I also noticed that I seemed to be running into issues with the built-in spreadsheet program blogging down, or locking up, so I downloaded and installed OpenOffice.

Still seeing periodic freezes, and not finding much discussion to indicate that others were seeing similar issues, I decided to try a fresh start before I got any more committed to that install. That was around four days ago, and things have run somewhat smoothly since then.

Gradually, though, there have been longer and longer moments of, for example, opening a spreadsheet and having to wait at least a few minutes before the system starts responding again. 

I have tried to keep this attempt as simple as possible to start, although I did have to add Zoom and Skype. Other than that,I use the system for email, online video, and some other basic web functions.

If I am seeing problems with the system bogging down or locking up entirely at this point, does anyone have any suggestions for where I could start troubleshooting? 

I am running an AMD A8-6500, with 4 gigs of RAM. With the new solid-state drive, it’s tempting to assume that I have enough hardware to make this work.

Thanks for any suggestions.

---

### Post by dino99 on 2020-05-13
When a user get problem with its install, the first thing to do is glancing at the output of 'journalctl -b' run from a terminal: pay attention to warnings (yellow lines) and errors (red lines (the ones that matter)

Also let us know about the installation: which format has been set ? (ext4, else), which session is used ? (gnome-shell on X or wayland, else)

---

### Post by kurt18947 on 2020-05-13
Is this a desktop or notebook? I have a Ryzen 3 2200G desktop and when using integrated graphics I've seen the lock up for a few minutes behavior. I think it has something to do with the Vega8 graphics in the APU. More of an issue for me was failure to resume from suspend. I have a dual monitor setup and one monitor would be solid lime green and the other blank. Nothing I tried would get it to a usable state. I could install an old Nvidia G210 card which worked fine. What finally seems to have fixed it was pretty counterintuitive. There is a screen in UEFI to select integrated graphics or external PCIe. I told it to use the external PCIe card as primary but didn't install one. It's been behaving well for a week or more. There haven't been many updates in that time so I don't know that an update fixed my problem.

---

### Post by pszumlas on 2020-05-13
Thanks dino and kurt;

Dino, the main thing I'm seeing in the log is a repeating block of around 20 lines, including these in red:

May 12 22:16:46 Socrates kernel: b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
May 12 22:16:46 Socrates kernel: b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
May 12 22:16:46 Socrates kernel: b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version

I just did a quick search, and I'm seeing discussions about wireless connections, which makes sense aside from the fact that I don't have any wireless hardware on this machine.

The df -Th command has a few entries that say ext4, but I don't know if that answers your format question. In the system information, it shows Gnome 3.28.2.


Kurt, this is a desktop, and I am running an nVidia Geforce... 8600 maybe. 

I appreciate the help.

---

### Post by pszumlas on 2020-05-13
Since that last reply, I've been thinking over the couple problems I've just started seeing, and when they happened. I think, in this second install, that all the errors have happened while I was running Zoom. It's very possible, then, that this is not a continuation of the more pervasive freezes I was seeing earlier, because I understand that Zoom has been struggling a bit to cope with higher demand right now. 

Because the results looked the same, I may have just jumped too quickly back to thinking about the original issue. I'd still love any suggestions, but if nothing seems obvious, please don't spend any time digging until I can be more confident that Zoom isn't the issue this time.

Thanks.

---

### Post by kurt18947 on 2020-05-13
> **pszumlas said:**
> Thanks dino and kurt;

<snip>
Kurt, this is a desktop, and I am running an nVidia Geforce... 8600 maybe. 

I appreciate the help.

That eliminates an AMD video issue then. I hope you're able to work it out.

---

