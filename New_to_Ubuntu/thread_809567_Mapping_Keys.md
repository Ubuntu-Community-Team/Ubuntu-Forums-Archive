---
title: "Mapping Keys"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by cowboy_mcd74 on 2008-05-27
Hey, sorry if this doesn't belong in this forum.

I'm trying to map my ThinkVantage key to open gnome-system-monitor...I need something to open it, cause I often need to kill processes that freeze the comp.

Anyways, I've mapped it already, but it doesn't open the system monitor! D=

I changed /etc/acpi/thinkpad-thinkpad.sh to run gnome-system-monitor. If I switch to the directory and run ./thinkpad-thinkpad.sh, it opens gnome-system-monitor, so I know that's working. Running acpi_listen also shows that my ThinkVantage key works, and sends the right HKEY code.... I've even checked /etc/acpi/events/thinkpad-thinkpad, and its action is /etc/acpi/thinkpad-thinkpad.sh

What could be going wrong?

---

