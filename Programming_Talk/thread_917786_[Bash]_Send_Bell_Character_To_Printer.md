---
title: "[Bash] Send Bell Character To Printer"
date: 2008-09-12
forum: Programming Talk
---

### Post by mike_g on 2008-09-12
I need to send a bell character to a printer. I have tried using lp and lpr, which print a file but wont work with a non-printable bell character.

Anyone know how I can do this?

Thanks.

---

### Post by kpatz on 2008-09-12
```

sudo bash -c "echo -e '\a' >/dev/lp0"

```

If your printer is on a different port than /dev/lp0, change it as appropriate.

Sudo is needed since the printer device is not normally writable by normal users.

---

