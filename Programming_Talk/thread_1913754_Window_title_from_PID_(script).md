---
title: "Window title from PID (script)"
date: 2012-01-23
forum: Programming Talk
---

### Post by steve_kam on 2012-01-23
Hi!

I need a shell script for Linux. It must show me the "window title" from process id (PID).

I found something here but it does not work: [http://blog.chewearn.com/2010/01/18/find-window-id-of-a-process-id-in-bash-script/](http://blog.chewearn.com/2010/01/18/find-window-id-of-a-process-id-in-bash-script/)

I will be happy if somebody can help me.

Thnak you!

---

### Post by Bachstelze on 2012-01-23
This will print a list of all windows and their PIDs, then you can parse it

```
for i in `xlsclients -l | grep "^ *Name" | awk '{print $2}'`; do
    echo -n "$i "
    xprop -name "$i" | grep PID | awk '{print $3}'
done
```

---

### Post by steve_kam on 2012-01-23
> **Bachstelze said:**
> This will print a list of all windows and their PIDs, then you can parse it

```
for i in `xlsclients -l | grep "^ *Name" | awk '{print $2}'`; do
    echo -n "$i "
    xprop -name "$i" | grep PID | awk '{print $3}'
done
```

Thank you! But i need the title of window not the name of process.

I need to list each chromium browsers tab title names. I wish i can do it because, each tab on chromium browser use new independed process. For example this:

xwininfo -root -children 2>/dev/null | grep chromium-browsegives me the chromium browsers title names. But i can not make a relationshipwith PID.

---

### Post by pbrane on 2012-01-23
This might help to get started, not exactly what you want though.
[http://www.linuxquestions.org/questions/programming-9/getting-the-pid-of-the-top-active-window-776938/]("http://www.linuxquestions.org/questions/programming-9/getting-the-pid-of-the-top-active-window-776938/")

and maybe this

[http://blog.chewearn.com/2010/01/18/find-window-id-of-a-process-id-in-bash-script/]("http://blog.chewearn.com/2010/01/18/find-window-id-of-a-process-id-in-bash-script/")

---

### Post by steve_kam on 2012-01-23
I look your sources. I can find the window id by grabbing it.

Now i need to find process id from window id. Is that possible? Or is there simple command line app which gives me the process id if i grab it with mouse?

---

### Post by Habitual on 2012-01-23
> **steve_kam said:**
> ...Or is there simple command line app which gives me the process id if i grab it with mouse?

Terminal >
```
xwininfo
```

click on desired window... and check the terminal for "Window ID" output...
Window id: 0x4e000a3 "Window title from PID (script) - Ubuntu Forums - Mozilla Firefox"

[http://www.daniweb.com/software-development/shell-scripting/threads/408029](http://www.daniweb.com/software-development/shell-scripting/threads/408029)

---

### Post by Vaphell on 2012-01-23
while you can get the window title in one way or another, i don't think you can get chromium tab names. Chromium seems to be registered as a single window which is not too surprising.

```
wids=( $(xprop -root | grep '_NET_CLIENT_LIST.*(WINDOW)' | sed 's/^.*#//' | sed 's/,/\n/g' | sort -u ) )
echo number of registered windows: ${#wids[@]}
for w in ${wids[@]}; do echo id: $w; xprop -id $w | grep -P '_NET_WM_PID|^WM_NAME'; done
```

this returns only one entry for chromium with multiple tabs

---

