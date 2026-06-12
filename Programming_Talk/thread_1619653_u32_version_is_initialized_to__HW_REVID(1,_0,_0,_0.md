---
title: "u32 version is initialized to  HW_REVID(1, 0, 0, 0, 0, 0, 0) how is it happening"
date: 2010-11-12
forum: Programming Talk
---

### Post by jamesbon on 2010-11-12
[http://lxr.free-electrons.com/source/drivers/net/8139too.c#L503](http://lxr.free-electrons.com/source/drivers/net/8139too.c#L503)
On above link a structure is defined
```
static const struct {
        const char *name;
        u32 version; /* from RTL8139C/RTL8139D docs */
        u32 flags;
}
```
in the structure there is a datatype 
```
u32 version 
```which is initialized as  ```
  HW_REVID(1, 0, 0, 0, 0, 0, 0),
```
I am not clear with what is 
1) u32 version
2) How u32 version is initialized to HW_REVID(1, 0, 0, 0, 0, 0, 0)

---

### Post by Arndt on 2010-11-12
> **jamesbon said:**
> [http://lxr.free-electrons.com/source/drivers/net/8139too.c#L503](http://lxr.free-electrons.com/source/drivers/net/8139too.c#L503)
On above link a structure is defined
```
static const struct {
        const char *name;
        u32 version; /* from RTL8139C/RTL8139D docs */
        u32 flags;
}
```
in the structure there is a datatype 
```
u32 version 
```which is initialized as  ```
  HW_REVID(1, 0, 0, 0, 0, 0, 0),
```
I am not clear with what is 
1) u32 version
2) How u32 version is initialized to HW_REVID(1, 0, 0, 0, 0, 0, 0)

Somewhere in the code, there is probably some line looking like "typedef sometype u32;". And another line defining the macro HW_REVID. They are probably in some header file. Look for them.

---

### Post by jamesbon on 2010-11-13
Ok I looked at it as you wanted to tell.
```
typedef uint32_t u32;
```
and 
```
#define u32 unsigned int
```
So I understand the version is an unsigned int
Now
Line number 498 on same link

```
#define [HW_REVID]("http://lxr.free-electrons.com/ident?i=HW_REVID")(b30, b29, b28, b27, b26, b23, b22) \
        (b30<<30 | b29<<29 | b28<<28 | b27<<27 | b26<<26 | b23<<23 | b22<<22)
```is defining this macro.
So in this case the structure 
```

static const struct {
        const char *name;
        u32 version; /* from RTL8139C/RTL8139D docs */
        u32 flags;
} rtl_chip_info[] = {
        { "RTL-8139",
          HW_REVID(1, 0, 0, 0, 0, 0, 0),
          HasHltClk,
        },
```gets expanded to
```

static const struct {
        const char *name;
        u32 version; /* from RTL8139C/RTL8139D docs */
        u32 flags;
} rtl_chip_info[] = {
        { "RTL-8139",
[B] (b30, b29, b28, b27, b26, b23, b22) 
        (b30<<30 | b29<<29 | b28<<28 | b27<<27 | b26<<26 | b23<<23 | b22<<22) 
(1, 0, 0, 0, 0, 0, 0),
          [/B]HasHltClk,
        },
```

---

### Post by GeneralZod on 2010-11-14
> **jamesbon said:**
> gets expanded to
```

static const struct {
        const char *name;
        u32 version; /* from RTL8139C/RTL8139D docs */
        u32 flags;
} rtl_chip_info[] = {
        { "RTL-8139",
[B] (b30, b29, b28, b27, b26, b23, b22) 
        (b30<<30 | b29<<29 | b28<<28 | b27<<27 | b26<<26 | b23<<23 | b22<<22) 
(1, 0, 0, 0, 0, 0, 0),
          [/B]HasHltClk,
        },
```

No, it gets expanded to:

```

static const struct {
        const char *name;
        u32 version; /* from RTL8139C/RTL8139D docs */
        u32 flags;
} rtl_chip_info[] = {
        { "RTL-8139",
        **(1<<30 | 0<<29 | 0<<28 | 0<<27 | 0<<26 | 0<<23 | 0<<22)**, 
          HasHltClk,
        },
```

---

### Post by jamesbon on 2010-11-14
Ok that makes it clear.Thanks for helping out.

---

