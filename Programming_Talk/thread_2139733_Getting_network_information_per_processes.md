---
title: "Getting network information per processes"
date: 2013-04-27
forum: Programming Talk
---

### Post by machikakara on 2013-04-27
I am looking for how to get network usage per processes. I am hoping there is something in /proc that can help me with this. I am not looking to use another application unless its built into the OS and not just Ubuntu, but Debian, red-hat based and so on. I am writing a system monitor so the less applications the user needs to have installed the better. Currently I dont make the user install anything on there server(other than my agent) and would like to keep it that way.

---

### Post by ofnuts on 2013-04-29
/proc/{pid}/net/netstat seems to have the required info (but you'll have to hunt for a description of the contents)

---

