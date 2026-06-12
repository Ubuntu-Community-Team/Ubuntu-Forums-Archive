---
title: "programming help"
date: 2010-07-19
forum: Programming Talk
---

### Post by ~Las~ on 2010-07-19
I wrote below to get an idea about network usage.But when i close it by clicking on X it wont kill iftop & nethogs.Is there a way to execute a command to kill nethogs & iftop when I click X??Or any better way to do the whole thing?

Thanks in advance

```
terminator --geometry 1280x450+0+24 & 
sleep 5
{
xdotool type 'sudo nethogs'
xdotool key Return

xdotool key Return
xdotool key Shift+ctrl+e
sleep 2
xdotool type 'sudo iftop'
xdotool key Return
sudo nethogs


}
```

---

### Post by Iowan on 2010-07-19
Moved to Programming Talk.
Hopefully more response here.

---

