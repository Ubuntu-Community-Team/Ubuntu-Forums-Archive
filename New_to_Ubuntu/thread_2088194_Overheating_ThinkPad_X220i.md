---
title: "Overheating ThinkPad X220i"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by EuropaCar on 2012-11-25
I've got a Thinkpad x220i and ubuntu is just short of unusable on it simply because it overheats. Everything runs smoothly but I am seeing CPU temperatures >90C!
Of course the temp rises when I have multiple programs running at once, but even when I have no programs running at all, I can still see the temp maintained above 70C. I have checked system monitor during these periods and there can be minimal CPU usage when this occurs. This is intermittent, and after maybe 10 minutes the temp drops back to its resting temp of mid 50s.
Anyone have any advice?
Thanks

Most of my search results come up with noisy fans, but that is not my issue (although I hope the fan is doing its job as best it can)

---

### Post by personalpc on 2012-11-25
Check bios fan settings and set it to autosense

or

install tpfand (thinkpad fan daemon)& tpfan-admin is a great GUI tool

code:
sudo apt-get install tpfand tpfan-admin

Also don't forget about the fact that OEM products use low grade compound on the heat sink. If you want cool temps always use a pure silver compound like Arctic Silver.

---

### Post by EuropaCar on 2012-11-25
Thanks for the response

So I should mention that this same computer runs Windows 7 (the OS that came with it) very cool. I can barely feel the heat when it's running windows 7. So I don't think there is an issue with the actual heat sink.

I will try what you have suggested though.

---

