---
title: "Sed, Pisg: Converting mIRC logs into Eggdrop logformat."
date: 2011-01-07
forum: Programming Talk
---

### Post by Daleth on 2011-01-07
Hiya, not sure if this is the correct forum to ask this but Ill give it a try since it involves programming, sed and eggdrop.

Heres the thing, Ive tried to convert mIRC logs into Eggdrop without any special success. Ive browsed some forums and found a person using mirc2egg.sed which is included in pisg, so I used it but it will only convert 
Session Start: Sat Oct 09 07:57:31 2010 
into 
[07:58] --- Sat Oct 09 2010 

This leaves out everything else like chat, mirc2egg.sed seems to be quite outdated but not sure if this makes any difference. Is there any other way to convert mIRC logs into Eggdrop? 

Cheers!

---

### Post by odyniec on 2011-01-07
Can you post a short sample of both log formats?

---

### Post by Daleth on 2011-01-07
mIRC:
(00:04:57) &#139;Nick&#155; chatchat chat chat
(00:04:57) &#139;Nick&#155; Lol.
(00:05:03) &#139;@Nick&#155; chatchat chat chat
(00:05:06) &#139;Nick&#155; chat chat
(00:05:09) &#139;Nick&#155; chatchat chat chat
(00:05:10) &#139;Nick&#155; chat chat

Eggdrop:
[00:04] <Nick> chatchat chat chat
[00:04] <Nick> Lol.
[00:05] <Nick> chatchat chat chat
[00:05] <Nick> chat chat
[00:05] <Nick> chatchat chat chat
[00:05] <Nick> chat chat

---

### Post by odyniec on 2011-01-07
So it's just the time part that needs to be converted? If so, then a simple sed substitution should do:

```
cat mirc_log_file | sed 's/^(\([0-9]\+:[0-9]\+\):[0-9]\+)/[\1]/'
```

If you also want the normal less-than/greater-than characters wrapped around the nick instead of the characters used by mIRC, use this longer variant:

```
sed 's/^(\([0-9]\+:[0-9]\+\):[0-9]\+) ‹\([^›]\+\)›/[\1] <\2>/'
```

---

