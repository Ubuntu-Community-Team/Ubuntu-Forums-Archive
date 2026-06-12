---
title: "Ubuntu 22.04.4 LTSwifi connection lost after some minutes"
date: 2024-07-09
forum: New to Ubuntu
---

### Post by jhsgarciamu on 2024-07-09
[COLOR=#0C0D0E][FONT=-apple-system]Well, this is my first time using Ubuntu. As far as I know, Linux is a more efficient OS than Windows, and I had an old laptop (Asus Vivobook), so I decided to give it a try to learn some stuff related to data engineering (If you have some books, courses relates, would be awesome, im newbie)[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]The problem? I can only navigate the internet for a couple of minutes. After that, the WiFi connection gets lost, and it won't appear anymore until I turn off the laptop. Then I'll have another 10 minutes until it happens again.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]What have I found? Well, a couple of things I discovered are interesting to mention:[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Sometimes the WiFi lasts longer. I don't really know why, but I suspect that when the laptop has the charger plugged in, it lasts a little longer.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Sometimes, the battery icon appears to do nothing. I mean, I know it's plugged in, and it should be charging, but it shows as if it wasn't. Although the battery doesn't drain.

here is some info about the pc:
[https://paste.ubuntu.com/p/CKnMVwD8RY/](https://paste.ubuntu.com/p/CKnMVwD8RY/)

---

### Post by ajgreeny on 2024-07-10
That link helps a bit but more info would be useful.
Please show us the output of command 
**inxi -Fzx**
Please use code tags for that output - there's a how-to in my signature below.

---

### Post by ActionParsnip on 2024-07-11
What is the output of:
```

sudo lshw -C network; lsb_release -a; uname -a

```
Thanks

---

