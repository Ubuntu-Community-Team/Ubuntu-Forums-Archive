---
title: "ubuntu hangs on shutdown/Restart after suspend"
date: 2018-01-21
forum: New to Ubuntu
---

### Post by mostafa.sh on 2018-01-21
[COLOR=#111111][FONT=Ubuntu][FONT=inherit]I know it seems that i have asked a Repetitious question. but it is really different![/FONT]
[FONT=inherit]there is no problem with restart, shutdown and suspend at first. but if I suspend the system just once, after that I can't restart or shutdown![/FONT]
[FONT=inherit]imagine --> you turn the laptop on --> no problem with restart or shutdown ![/FONT]
[FONT=inherit]but(!) --> if you suspend the system and come back --> after that if you try to restart the system or shut it down, the system freezes![/FONT]
[FONT=inherit]I have ubuntu 16.04.3 lts. 20gb swap, 30gb root and 100gb home beside windows 10.[/FONT]
[FONT=inherit]I have removed unity and installed gnome 3. notice that The problem was already there before changing unity to gnome 3.[/FONT]
[FONT=inherit]How can I solve this problem?[/FONT]
[/FONT][/COLOR]

---

### Post by cruzer001 on 2018-01-21
Have you tried a reboot in terminal?  It may show errors.

```
reboot
```

---

### Post by mostafa.sh on 2018-01-24
yeah i did. but no report was returned.
does ubuntu make error_log files? if does, where can I find it?

---

### Post by cruzer001 on 2018-01-24
Yes there are system logs

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

I would also try a previous kernel at boot (grub) in Advance Options.

I assume your fully updated.

```
sudo apt update && sudo apt full-upgrade
```

What kernel are you on?

```
inxi -b
```

Please post the output.

---

