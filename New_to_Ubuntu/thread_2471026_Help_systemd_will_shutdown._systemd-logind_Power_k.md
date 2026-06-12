---
title: "Help: systemd will shutdown. systemd-logind: Power key pressed"
date: 2022-01-20
forum: New to Ubuntu
---

### Post by donbe1215 on 2022-01-20
When I was scrutinizing my previous post about powering down, I found in the auth.log that systemd was running out of control.

[https://ubuntuforums.org/showthread.php?t=2470777](https://ubuntuforums.org/showthread.php?t=2470777)

```
Jan 20 13:15:23 yo-PRIMERGY systemd-logind[1001]: Power key pressed.
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@Jan 20 13:28:14 yo-PRIMERGY systemd-logind[1025]: New seat seat0.

```

How to prevent systemd from pressing the power button
I understand that I can enable > HandlePowerKey=poweroff in > /etc/systemd/logind.conf to prevent systemd from pressing the power button.




I want to prevent systemd from pressing the power button.
However, I want the power button to work when touched by a human.


What should I do in this case?
Thank you.

---

### Post by jeremy31 on 2022-01-21
Duplicate of [https://ubuntuforums.org/showthread.php?t=2471096](https://ubuntuforums.org/showthread.php?t=2471096)
Thread closed

---

