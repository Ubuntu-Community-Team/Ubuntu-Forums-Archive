---
title: "Missing operating system for 30 seconds"
date: 2020-09-24
forum: New to Ubuntu
---

### Post by chris-burmajster on 2020-09-24
Hello,

After removing my GTX 750 card and putting it back two days later, my Ubuntu operating system shows 'missing operating system' for 30 seconds on boot. Is there anything I can do about this?

Chris Burmajster

---

### Post by dino99 on 2020-09-25
glance at 'journalctl -b' output to find error (red lines) and warnings (yellow lines)

---

### Post by chris-burmajster on 2020-09-25
Hello,

I've cured it. I duck'ed grub and re-installed it from Boot.

Chris

---

