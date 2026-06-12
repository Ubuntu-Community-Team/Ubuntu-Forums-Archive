---
title: "Listening to ACPI Events In Python"
date: 2007-12-20
forum: Programming Talk
---

### Post by roadkillbunny on 2007-12-20
Hi,

I am working on a script for my tablet that will rotate the screen based on its physical orientation as indicated with the built in accelerator when in tablet mode. I got the rotating part working, now I just have to enable it only when I flip the screen down and disable it when I flip the screen up. Both of the actions are detected by ACPI as events and I could add listeners to /etc/acpi/events to start and kill my script. However I want to add a bit more functionality, like the ability for the user to enable/disable the script using the manual rotate button located on the screen. So I was thinking of starting the script on login so I can listen for button presses too.

However I do not know how to detect the ACPI events from the script that way. Is there some kind of a python API that has access to ACPI events or would I have to parse the ACPI log file (assuming it's enabled)?

---

### Post by Lt_Worf on 2011-10-14
Try that

s = socket.socket(socket.AF_UNIX, socket.SOCK_STREAM)
s.connect("/var/run/acpid.socket")

s.recv(4096)

---

### Post by kostkon on 2011-10-14
> **roadkillbunny said:**
> However I do not know how to detect the ACPI events from the script that way. Is there some kind of a python API that has access to ACPI events or would I have to parse the ACPI log file (assuming it's enabled)?
[UPower]("http://upower.freedesktop.org/") maybe? You can use its DBus interface with Python.

Check the [docs]("http://upower.freedesktop.org/docs/UPower.html") here and/or install [D-Feet]("https://apps.ubuntu.com/cat/applications/natty/d-feet/") to explore and test it.

EDIT: whoops, the original post was very old; necromancy!!

---

### Post by nothingspecial on 2011-10-14
Old thread

closed

---

