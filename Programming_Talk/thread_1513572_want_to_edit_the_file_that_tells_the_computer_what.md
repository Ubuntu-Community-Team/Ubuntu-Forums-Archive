---
title: "want to edit the file that tells the computer what to do when the lid is closed"
date: 2010-06-19
forum: Programming Talk
---

### Post by LutraMan on 2010-06-19
I have basic C and C++ knowledge and I believe I can find a way to tell it to do what I want (I want to tell it to turn the screen off, but if a secondary screen is connected, turn off only the laptop screen).

my main problem is that I don't know how to find the file (or files) that I need to edit (and probably there are some system calls that I need to find)
but mainly, I need to know what file, or alternatively, how to find the file(s), that I need to edit.

any help would be greatly appreciated.

---

### Post by gmargo on 2010-06-19
I can only give the smallest of clues: it involves the file /etc/acpi/lid.sh from the acpi-support package.

---

### Post by soltanis on 2010-06-19
Probably not system calls. Think a little higher in terms of API. You will probably need to talk to acpid (or whatever its replacement might be), the power management daemon, which probably has control over things like which screens are on; failing that, my next guess is the X server.

However, the above hint is correct; the lid.sh script is executed when you close your laptop lid, so that should be your starting point. When I had a laptop, I noticed that whenever I closed my lid, the screen would blank but the backlight would stay on, so I edited this script so that it would shut off the backlight (that was done using another script -- I don't remember its name -- but it's in one of those directories) and also lock my screen.

---

