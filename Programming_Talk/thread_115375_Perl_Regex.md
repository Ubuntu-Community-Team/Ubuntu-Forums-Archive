---
title: "Perl Regex"
date: 2006-01-10
forum: Programming Talk
---

### Post by theFallen on 2006-01-10
Hi all,

sorry to bother you with this, but I don'T have the time and the nerve to learn Perl for a simple renaming issue.
I need a skript or expression to rename file names.

e.g.:
000 fooo 01.rar -> fooo 01.rar

Whereas the leading numbers can occupy 2-4 digits.

I'd be happy if someone has the time and helps me.
Is there something equal to Total Commander's Mass Rename Tool? I know of Purrr, but it not nearly as powerfull as the one of TCM.

---

### Post by [2]BoxingFiend on 2006-01-10
regex:
/^[0-9]{2,4} /

---

