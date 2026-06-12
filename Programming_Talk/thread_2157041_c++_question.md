---
title: "c++ question"
date: 2013-06-24
forum: Programming Talk
---

### Post by MikeCyber on 2013-06-24
Hi
what does that mean/do:

#define    afcs_apstate_hdg         0x00002
#define    afcs_apstate_wlv         0x00004
#define    afcs_apstate_spd         0x00008

etc. Could I write the same differently? (might help me to understand)
Thanks

---

### Post by r-senior on 2013-06-24
Those lines are preprocessor lines (it's the same for C and Objective-C). They define three macros that are substituted into the program source code before it is compiled. Where your code refers to afcs_apstats_hdg, the preprocessor substitutes 0x00002.

It's a common convention to use uppercase for #define macros so that they are clearly identified as such; many programmers would prefer AFCS_APSTATE_HDG, etc. 

The values themselves are hexadecimal literals. They look like they are intended to be used as bit masks; in binary they would be:

```
0000 0010
0000 0100
0000 1000
```

A bit mask is usually used where multiple flags are encoded into a single value and they are extracted by bitwise AND, for example:

```
if (flags & afcs_apstate_hdg)
    // This evaluates true if the second least significant bit in flags is 1

```

A common alternative to using #define would be to create an enum. For example:

```
enum APState {AfcsApStateHDG=0x02, AfcsApStateWLV=0x04, AfcsApStateSPD=0x08};
```

Enumerated types are generally more type safe but that doesn't mean #define is completely frowned upon.

Naming conventions for such things probably differ between languages/platforms/projects.

---

### Post by MikeCyber on 2013-06-24
Thanks. So it's only because the author prefers it to decimal? For me it only complicates stuff and I don't see any advantage for now.

---

### Post by ofnuts on 2013-06-24
No, it very common for bitmasks to be written in hexadeceimal or octal. Every C programmer worth his salt knows the powers of two by heart, but you may have some combos that are harder to identify as bit masks in decimal but still easy to spot in hex: compare 0x00FFF000 and 16773120. In practice the mere fact that the number is in hex or octal is a clue that it is really a bitmask.

---

