---
title: "[SOLVED] Default window size for Konsole"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Qtips on 2008-09-01
Hi everyone,

I want to change the default window size of the Konsole application under Kubuntu to something 130x30...

I know that with the gnome-terminal, i need to use the following command : 
gnome-terminal --geometry 130x30+30+42 but i've try with the Konsole and this doesn't seem to work...

Anyone know how to do that ?

Thanks

---

### Post by Sarah L on 2008-09-01
You can try going to Settings -> Size -> Custom... and setting a preferred size.
Then that size can be saved as a default by going to Settings -> Save as Default.

Hope this helps,
Sarah

---

### Post by Qtips on 2008-09-01
Hi Sarah!

Your advice worked ! Thanks a lot ;)

---

### Post by eneville on 2010-10-19
> **Qtips said:**
> Hi Sarah!

Your advice worked ! Thanks a lot ;)

Its a bit annoying but this is no longer the case. I was all set to switch to konsole being the primary terminal (since it behaves a little better with screen, but that's another case).

Unfortunately it's not integrated in the same way as most other X programs are with the --geometry, or even konsole's own --vt_sz which has disappeared.

-1

---

