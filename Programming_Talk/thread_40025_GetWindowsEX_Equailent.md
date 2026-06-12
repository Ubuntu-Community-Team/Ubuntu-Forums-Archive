---
title: "GetWindowsEX Equailent?"
date: 2005-06-07
forum: Programming Talk
---

### Post by Kimm on 2005-06-07
I was woundering if there is an equailent to GetWindowsEX in Linux?
and, also, if I can use this to send messages to a game running in Cedega?

---

### Post by Cossins on 2005-06-10
There isn't a direct equivalent, but you can probably do the same by other means. The thing  is that X11 works quite differently from Windows.

To send messages to games running in Cedega, you would need to use winelib to communicate. I have no experience with Wine programming, but it should be possible.

- Simon

---

