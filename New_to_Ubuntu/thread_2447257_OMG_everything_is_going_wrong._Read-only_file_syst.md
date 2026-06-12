---
title: "OMG everything is going wrong. Read-only file system"
date: 2020-07-15
forum: New to Ubuntu
---

### Post by xcfstarflight1 on 2020-07-15
Hi!
Whenever I do some changes in the terminal, install applications or whatever I do,
when I log out i get alot of : read-only file system error messages.
Also, when I restart I need to go into recovery mode and do fsck /dev/sdc6 alot
of times to fix the inodes and when they are fixed I restart and I can log in.
When i close down firefox it sometimes just quit the program..
Installations are not working. Alot of things about this read-only file system stuff.
Can someone pinpoint the exact problem or help me figure out what to do?

---

### Post by guiverc on 2020-07-15
A RW (read-write) file system only trips to RO (read-only) because

- a command/instruction caused it, OR
- corruption was detected by the OS and it flipped RO to prevent data loss.

If it was the latter, a `fsck` or *file-system check* will check and correct errors, meaning it can be remounted correctly and used normally.

If it occurs once, it's no big deal, but if it keeps occurring, I would very quickly stop treating the symptom (flipping to RO & needing to `fsck` again), but look for a cause.  Looking at clues in your event logs (`dmesg`, `journalctl` etc) may provide clues, but even more so the corruption maybe because of a failing drive, so when was the last time you checked the health of your drive? and do you monitor that regularly or semi-regularly?

Myself I always use any problem as a trigger to boot into 'live' mode (eg. Ubuntu install media) and check the health of my drives using their inbuilt SMART capabilities ([https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)).   If no problems are detected, I'd likely test other hardware components likely next being memory (memtest is real easy to run) before I'd eventually find the probable or likely cause. 

(*if no hardware issues are at fault, I'd look at software using the ~date at which problems started occurring, and changes which could have corrupted something wrong before that ~date that could have caused this - as I don't know what if any changes you've made, and you haven't mentioned any, this software cause is listed last or as an after thought*)

---

### Post by Impavidus on 2020-07-16
+1

My first guess would be a failing hard drive too. I (semi-)regularly check the smart status of my hard drive from my installed system (if your system still runs well, no need for a live disk here – although I keep one ready anyway) and not only look at the numbers, but also the rate of change of the numbers. Keep in mind that if your hard drive passes the test, it's likely, but not guaranteed, that there's no hard drive problem. There are false negatives.

---

### Post by ActionParsnip on 2020-07-16
I suggest you boot to Ubuntu liveCD desktop and run a full fsck to check and repair the data

---

