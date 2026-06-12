---
title: "Lose power to keyboard and mouse upon resuming from sleep? Help"
date: 2020-04-13
forum: New to Ubuntu
---

### Post by gedkirkham on 2020-04-13
Hello,

When waking my computer - i3wm-gaps - up from sleep - systemctl suspend - I sometimes, but not all the time, lose power to the keyboard and mouse for ~30-60 seconds. I have tried disconnecting all USB devices but that does not appear to change anything. I have also disabled autosuspend for the USB ports. The issue only appears after a few "systemctl suspend" commands and always works flawlessly from the first wake. I also have tried using the USB slots directly on the computer, and a USB powered hub. Again, no change.

I have attached two .txt files that I have captured from journalctl during both success and failure state. Line 164-170 in suspend-failure-*.txt only occurs when I lose power to the keyboard. I have checked to see what usb 1-6.4 is, and it relates to Hydra Series H150i Pro Liquid CPU Cooler. From what I have read, error -110 relates to potential power loss, so there appears to be a link here to my issue with the keyboard.

In both success and failure states, journalctl writes to the log "System suspend" but then proceeds to cancel that process. Why is that even happening once I begin to wake the computer? This can be seen on line 178-190 of suspend-failure-*.txt.

I am at a loss as to where to look next for answers. Does anyone have any idea why this may be happening?

Thank you,
Ged

---

### Post by justinpang1345wr on 2020-04-14
Did you get a reply?

---

