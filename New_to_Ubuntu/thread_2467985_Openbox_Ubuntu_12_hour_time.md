---
title: "Openbox Ubuntu 12 hour time"
date: 2021-10-14
forum: New to Ubuntu
---

### Post by catipads-aacc on 2021-10-14
Hi,

I have a question that I am hoping that someone may be able to help me with. I am running Ubuntu 20.04 with Openbox. I am in the USA and the locale seems to be set to en_US on this machine. However, when I execute a ls-la command, or attach a file in Thunderbird, or open a file in LibreOffice, all of the timestamps are in 24-hour time.

Is there anything that I can do to make these appear in 12-hour time (am/pm)?

Thank you for any help that you can provide.

---

### Post by coley9225 on 2021-10-15
Hello catipads. I use Lubuntu, and I can right click on the clock in the sys tray, choose the configure option. From there I can set to 12/24 hour time, whether to show date and format for that, etc. Hope this helps.

---

### Post by ActionParsnip on 2021-10-15
The terminal is not affected by the WM/DE you use. It's the terminal. Which terminal application are you using and which shell please? (If you are unsure of the shell it's probably BASH).

---

### Post by Holger_Gehrke on 2021-10-15
The time stamps for files are stored in a locale independent way (seconds since 1.1.1970, 0:00:00 UTC). How a program displays that time is up to the program. I don't know about Thunderbird or LibreOffice, but 'ls' has an option '--time-style' which will accept the same format codes as 'date'. So to get the time format for your locale you'd use 'ls -la --time-style=+%c'. If that still doesn't give you a twelve hour time format, you could try 'ls -la --time-style="+%a, %B %d %Y %r %p"'. If that works the way you want, you might set an alias for it in ~/.bashrc.

Holger

---

