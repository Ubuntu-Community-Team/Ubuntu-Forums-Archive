---
title: "Ubuntu Root using 97% cpu"
date: 2017-05-04
forum: New to Ubuntu
---

### Post by noahmthomas on 2017-05-04
Hello all,

This is my first installation of Ubuntu. It is on my ASUS F555U dual booting alongside windows on a 250GB partition with 8GB of ram. I have noticed that Ubuntu had been running very slow. Originally I thought it was Firefox eating resources but it still persists to take a second to execute commands both through  the GUI and in the terminal. I have look into other issues taking up lots of processing but none of them were Root. I have taken a screen shot of the processes and memory usage. Any help would be greatly appreciated!
[ATTACH=CONFIG]274952[/ATTACH][ATTACH=CONFIG]274953[/ATTACH]

---

### Post by mastablasta on 2017-05-04
it's not root it's systemd-journal and kworker. looks liek more have this issue also on other linux OS:
[https://forum.manjaro.org/t/high-cpu-usage-from-systemd-journald-and-kworker/8453](https://forum.manjaro.org/t/high-cpu-usage-from-systemd-journald-and-kworker/8453)

the issue seems to happen when something is wrong and is doing a loop restarting over and over. apparetnly checking the journal itself might reveal a clue as to what is wrong and what wants to start but can't.
the thing that is failing can be wrong or bad driver or simply a process having an issue to start. for example:
[https://ubuntuforums.org/showthread.php?t=2276522](https://ubuntuforums.org/showthread.php?t=2276522)

in anycase we are fishing here, without knowing what the logs are saying.

offtopic: well done systemd. well done. :twisted:

---

