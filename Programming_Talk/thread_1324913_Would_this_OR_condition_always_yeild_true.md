---
title: "Would this OR condition always yeild true?"
date: 2009-11-13
forum: Programming Talk
---

### Post by lavinog on 2009-11-13
I was looking at the source for libatasmart_0.17 and came across the following:
```

if ((!strcmp(a->name, "reallocated-sector-count") ||
                     !strcmp(a->name, "current-pending-sector")) &&
                    a->pretty_value > 0)
                        a->warn = TRUE;

```

Am I mistaken or wont the condition before the && always be true?
isn't that the same as:
```
if (x != 1) || (x != 2)

```

---

### Post by jpkotta on 2009-11-13
strcmp() returns 0 only if the strings match.  The ! of course inverts this.  So if neither matches, you get 0 || 0 == 0.

---

### Post by lavinog on 2009-11-13
> **jpkotta said:**
> strcmp() returns 0 only if the strings match.  The ! of course inverts this.  So if neither matches, you get 0 || 0 == 0.

ahh yes,
I have been messing with python too much...I am really forgetting a lot about c.

Thank you for responding.

---

